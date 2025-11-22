
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

# 重要例題

# 大會考

1. $\int_{0}^{e-2}\ln(2+x) \ dx= \ ?$ 

Sol:
令 $t=2+x$，則 $dt=dx$。
$\int_{0}^{e-2}\ln(2+x) \ dx= \int_{2}^{e}\ln t  \, dt$ 
注意，這邊看起來很簡單，所以你可能會忘記要求反導函數而不是直接帶入！
利用 IBP，令 $u=\ln t，dv=dt$，則：
$\int_{2}^{e}\ln t \ dt=[t\ln t]^{e}_{2}-\int_{2}^{e}  \, dt=2-2\ln2$ 