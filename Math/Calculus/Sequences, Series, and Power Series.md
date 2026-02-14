
# Sequences

## Infinite Sequences

一個 $\{a_{1},a_{2},\dots\}$ 數列也可被寫成 $\{a_{n}\}$ 或 $\{a_{n}\}^{\infty}_{n=1}$。

## The Limit of a Sequence

一個數列可以通過每項係數呈現在數線上，也可以藉由圖像表示。

注意到數列 $\{a_{n}\}_{n=1}^{\infty}$ 是一個定義域為正整數的函數，所以其圖像應由離散的點構成。

若當 $n$ 越來越大時，可以使得 $a_{n}$ 越來越靠近 $L$，則數列 $\{a_{n}\}$ 的極限為 $L$ 且表示成：

$$
\lim_{ n \to \infty } a_{n}=L\quad\text{ or }\quad a_{n}\to L\text{ as }n\to \infty
$$

若 $\lim_{ n \to \infty }a_{n}$ 存在則稱該數列收斂，否則稱該數列發散。

一個更嚴謹的定義如下：若對任意 $\epsilon >0$ 都可以找到一個**整數** (注意到定義域必須為整數) $N$ 使得若 $n>N$ 則 $|a_{n}-L|<\epsilon$，則有 $\lim_{ n \to \infty }a_{n}=L$。

並且，我們如下定義無窮極限：若對任意正整數 $M$ 都可以找到一個整數 $N$ 使得若 $n>N$ 則 $a_{n}>M$，則有 $\lim_{ n \to \infty }a_{n}=\infty$。

## Properties of Convergent Sequences

對比第二章極限的定義，我們有以下發現。

若 $\lim_{ x \to \infty }f(x)=L$ 且當 $n$ 為整數時 $f(n)=a_{n}$，則 $\lim_{ n \to \infty }a_{n}=L$。

並且，當數列極限收斂時所有 Limit Laws 都可以被套用。

而且數列有一個很好用的性質，稱為 Power Law：若 $p>0$ 且 $a_{n}>0$ 則 $\lim_{ n \to \infty }(a_{n})^{p}=[\lim_{ n \to \infty }a_{n}]^{p}$。

還可以將夾擠定理套用到數列上：若當 $n\geq n_{0}$ 時 $a_{n}\leq b_{n}\leq c_{n}$，且 $\lim_{ n \to \infty }a_{n}=\lim_{ n \to \infty }c_{n}=L$，則 $\lim_{ n \to \infty }b_{n}=L$。

最後，我們有：若 $\lim_{ n \to \infty }|a_{n}|=0$ 則 $\lim_{ n \to \infty }a_{n}=0$。

proof:
使用 $\epsilon-N$ 定義證明。
已知 $\lim_{ n \to \infty }|a_{n}|=0$，所以對任意 $\epsilon>0$ 一定存在某整數 $N$ 使得：
當 $n>N$ 則 $||a_{n}|-0|<\epsilon$ 成立。
又有 $||a_{n}|-0|=||a_{n}||=|a_{n}|$，且 $|a_{n}-0|=|a_{n}|$，所以必定有：
當 $n>N$ 則 $|a_{n}-0|<\epsilon$ 成立。
$\implies \lim_{ n \to \infty }a_{n}=0$ By the definition of a limit.

並且我們還有最最後一個性質：若 $\lim_{ n \to \infty }a_{n}=L$ 且 $f$ 為一個連續函數，則：

$$
\lim_{ n \to \infty }f(a_{n})=\lim_{ n \to \infty } f(L)
$$

此節以一個結論收尾：

數列 $\{r^{n}\}$ 僅在 $-1<r\leq1$ 時收斂，否則發散。

$$
\lim_{ n \to \infty } {r^{n}}=\begin{cases}
0 & \text{if }-1<r<1 \\
1 & \text{if }r=1 
\end{cases}
$$

## Monotonic and Bounded Sequences

一個數列若對所有 $n\geq1$ 都有 $a_{n}<a_{n+1}$ 則稱為遞增，相反稱為遞減。若一個數列是遞增或遞減的，則其為單調 (Monotonic) 數列。

若存在一個數 $M$ 使得 $a_{n}\leq M \quad\forall n \geq1$ 則稱 $\{a_{n}\}$ 有上界。若存在一個數 $m$ 使得 $a_{n}\geq m\quad\forall n\geq1$ 則稱 $\{a_{n}\}$ 有下界。

注意到一個數列是單調的並無法保證數列收斂，而且一個有界的數列也無法保證收斂 (反例：$(-1)^{n}$)。

但是，一個單調有界的數列則必定收斂。此定理稱為**單調數列定理 (Monotonic Sequence Theorem)**。

設 $\{a_{n}\}$ 為遞增數列。因為 $\{a_{n}\}$ 有界，所以集合 $S=\{a_{n}|n\geq1\}$ 存在上界。根據完備性公理， $S$ 存在一個最小上界 $L$。
因為 $L$ 為最小上界，所以 $L-\epsilon$ 不是 $S$ 的上界，則必存在某數 $N$ 使得 $a_{N}>L-\epsilon$。
又因為 $\{a_{n}\}$ 為遞增數列，所以當 $n>N$ 時有 $a_{n}>a_{N}>L-\epsilon$。
因為 $L\geq a_{n}$，所以有 $0\leq L-a_{n}<\epsilon\implies|L-a_{n}|<\epsilon$ (當 $n>N$)。
也就是說，$\lim_{ n \to \infty }a_{n}=L$。
若 $\{a_{n}\}$ 為遞減數列，同理可證。

# Series

## Infinite Series

若我們將數列 $\{a_{n}\}_{n=1}^{\infty}$ 各項相加 $a_{1}+a_{2}+\dots$，我們將此稱為**無限級數(infinite series)**。並且表示為：

$$
\sum_{n=1}^{\infty}a_{n}\quad\text{ or }\quad\sum a_{n}
$$

其中，我們定義第 $n$ 個**部分和(partial sum)** 為級數前 $n$ 項相加。

若令 $s_{n}$ 為第 $n$ 個部分和，則：

$$
s_{n}=\sum_{i=1}^{n}a_{i}
$$

若數列 $\{s_{n}\}$ 收斂且 $\lim_{ n \to \infty }s_{n}$ 存在且為實數，則無限級數 $\sum a_{n}$ 收斂。並且我們寫成：

$$
a_{1}+a_{2}+\dots=s\quad\text{ or }\quad\sum_{n=1}^{\infty}a_{n}=s
$$

並且，若 $\{s_{n}\}$ 發散，則級數發散。

# Sum of a Geometric Series

無限級數中一個重要的例子就是**幾何級數(Geometric Series)**。

$$
a+ar+ar^{2}+{\dots}+ar^{n-1}+\dots=\sum_{n=1}^{\infty}ar^{n-1}\quad a\neq0
$$

其中級數和公式可以如下推導：

根據定義將部分和公式寫出：

$$
\begin{align}
 & s_{n}=a+ar+\dots+ar^{n-1} \\
 & rs_{n}=ar+\dots +ar^{n-1}+ar^{n} \\
 & \implies s_{n}-rs_{n}=a-ar^{n} \\
 & \implies s_{n}=\frac{a(1-r^{n})}{1-r}
\end{align}
$$

因為當 $-1<r<1$ 時 $\lim_{ n \to \infty }r^{n}=0$，所以有：

若 $|r|<1$ 時幾何級數收斂且和為：

$$
\sum_{n=1}^{\infty}ar^{n-1}=\lim_{ n \to \infty } \frac{a(1-r^{n})}{1-r}=\frac{a}{1-r}
$$

## Test for Divergence

回憶到若某級數對應的部分和數列發散，則該級數發散。

那麼我們有個定理：若級數 $\sum a_{n}$ 收斂，則 $\lim_{ n \to \infty }a_{n}=0$。

proof:
令 $s_{n}=a_{1}+\dots a_{n}$，則 $a_{n}=s_{n}-s_{n-1}$。
因為 $\sum a_{n}$ 收斂，所以 $\{s_{n}\}$ 收斂。
令 $\lim_{ n \to \infty }s_{n}=s$，因為當 $n\to \infty$ 時 $n-1\to \infty$，所以我們還有 $\lim_{ n \to \infty }s_{n-1}=s$。
所以：$\lim_{ n \to \infty }a_{n}=\lim_{ n \to \infty }(s_{n}-s_{n-1})=0$。

注意到，這個定理可以從左推到右，但不能從右推到左。也就是說 $\lim_{ n \to \infty }a_{n}=0$ 並**不能保證 $\sum a_{n}$ 收斂**。

雖之而來的，是另一個定理。若 $\lim_{ n \to \infty }a_{n}$ 不存在或 $\lim_{ n \to \infty }a_{n}\neq 0$，則級數 $\sum a_{n}$ 不收斂。

## Properties for Convergent Series

若級數 $\sum a_{n}$ 與 $\sum b_{n}$ 還有 $\sum ca_{n}$、$\sum(a_{n}\pm b_{n})$ 皆收斂，則

$$
\begin{align}
 & (i)\ \ \sum_{i=1}^{n}ca_{n}=c\sum_{i=1}^{n}a_{n} \\
 & (ii) \ \sum_{i=1}^{n}(a_{n}\pm b_{n})=\sum_{i=1}^{n}a_{n}\pm \sum_{i=1}^{n}b_{n}
\end{align}
$$

注意到：有限項不會影響到收斂與否的結果。

例如：$\sum_{i=2}^{\infty}a_{n}$ 收斂，則 $\sum_{i=1}^{\infty}=a_{1}+\sum_{i=2}^{\infty}$ 也必定收斂。

# The Integral Test and Estimates of Sums

## The Integral Test

假設 $f$ 在 $[1,\infty)$ 上連續、始終為正，且遞減。令 $a_{n}=f(n)$，則：
- 若 $\int_{1}^{\infty}f(x) \ dx$ 收斂，則 $\sum a_{n}$ 收斂。
- 若 $\int_{1}^{\infty}f(x) \ dx$ 發散，則 $\sum a_{n}$ 發散。

注意，對於 Integral Test，我們不需要從 $n=1$ 開始，就像之前計算狹積分那樣。

還有，$f$ 並不需要總是遞減的。我們只需要保證最終 $f$ 在 $n>N$ 時保證遞減即可。

我們定義 p-series 為 $\sum_{n=1}^{\infty} \frac{1}{n^{p}}$。而 p-series 在 $p>1$ 時收斂，在 $p\leq 1$ 時發散。

因為，對於 $p<1$，$\lim_{ n \to \infty } \frac{1}{n^{p}}=\infty$。又對於 $p= 0$，$\lim_{ n \to \infty } \frac{1}{n^{p}}=1$。根據 Test for Divergence，此二情況 p-series 發散。

或者，我們可以使用 integral test，對狹積分 $\int_{1}^{\infty} \frac{1}{x^{p}} \ dx$ 來說，當 $1-p<0\implies p>1$ 時收斂。

我們需要小心：$\sum a_{n}\neq \int_{1}^{\infty}f(x) \ dx$。

proof:
我們現在要證明若 $f$ 在 $[1,\infty)$ 上連續、始終為正，且遞減，則可以用狹積分的收斂與否判斷級數的收斂。
將 $f$ 劃分成 $n$ 份寬度為 $1$ 的間隔，利用右端點估計函數的積分值，會得到：$a_{2}+a_{3}+\dots+a_{n}\leq \int_{1}^{n}f(x) \ dx$。
利用左端點估計函數的積分，會得到 $a_{1}+a_{2}+\dots+a_{n-1}\geq \int_{1}^{n}f(x) \ dx$。
(i)
若 $\int_{1}^{\infty}f(x) \ dx$ 收斂，則有：$a_{2}+a_{3}+\dots+a_{n}\leq \int_{1}^{n}f(x) \ dx\leq \int_{1}^{\infty}f(x) \ dx$。
因為 $f\geq0$，所以 $s_{n}=a_{1}+\sum_{i=2}^{n}a_{i}\leq \int_{1}^{\infty}f(x) \ dx=M$。可知 $s_{n}$ 有上界。
又 $s_{n+1}=a_{n+1}+s_{n}\geq s_{n}$ 所以 $\{s_{n}\}$ 遞增。(非嚴格遞增也沒事)
根據單調有界定理，$\sum a_{n}$ 收斂。
(ii)
若 $\int_{1}^{\infty}f(x) \ dx$ 發散，則隨著 $n\to \infty$，$\int_{1}^{n}f(x) \ dx\to \infty$。
又有 $s_{n-1}=\sum_{i=1}^{n-1}a_{i}\geq \int_{1}^{n}f(x) \ dx$，所以當 $n\to \infty$ 時 $s_{n-1}\to \infty$。
這隱含了 $s_{n}\to \infty\text{ as }n\to \infty$。也就是 $\sum a_{n}$ 發散。

## Estimating the Sum of a Series

假設我們可以通過 Integration Test 知道級數 $\sum a_{n}$ 收斂，我們應該如何估計級數的值？

確實，我們使用 $s_{n}$ 做估計 (因為 $\lim_{ n \to \infty }s_{n}=s$)。但是，我們會想知道預估值與實際值差了多少 (remainder)。

令：

$$
R_{n}=s-s_{n}=a_{n+1}+a_{n+2}+\dots
$$

我們假設 $f$ 在 $[n,\infty)$ 上遞減，對比下圖中當 $x\geq n$ 時，長方形面積與函數底下面積的大小：

![[Pasted image 20260110214256.png]]

$$
R_{n}=a_{n+1}+a_{n+2}+\dots\leq \int_{n}^{\infty}f(x) \ dx
$$

類似地，我們還有：

![[Pasted image 20260110214458.png]]

$$
R_{n}=a_{n+1}+a_{n+2}+\dots\geq \int_{n+1}^{\infty}f(x) \ dx
$$

綜上所述，我們有了 Remainder Estimate for the Integral Test：假設 $f(k)=a_{k}$，其中當 $x\geq n$ 時 $f$ 恆正、連續且遞減。而且，$\sum a_{n}$ 收斂。若 $R_{n}=s-s_{n}$，則：

$$
\int_{n+1}^{\infty}f(x) \ dx \leq R_{n} \leq \int_{n}^{\infty}f(x) \ dx
$$

如果我們左右同加 $s_{n}$，可得：

$$
s_{n}+\int_{n+1}^{\infty}f(x) \ dx \leq s \leq s_{n}+\int_{n}^{\infty}f(x) \ dx
$$

這可以幫助我們預估實際值 $s$ 的上下界，讓我們得到更準確的預估值。

# Tips

- 遇到在正負間反覆橫跳的函數，考慮性質 $\lim_{ n \to \infty }|a_{n}|=\lim_{ n \to \infty }a_{n}$ (若 $a_{n}$ 收斂到 $0$)。
- $a^{n}-b^{n}=(a-b)(a^{n-1}+a^{n-2}b+a^{n-3}b^{2}+\dots+ab^{n-2}+b^{n-1})$ 
- partial fraction decomposition：$\frac{1}{i(i+1)}=\frac{1}{i}-\frac{1}{i+1}$ 

# 重要例題

收斂還是發散？
![[Pasted image 20260104162914.png]]

Sol:
寫的時候不知道發生啥了，竟然想成會不停震盪。
應該這樣寫：
$\lim_{ n \to \infty }|a_{n}|=\lim_{ n \to \infty } \frac{3^{n}}{n!}=\lim_{ n \to \infty } \frac{3\times \dots \times3}{1\times\dots \times n}=\lim_{ n \to \infty } \frac{3\times3\times 3}{1\times 2\times 3} \frac{3\times\dots \times3}{4\times\dots \times n}$ 
$=\lim_{ n \to \infty } \frac{9}{2} \frac{3\times \dots \times 3}{4\times \dots \times n}=\frac{9}{2}\cdot0=0$ 
所以 $\lim_{ n \to \infty }a_{n}=\lim_{ n \to \infty }|a_{n}|=0$ 。

![[Pasted image 20260104164927.png]]

Sol:
(a)
令 $\lim_{ n \to \infty }a_{n}=L$，則有：對任意 $\epsilon> 0$ 都存在一個正整數 $N$ 使得
若 $n>N$ 則 $|a_{n}-L|<\epsilon$。
對於 $a_{n+1}$，因為 $n+1>N+1>N$，所以 $|a_{n+1}-L|<\epsilon$ 恆成立。
也就是說 $\lim_{ n \to \infty }a_{n+1}=L=\lim_{ n \to \infty }a_{n}$。
(b)
令 $\lim_{ n \to \infty }a_{n}=L$，則 $\lim_{ n \to \infty } a_{n+1}= \frac{1}{1+L}$。
利用 (a)，有 $L=\frac{1}{1+L}\implies L= \frac{-1+ \sqrt{ 5 }}{2}$ (注意，負不合)

![[Pasted image 20260104172422.png]]

Sol:
利用歸納法證明。
當 $k=1$ 時：
$a_{2}=1$，所以 $0<a_{2}<a_{1}\leq2$ 成立。
設 $k=n$ 時 $0<a_{k+1}<a_{k}\leq2$ 成立。
考慮 $k=n+1$ 時：
$a_{k+1}<a_{k}\implies-a_{k+1}>-a_{k}\implies \frac{1}{3-a_{k+1}}< \frac{1}{3-a_{k}}$ (分母為正)
$\implies a_{k+2}<a_{k+1}$ 成立。
根據我們的假設，$0<3-a_{k+1}\leq2$ 成立 ($a_{k+1}\leq2$)，所以 $0<a_{k+2}<a_{k+1}\leq{2}$ 成立。
根據單調有界定理，此數列收斂。

![[Pasted image 20260104182213.png]]

Sol:
$\frac{b^{n+1}-a^{n+1}}{b-a}=b^{n}+b^{n-1}a+\dots+ba^{n-1}+a^{n}<b^{n}+b^{n}+\dots+b^{n}+b^{n}=(n+1)b^{n}$ 