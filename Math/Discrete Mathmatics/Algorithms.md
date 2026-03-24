# Algorithm

算法：由規則或步驟組成的集合，具有五種基本特性：
- 輸入：**零**或多個
- 輸出：**一**或多個
- **確切性(Definiteness)**：算法的每一步必須有確切定義
- **有限性(Finiteness)**：保證在執行**有限個**步驟後結束
- **可行性(Effectiveness)**：能夠精確運行，人可以用筆與紙做有限次運算完成

又有定義稱：算法是解決一個問題或計算的有限序列的準確指令。

提供兩種偽代碼風格：

![[Pasted image 20260323122739.png|805]]

![[Pasted image 20260323122758.png|799]]

# Search

## Linear Search

![[Pasted image 20260323123357.png|805]]

## Binary Search

前提：sorted

> [!error] 小心
> 下圖有誤，沒考慮 $x==a_{m}$ 的情況，導致無法找到答案。
> 應該 $\mathbf{if}\ x=a_{m}\ \mathbf{then}\ \mathbf{return}\ m$。

![[Pasted image 20260323123727.png|767]]

分析一下 worst case 需要的次數：

![[Pasted image 20260323124617.png|795]]

最差需要 $k+1$ 步，若輸入為 $n=2^{k}$，且夠大時可視為 $k$ 步。

$n=2^{k}\implies k=\log_{2} n$。

# Sorting

# Stable / Unstable

排序算法一定可以把數組排序，問題在於權重相同的項，是否可保持相對位置。

若權重相同的項保持排序前次序，則此算法稱**穩定排序(stable sorting)**。否則，稱 unstable sorting。

## In-place / Out-of-place

In-place：只需要**固定大小**的額外空間 $O(1)$。

> [!note]
> 不是不用額外空間喔。

Out-of-place：使用額外空間的大小隨輸入而不同。

![[Pasted image 20260323130737.png|707]]
## Bubble Sort

思想：對 $a_{i}$ 與 $a_{i+1}$ 兩兩比較排序，每回都找到待處理區域最大值並移動到待處理區末尾，所以下次迭代待處理區 $-1$。

![[Pasted image 20260323125557.png|829]]

> [!note]
> outer loop 在 $n-1$ 終止，因為 $n-1$ 時會對比 $a_{n-1}$ 與 $a_{n}$。

補充 swap 偽代碼：

![[Pasted image 20260323130044.png|447]]

## Insert Sort

思想：從 $j=2$ 開始，將 $a_{j}$ 插入已排序的 $a_{1},a_{2},\dots,a_{j-1}$ 的正確位置。

![[Pasted image 20260323215236.png|767]]

> [!note]
> 注意到 for 循環終止條件 $j-i-1$，因為 $k$ 從零開始。

# Greedy Algorithm

思想：專注於局部最佳解，可能無法找到全局最佳解。

現考慮如何使用最少步驟將密碼輪盤轉到給定密碼。

注意到，將密碼旋轉一圈回到原位需要轉 $10$ 次。所以，取 $\text{min}(\text{abs}(a-b),10-\text{abs}(a-b))$ 即可。

![[Pasted image 20260323220408.png|802]]

考慮：為 $m$ 元換幣，使用最少硬筆表達 $m$ 元。以下是可使用的單位 $\{ 1,2,5,10,20,50,100,200 \}$。

![[Pasted image 20260323220810.png|810]]

> [!warning] 注意
> 貪婪不是所有情況下都能找到最佳解，最佳解使用 dp。
> ![[Pasted image 20260323220952.png]]

# Halting Problem

問題：能否寫出判斷某程序是否會終止運行或無限循環的程序？

不能。

例如：哥德巴赫猜想：任意大於 $2$ 的整偶數都可寫成兩個質數相加。

我們如何證明無法寫出這樣的判斷程序？我們通過矛盾證明。

假設我們可寫出這樣的程序，如：

![[Pasted image 20260323221558.png|873]]

構建：

![[Pasted image 20260323221625.png|850]]

運行情況：

![[Pasted image 20260323221722.png]]

與前提矛盾。

# The Growth of Functions

我們需要一種複雜度表示法，因為：否則程序運行速度受電腦配置高低影響。

注意到輸入數據大小與運行時間的關係獨立於平台差異，這貌似是個好依據呦。

$O$ 總是考慮**最壞**情況下的複雜度，並且不考慮係數。

例如：$O(1000\log n+3n^{2}+2n+1)\implies O(n^{2})$，因為當 $n$ 足夠大時 $n^{2}>\log n$。

![[Pasted image 20260323224300.png|744]]

> [!warning] 注意
> $O(n!)$ 很快，只比 $O(n^{n})$ 慢。

Big-O 正式定義如下。

若存在實數 $c>0$ 與正整數 $n_{0}>0$ 使得：

$$
f(n)\leq cg(n)\quad\forall n\geq n_{0}
$$

則 $f(n)=O(g(n))$。

> [!note]
> ![[Pasted image 20260323224940.png]]

> [!warning] 注意
> 由精確定義得 $7n^{2}=O(n^{3})$。
> 取 $c=1$ 與 $n_{0}=8$ 即可。
> 注意到 $O$ 是集合關係，$O(1)\subseteq O(n)\subseteq O(n^{2})\subseteq\dots$。

嘗試證明 $n^{3}\neq O(n^{2})$。

Sol:
假設 $n^{3}=O(n^{2})$。
則有實數 $c>0$ 與正整數 $n_{0}>0$ 使得：
$n^{3}\leq cn^{2}\quad\forall n>n_{0}$。
對固定的 $c$ 與 $n_{0}$，若 $n>\text{max}(c,n_{0})$ 則有 $n>c$。
即 $n^{3}\geq cn^{2}\quad\forall n>\text{max}(c,n_{0})$，與假設矛盾。

> [!warning] 注意
> 取 $n>\text{max}(c,n_{0})$。
> 你可能會發現取 $n>c$ 就有矛盾，但我們必須證明 $n$ 同時還滿足前提條件。

嘗試用 Big-O 表示 $\log n!$。

Sol:
$n! = 1\times 2\times 3\times \dots \times n<n\times n\times n\times\dots \times n=n^{n}$ 
$\implies\log n!<\log n^{n}=n\log n$ 
取 $c=1$ 與 $n_{0}=1$，有：
$\log n!\leq n\log n\quad\forall n\geq1$ 

more example: 

![[Pasted image 20260323231137.png|830]]

> [!note]
> 套嵌一個常數次循環不會增加複雜度。

![[Pasted image 20260323231305.png|698]]

來個考試會考類型：

State the Big-O complexity of the function and prove it.

$$
f(n)=\log n+\frac{n}{2}+5
$$

Sol:
取 $g(n)=n$。
$f(n)=\log n+\frac{n}{2}+5\leq n+n+5n\quad\forall n\geq1$  
令 $c=7$，$n_{0}=1$，有：
$f(n)\leq cg(n)\quad\forall n\geq n_{0}$ 
所以 $f(n)=O(n)$。

> [!note]
> 注意答題模板。
> 第二行 $\forall n\geq1$ 條件。
> 取 $c$ 與 $n_{0}$ 的順序。
> 最終對 Big-O 的精確定義驗證。

Extended Example：

![[Pasted image 20260323232334.png|771]]

Sol:
假設 $n=2^{k}$ 
step 1.  $i=1=2^{0}$ 
step 2. $i=2=2^{1}$ 
step 3. $i=4=2^{2}$ 
...
step k. $i=2^{k-1}$ 
共迭代 $k$ 次。
若 $n=2^{k}$，則 $k=\log_{2}n$。
所以，時間複雜度為 $O(\log_{2}n)$。
若 $n\neq2^{m}$ for some $m$，則可找到一個正整數 $k$ 使得 $2^{k-1}<n<2^{k}$。
同理可得時間複雜度為 $O(\log_{2}n)$。

![[Pasted image 20260323234454.png|538]]

Sol:
假設 $n=k^{2}$，$k\in \mathbb{Z}^{+}$。
step 1.  $i=1\text{ and }1^{2}\leq k^{2}=n$ 
step 2. $i=2\text{ and }2^{2}\leq k^{2}=n$ 
step 3. $i=3\text{ and }3^{2}\leq k^{2}=n$ 
...
step $k$. $i=k\text{ and }k^{2}=n$ 
因為 $k^{2}=n$，所以 $k=\sqrt{ n }$，時間複雜度為 $O(\sqrt{ n })$。

![[Pasted image 20260323235021.png|713]]

Sol:
內層循環執行次數為：
$0 + 1n+2n+3n+\dots+(n-1)n=n(1+2+3+\dots+n-1)=n\cdot \frac{(n-1)n}{2}$ 
所以，時間複雜度為 $O\left( n\cdot \frac{(n-1)n}{2} \right)=O(n^{3})$。

![[Pasted image 20260323235344.png|330]]

Sol:
第一個循環執行 $n+1$ 次。
其中，$\text{count}=1+2+3+\dots+n= \frac{n(n+1)}{2}$。
所以，第二個循環執行 $\frac{n(n+1)}{2}$ 次。
所以，時間複雜度為 $O\left( n+1+ \frac{n(n+1)}{2} \right)=O(n^{2})$。

> [!note]
> 執行 $n+1$ 次，不是 $n$ 次。

# Review Insertion Sort

![[Pasted image 20260324000107.png|801]]

最佳情況：對已排序數組，時間複雜度為 $O(n)$。(不會進入 while 與 for 循環)

最差情況：對反序鏈錶 (插入時省去搬運，又或者數組搬運次數與比較次數相同)，需要 $0+1+2+\dots+(n-1)=\frac{1}{2}n^{2}-\frac{1}{2}n$ 次比較，時間複雜度為 $O(n^{2})$。

平均情況：時間複雜度 $O(n^{2})$，證明略。期中考出了就送給他吧。

# Complexity of Algorithms

![[Pasted image 20260324134515.png|737]]

上圖算法從最低算到最高。

執行 $2n$ 次乘法，$n$ 次加法。

![[Pasted image 20260324134537.png|750]]

上圖算法從最**高**算到最低。

執行 $n$ 次乘法與加法。

其原理為：

$$
\begin{align}
P(x) & =a_{n}x^{n}+a_{n-1}x^{n-1}+\dots+a_{1}x+a_{0} \\
 & =x(a_{n}x^{n-1}+a_{n-1}x^{n-2}+\dots+a_{1})+a_{0} \\
 & =(((a_{n}x+a_{n-1})x+a_{n-2})x+\dots+a_{1})x+a_{0}
\end{align}
$$

考慮線性查找的平均時間複雜度：

![[Pasted image 20260324135414.png|370]]

當 $x=a_{i}$ 時，需要 $2i+1$ 次比較 (`while` 裡 $2i$ 次，`if` $1$ 次)，而 $x=a_{1},a_{2},\dots,a_{n}$ 的機率都為 $\frac{1}{n}$。

所以，平均需要：

$\sum_{i=1}^{n}(2i+1)\left( \frac{1}{n} \right)=\frac{1}{n}\sum_{i=1}^{n}(2i+1)=\frac{1}{n}\left( 2\sum_{i=1}^{n}i+n \right)$ 
$=\frac{1}{n}\left( 2\cdot \frac{n(n+1)}{2} +n\right)=n+2$ 

那麼，平均時間複雜度為 $O(n)$。

![[Pasted image 20260324135914.png|724]]

