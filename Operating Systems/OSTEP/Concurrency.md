
# Introduction to Concurrency

單線程與多線程程序的地址空間是不同的，區別在單線程程序的棧存放在地址空間的底部，而多線程程序的棧則有多個，從地址空間底部向上排列。

線程的狀態需要保存在 TCB(Thread Control Block) 中，使得(線程的)上下文切換時可以將狀態轉移。

不同的是，進程的狀態保存在 PCB(Process Control Block) 中，上下文切換通過 PCB 轉移狀態。

線程與進程的上下文切換的差別在於，線程的上下文切換會保持地址空間不變，即不需要切換頁表。

## 共享數據

當兩個線程同時訪問全局變量時，就會發生**競態條件(race condition)**。

例如：創建兩個對 `counter` 遞增到 100 的線程，但是運行後 `counter` 的值可能小於 200。

Why? 讓我們使用彙編代碼看看，我們假設 `counter` 存放在位置 `0x8049a1c` 中。

``` asm
mov 0x8049a1c, eax
add $1, eax
mov eax, 0x8049a1c
```

若不幸的，線程 A 在運行完第二條代碼後遭遇時鐘中斷，切換到線程 B 。線程 B 比較幸運，完整運行完三行代碼並將 `eax` 的值 51 寫入了 `counter`。此時回到線程 A 運行，再次將運算的結果 51 寫入 `counter` ，導致兩次對 `counter` 的加法，只有一次真正作數。這就是一種經典的競態條件。

## 原子性願望

**同步原語(synchronization primitive)**：硬件提供的，可以用於在這些指令上構建一個通用集合的指令。

**臨界區(critical section)**：訪問共享資源的一段代碼，若多個線程大約同時進入臨界區就可能導致競態條件。

# 線程 API

## 線程創建

``` C
#include <pthread.h>
int pthread_create(
	pthread_t *thread,
	const pthread_attr_t *attr,
	void * (*start_routine)(void*),
	void *arg
);
```

## 等待線程

``` c
int pthread_join(pthread_t thread, void **value_ptr);
```

因為我們會修改 `value_ptr` 指針的內容，所以必須定義為指向指針的指針。

例子：

``` c
#include <pthread.h>

typedef struct myarg_t {
	int a;
	int b;
} myarg_t;

typedef struct myret_t {
	int x;
	int y;
} myret_t;

void *mythread(void *arg)
{
	myarg_t *m = (myarg_t *)arg;
	printf("%d %d \n", arg->a, arg->b);
	myret_t *r = malloc(sizeof(myret_t));
	r->x = 1;
	r->y = 2;
	return (void *)r;
}

int main()
{
	pthread_t p;
	myarg_t args;
	myret_t *m;
	args.a = 10;
	args.b = 20;
	pthread_creat(&p, NULL, mythread, &args);
	pthread_join(p, (void **)&a);
	printf("returned %d %d \n", m->x, m->y);
}
```

## 鎖

``` c
int pthread_mutex_init(pthread_mutex_t * mutex, const pthread_mutexattr_t * attr);
int pthread_mutex_lock(pthread_mutex_t *mutex);
int pthread_mutex_unlock(pthread_mutex_t *mutex);
int pthread_mutex_destroy(pthread_mutex_t *mutex);
```

我們可以如下創建並使用一個鎖：

``` c
pthread_mutex_t lock;    // 也可以直接使用 lock = PTHREAD_MUTEX_INITIALIZER 靜態初始化 (適用全局變量)
int rc;
rc = pthread_mutex_init(&lock, NULL);    assert(rc == 0);
rc = pthread_mutex_lock(&lock);    assert(rc == 0);
x += 1;
rc = pthread_mutex_unlock(&lock);    assert(rc == 0);
rc = pthread_mutex_destroy(&lock);    assert(rc == 0);
```

## 條件變量

``` c
int pthread_cond_wait(pthread_cond_t *cond, pthread_mutex_t *mutex);
int pthread_cond_signal(pthread_cond_t *cond);
```

`pthread_cond_wait()` 可以使線程修休眠，等待其他線程發出信號。

之所以 `pthread_cond_wait` 接受兩個參數而 `pthread_cond_signal` 僅接收一個，是因為 `pthread_cond_wait` 在令線程休眠時，需要釋放鎖以供其他線程使用。

以下為條件變量的例子：

``` c
/* thread 1 */
pthread_mutex_t lock = PTHREAD_MUTEX_INITIALIZER;
pthread_cond_t cond = PTHREAD_COND_INITIALIZER;
Pthread_mutex_lock(&lock);
while (ready == 0)
	Pthread_cond_wait(&cond, &lock);
Pthread_mutex_unlock(&lock);

/* thread 2 */
Pthread_mutex_lock(&lock);
ready = 1;
Pthread_cond_signal(&cond);
Pthread_mutex_unlock(&lock);
```

注意，在 `thread 1` 中我們使用 `while` 來判斷 `ready` 的值，這是因為休眠的線程可能被錯誤的喚醒，其實 `ready` 並未被設置。所以我們需要使用 `while` 重複確認。我們必須假設線程被喚醒總是可能因為事故發生。

## 編譯與運行

代碼必須包含 `pthread.h`，還必須鏈接 `pthread` 庫：

``` shell
gcc -o main main.c -lpthread
```