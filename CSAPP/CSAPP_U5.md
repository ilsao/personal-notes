
# 優化編譯器的能力和侷限性

編譯器只能對程序使用安全的優化。例如以下代碼：

``` C
void twiddle1(long *xp, long *yp) {
	*xp += *yp;![[A Way Out.url]]
	*xp += *yp;
}

void twiddle2(long *xp, long *yp) {
	*xp += 2 * (*yp);
}
```

以上兩函數看起來實現的功能相似。的確，當`*xp`與`*yp`指向兩個不同的內存地址時兩個函數的行為相同。但如果兩個指針指向相同的內存地址，則`twiddle1()`會把值翻4倍，而`twiddle2()`只會把值翻3倍。

這種兩個指針可能指向同一個內存位置的情況稱**內存別名使用(memory aliasing)**，會嚴重限制編譯器優化代碼性能。

還有一個妨礙優化的因素是函數調用，考慮以下代碼：

``` C
long f();

long func1() {
	return f() + f();
}

long func2() {
	return 2 * f();
}
```

直覺上可能會認為以上兩函數具有相同的行為，但是如果`f()`的結果跟隨其執行次數上升而有不同的執行結果時，二函數的返回值則會有所不同。

## 練習題

5.1

`*xp`與`*yp`的值都為0。

5.2

數學問題，此略。

# 表示程序性能

我們使用**每元素的周期數(Cycles Per Element, CPE)** 表示程序性能。

# 程序示例

我們定義一個向量數據結構：

``` C
typedef struct {
	long len;
	data_t *data;
}vec_rec, *vec_ptr;
```

其中，`data_t`是我們自行使用`typedef`定義出來的數據類型。

接著，我們定義一個函數，它的作用是對向量做一系列操作。之後都會針對這個函數進行一系列優化。

``` C
void combine1(vec_ptr v, data_t *dest) {
	long i;
	*dest = IDENT;
	for(i = 0; i < vec_length(v); i++) {
		data_t val;
		get_vec_element(v, i, &val);
		*dest = *dest OP val;
	}
}
```

對以上代碼在具有Intel Core i7 Haswell的參考機上測試，得到以下結果(單位為CPE)。

![[Pasted image 20250705172042.png]]

# 消除循環的低效率

在`combine1()`中，我們調用函數`vec_length()`作為`for`循環的邊界條件。由於向量的長度不會在此函數運行期間改變，所以每次循環都調用函數取得向量長度屬於浪費，我們將取得向量長度的代碼移動到循環外。

``` C
void combine2(vec_ptr v, data_t *dest) {
	long i;
	long length = vec_length(v);
	*dest = IDENT;
	for(i = 0; i < length; i++) {
		data_t val;
		get_vec_element(v, i, &val);
		*dest = *dest OP val;
	}
}
```

![[Pasted image 20250705172911.png]]

可以看到性能有了略微提升。我們稱這種優化**代碼移動(code motion)**

# 減少過程調用

`combine2`的代碼給次循環都調用`get_vec_element()`獲取元素，非常低效。我們新設計一個函數`get_vec_start()`作為替代，然後使用數組形式訪問數據。

``` C
void combine3(vec_ptr v, data_t *dest) {
	long i;
	long length = vec_length(v);
	data_t *data = get_vec_start(v);
	*dest = IDENT;
	for(i = 0; i < length; i++) {
		*dest = *dest OP data[i];
	}
}
```

![[Pasted image 20250705174224.png]]

可惜，這次改動反而讓性能變得更差。循環中的其他操作造成瓶頸，限制性能超過調用`get_vec_element()`。

# 消除不必要的內存引用

在`combine3`中，每次循環都需要從內存中讀取`*dest`的值。為了消除這種不必要的內存引用，我們引入一個臨時變量`acc`：

``` C
void combine4(vec_ptr v, data_t *dest) {
	long i;
	long length = vec_length(v);
	data_t *data = get_vec_start(v);
	data_t acc = IDENT;
	for(i = 0; i < length; i++) {
		acc = acc OP data[i];
	}
	*dest = acc;
}
```

![[Pasted image 20250705174847.png]]

這次程序性能有了顯著提升。

## 練習題

5.4

A. `%xmm0`在`-O2`中當累積者，在`-O1`中當臨時變量。

B. 是的。

C. 因為每次循環開頭讀取的值與循環末尾寫入的值相同，所以可以這樣變化。

# 理解現代處理器

有兩種下界限制了程序的最大性能：
1. 延遲界線(latnecy bound)：數據相關導致下一條代碼執行前，當前代碼必須先執行完。
2. 吞吐量界線(throughput bound)：處理器功能單元的原始計算能力。

## 整體操作

![[Pasted image 20250705223309.png]]

上圖示現代微處理器的簡化版示意圖。這種處理器稱為**超標量(superscalar)**，可以在一個時鐘周期內執行多個操作，而且是**亂序(out-of-order)** 的。

整個設計分為兩個部分：
1. **指令控制單元(Instruction Control Unit, ICU)**：從內存讀出指令序列，據此生成針對程序數據的基本操作。
2. **執行單元(Execution Unit, EU)**：執行ICU生成的操作。

ICU從**指令高速緩存(instruction cache)** 中讀取指令。通常ICU會在當前執行指令的很早之前取指，這樣它才有時間對指令譯碼並發送到EU。

當程序遇到分支，ICU使用一種稱為**分支預測(branch prediction)** 的技術。通過**投機執行(speculative execution)** ，處理器會在確定分支正確性前開始執行這些指令。如果之後發現預測錯誤，會將狀態重新設置道分支點的狀態，並取出正確的指令。標記為**Fetch Control**的塊包括分支預測，以確定取出那些指令。

**Insturction Decode** 接收程序指令，並將它們轉換成一組基本操作(或稱**微操作**)。

``` C
addq %rax, %rdx
```

以上代碼在典型x86實現中，會被轉化成一個操作。

``` C
addq %rax, 8(%rdx)
```

以上代碼則會被轉換成三個操作，一個讀內存值，一個將`%rax`與內存值相加，一個寫內存值。

EU接收來自取指單元的操作。這些操作被分派到**功能單元(Functional Units)** 中並執行實際操作。

讀寫內存由加載和存儲單元實現，通過**數據高速緩存(data cache)** 來訪問內存。

使用投機執行技術對操作求值，但結果暫時不會存放回寄存器或內存中。當分支操作送到EU，確定分支預測正確性後，若錯誤則丟棄計算結果，否則將數據寫回存儲器。

**算術運算(Arithmetic operations)** 塊通常不只一個，使得操作可以並行運行。

ICU中的**退役單元(retirement unit)** 控制著指令的結束。譯碼時，指令被放在對列中，直到分支預測正確而退役，或分支預測錯誤而被**清空(flushed)**，此時丟棄計算出來的結果。

控制操作數在執行單元間傳送的機制稱為**寄存器重命名(register renaming)**。

## 功能單元的性能

**延遲(latency)**：完成運算所需的總時間。

**發射時間(issue time)**：兩個同類型指令連續執行之間所需的最短周期數。

**容量(capacity)**：能執行該計算的功能單元數量。

**完全流水線化(fully pipelined)**：發射時間為1者。

**吞吐量**：發射時間的倒數。

## 練習題

5.5

A. $2n$次加法(答案說$n$次，我猜他省略了整數加法`i++`)，$2n$次乘法  

B. 循環中消耗最大的是`a[i] * xpwr`和`x * xpwr`，而這兩個乘法可以並行，占五個時鐘週期。而`result`和`x`沒有依賴關係，可以將加法放到下次迭代計算，所以CPE為5。

5.6

A. $n$次加法，$n$次乘法。

B. 此函數中`result`和`x`有先後依賴關係，不可將本次迭代的計算延遲到下次迭代計算。所以CPE為$5+3=8$。

C. 5.5沒有數據冒險。

# 循環展開

循環展開通過增加每次迭代計算元素的數量，減少循環迭代的次數。

循環展開從兩方面增進程序的性能：
1. 減少不直接參與結果計算的操作數量，例如循環索引計算或條件分支。
2. 循環展開提供一些方法進一步變化代碼，減少計算中關鍵路徑上的操作數量。

若將一個循環按任意因子$k$展開，稱$k\times 1$循環展開。

我們令向量長度為$n$，則此循環的上限應為$n-k+1$，且循環內對元素$i$到$i+k-1$應合併運算。每次迭代索引$i$加$k$。

由於最大循環索引$i+k-1$會小於$n$，所以我們需要第二個循環，每次循環處理一個元素直到最後。此循環會執行$0\sim k-1$次。

![[Pasted image 20250703161122.png]]

觀察上圖我們可以發現，這種變換只改進了整數加法的性能。

![[Pasted image 20250703161806.png]]

假設操作為`double`的乘法，每次操作需要從內存中加載一個數組元素並將這個值乘以累積值。

通過上圖我們可以觀察出，雖然關鍵路徑上迭代的次數減半，但是每次迭代中仍有兩個順序的乘法操作，這就是限制性寧提升的關鍵。

### 練習題

5.7

``` C
void combine5(vec_ptr v, data_t *dest) {
	long i;
	long length = vec_length(v);
	long limit = length - 4;
	data_t *data = get_vec_start(v);
	data_t acc = IDENT;

	/* Combine 5 element at a time */
	for (i = 0; i < limit; i += 5) {
		acc = (acc OP data[i]) OP data[i + 1];
		acc = (acc OP data[i + 2]) OP data[i + 3];
		acc = acc OP data[i + 4];
	}

	/* Finish any remaining elements */
	for (; i < length; i++) {
		acc = acc OP data[i];
	}
	*dest = acc;
}
```

# 提高並行性

由於我們將累積值放在單個變量中，在前面的計算完成前，都不能計算`acc`的新值，導致性能被限制。

## 多個累積變量

通過將偶數元素積累在`acc0`中，將奇數元素累積在`acc1`中，我們可以實現$2\times 2$循環展開。

``` C
void combine6(vec_ptr v, data_t *dest) {
	long i;
	long length = vec_length(v);
	long limit = length - 1;
	data_t *data = get_vec_start(v);
	data_t acc0 = IDENT;
	data_t acc1 = IDENT;

	/* Combine 2 element at a time */
	for (i = 0; i < limit; i += 2) {
		acc0 = acc0 OP data[i];
		acc1 = acc1 OP data[i+1];
	}

	/* Finish any remaining elements */
	for (; i < length; i++) {
		acc0 = acc0 OP data[i];
	}
	*dest = acc0 OP acc1;
}
```

![[Pasted image 20250707130328.png]]

上表可知我們打破了延遲界線，代表我們不需要延遲一個加法或乘法以等待上一個操作完成。

![[Pasted image 20250707130624.png]]

![[Pasted image 20250707130643.png]]

可以看到關鍵路徑上的操作減半，所以對比`combine5`和`combine6`可以發現CPE幾乎砍半。

我們可以通過將循環展開$k$次，並行$k$次得到$k \times k$循環展開。

通常，只有所有執行該操作的功能單元的流水線都是滿的時，程序才能達到吞吐量界線。

對延遲$L$，容量$C$的操作而言，要求循環展開因子$k \geq C \cdot L$。

例如，浮點乘有$C=2, \ L=5$，則循環因子為$k \geq 10$。

## 重新結合變換

考慮將`combine5`中的：

``` C
acc = (acc OP data[i]) OP data[i+1];
```

括號修改順序形成新函數`combine7`：

``` C
acc = acc OP (data[i] OP data[i+1]);
```

這種行為我們稱為**重新結合變換(reassociation transformation)**。

因為括號改變元素與累積值`acc`的合併順序，我們稱$2\times 1a$循環展開。

![[Pasted image 20250707144712.png]]

之所以會有這樣的提升是因為後者解除了數據依賴。

### 練習題

5.8 CPE = 5P/3

A1: 5.00

A2: 3.33

A3: 1.67

A4: 1.67

A5: 3.33

# 一些限制因素

## 寄存器溢出

如果我們的並行度$p$超過可用的寄存器數量，那麼編譯器會訴諸**溢出(spilling)**，將某些臨時值存放在內存中，通常在運行時堆棧上分配空間。

一旦編譯器必須訴諸溢出，那維護多個寄存器的優勢就可能會消失，使CPE上升。

## 分支預測和預測錯誤處罰

因為條件傳送指令可以被實現為普通指令流水線化處理，沒必要猜測條件是否滿足，所以沒有猜測錯誤處罰。

因為條件傳送指令不會改變PC，且現代處理器可以亂序執行，所以流水線可以先運行其他指令，等條件傳送指令計算完再執行該指令。

現在我們關心如何保證分支預測處罰不會阻礙程序效率？

1. 不用過分關心可預測的分支：例如可預測的邊界檢查
2. 書寫適合用條件傳送實現的代碼
	之前說過條件傳送指令不會因預測錯誤而受處罰。所以如果可以，我們想要用條件重送指令替代分支。即，使用**功能式**指令替代**命令式**指令。

``` C
void minmax1(long a[], long b[], long n) {
	long i;
	for (i = 0; i < n; i++) {
		if (a[i] > b[i]) {
			long t = a[i];
			a[i] = b[i];
			b[i] = t;
		}
	}
}

void minmax2(long a[], long b[], long n) {
	long i;
	for (i = 0; i < n; i++) {
		long min = a[i] < b[i] ? a[i] : b[i];
		long max = a[i] > b[i] ? a[i] : b[i];
		a[i] = min;
		b[i] = max;
	}
}
```

以上代碼`minmax2()`更容易被編譯成條件傳送指令。

### 練習題

5.9

``` C
long min = src1[i1] < src2[i2] ? src1[i1++] : src2[i2++];
dest[id++] = min;
```

# 理解內存性能

## 加載的性能

我們可以簡單編寫一系列互相依賴的加載操作來計算加載性能：

``` C
long list_len(list_ptr ls) {
	long len = 0;
	while(ls) {
		len++;
		ls = ls -> next;
	}
	return len;
}
```

``` C
.L3:
	addq $1, %rax
	movq (%rdi), %rdi
	testq %rdi, %rdi
	jne .L3
```

可以觀察出`movq`是循環中的性能瓶頸。後面的`%rdi`值都依賴於這個操作。在參考機上我們測得CPE為4.0，與參考機中L1級cache的4週期訪問時間一致。

## 存儲的性能

存儲操作不影響任何寄存器值，除非有加載操作否則不會產生數據相關。

![[Pasted image 20250707161330.png]]

由於`Example A`沒有產生**寫/讀相關(write/read dependency)** 所以CPE較小，CPE=1.3。

而`Example B`產生寫/讀相關所以CPE較大，CPE=7.3。

![[Pasted image 20250707162223.png]]

上圖是加載和存儲執行單元。

存儲單元包含一個**存儲緩衝區(store buffer)**，它包含已經被發射到存儲單元但還沒完成(包括更新數據高速緩存)存儲操作的地址和數據。

`write_read()`內循環匯編碼如下：

``` C
# src in %rdi, dst in %rsi, val in %rax
.L3:
	movq %rax, (%rsi)
	movq (%rdi), %rax
	addq $1, %rax
	subq $1, %rdx
	jne .L3
```

其中，`movq %rax, (%rsi)`被拆分成兩步：`s_addr`計算地址，並在存儲緩衝區創建該條地址目的條目。`s_data`設置該條目的數據。

![[Pasted image 20250707162826.png]]

`s_data`和`load`有數據相關，但是有條件：如果地址相同，`load`必須等`s_data`將數據放入緩衝區。如果地址不同，兩個操作可以獨立運行。

![[Pasted image 20250707163521.png]]

### 練習題

5.10

A. `a`全項左移

B. `a`全項被設為`a[0]`

C. B沒有寫/讀相關

D. CPE=1.2，因為沒有寫/讀相關，所以與A同

5.11

此次寫入的`p[i]`在`i`自增後，與下次的`p[i-1]`代表同一地址。產生寫/讀相關。

5.12

``` C
void psum(float a[], float p[], long n) {
	long i;
	p[0] = a[0];
	float tmp = a[0];
	for (i = 1; i< n; i++)
		tmp += a[i];
		p[i] = tmp;
}
```

# 確認和消除性能瓶頸

Unix系統提供一個程序**剖析(profiling)** 的工具GPROF。

我們需要為需要剖析的程序添加標誌`-Og`和`-pg`：

``` Bash
gcc -Og -pg prog.c -o prog
```

然後正常執行：

``` bash
./prog
```

它會產生一個文件`gmon.out`，且通常會運行的比正常慢2倍。

調用GPROF來分析`gmon.out`中的數據：

``` bash
gprof prog
```

需要注意，對於運行時間少於1秒的程序GPROF的計時不準確。