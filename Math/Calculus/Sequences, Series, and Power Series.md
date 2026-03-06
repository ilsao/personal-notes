
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

> [!error] 注意
> 想用洛必達解數列極限時，令函數 $f(x)$ 並在該函數上操作，而非直接對數列應用洛必達。
> 因為數列不連續 (因而不可微)，不能直接套用洛必達。

而且數列有一個很好用的性質，稱為 Power Law：**若 $p>0$ 且 $a_{n}>0$** 則 $\lim_{ n \to \infty }(a_{n})^{p}=[\lim_{ n \to \infty }a_{n}]^{p}$。

還可以將夾擠定理套用到數列上：若當 $n\geq n_{0}$ 時 $a_{n}\leq b_{n}\leq c_{n}$，且 $\lim_{ n \to \infty }a_{n}=\lim_{ n \to \infty }c_{n}=L$，則 $\lim_{ n \to \infty }b_{n}=L$。

> [!note]
> Squeeze Theorem 不一定要將整個數列夾住，只要在數列 $n>N$ 時夾住即可。

> [!warning] 注意
> 找到 $b_{n}$ 並夾住後，要先定義數列 $a_{n}$ 與 $c_{n}$ 才可套用數列的 Squeeze Theorem！

以及，若 $\lim_{ n \to \infty }a_{n}=L$ 且 $f$ 在 $L$ 連續，則：$\lim_{ n \to \infty }f(a_{n})=f(L)=f(\lim_{ n \to \infty }a_{n})$。

> [!warning] 注意
> 要先**寫出判定** $\lim_{ n \to \infty }a_{n}=L$ 且 $f$ 在 $L$ 連續，才可套用喔！

最後，我們有：若 $\lim_{ n \to \infty }|a_{n}|=0$ 則 $\lim_{ n \to \infty }a_{n}=0$。

proof:
(I)
使用 $\epsilon-N$ 定義證明。
已知 $\lim_{ n \to \infty }|a_{n}|=0$，所以對任意 $\epsilon>0$ 一定存在某整數 $N$ 使得：
當 $n>N$ 則 $||a_{n}|-0|<\epsilon$ 成立。
又有 $||a_{n}|-0|=||a_{n}||=|a_{n}|$，且 $|a_{n}-0|=|a_{n}|$，所以必定有：
當 $n>N$ 則 $|a_{n}-0|<\epsilon$ 成立。
$\implies \lim_{ n \to \infty }a_{n}=0$ By the definition of a limit.
(II)
使用 Squeeze Theorem
$0\leq a_{n}+|a_{n}|\leq2|a_{n}|$ 
$a_{n}=(a_{n}+|a_{n}|)-|a_{n}|$ 

> [!note]
> 其實關係是 $\lim_{ n \to \infty }|a_{n}|=0\iff \lim_{ n \to \infty }a_{n}=0$。

並且我們還有最最最後一個性質：若 $\lim_{ n \to \infty }a_{n}=L$ 且 $f$ 為一個連續函數，則：

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

> [!warning] 注意
> $\lim_{ n \to \infty }(a_{n}+b_{n})$ 只有兩個數列都收斂時才可套用 limit laws，若兩個數列都發散，也不可用 limit laws 斷定最終結果發散！

> [!note]
> 子數列發散 $\implies$ 原數列發散。

## Monotonic and Bounded Sequences

一個數列若對所有 $n\geq1$ 都有 $a_{n}<a_{n+1}$ 則稱為遞增，相反稱為遞減。若一個數列是遞增或遞減的，則其為單調 (Monotonic) 數列。

若存在一個數 $M$ 使得 $a_{n}\leq M \quad\forall n \geq1$ 則稱 $\{a_{n}\}$ 有上界。若存在一個數 $m$ 使得 $a_{n}\geq m\quad\forall n\geq1$ 則稱 $\{a_{n}\}$ 有下界。

有界則代表存在某數 $M>0$ 使得：$|a_{n}|\leq M$。 

但是，一個單調有界的數列則必定收斂。此定理稱為**單調數列定理 (Monotonic Sequence Theorem)**。

> [!warning] 注意
> 一個數列是單調的並無法保證數列收斂，而一個有界的數列也無法保證收斂 (反例：$(-1)^{n}$)。
> 話雖如此，但是收斂不一定需要單調。

proof:
核心想法：利用有界與完備性公理找到最小界，然後利用單調確保數值不能回退。
設 $\{a_{n}\}$ 為遞增數列。因為 $\{a_{n}\}$ 有界，所以集合 $S=\{a_{n}|n\geq1\}$ 存在上界。根據完備性公理， $S$ 存在一個上確界 $L$。
因為 $L$ 為上確界，所以 $L-\epsilon$ 不是 $S$ 的上界，則必存在某數 $N$ 使得 $a_{N}>L-\epsilon$。
又因為 $\{a_{n}\}$ 為遞增數列，所以當 $n>N$ 時有 $a_{n}>a_{N}>L-\epsilon$。
因為 $L\geq a_{n}$，所以有 $0\leq L-a_{n}<\epsilon\implies|L-a_{n}|<\epsilon$ (當 $n>N$)。
也就是說，$\lim_{ n \to \infty }a_{n}=L$。
若 $\{a_{n}\}$ 為遞減數列，同理可證。

> [!note]
> 此處題目可能要求判斷數列是否單調或遞增。
> 考慮單調性，我們可以通過對比 $a_{n}$ 與 $a_{n+1}$ 的大小關係得到。
> 考慮有界，如果數列極限存在則必有界。
> 因為 $\lim_{ n \to \infty }a_{n}=L$ 代表當 $n>N$ 時， $|a_{n}-L|<\epsilon\implies a_{n}\in(L-\epsilon,L+\epsilon)$。而當 $n\leq N$ 時，包含的項數有限 ($n$ 被限定為整數)，一定有最大最小值。

> [!note]
> 對於求解遞歸定義數列的極限，套用 $\lim_{ n \to \infty }a_{n}=\lim_{ n \to \infty }a_{n}+1$ (前提是先確定數列收斂，利用單調數列定理)。

> [!Note]
> 若給一遞歸定義數列與一有界範圍假設，可使用數學歸納法證明。

## Skills For Sequence Limits

1. Limit laws
2. Squeeze theorem
3. The $\epsilon-N$ definition
4. If $\lim_{ n \to \infty }|a_{n}|=0$，then $\lim_{ n \to \infty }a_{n}=0$ 
5. If $f(n)=a_{n}$, $\lim_{ x \to \infty }f(x)=L\implies \lim_{  n \to \infty }a_{n}=L$ 
6. The monotonic sequence theorem

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

若數列 $\{s_{n}\}$ 收斂且 $\lim_{ n \to \infty }s_{n}$ 存在且為實數，則無限級數 $\sum a_{n}$ 收斂。我們寫成：

$$
a_{1}+a_{2}+\dots=s\quad\text{ or }\quad\sum_{n=1}^{\infty}a_{n}=s
$$

並且，若 $\{s_{n}\}$ 發散，則級數發散。

> [!note] 
> 這邊若涉及到將求和展開，可以使用：$\frac{1}{n(n+1)}=\frac{1}{n}-\frac{1}{n+1}$。
> 或者更延伸的，將 $\frac{1}{f(x)p(x)q(x)}$ 拆成 $\frac{A}{f(x)}+\frac{B}{p(x)}+\frac{C}{q(x)}$。

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

**當 $|r|<1$ 時幾何級數收斂**且和為：

$$
\sum_{n=1}^{\infty}ar^{n-1}=\lim_{ n \to \infty } \frac{a(1-r^{n})}{1-r}=\frac{a}{1-r}
$$

> [!warning] 注意
> 對於 11.2 節的題目來說，涉及求無窮級數值的問題，通常都使用幾何級數解。
> 少部分題目要求將各項列出，互消後得出答案。(telescoping sum)

> [!note]
> 因為數列離散而無法微分，我們使用**差分**來研究數列的增長情況 (即相鄰兩項相減 $d_{n}=d_{n+1}-d_{n}$) 。
> 對於遞歸定義的數列，差分通常可以用來降階。通過表達差分間的關係，我們有機會還原原數列的某些關係。
> 
> 若
> - $d_{n}=d_{n-1}$ 數列是等差數列。
> - $d_{n}=rd_{n-1}$ 數列是等比 + 常數。
> 
> 最後，我們可以將 $a_{n}$ 表達成：$a_{n}=a_{1}+\sum_{k=1}^{n-1}d_{k}$。

## The Test for Divergence

> [!note]
> 若某級數對應的部分和數列發散，則該級數發散。 

我們有個定理：若級數 $\sum a_{n}$ 收斂，則 $\lim_{ n \to \infty }a_{n}=0$。

> [!note] Tip for proof
> 考慮將條件寫下：$\lim_{ n \to \infty }s_{n}=L$，想推得 $\lim_{ n \to \infty }a_{n}=0$。
> 思考 $s_{n}$ 如何轉 $a_{n}$？利用 $a_{n}=s_{n}-s_{n-1}$ 即可。

proof:
令 $s_{n}=a_{1}+\dots a_{n}$，則 $a_{n}=s_{n}-s_{n-1}$。
因為 $\sum a_{n}$ 收斂，所以 $\{s_{n}\}$ 收斂。
令 $\lim_{ n \to \infty }s_{n}=s$，因為當 $n\to \infty$ 時 $n-1\to \infty$，所以我們還有 $\lim_{ n \to \infty }s_{n-1}=s$。
所以：$\lim_{ n \to \infty }a_{n}=\lim_{ n \to \infty }(s_{n}-s_{n-1})=0$。

> [!warning] 注意
> 此定理可以從左推到右，但不能從右推到左。也就是說 $\lim_{ n \to \infty }a_{n}=0$ 並**不能保證 $\sum a_{n}$ 收斂**，因為 $\lim_{ n \to \infty }a_{n}=0$ 只能代表每項逐漸接近 $0$，但不代表趨近的足夠快。調和級數就是反例。

> [!note]
> 正因如此，此定理通常用在**證明某級數發散** ($\lim_{ n \to \infty }a_{n}\neq0$)，而非證明收斂。

雖之而來的，是另一個定理。(好吧，學完離散後就知道其實是 $\neg q\to \neg p$)

若 $\lim_{ n \to \infty }a_{n}$ 不存在或 $\lim_{ n \to \infty }a_{n}\neq 0$，則級數 $\sum a_{n}$ 不收斂。因為呀，每次加的數都是非零，怎麼可能收斂呢？

## Properties for Convergent Series

若級數 $\sum a_{n}$ 與 $\sum b_{n}$ 還有 $\sum ca_{n}$、$\sum(a_{n}\pm b_{n})$ 皆收斂，則

$$
\begin{align}
 & (i)\ \ \sum_{i=1}^{n}ca_{n}=c\sum_{i=1}^{n}a_{n} \\
 & (ii) \ \sum_{i=1}^{n}(a_{n}\pm b_{n})=\sum_{i=1}^{n}a_{n}\pm \sum_{i=1}^{n}b_{n}
\end{align}
$$

> [!note] 注意到：
> 有限項不會影響到收斂與否的結果。
> 例如：$\sum_{i=2}^{\infty}a_{n}$ 收斂，則 $\sum_{i=1}^{\infty}=a_{1}+\sum_{i=2}^{\infty}$ 也必定收斂。

# The Integral Test and Estimates of Sums

## The Integral Test

假設 $f$ 在 $[1,\infty)$ 上**連續**、**恆正**，且**遞減**。**令 $a_{n}=f(n)$**，則：
- 若 $\int_{1}^{\infty}f(x) \ dx$ 收斂，則 $\sum a_{n}$ 收斂。
- 若 $\int_{1}^{\infty}f(x) \ dx$ 發散，則 $\sum a_{n}$ 發散。

對於 Integral Test，我們不需要從 $n=1$ 開始，就像之前計算狹積分那樣。

> [!note]
> $f$ 並不需要總是遞減的。我們只需要最終 $f$ 在 $n>N$ 時保證遞減即可。

> [!warning] 注意
> 注意 The Integral Test 的適用前提。後續章節可以想辦法構建 The Integral Test 的適用條件。

我們定義 p-series 為 $\sum_{n=1}^{\infty} \frac{1}{n^{p}}$。而 p-series 在 $p>1$ 時收斂，在 $p\leq 1$ 時發散。

因為對於 $p<0$，$\lim_{ n \to \infty } \frac{1}{n^{p}}=\infty$。又對於 $p= 0$，$\lim_{ n \to \infty } \frac{1}{n^{p}}=1$。根據 Test for Divergence，此二情況 p-series 發散。若 $p>0$，當 $p=1$ 時極限發散。又 $\frac{1}{n^{p}}$ 顯然在 $[1,\infty)$ 上連續、恆正且遞減，我們可以使用 integral test。對狹積分 $\int_{1}^{\infty} \frac{1}{x^{p}} \ dx$ 來說，當 $1-p<0\implies p>1$ 時收斂。

> [!warning] 注意
> 雖然可以用 integral test 測試收斂，但$\sum a_{n}\neq \int_{1}^{\infty}f(x) \ dx$。

proof:
我們現在要證明若 $f$ 在 $[1,\infty)$ 上連續、始終為正，且遞減，則可以用狹積分的收斂與否判斷級數的收斂。
將 $f$ 劃分成 $n$ 份寬度為 $1$ 的間隔，利用右端點估計函數的積分值，會得到：$a_{2}+a_{3}+\dots+a_{n}\leq \int_{1}^{n}f(x) \ dx$。
利用左端點估計函數的積分，會得到 $a_{1}+a_{2}+\dots+a_{n-1}\geq \int_{1}^{n}f(x) \ dx$。
(i)
若 $\int_{1}^{\infty}f(x) \ dx$ 收斂，則有：$a_{2}+a_{3}+\dots+a_{n}\leq \int_{1}^{n}f(x) \ dx\leq \int_{1}^{\infty}f(x) \ dx$。
因為 $f\geq0$，所以 $s_{n}=a_{1}+\sum_{i=2}^{n}a_{i}\leq a_{1}+\int_{1}^{\infty}f(x) \ dx=M$。可知 $s_{n}$ 有上界。
又 $s_{n+1}=a_{n+1}+s_{n}\geq s_{n}$ 所以 $\{s_{n}\}$ 遞增。(非嚴格遞增也沒事)
根據單調有界定理，$\sum a_{n}$ 收斂。
(ii)
若 $\int_{1}^{\infty}f(x) \ dx$ 發散，則隨著 $n\to \infty$，$\int_{1}^{n}f(x) \ dx\to \infty$。
又有 $s_{n-1}=\sum_{i=1}^{n-1}a_{i}\geq \int_{1}^{n}f(x) \ dx$，所以當 $n\to \infty$ 時 $s_{n-1}\to \infty$。
這隱含了 $s_{n}\to \infty\text{ as }n\to \infty$。也就是 $\sum a_{n}$ 發散。

> [!note]
> 注意 Integral Test 條件。
> 如果遇到恆負遞增的情況，通過令 $b_{n}=-a_{n}$ 且對 $b_{n}$ 做測試一樣可解。
> 因為 $b_{n}$ 收斂 $\iff$ $a_{n}$ 收斂。

> [!note]
> 如果發現 $\lim_{ n \to \infty }s_{n}$ 不會求，考慮判斷一下是否發散吧！

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

> [!warning] 注意
> 是 $\geq$ 與 $\leq$ 喔，不是 $>$ 或 $<$。

## The Comparison Tests

## The Direct Comparison Test

若 $\sum a_{n}$ 與 $\sum b_{n}$ 為級數且**恆正**，則：

$$
\begin{align}
 & (i) \text{若 } \sum b_{n}\text{ 收斂且對所有 } n\text{ 都有 }a_{n}\leq b_{n}\text{，則} \sum a_{n}\text{ 也收斂。} \\
 & (i) \text{若 } \sum b_{n}\text{ 發散且對所有 } n\text{ 都有 }a_{n}\geq b_{n}\text{，則} \sum a_{n}\text{ 也發散。}
\end{align}
$$

proof:
(i)
令 $s_{n}=\sum_{i=1}^{n}a_{i}$，$t_{n}=\sum_{i=1}^{n}b_{i}$，$t=\sum_{i=1}^{\infty}b_{i}$。
$t_{n}\to t$ ，所以對任意 $n$ 都有 $t_{n}\leq t$。
又 $a_{n}\leq b_{n}\ \forall n$，所以 $s_{n}\leq t\ \forall n$。
又 $s_{n}$ 單調遞增，根據單調數列定理，$\sum a_{n}$ 收斂。
(ii)
此時 $t_{n}\to \infty$，又 $a_{n}\geq b_{n}\ \forall n$，所以 $s_{n}\to \infty$，$\sum a_{n}$ 發散。

使用 direct comparison test 時，我們對 $b_{n}$ 的選擇通常為：
- p-series
- 無窮等比級數

## Limit Comparison Test

當某待測級數比已知收斂級數稍大，或比已知發散級數稍小，就無法套用 direct comparison test。此時，可以嘗試 limit comparison test。

若 $\sum a_{n}$ 與 $\sum b_{n}$ 為級數且**恆正**，則：

若 $\lim_{ n \to \infty } \frac{a_{n}}{b_{n}}=c$ ，$\boxed{c>0}$ 且為有限數，則 $a_{n}$ 與 $b_{n}$ 會同時收斂或發散。

> [!warning] 注意
> 注意到 $c>0$。

若 $\lim_{ n \to \infty } \frac{a_{n}}{b_{n}}=0$ 且 $\sum_{n=1}^{\infty}b_{n}$ 收斂，則 $\sum_{n=1}^{\infty}a_{n}$ 收斂。

若 $\lim_{ n \to \infty } \frac{a_{n}}{b_{n}}=\infty$ 且 $\sum_{n=1}^{\infty}b_{n}$ 發散，則 $\sum_{n=1}^{\infty}a_{n}$ 發散。

proof:
我們只證第一種情況，後兩種情況留在作業證明。
令 $m$ 與 $M$ 為兩正數，且使得 $m<c<M$。
因為 $\lim_{ n \to \infty } \frac{a_{n}}{b_{n}}=c$，所以存在某數 $N$ 使得 $n>N$ 時有：$m< \frac{a_{n}}{b_{n}}<M$。
$\implies mb_{n}<a_{n}<Mb_{n}$ 
當 $\sum b_{n}$ 收斂時 $\sum Mb_{n}$ 也收斂，$\sum b_{n}$ 發散時 $\sum mb_{n}$ 也發散。所以，根據 direct comparison test 結論成立。

## Estimating Sums

若我們使用 direct comparison test 來證明 $\sum a_{n}$ 收斂，則我們可以通過比對二者來估計 $\sum a_{n}$。

令：

$$
\begin{align}
 & R_{n}=s-s_{n}=a_{n+1}+a_{n+2}+\dots \\
 & T_{n}=t-t_{n}=b_{n+1}+b_{n+2}+\dots
\end{align}
$$

因為 $\forall n$ 都有 $a_{n}\leq b_{n}$，所以 $R_{n}\leq T_{n}$。

若 $\sum b_{n}$ 是 p-series，則我們可使用 11.3 節的方法來預估。若是無窮等比級數，則可用 $\frac{a}{1-r}$ 計算。

# Alternating Series and Absolute Convergence

之前我們討論時，很多定理都只對恆正的級數作用。是時候處理點不是恆正的級數啦～

## Alternating Series

我們將一正一負反覆出現的級數為**交錯級數(alternating series)**。也就是其中每項的形式為：

$$
a_{n}=(-1)^{n}b_{n-1}\quad\text{ or }\quad a_{n}=(-1)^{n}b_{n}\quad\text{ where } b_{n}\text{ is a positive number }(|a_{n}|)
$$

我們使用 Alternating Series Test 檢測交錯級數的收斂與否：

若交錯級數：

$$
\sum_{n=1}^{\infty}(-1)^{n}b_{n}=-b_{1}+b_{2}-b_{3}+b_{4}-b_{5}+\dots\quad (b_{n}>0)
$$

滿足以下條件：

$$
\begin{align}
( & i)\ \  b_{n+1}\leq b_{n}\quad\forall n \\
(i & i)\ \lim_{ n \to \infty } b_{n}=0
\end{align}
$$

則此交錯級數收斂。

在開始證明前，我們先看看下圖。看起來確實會收斂到一個數 $s$ 哈。

![[Pasted image 20260305233957.png]]

proof:


> [!warning] 注意
> 書銘說 Q1 會考這個證明，記得讀喔！

## Estimating Sums of Alternating Series

## Absolute Convergence and Conditional Convergence

## Rearrangements

# Skills For Series Divergence Questions

1. The test for divergence
	1. $\sum a_{n}$ 收斂 $\implies \lim_{ n \to \infty }a_{n}=0$ (通常用在證明極限發散)
2. The integral test
	1. 條件：$f(x)$ 在 $[1,\infty)$ 上連續、恆正、遞減。
	2. 若 $a_{n}=f(n)$ 且 $\int_{1}^{\infty}f(x)\ dx$ 收斂，則 $\sum a_{n}$ 收斂。反之發散。
		1. 瑕積分可能需要使用 comparison 幫助求解。
3. 使用求和公式化簡級數，然後求 $n\to \infty$ 時的極限。
4. 當級數為幾何級數時，$|r|<1$ 時收斂。
5. p-series test，$p>1$ 時收斂。
6. 子序列發散，使得原序列發散。
7. Comparison Test
	1. p-series
	2. 無窮等比級數

# Tips

- 遇到在正負間反覆橫跳的函數，考慮性質 $\lim_{ n \to \infty }|a_{n}|=\lim_{ n \to \infty }a_{n}$ (若 $a_{n}$ 收斂到 $0$)。
- $a^{n}-b^{n}=(a-b)(a^{n-1}+a^{n-2}b+a^{n-3}b^{2}+\dots+ab^{n-2}+b^{n-1})$ 
- partial fraction decomposition：$\frac{1}{i(i+1)}=\frac{1}{i}-\frac{1}{i+1}$ 
- 數列收斂 $\implies$ 有界。

# 重要例題

收斂還是發散？
![[Pasted image 20260104162914.png]]

Sol:
寫的時候不知道發生啥了，竟然想成會不停震盪。注意到第二次寫也想成會不停震盪。
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
注意，不要想成求通項公式後取極限，因為嘗試後做不到。
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

Determine whether the series is convergent or divergent by expressing $s_{n}$ as a telescoping sum. If it is convergent, find its sum. $\sum_{n=2}^{\infty} \frac{1}{n^{3}-n}$ 

Sol:
令 $\frac{1}{n^{3}-n}= \frac{A}{n}+\frac{B}{n+1}+\frac{C}{n-1}$，通分解得 $A=-1, B=C=\frac{1}{2}$。
$s_{n}=\sum_{i=2}^{n} \frac{1}{i^{3}-i}=\sum_{i=2}^{n}\left( -\frac{1}{i}+\frac{1}{2}\cdot \frac{1}{i+1}+\frac{1}{2}\cdot \frac{1}{i-1} \right)$ 
$=\frac{1}{2}\sum_{i=2}^{n}\left( -\frac{2}{i}+\frac{1}{i+1}+\frac{1}{i-1} \right)$ (共提出 $\frac{1}{2}$，因為多乘 $2$ 在分子比乘 $2$ 在分母好算)
我們列出幾項看看：
$s_{n}=\frac{1}{2}[ \left( -1+\frac{1}{3}+1 \right)+\left( -\frac{2}{3}+\frac{1}{4}+\frac{1}{2} \right)+\left( -\frac{1}{2}+\frac{1}{5}+\frac{1}{3} \right)+\dots$ 
$+\left( -\frac{2}{n-2}+\frac{1}{n-1}+\frac{1}{n-3} \right)+\left( -\frac{2}{n-1}+\frac{1}{n}+\frac{1}{n-2} \right)+\left( -\frac{2}{n}+\frac{1}{n+1}+\frac{1}{n-1} \right) ]$ 
注意力驚人的你，肯定注意到了：第一項的第二位 + (第二項的第一位 + 第三項的第三位) 運算後等於零！
於是最後會化簡到 $\frac{1}{2}\left[ -1+1+\frac{1}{2}+\frac{1}{n}-\frac{2}{n}+\frac{1}{n+1} \right]=\frac{1}{4}-\frac{1}{2n}+\frac{1}{2n+2}$ 
於是 $\lim_{ n \to \infty }s_{n}=\frac{1}{4}$。

![[Pasted image 20260227162722.png]]
![[Pasted image 20260227162750.png]]

Sol:
這題當時我沒看出他是個等比數列，我好傻。
意識到這東西是個等比數列，且 $r=\frac{\sin x}{3}$。
想要級數收斂 $|r|<1$，也就是 $-1<\frac{\sin x}{3}<1$。不等式對 $\forall x$ 皆成立。
而無窮級數的值為 $\frac{a}{1-r}=\frac{3}{3-\sin x}$。

A sequence ${a_{n}}$ is defined recursively by the equation $a_{n}=\frac{1}{2}(a_{n-1}+a_{n-2})$ for $n\geq 3$, where $a_{1}$ and $a_{2}$ can be any real number. Find $\lim_{ n \to \infty }a_{n}$ in terms of $a_{1}$ and $a_{2}$ by expressing $a_{n+1}-a_{n}$ in terms of $a_{2}-a_{1}$ and summing a series.

Sol:
這題使用差分技巧。
看到遞歸，考慮使用 $\lim_{ n \to \infty }a_{n}=\lim_{ n \to \infty }a_{n+1}$。但是這裡顯然不能這樣用。
那便考慮差分吧，因為有 $a_{n}=a_{1}+\sum_{k=1}^{n-1}d_{k}$。
$d_{n}=a_{n+1}-a_{n}=\frac{1}{2}(a_{n}+a_{n-1})-a_{n}=-\frac{1}{2}(a_{n}-a_{n-1})\implies d_{n}=-\frac{1}{2}d_{n-1}$ 
那麼有 $\lim_{ n \to \infty }a_{n}=a_{1}+\sum_{k=1}^{\infty}d_{n}=a_{1}+ \frac{d_{1}}{1+\frac{1}{2}}=a_{1}+ \frac{a_{2}-a_{1}}{\frac{3}{2}}= \frac{a_{1}+2a_{2}}{3}$。

![[Pasted image 20260305154515.png]]

Sol:
這題可以幫助了解之前沒懂的部分。
注意到你雖然可以想說，以左端點開始算，會小於 $\int_{0}^{\infty}$，但注意到這邊錯誤地從 $0$ 開始算而非 $1$。
![[Pasted image 20260305154643.png]]根據上圖，可知：$\sum_{i=2}^{6}a_{i}<\int_{1}^{6}f(x)\ dx<\sum_{i=1}^{5}$。

![[Pasted image 20260305155641.png]]
收斂嗎？

Sol:
這題用來複習 Substitution Rule。
令 $f(x)$ 滿足 $f(n)=a_{n}$。
$\int_{1}^{\infty} \frac{\tan^{-1}x}{1+x^{2}}\ dx=\lim_{ t \to \infty }\int_{1}^{t} \frac{\tan^{-1}x}{1+x^{2}}\ dx$ 
令 $n=\tan^{-1}x$ 則 $dn=\frac{1}{1+x^{2}}\ dx$。
$\implies \lim_{ t \to \infty }\int^{\tan^{-1}t}_{\tan^{-1}1}u \ du=\left[ \frac{1}{2}u^{2} \right]^{\tan^{-1}t}_{\tan^{-1}1}=\frac{3\pi^{2}}{32}$ 
By the Integral Test，級數收斂。
這題有兩點要注意，首先是 substitution rule 的應用，其次是替換後積分上下界的改變。

![[Pasted image 20260305161513.png]]

Sol:
再複習一題 Integration by Parts。
令 $f(x)$ 滿足 $f(n)=a_{n}$。
$\lim_{ t \to \infty }\int_{2}^{t} \frac{\ln x}{x^{2}}\ dx$，令 $u = \ln x$ 則 $du=\frac{1}{x} \ dx$ 且 $x=e^{u}$。
$\implies \lim_{ t \to \infty }\int_{\ln2}^{\ln t}ue^{-u}\ du$ 使用 Integration by Parts
令 $k=u$，$dv=e^{-u}\ du$，則 $dk = du$，$v=-e^{-u}\ du$。
$\implies \lim_{ t \to \infty }\left( [-ue^{-u}]^{\ln t}_{\ln 2}+\int_{\ln 2}^{\ln t}e^{-u}\ du \right)=\frac{\ln2-1}{2}$ 
By the Integral Test, 級數收斂。

![[Pasted image 20260305171914.png]]
找到 $p$ 的範圍使級數收斂。

Sol:
因為上述東西在 $[1,\infty)$ 上連續、遞減、恆正，所以可以使用 Integral Test。
令 $f(x)$ 滿足 $f(n)=a_{n}$。
$\lim_{ t \to \infty }\int_{1}^{t} \frac{\ln x}{x^{p}} \ dx$ 令 $u=\ln x$ 則 $du=\frac{1}{x}\ dx$。
$\implies \lim_{ t \to \infty }\int_{\ln1}^{\ln t} \frac{u}{e^{(p-1)u}} \ du=\lim_{ t \to \infty }\left( \left[ \frac{e^{(1-p)u}u}{1-p} \right]^{\ln t}_{\ln 1}-\int_{\ln1}^{\ln t} \frac{e^{(1-p)u}}{1-p} \ du \right)$ 
$\implies$ 上述收斂，等於求 $\int_{\ln 1}^{\ln t} e^{(1-p)u} \ du$ 收斂，即，$\lim_{ u \to \infty } \frac{e^{(1-p)u}}{1-p}$ 收斂。
$\implies$ 對 $u\to \infty$，僅當 $1-p<0$ 時極限存在。
所以，$p>1$ 時級數收斂。

![[Pasted image 20260305180823.png]]

Sol:
$\int_{n+1}^{\infty} \frac{1}{x(\ln x)^{2}}\ dx\leq s-s_{n}\leq \int_{n}^{\infty} \frac{1}{x(\ln x)^{2}} \ dx$ 
我們要解 $\int_{n}^{\infty} \frac{1}{x(\ln x)^{2}} \ dx<0.01$ $[\text{substitution }u=\ln x]$ 
$\lim_{ t \to \infty }\int^{\ln t}_{\ln n}u^{-2} \ du=\lim_{ t \to \infty }\left( \frac{1}{\ln n}-\frac{1}{\ln t} \right)=\frac{1}{\ln n}<0.01$  
$\implies n>e^{100}$ 

![[Pasted image 20260305204022.png]]![[Pasted image 20260305204040.png]]

Sol:
(a)
觀察下圖，可知：$\sum_{i=1}^{n} \frac{1}{n}>\int_{1}^{n+1} \frac{1}{x} \ dx$。其實所求就是長方形區域扣掉曲線下面積。
又 $\int_{1}^{n+1} \frac{1}{x} \ dx=\ln(n+1)>\ln n$，所以有：$t_{n}=1+\frac{1}{2}+\frac{1}{3}+\dots+\frac{1}{n}-\ln n>0$。
![[Pasted image 20260305204228.png]]
(b)
我們將 $t_{n}-t_{n+1}$ 視為整塊弧形面積剪掉下面的長方形。
因為 $\int_{n}^{n+1} \frac{1}{x} \ dx=[\ln(n+1)-\ln n]$，所以再減去小長方形面積就是：$[\ln(n+1)-\ln n]- \frac{1}{n+1}$。
且因為 $t_{n}-t_{n+1}>0$，所以此級數單調遞減。
![[Pasted image 20260305204345.png]]
(c)
由於函數單調遞減，且恆正，所以級數 $0<t_{n}<t_{1}=1$ 有界。
由 M.S.T.，級數收斂。

# 大會考

![[Pasted image 20260302200648.png]]

Sol:
剛看到題你可能很矇逼，但轉念一想下面那東西跟 $x$ 是不是一模一樣？
於是設：$x=\frac{1}{4+x}\implies x=2\pm \sqrt{ 5 }$，又 $x>0$ 所以負不和。

![[Pasted image 20260302201611.png]]

Sol:
注意到：$a_{n+1}=\sqrt{ 3a_{n} }$。
令 $\lim_{ n \to \infty }a_{n}=L$，則 $L=\sqrt{ 3L }\implies L=0\text{ or }3$，$0$ 不合。

![[Pasted image 20260302202330.png]]

Sol:
利用差分。
$a_{n+1}-a_{n}=-\frac{1}{3}(a_{n}-a_{n-1})\implies d_{n}=-\frac{1}{3}d_{n-1}=\left( -\frac{1}{3} \right)^{n-1}d_{1}$ 
$a_{n}=a_{1}+\sum_{i=1}^{n-1}d_{i}$ 
$\implies \lim_{ n \to \infty }a_{n}=\frac{a}{1-r}=\frac{1}{1+\frac{1}{3}}=\frac{3}{4}$ 

![[Pasted image 20260302203408.png]]

Sol:
(a)
令 $b_{n}=\ln a_{n}=n\ln\left( 1+\frac{2}{n} \right)$ 
這邊我們想用洛必達，當好 $\ln$ 裡面有個 $n$ 在分母，想辦法把它換出來。
令 $x_{n}=\frac{2}{n}$，則 $x_{n}\to0\text{ as }n\to \infty$。
此時 $\lim_{ x_{n} \to 0}b_{n}=2\cdot \frac{\ln(1+x)}{x}=2$ 。
因為 $a_{n}=e^{b_{n}}$，所以 $\lim_{ n \to \infty }a_{n}=\lim_{ n \to \infty }e^{b_{n}}=e^{2}$ 收斂。
(d)
看到有除法，我們可以通過相鄰兩相相除將除法消除。
$\frac{a_{n+1}}{a_{n}}=\frac{n+1}{2}$，當 $n\to \infty$ 時乘法因子不收斂，所以整體不收斂。

![[Pasted image 20260302205020.png]]

Sol:
(b)
在嘗試解 (d) 時會解出 $L=1\text{ or }4$，那我們假設 $1\leq a_{n}\leq4$。
使用歸納法證明。
當 $k=0$ 時顯然成立。
假設當 $k=n$ 時命題成立。
則當 $k=n+1$ 時，因為 $1\leq a_{n}\leq4\implies \frac{1}{4}\leq \frac{1}{a_{n}}\leq1\implies 1\leq \frac{4}{a_{n}}\leq4$，所以根據 M.I. 命題成立。
(a)
如果想直接推很難，因為我們不清楚這數列的界。
但是先從 (b) 下手就好過多了。
$a_{n+1}-a_{n}= \frac{-(a_{n}-1)(a_{n}-4)}{a_{n}}>0$ (由 $1\leq a_{n}\leq 4$)
(c) 顯然錯誤
(d)
根據單調數列定理，數列收斂。
設 $\lim_{ n \to \infty }a_{n}=L$，則 $L=5-\frac{4}{L}\implies L=1\text{ or }4$ 但又數列遞增且 $a_{0}=2$，$1$ 不合所以 $L=4$。

![[Pasted image 20260302221128.png]]

Sol:
注意這題套用 comparison test 的範圍。
本來我笨笨的選 (A)，但是沒想到有反例：$a_{n}=\frac{1}{n^{2}}$，$b_{n}=-\frac{1}{n}$。
我們看 (C)，這保證了 $0\leq|b_{n}|\leq|a_{n}|$，利用 comparison test 保證 $b_{n}$ 收斂。