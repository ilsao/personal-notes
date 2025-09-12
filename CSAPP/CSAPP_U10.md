
# Unix I/O

在 Unix 類系統中，所有I/O設備都被抽象成文件。

打開文件：要求內核打開文件，並宣告想要訪問某I/O設備。內核會返回一個描述符來標示此文件。

Linux Shell 創建的進程在開始時會默認打開三個文件，標準輸入、輸出、錯誤。描述符分別為$0\sim{2}$。`<unistd.h>`定義了常量`STDIN_FILENO, STDOUT_FILENO, STDERR_FILENO`來表示這幾個數字。

# 文件相關函數

> [!NOTE] `size_t` 和 `ssize_t` 的差別
> `size_t` 被定義為 `unsigned long`， `ssize_t` 被定義為 `long`

`open()`

`close()`

`read()`

`write()`

`lseek()`

# 讀取文件元數據

`stat()`

`fstat()`

# 讀取目錄內容

`opendir()`

`readdir()`

`closedir()`

# 共享文件

內核是這樣表示打開的文件的：
- 描述符表：每個進程獨立，以進程打開的文件描述符為索引，每項指向文件表的一個表項。
- 文件表：所有進程共享，包含當前文件位置，引用記數，以及指向v-node表的指針。
- v-node表：所有進程共享，每項包含 `stat` 結構中的大多數信息。

![[Pasted image 20250810154313.png]]

上圖展示了兩個文件描述符通過兩個打開文件表項共享同一個磁盤文件。

# I/O 重定向

`dup2(int oldfd, int newfd)` 通過將 `oldfd` 描述符複製到 `newfd` 描述符項來將 `newfd` 重定向到 `oldfd`。

![[Pasted image 20250810154758.png]]

## 練習題

10.2

c = f

10.3

c = o

10.4

`dup2(5, STDIN_FILENO);`

10.5

c = o