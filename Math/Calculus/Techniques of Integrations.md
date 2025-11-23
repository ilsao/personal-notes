
在章首我們列出我們學過的不定積分值。

![[Pasted image 20251121210001.png]]

# Integration by Parts

## Integration by Parts: Indefinite Integrals

下式為 integration by parts 的公式：

$$
\int f(x)g'(x)=f(x)g(x) - \int f'(x)g(x)
$$

proof:
$\frac{d}{dx}[f(x)g(x)]=f'(x)g(x)+f(x)+g'(x)$ 
$f(x)g(x)=\int[f'(x)g(x)+f(x)g'(x)]=\int f'(x)g(x)+\int f(x)g'(x)$ 
$\implies \int f(x)g'(x)=f(x)g(x)-\int f'(x)g(x)$ 

或者，令 $u=f(x),v=g(x)$ 我們可以寫成：

$$
\int u \ dv=uv-\int v \ du
$$

注意 $f(x)$ 與 $g(x)$ 的選擇。我們應選擇微分後 $f'(x)$ 會比 $f(x)$ 簡單，且可以輕易從 $g'(x)$ 找出 $g(x)$ 者，這樣才能化簡式子。

你可能會困惑，什麼時候使用 Integration by Parts，什麼時候用 Substitution Rule？

我們這樣分類：
- Substitution Rule：一個函數包著另一個函數，旁邊還有他的導數。
- Integration by Parts：互不相干的函數相乘。

有的時候你可能 IBP 一次，發現誒？問題沒有變簡單，也沒有變複雜誒～這個時候不要慌，咱們在 IBP 一次，可能會發現回到了原來的問題。這個時候移項就是答案啦！

Ex: Evaluate $\int e^{x}\sin x \ dx$. 

發現不管選誰好像都沒用，那就直接 $u=e^{x}, dv=\sin x \ dx$。
$\int e^{x}\sin x \ dx=-e^{x}\cos x + \int e^{x}\cos x \ dx$ 
好勒，再 IBP 一次，咱就不信了！
取 $u=e^{x}, dv=\cos \ dx$。
$\int e^{x}\cos x \ dx=e^{x}\sin x - \int e^{x}\sin x \ dx$ 
代回得：$\int e^{x}\sin x \ dx=-e^{x}\cos x + e^{x}\sin x - \int e^{x}\sin x \ dx$ 
$\implies2\int e^{x}\sin x \ dx=e^{x}(\sin x-\cos x)$ 
$\implies \int e^{x}\sin x \ dx=\frac{1}{2}e^{x}(\sin x-\cos x)+C$

## Integration by Parts: Definite Integrals

$$
\int_{a}^{b}f(x)g'(x) \ dx=f(x)g(x)|^{b}_{a}-\int_{a}^{b}f'(x)g(x) \ dx
$$

## Reduction Formulas

喔沒有啦，這邊只是要讓我們證明一個等式：

$$
\int \sin^{n}x \ dx=-\frac{1}{n}\cos x\sin^{n-1}x+ \frac{n-1}{n}\int \sin^{n-2}x \ dx
$$

其中，$n\geq 2$ 且為整數。

proof:
取 $u=\sin^{n-1}x$，$dv=\sin x \ dx$。
$\int \sin^{n}x \ dx=-\cos x\sin^{n-1}x + (n-1)\int \sin^{n-2}x\cos^{2} x \ dx$  ($\cos^{2}x=1-\sin^{2} x$)
$=-\cos x\sin^{n-1}x+(n-1)\int \sin^{n-2}x \ dx-(n-1)\int \sin^{n}x \ dx$ 
$\implies n\int \sin^{n}x \ dx=-\cos x\sin^{n-2}x+(n-1)\int \sin^{n-1}x$ 
$\implies \int \sin^{n}x \ dx=-\frac{1}{n}\cos x\sin^{n-1}x+ \frac{n-1}{n}\int \sin^{n-2}x$ 

這個公式非常有用，因為它可以把 $\int\sin^{n}x\ dx$ 化簡為 $\int \sin x \, dx$ ($n$ 為奇數) 或 $\int  \, dx$ ($n$ 為偶數)。

# Trigonometric Integrals

## Integrals of Powers of Sine and Cosine

對於計算 $\int \sin^{m}x\cos^{n}x \ dx$，我們有如下策略：

(a)

若 $n$ 為奇數 $2k+1$，則留下一個 cosine 並使用 $\cos^{2}x=1-\sin^{2}x$ 替代剩下的 cosine。最後使用 $u=\sin x$ 代換。($du=\cos x\ dx$)

$\int \sin^{m}x\cos^{2k+1}x \ dx=\int\sin^{m}x(\cos^{2})^{k}\cos x=\int\sin^{m}x(1-\sin^{2})^{k}\cos x \ dx$ 

(b)

若 $m$ 為奇數 $2k+1$，同理可得。

注：若 $m$ 與 $n$ 都是奇數，則 (a) 或 (b) 隨便你愛用啥用啥。

(c)

若 $m$ 與 $n$ 都是偶數，則使用半角公式。

$$
\sin^{2}x=\frac{1}{2}(1-\cos2x)\quad\cos^{2}x=\frac{1}{2}(1+\cos 2x)
$$

或者使用：

$$
\sin x\cos x=\frac{1}{2}\sin2x
$$

## Integrals of Powers of Secant and Tangent

對於計算 $\int \tan^{m}x\sec^{n}x \ dx$，我們有以下策略：

(a)

若 $n=2k$ 為偶數且 $k\geq2$，則保留 $\sec^{2}x$ 並利用恆等式 $\sec^{2}x=\tan^{2}x+1$ 代替剩下的 secant。最後使用 $u=\tan x$ 代換。($du=\sec^{2}x \ dx$)

(b)

若 $m=2k+1$ 為奇數，則保留 $\sec x\tan x$，並利用恆等式代替剩下的 tangent。最後使用 $u=\sec x$ 代換。($du = \sec x\tan x \ dx$)

(c)

若存在偶數個 tangent 與奇數個 secant，將 tangent 全部換成 secant，然後使用 Integration By Parts。

有時後，我們會需要使用以下兩條式子幫助求解：

$$
\int \tan x \, dx = \ln|\sec x|+C
$$

$$
\int \sec x \, dx = \ln|\tan x+\sec x|+C
$$

最後，$\int \cot^{m}x\csc^{n}x \ dx$ 可以使用類似的方法求解。($1+\cot^{2}x=\csc^{2}x$)

## Using Product Identities

若想解：
(a) $\int \sin mx\cos nx \ dx$
(b) $\int \sin mx\sin nx \ dx$ 
(c) $\int \cos mx\cos nx \, dx$ 

以下的公式對求解三角函數積分非常有用，而我之前從未學過：

(a)

$$
\sin A\cos B=\frac{1}{2}[\sin(A-B)+\sin(A+B)]
$$

(b)

$$
\sin A\sin B=\frac{1}{2}[\cos(A-B)-\cos(A+B)]
$$

(c)

$$
\cos A\cos B=\frac{1}{2}[\cos(A-B)+\cos(A+B)]
$$

# 重要例題

# 大會考

1. $\int_{0}^{e-2}\ln(2+x) \ dx= \ ?$ 

Sol:
令 $t=2+x$，則 $dt=dx$。
$\int_{0}^{e-2}\ln(2+x) \ dx= \int_{2}^{e}\ln t  \, dt$ 
注意，這邊看起來很簡單，所以你可能會忘記要求反導函數而不是直接帶入！
利用 IBP，令 $u=\ln t，dv=dt$，則：
$\int_{2}^{e}\ln t \ dt=[t\ln t]^{e}_{2}-\int_{2}^{e}  \, dt=2-2\ln2$ 