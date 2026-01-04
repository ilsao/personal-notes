
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

# Tips

- 遇到在正負間反覆橫跳的函數，考慮性質 $\lim_{ n \to \infty }|a_{n}|=\lim_{ n \to \infty }a_{n}$ (若 $a_{n}$ 收斂)。
- $a^{n}-b^{n}=(a-b)(a^{n-1}+a^{n-2}b+a^{n-3}b^{2}+\dots+ab^{n-2}+b^{n-1})$ 

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