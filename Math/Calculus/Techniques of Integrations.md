
在章首我們列出我們學過的不定積分值。

![[Pasted image 20251121210001.png]]

# Integration by Parts

## Integration by Parts: Indefinite Integrals

下式為 integration by parts 的公式：

$$
\int f(x)g'(x)=f(x)g(x) - \int f'(x)g(x)
$$

proof:
$\frac{d}{dx}[f(x)g(x)]=f'(x)g(x)+f(x)g'(x)$ 
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
\int \cot x \ dx=\ln|\csc x|+C
$$

$$
\int \sec x \, dx = \ln|\sec x+\tan x|+C
$$

$$
\int \csc x \ dx=-\ln|\csc x+\cot x|+C
$$

最後，$\int \cot^{m}x\csc^{n}x \ dx$ 可以使用類似的方法求解。($1+\cot^{2}x=\csc^{2}x$)

## Using Product Identities

若想解：
(a) $\int \sin mx\cos nx \ dx$
(b) $\int \sin mx\sin nx \ dx$ 
(c) $\int \cos mx\cos nx \, dx$ 

以下的公式對求解三角函數積分非常有用，而我之前從未學過(二評：好難背啊啊啊，三評：根本背不起來... )：

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

# Trigonometric Substitution

這邊你需要先知道一下 inverse substitution：對於給定的 $\int f(x) \ dx$ 找 $\int f(g(t))g'(t) \, dt$ 的行為。

想尋找 inverse substitution，我們必須令 $g$ 的反函數存在，也就是說 $g$ 是一個 one-to-one function。

下表展示了一些有用的 trigonometric substitution：

| Expression             | Substitution                                                                                                                                                                                                        | Identity                           |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------- |
| $\sqrt{ a^{2}-x^{2} }$ | $x=a\sin \theta\quad -\frac{\pi}{2}\leq \theta\leq \frac{\pi}{2}$                                                                                                                                                   | $\cos^{2}\theta=1-\sin^{2}\theta$  |
| $\sqrt{ a^{2}+x^{2} }$ | $x=a\tan \theta\quad -\frac{\pi}{2}\leq \theta\leq \frac{\pi}{2}$                                                                                                                                                   | $\sec^{2}\theta=1+\tan^{2} \theta$ |
| $\sqrt{ x^{2}-a^{2} }$ | $x=a\sec \theta\quad 0\leq \theta< \frac{\pi}{2}\text{ or } \pi\leq \theta< \frac{3\pi}{2}$ <br>注意此處 $\theta$ 的選擇，因為根號開出來必須要大於零，所以 $0\leq \theta\leq \pi$ 不可行。<br>($\tan \theta$ 在 $\frac{\pi}{2}<\theta<\pi$ 時小於零) | $\tan^{2}\theta=1-\sec^{2}\theta$  |

誒，但別寫魔怔了，看到啥就帶啊！萬一普通的 substitution 更簡單呢？

# Integration of Rational Function by Partial Fractions

## The Method of Partial Fractions

當給定 $f(x)= \frac{P(x)}{Q(x)}$，如果 $\text{deg}(P)\geq\text{deg}(Q)$ 則將 $f(x)$ 表示成：

$$
f(x)=\frac{P(x)}{Q(x)}=S(x)+\frac{R(x)}{Q(x)}
$$

如果 $Q(x)$ 可以被因式分解，則將其盡可能的分解。$Q(x)$ 一定可以被分解成線性 ($ax+b$) 與二次 ($ax^{2}+bx+c$，$b^{2}-4ac<0$) 的乘積。(非實數根共軛出現)

然後，將 $\frac{R(x)}{Q(x)}$ 化成 partial fractions 的形式：

$$
\frac{A}{(ax+b)^{i}}\text{ or } \frac{Ax+B}{(ax^{2}+bx+c)^{j}}
$$

很矇逼吧～沒關係，我們分幾種情況討論：

### CASE I: The denominator  $Q(x)$ is a product of distinct linear factors

此情況下 $Q(x)$ 可以被分解成 $Q(x)=(ax_{1}+b_{1})(ax_{2}+b_{2})\dots(ax_{k}+b_{k})$。

此時有：

$$
\frac{R(x)}{Q(x)}= \frac{A_{1}}{ax_{1}+b_{1}}+\frac{A_{2}}{ax_{2}+b_{2}}+\dots+\frac{A_{k}}{ax_{k}+b_{k}}
$$

### CASE II: $Q(x)$ is a product of linear factors, some of which are repeated

此情況下，假設 $(a_{1}x+b_{1})$ 重複了 $r$ 次，我們對每個重複相都如下分解：

$$
\frac{A_{1}}{ax_{1}+b_{1}}+\frac{A_{2}}{(a_{1}x+b_{1})^{2}}+\dots+\frac{A_{r}}{(a_{1}x+b_{1})^{r}}
$$

誒，注意這裡是 $\frac{A_{r}}{(a_{1}x+b_{1})^{r}}$ 不是 $\frac{A_{r}x+B_{r}}{(a_{1}x+b_{1})^{r}}$ 呀！！！

### CASE III: $Q(x)$ contains irreducible quadratic factors, none of which is repeated

此情況下，$Q(x)$ 包含了一個無解的(不可因式分解的)二次項。

對每個這樣的項，我們將其分解成：

$$
\frac{Ax+B}{ax^{2}+bx+c}
$$

喔對，這邊的積分可以使用三角代換幫忙呦～

$$
\int \frac{1}{x^{2}+a^{2}} \, dx=\frac{1}{a}\tan^{-1}\left( \frac{x}{a} \right)+C
$$

例如：$\int \frac{x-1}{x^{2}+2} \, dx$ 其實不用套很煩的三角代換，可以分解。

$\int \frac{x-1}{x^{2}+2} \, dx=\int \frac{x}{x^{2}+2} \, dx-\int \frac{1}{x^{2}+2} \, dx$ 這樣一來，第一個可以用 substitution，第二個直接帶公式就好。

$=\frac{1}{2}\ln |x^{2}+2|-\frac{1}{\sqrt{ 2 }}\tan^{-1}\left( \frac{x}{\sqrt{ 2 }} \right)+C$ 

對於任意 $ax^{2}+bx+c$ 我們都可以通過配方 + 代換的方式變成 $u^{2}+d$ 的形式。

而對於任意 $\int\frac{Cu+D}{u^{2}+d}$ 我們都可以化成 $C\int \frac{u}{u^{2}+d} \ dx+D\int \frac{1}{u^{2}+d} \ dx$ 的形式，前者會變成 $\ln$，後者會變成 $\arctan$。

### CASE IV: $Q(x)$ contains a repeated irreducible quadratic factor

$Q(x)$ 會包含 $r$ 個不可分解的二次方程，對於每個這樣的元素，我們都將其展開成：

$$
\frac{A_{1}x+B_{1}}{(ax^{2}+bx+c)}+\frac{A_{2}x+B_{2}}{(ax^{2}+bx+c)^{2}}+\dots+\frac{A_{r}x+B_{r}}{(ax^{2}+bx+c)^{r}}
$$

## Rationalizing Substitutions

有時我們會將非有理函數通過適當的代換轉為有理函數處理。

例如，當有 $x^{n/2}$ 的形式時，令 $u=x^{n/2}$ 可能會有用。

例如：$\int \frac{\sqrt{ x+4 }}{x} \ dx$。令 $u=\sqrt{ x+4 }$，則 $x=u^{2}-4$ 且 $dx=2u \ du$。

$\int \frac{\sqrt{ x+4 }}{x} \ dx=\int \frac{u}{u^{2}-4} \ 2u \ du$。

# Improper Integrals

## Type 1: Infinite Intervals

(a)

若 $\int_{a}^{t}f(x) \ dx$ 對任意 $t\geq a$ 都存在，則：

$$
\int_{a}^{\infty}f(x) \ dx=\lim_{ t \to \infty } \int_{a}^{t}f(x)\ dx
$$

若此極限存在且有限，則 $\int_{a}^{\infty}f(x) \ dx$ **收斂(convergent)**。

若此極限不存在，則稱 $\int_{a}^{\infty}f(x) \ dx$ **發散(divergent)**。

你可能會疑惑，既然說了 $\int_{a}^{t}f(x) \ dx$ 對任意 $t\geq a$ 都存在，那為啥 $\lim_{ t \to \infty }\int_{a}^{t} f(x) \ dx$ 會不存在呢？

舉一個簡單的反例，$\int_{a}^{t}x \ dx$ 對於任意 $t\geq a$ 都存在，但是 $\lim_{ t \to \infty }\int_{a}^{t}x \ dx$ 不存在。

(b)

若 $\int_{t}^{b}f(x) \ dx$ 對任意 $t\leq b$ 都存在，則：

$$
\int_{-\infty}^{b}f(x) \ dx = \lim_{ t \to -\infty } \int_{t}^{b} f(x) \ dx
$$

若此極限存在且有限，則 $\int_{-\infty}^{b}f(x) \ dx$ 收斂。

(c)

若 $\int_{-\infty}^{a}f(x) \ dx$ 與 $\int_{a}^{\infty}f(x) \ dx$ 都收斂，則我們定義：

$$
\int_{-\infty}^{\infty}f(x) \ dx=\int_{-\infty}^{a}f(x) \ dx + \int_{a}^{\infty}f(x) \ dx
$$

## Type 2: Discontinuous Integrands

(a)

若 $f$ 在 $[a,b)$ 連續，但在 $b$ 不連續，則：

$$
\int_{a}^{b}f(x)\ dx=\lim_{ t \to b^{-} } \int_{a}^{t}f(x) \ dx
$$

若極限存在且有限。

(b)

若 $f$ 在 $(a,b]$ 連續，但在 $a$ 不連續，則：

$$
\int_{a}^{b}f(x) \ dx=\lim_{ t \to a^{+} } \int_{t}^{b}f(x) \ dx
$$

若極限存在且有限。

(c)

若 $a<c<b$ 且 $f$ 在 $c$ 不連續，且 $\int_{a}^{c}f(x) \ dx$ 與 $\int_{c}^{b}f(x) \ dx$ 都收斂，則：

$$
\int_{a}^{b}f(x) \ dx = \int_{a}^{c}f(x) \ dx + \int_{c}^{b} f(x)\ dx
$$

## A Comparison Test for Improper Integrals

有時候雖然很難求得狹積分的實際值，但我們還是可以知道該積分收斂還是發散。

注意，雖然以下只對 Type 1 進行說明，但是對 Type 2 的狹積分該結論亦成立。

若 $f$ 與 $g$ 在 $x>a$ 時為連續函數且 $f(x)\geq g(x)\geq 0$，則：
1. 若 $\int_{a}^{\infty}f(x) \ dx$ 收斂，則 $\int_{a}^{\infty}g(x) \ dx$ 也收斂。
2. 若 $\int_{a}^{\infty}g(x) \ dx$ 發散，則 $\int_{a}^{\infty}g(x) \ dx$ 也發散。

你需要注意的點有：第一點與第二點 $f$ 與 $g$ 的順序，還有 $f(x)\geq g(x)\geq \boxed{0}$。喔對，還有第一與第二點的反向敘述都不一定成立。

什麼時候要用到 The Comparison Theorem？當你很難將某個函數的反導函數找出來的時候。但是，你需要精明的用這個定理。

或許你可以將某個很難確定的積分切割成一個定積分問題 + 狹積分問題，這樣可能會比較好算？

例如：判斷 $\int_{0}^{\infty}e^{-x^{2}} \ dx$ 是否收斂。你應該把它切成 $\int_{0}^{1}e^{-x^{2}}\ dx+\int_{1}^{\infty}e^{-x^{2}} \ dx$，前面明顯是個定積分問題必收斂，後面是一個狹積分問題。

為什麼要這樣切？因為我們想要用 $x\geq1$ 時 $e^{-x^{2}}\leq e^{-x}$ 來套 Comparison Theorem。如果我們還要對 $x$ 討論來討論去顯然很麻煩。

# Tips

1. $\int \frac{1}{2\cos^{2}\theta} \ d\theta=\int \frac{1}{2}\sec^{2}\theta \ d\theta=\frac{1}{2}\tan \theta$ 
2. $\int_{-1}^{1} \frac{1}{x^{1/3}} \ dx$ 不可以用第五章的理論說因為奇函數所以等於零。因為這是一個狹積分問題。
3. 寫 7.3 trigonometric substitution 時，記得最後**帶回 $x=$ 某個三角函數**。
4. 當令 $u=g(x)$ 代換 $x$ 想求 $du$ 但 $g'(x)$ 不好求時，可以考慮求 $x=g^{-1}(u)$ 則 $dx = (g^{-1})'(u) \ du$ 可能比較方便。
5. 令 $t=\tan\left( \frac{x}{2} \right)$ 可以將 $\sin x=\frac{2t}{1+t^{2}}$ 與 $\cos x=\frac{1-t^{2}}{1+t^{2}}$ 轉成 rational function。
6. 注意，求積分前必須先判斷是正常積分還是狹積分，否則可能得到錯誤的答案。
7. 若 $\int_{a}^{\infty}f(x) \ dx$ 在 $a$ 不連續，則需要將這個積分拆成兩個狹積分算。例：$\int_{0}^{\infty} \frac{1}{x^{2}} \ dx=\int_{0}^{1} \frac{1}{x^{2}} \ dx+\int_{1}^{\infty} \frac{1}{x^{2}} \ dx$ 才能算。
8. 我們只會對狹積分討論 convergent 與 divergent，對定積分不做這個討論。
9. $\int_{-\infty}^{\infty}\tan^{-1}x \ dx$ 發散。不要以為兩個面積抵銷所以等於零。因為狹積分的定義要兩個極限分別存在。
10. 三角代換要注意 $\theta$ 範圍。

# 重要例題

1. Evaluate $\int_{0}^{\pi/4}\sin^{2}2\theta \ d\theta$ 

Sol:
這題可能會想成把 $\sin 2\theta=2\sin \theta \cos \theta$，但是這樣反而會令問題變複雜。
使用 $\sin^{2}\theta=\frac{1}{2}(1-\cos2\theta)$。
$\int_{0}^{\pi/4}\sin^{2}2\theta \ d\theta=\frac{1}{2}\int_{0}^{\pi/4}(1-\cos4\theta)  \, dx=\frac{1}{2}\left[ \theta-\frac{1}{4}\sin4\theta \right]^{\pi/4}_{0}=\frac{\pi}{8}$ 

2. Find $\int x\tan^{2}x \ dx$. 

Sol:
很自然的想到 IBP，但是不能直接 IBP，因為你發現你不會找 $\tan^{2}x$ 的反導函數。
那麼，很自然的把 $\tan^{2}x=\sec^{2}x-1$ 然後就可以很簡單的找到 $\sec^{2}x$ 的反導函數 $\tan x$。
然後你就會力，不用繼續寫了吧。

3. Find $\int \frac{1}{\sec \theta+1} \, d\theta$. 

Sol:
$\int \frac{1}{\sec \theta+1} \, d\theta=\int \frac{\cos \theta}{1+\cos \theta} \, d\theta$ 
沒法往下做，思考生出一個平方有沒有用？試試看吧。
$\cos \theta=2\cos^{2} \frac{\theta}{2}-1$，代入：
$\int \frac{\cos \theta}{1+\cos \theta} \, d\theta=\int \frac{2\cos^{2} \frac{\theta}{2}-1}{2\cos^{2} \frac{\theta}{2}} \ d\theta=\int 1- \frac{1}{2}\sec^{2} \frac{\theta}{2} \ d\theta=\theta-\frac{1}{2}\tan \frac{\theta}{2}+C$。
`~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^ 注意此處代換`


4. Prove the formula $\int_{-\pi}^{\pi}\sin mx\sin nx \ dx=\begin{cases}0 & \text{if }m\neq n \\ \pi & \text{if }m=n\end{cases}$, where $m$ and $n$ are positive integers. 

Sol:
這個不能直接說 $\sin mx\sin nx$ 為奇函數，因為必須按照 $m$ 與 $n$ 的值分類討論。
$\int_{-\pi}^{\pi}\sin mx\sin nx \ dx=\frac{1}{2}\int_{-\pi}^{\pi}\cos(m-n)x-\cos(m+n)x \ dx$ 
當 $m\neq n$：
$\frac{1}{2}\int_{-\pi}^{\pi}\cos(m-n)x-\cos(m+n)x \ dx=\frac{1}{2}\left[  \frac{\sin(m-n)x}{m-n}- \frac{\sin(m+n)x}{m+n} \right]^{\pi}_{-\pi}=0$ 
當 $m=n$：
$\frac{1}{2}\int_{-\pi}^{\pi}\cos(m-n)x-\cos(m+n)x \ dx=\frac{1}{2}\int_{-\pi}^{\pi}1-\cos2mx \ dx=\frac{1}{2}\left[ x-\frac{1}{2m}\sin2mx \right]^{\pi}_{-\pi}=\pi$ 

5. A finite Fourier series is given by the sum $f(x)=\sum_{n=1}^{N}a_{n}\sin nx$. Use the result of (3) to show that $a_{m}=\frac{1}{\pi}\int_{-\pi}^{\pi}f(x)\sin mx \ dx$. 

Sol:
不要怕，咱們把 $f(x)$ 的定義代進公式：
$a_{m}=\frac{1}{\pi}\int_{-\pi}^{\pi}\sum_{n=1}^{N}a_{n}\sin nx\sin mx=a_{m}$ 
根據 (3)，因為除了第 $m$ 項使得 $m=n$ 時會等於 $\pi$，其他的 $n$ 值都會導致積分得到 $0$。

6. Find $\int_{0}^{0.3} \frac{x}{(9-25x^{2})^{3/2}} \ dx$. 

Sol:
因為想湊完全平方，所以令 $x=\frac{3}{5}\sin \theta$，則 $dx=\frac{3}{5}\cos \theta \ d\theta$。
(注意上下界值的變換)
$\int_{0}^{0.3} \frac{x}{(9-25x^{2})^{3/2}} \ dx=\int_{0}^{\pi/6} \frac{\frac{3}{5}\cos \theta}{(3\cos \theta)^{3}}  \frac{3}{5}\cos \theta \ dx=\frac{1}{75}\int_{0}^{\pi/6} \frac{\sin \theta}{\cos^{2}\theta} \ d\theta$ 
接下來有兩種處理方式：
(I)
令 $u=\cos \theta$，則 $\frac{1}{75}\int_{0}^{\pi/6} \frac{\sin \theta}{\cos^{2}\theta} \ d\theta=-\frac{1}{75}\int_{1}^{\sqrt{ 3 }/2} u^{-2} \ du=-\frac{1}{75}[-u^{-1}]^{\sqrt{ 3 }/2}_{1}=\frac{1}{75}\left( \frac{2}{\sqrt{ 3 }}-1 \right)$。
(II)
$\frac{1}{75}\int_{0}^{\pi/6} \frac{\sin \theta}{\cos^{2}\theta} \ d\theta=\frac{1}{75}\int_{0}^{\pi/6}\sec \theta \tan \theta \ d\theta=\frac{1}{75}[\sec \theta]^{\pi/6}_{0}=\frac{1}{75}\left( \frac{2}{\sqrt{ 3 }}-1 \right)$ 

7. Evaluate $\int_{-a}^{L-a} \frac{\lambda b}{4\pi\epsilon_{0}(x^{2}+b^{2})^{3/2}} \ dx$. 

Sol:
不難，這邊主要想講上下界的處理，不要直接把反三角函數寫積分上下界那邊，抄得很累。
令 $x=b\tan \theta$，$\theta_{2}=\tan^{-1}\left( \frac{L-a}{b} \right)$，$\theta_{1}=\tan^{-1}\left( -\frac{a}{b} \right)$。
$\int_{-a}^{L-a} \frac{\lambda b}{4\pi\epsilon_{0}(x^{2}+b^{2})^{3/2}} \ dx= \frac{\lambda}{4\pi\epsilon_{0}b}\int_{\theta_{1}}^{\theta_{2}}\cos \theta \ d\theta=\frac{\lambda}{4\pi\epsilon_{0}b}[\sin \theta]^{\theta_{2}}_{\theta_{1}}$ (畫圖可得 $\sin \theta_{1}$ 與 $\sin \theta_{2}$ 值)
$=\frac{\lambda}{4\pi\epsilon_{0}b}\left[ \frac{L-a}{\sqrt{ (L-a)^{2}+b^{2} }}- \frac{a}{\sqrt{ a^{2}+b^{2} }} \right]$ 

8. Evaluate $\int \frac{1}{1-\cos x} \, dx$.

Sol:
(I)
令 $t=\tan\left( \frac{x}{2} \right)$，$dt=\frac{1}{2}\sec^{2}\left( \frac{x}{2} \right)\ dx\implies dx=\frac{2}{ 1+t^{2} }$。
($\cos= \frac{1-t^{2}}{1+t^{2}}$)
代進去得到 $\int \frac{1}{1-\cos x} \, dx=\int t^{-2} \ dt=-\cot\left( \frac{x}{2} \right)+C$ 
(II)
湊平方：$\int \frac{1}{1-\cos x} \, dx=\int \frac{1}{1-\cos x} \frac{1+\cos x}{1+\cos x} \ dx=\int \frac{1+\cos x}{\sin^{2}x} \ dx$ 
$=\int \frac{1}{\sin^{2}x} \, dx+\int \frac{\cos x}{\sin^{2}x} \, dx=-\cot x-\csc x+C$ 

9. Evaluate $\int \frac{1}{\sqrt{ x }- ^{3}\sqrt{ x }} \ dx$. 

Sol:
誒注意這裡 $^{3}\sqrt{ x }=x^{1/3}\neq x^{3/2}$。
因為我們想讓這個東東變成 rational function，如果取 $u=x^{1/3}$ 代進去 $\sqrt{ x }=u^{3/2}$ 不是整數不好。
所以取 $u=x^{1/6}$。
然後你就會做了！

10. Find $\int_{-\infty}^{0} \frac{z}{z^{4}+4} \ dz$. 

Sol:
沒法直接三角代換，先用 substition rule 然後再三角代換。
$\int_{-\infty}^{0} \frac{z}{z^{4}+4} \ dz=\lim_{ t \to -\infty }\int_{t}^{0} \frac{z}{z^{4}+4} \ dz$ $[\text{let }u=z^{2}]$ 
$=\lim_{ t \to -\infty } \frac{1}{2}\int_{t^{2}}^{0} \frac{1}{u^{2}+4} \ du$ 
`~~~~~~~~~~~^ 注意這裡變 t 平方`
$=\lim_{ t \to -\infty } \frac{1}{2}\left[ \frac{1}{2}\tan^{-1}\left( \frac{u}{2} \right) \right]^{0}_{t^{2}}=-\frac{\pi}{8}$  

11. Find the values of $p$ for which the integral converges and evaluate the integral for those values of $p$. $\int_{0}^{1} \frac{1}{x^{p}} \ dx$. 

Sol:
注意到，當 $p<0$，積分 proper，所以不會用來討論 converge 與 diverge。
又注意到當 $p=1$ 時，$\int_{0}^{1} \frac{1}{x}\ dx=\lim_{ t \to 0^{+} }[\ln|x|]^{1}_{t}=\infty$ divergent。
當 $p\neq 1$ 時：$\int_{0}^{1} \frac{1}{x^{p}} \ dx= \frac{1}{1-p}\lim_{ t \to 0^{+} }\left( 1- \frac{1}{t^{p-1}} \right)$ 
當 $p>1$ 時極限不存在 $\implies$ divergent
當 $p<1$ 時極限存在且等於 $1\implies$ convergent 且值為 $\frac{1}{1-p}$。

12. Evaluate $\int \sin^{4}\theta \cos^{2}\theta \ d\theta$. 

Sol:
首先你肯定不會想要瘋狂降次展開，那麼就只能考慮先換 $\sin \theta \cos \theta=\frac{1}{2}\sin 2\theta$。
所以：$\int \sin^{4}\theta \cos^{2}\theta \ d\theta=\frac{1}{4}\int \sin^{2}\theta \sin^{2}2\theta \ d\theta=\frac{1}{4}\int \frac{1}{2}\left(1-\cos2\theta  \right)\sin^{2}2\theta \ d\theta$ 
$=\frac{1}{8}\int \sin^{2}2\theta-\sin^{2}2\theta \cos2\theta \ d\theta= \frac{1}{8}\int \frac{1}{2}(1-\cos4\theta) \ d\theta- \frac{1}{8}\int \sin^{2}2\theta \cos2\theta \ d\theta$ 
然後你就會了。

# 大會考

1. $\int_{0}^{e-2}\ln(2+x) \ dx= \ ?$ 

Sol:
令 $t=2+x$，則 $dt=dx$。
$\int_{0}^{e-2}\ln(2+x) \ dx= \int_{2}^{e}\ln t  \, dt$ 
注意，這邊看起來很簡單，所以你可能會忘記要求反導函數而不是直接帶入！
利用 IBP，令 $u=\ln t，dv=dt$，則：
$\int_{2}^{e}\ln t \ dt=[t\ln t]^{e}_{2}-\int_{2}^{e}  \, dt=2-2\ln2$ 

2. Evaluate $\int \frac{x}{\sqrt{ x^{2}+x+1 }} \ dx$. 

Sol:
解這種題：
1. 對根號內部配方。
2. 把平方者代換。
3. 把代換者再次用三角函數代換。
4. 解不定積分。
5. 把不定積分中的三角函數換回 $u$。
6. 把 $u$ 換回 $x$。

什麼？你說這看起來很簡單？你行你上。
$\int \frac{x}{\sqrt{ x^{2}+x+1 }} \ dx=\int \frac{x}{\sqrt{ \left( x+\frac{1}{2} \right)^{2}+\frac{3}{4} }} \ dx$ $\left[ \text{let }u=x+\frac{1}{2}\text{, }du=dx \right]$ 
$=\int \frac{u-\frac{1}{2}}{\sqrt{ u^{2}+\frac{3}{4} }} \ du$ $\left[ \text{let }u=\frac{\sqrt{ 3 }}{2}\tan \theta\text{, }du=\frac{\sqrt{ 3 }}{2}\sec^{2}\theta \right]$ 
$=\int \frac{\frac{\sqrt{ 3 }}{2}\tan \theta-\frac{1}{2}}{\frac{\sqrt{ 3 }}{2}\sec \theta} \frac{\sqrt{ 3 }}{2}\sec^{2}\theta \ d\theta=\frac{\sqrt{ 3 }}{2}\sec \theta-\frac{1}{2}\ln|\sec \theta+\tan \theta|+C$ 
$=\frac{\sqrt{ 3 }}{2} \frac{\sqrt{ 4u^{2}+3 }}{\sqrt{ 3 }}-\frac{1}{2}\ln| \frac{\sqrt{ 4u^{2}+3 }}{\sqrt{ 3 }}+\frac{2u}{\sqrt{ 3 }}|+C$ 
$=\sqrt{ x^{2}+x+1 }-\frac{1}{2}\ln| \frac{2}{\sqrt{ 3 }}\sqrt{ x^{2}+x+1 }+ \frac{2}{\sqrt{ 3 }}\left( x+\frac{1}{2} \right)|+C$ 

3. Evaluate $\int \frac{1}{(x^{2}+1)^{2}} \ dx$ 

Sol:
誒這個看起來很難解。
不會，用三角代換令 $x=\tan \theta$ 就好。
喔，要記得最後把 $\theta$ 換回 $x$。說很多遍了還錯。

4. Evaluate $\int \frac{1}{x^{8}-x} \ dx$. 

Sol:
$\int \frac{1}{x^{8}-x} \ dx=\int \frac{1}{x(x^{7}-1)} \ dx$ 
令 $u=x^{7}$ 則 $dx = \frac{1}{7}x^{-6} \ du$。(注意此處 $u\neq x^{7}-1$)
`~~~^ key`
$\int \frac{1}{x(x^{7}-1)} \ dx= \frac{1}{7}\int \frac{1}{u-1}\cdot \frac{1}{x}\cdot \frac{1}{x^{6}} \ du= \frac{1}{7}\int \frac{1}{u}\cdot \frac{1}{u-1} \ du = \frac{1}{7}\int \frac{-1}{u}+ \frac{1}{u-1} \ du$ 
$=\frac{1}{7}\ln| \frac{x^{7}-1}{x^{7}}|+C$ 

5. Set $f(x)= \frac{1}{x[\ln (x+1)]^{p}} \ dx$. Determine all positive values of $p$ for which the improper integral $\int_{1}^{\infty} f(x) \ dx$ converges.

Sol:
因為 $f(x)$ 在 $[1,\infty)$ 有界，所以可以只考慮 $\int_{e}^{\infty}f(x) \ dx$ 因為 $\int_{1}^{e}f(x) \ dx$ 必定收斂。
因為 $x[\ln(x+1)]^{p}>x[\ln x]^{p}\quad\forall p>0\text{ on }[e,\infty)$，所以 $f(x)< \frac{1}{x[\ln x]^{p}}\quad\forall p>0\text{ on }[e,\infty)$。
令 $u=\ln x$，則：
$\lim_{ t \to \infty }\int_{e}^{t} \frac{1}{x[\ln x]^{p}} \ dx=\lim_{ t \to \infty }\int_{1}^{\ln t} \frac{1}{u^{p}} \ du=\lim_{ t \to \infty }\int_{1}^{\ln t} \frac{1}{u^{p}} \ du$ 
當 $p=1$，$\lim_{ t \to \infty }\int_{1}^{\ln t} \frac{1}{u^{p}} \ dx$ 發散。
當 $p\neq 1$，$\lim_{ t \to \infty }\int_{1}^{\ln t} \frac{1}{u^{p}} \ dx=\lim_{ t \to \infty }\left[ \frac{1}{1-p}u^{1-p} \right]^{\ln t}_{1}$ 僅在 $1-p<0\implies p>1$ 時收斂。
(如果此時我們沒有在題目一開始考慮 $[e,\infty)$，就會變成要考慮 $\int_{0}^{\infty} \frac{1}{u^{p}} \ du$ 無論如何都會發散，也就無法夾出來我們的 $p$ 的條件了)

6. For which values of $a$ does the improper integral $\int_{0}^{\infty} \frac{x^{a}}{1+x^{2}} \ dx$ converge? 

Sol:
我不會，請外援。