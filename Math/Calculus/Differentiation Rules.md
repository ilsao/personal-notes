
# Derivatives of Polynomials and Exponential Functions

## Constant Funcitons

對於常數函數 $f(x)=c$ ，我們可以由導數的定義：

$f'(x)=\lim_{ h \to 0 } \frac{f(x+h)-f(x)}{h}=\lim_{ h \to 0} \frac{c-c}{h}=0$ 

所以，我們有：

$$
\boxed{\frac{d}{dx}(c)=0}
$$

## Power Functions

對於冪函數 $f(x)=x^{n}$，我們可以如下推導：

(I)
$f'(a)=\lim_{ x \to a } \frac{f(x)-f(a)}{x-a}=\lim_{ x \to a } \frac{x^{n}-a^{n}}{x-a}=\lim_{ x \to a }(x^{n-1}+x^{n-2}a+x^{n-3}a^{2}+\dots+a^{n-1})$ 
$=a^{n-1}+a^{n-1}+\dots+a^{n-1}=na^{n-1}$ 

(II)
$f'(x)=\lim_{ h \to 0 } \frac{f(x+h)-f(x)}{h}=\lim_{ h \to 0 } \frac{(x+h)^{n}-x^{n}}{h}=\lim_{ h \to 0 } \frac{\left[ x^{n}+nx^{n-1}h+ \frac{n(n-1)}{2}x^{n-2}h^{2}+\dots+h^{n} \right]-x^{n}}{h}$ 
$=\lim_{ h \to 0 } nx^{n-1}+ \frac{n(n-1)}{2}x^{n-2}h + \dots + h^{n-1}=nx^{n-1}$ 

所以，如果 $n \in \mathbb{R}$，我們有：

$$
\boxed{\frac{d}{dx}(x^{n})=nx^{n-1}}
$$

## New Derivatives from Old

如果我們有 $g(x)=cf(x)$，那麼：

$g'(x)=\lim_{ h \to 0 } \frac{cf(x+h)-cf(x)}{h}=c\lim_{ h \to 0 } \frac{f(x+h)-f(x)}{h}=cf'(x)$ 
`~~~~~~~~~~~~~~~~~~~~~~~~^ By Limit Law 3`

所以，如果 $c$ 是一個常數，$f$ 是一個可導函數，我們有：

$$
\boxed{\frac{d}{dx}(cf(x))=c\frac{d}{dx}f(x)}
$$

更進一步，對於 $F(x)=f(x)+g(x)$：

`~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ˇ By Limit Law 1`
$F'(x)=\lim_{ h \to 0 } \frac{f(x+h)+g(x+h)-f(x)-g(x)}{h}=\lim_{ h \to 0 } \frac{f(x+h)-f(x)}{h}+\lim_{ h \to 0 } \frac{g(x+h)-g(x)}{h}$ 
$=f'(x)+g'(x)$ 

所以，如果 $f$ 和 $g$ 可導，我們有：

$$
\boxed{\frac{d}{dx}(f(x)+g(x))=\frac{d}{dx}f(x)+\frac{d}{dx}g(x)}
$$

想要證明更多個函數相加的導數算法，我們可以遞歸的使用上述結論：

$(f+g+h)'=[(f+g)+h]'=(f+g)'+h'=f'+g'+h'$ 

我們還可以由以上結果推導出，一個多項式函數的導數仍是多項式函數。

## Exponential Functions

如果有函數 $f'(x)=b^{x}$，嘗試計算他的導數：

$f'(x)=\lim_{ h \to 0 } \frac{b^{x+h}-b^{x}}{h}=\lim_{ h \to 0 } \frac{b^{x}(b^{h}-1)}{h}=b^{x}\lim_{ h \to 0 } \frac{b^{h}-1}{h}$ 
$=b^{x}f'(0)$ 

這說明了如果 $f$ 在 $x=0$ 可導，那麼該函數處處可導。

在 3.4 節(P204)，我們會說明指數函數的導數為：

$$
\boxed{\frac{d}{dx}b^{x}=f'(0)b^{x}=(\ln b)b^{x}}
$$

回想我們定義自然常數 $e$ 在 $x=0$ 時斜率為 $1$。所以，$e$ 的定義為滿足以下式子的數：

$$
\boxed{\lim_{ h \to 0 } \frac{e^{h}-1}{h}=1 }
$$

而且，我們可以得到 $e$ 的導數：

$$
\boxed{\frac{d}{dx}e^{x}=e^{x}}
$$

我們來偷用 3.4 節的東西來證明：$f(x)=a^{x}\implies f'(x)=a^{x}\ln a$ 。

首先，我們有：

$$f(x)=a^{x}=(e^{\ln a})^{x}=e^{(\ln a)x}$$

然後，利用 Chain Rule，我們有：

$$f'(x)=e^{(\ln a)x}\ln a=\boxed{a^{x}\ln a}$$

# The product and Quotient Rules

## The Product Rule

對於兩個可導函數 $f(x)$ 與 $g(x)$，我們如下推導 $f(x)g(x)$ 的微分公式：

$\lim_{ h \to 0 } \frac{f(x+h)g(x+h)-f(x)g(x)}{h}$ (補上 $f(x+h)g(x)-f(x+h)g(x)$)
$=\lim_{ h \to 0 } \frac{f(x+h)[g(x+h)-g(x)]}{h}+\lim_{ h \to 0 } \frac{g(x)[f(x+h)-f(x)]}{h}$ 
$=\lim_{ h \to 0 }\left[ f(x+h) \frac{g(x+h)-g(x)}{h} \right]+\lim_{ h \to 0 }\left[ g(x) \frac{f(x+h)-f(x)}{h} \right]$ 
$=f(x)g'(x)+g(x)f'(x)$ 

所以，如果 $f$ 與 $g$ 皆可導，我們有：

$$
\boxed{\frac{d}{dx}[f(x)g(x)]=\frac{d}{dx}[f(x)]g(x) + \frac{d}{dx}[g(x)]}
$$

對於多個函數連乘的導數，我們有 $(fgh)'=f'gh + fg'h + fgh'$。

可以注意的是，如果有機會先將函數化簡，有可能不用使用 product rule 就能解決問題。所以每次求導前，先嘗試化簡吧～

## The Quotient Rule

讓我們用類似的方法推導一次 quotient rule：

$\lim_{ h \to 0 } \frac{\frac{f(x+h)}{g(x+h)}- \frac{f(x)}{g(x)}}{h}=\lim_{ h \to 0 } \frac{g(x)f(x+h)-g(x+h)f(x)}{g(x)g(x+h)h}=\lim_{ h \to 0 } \frac{g(x)f(x+h)-g(x+h)f(x)+f(x)g(x)-f(x)g(x)}{g(x)g(x+h)h}$
$=\lim_{ h \to 0 } \frac{g(x)[f(x+h)-f(x)]-f(x)[g(x+h)-g(x)]}{g(x)g(x+h)h}=\lim_{ h \to 0 } \frac{g(x)}{g(x)g(x+h)} \cdot \frac{f(x+h)-f(x)}{h}- \lim_{ h \to 0 } \frac{f(x)}{g(x)g(x+h)} \cdot \frac{g(x+h)-g(x)}{h}$ 
$=\frac{f'(x)g(x)-f(x)g'(x)}{[g(x)]^{2}}$ 

所以，若 $f$ 與 $g$ 皆可導，我們有：

$$
\boxed{\frac{d}{dx}\left[ \frac{f(x)}{g(x)} \right]=\frac{\frac{d}{dx}[f(x)]g(x)-f(x) \frac{d}{dx}[g(x)]}{[g(x)]^{2}}}
$$

有了這個我們就可以計算有理函數了誒，好棒～

喔對，不要每次看到分數就用這個很醜的公式喔！先試試化簡好嘛～

例如：求導 $F(x)=\frac{3x^{2}+2\sqrt{ x }}{x}$ 。

可以先將 $F(x)$ 化成 $3x+2x^{-1/2}$，然後再求導是不是簡單多啦！

你可能會問，又不能保證 $x\neq 0$，怎麼可以亂約分捏？

但是你想喔，$F(x)$ 一定是可導的嘛，那可導是不是必連續呀？說明什麼捏？說明 $x=0$ 是不是根本不在函數的定義域裡面咩？所以可以放心的約掉 $x$ 啦！

# Derivatives of Trigonometric Functions

首先我們要先來證明兩個性質：

$$
\boxed{\lim_{ x \to 0 } \frac{\sin x}{x}=1}
$$

proof:
![[Pasted image 20251014175953.png]]

由圖，我們可以得到 $|BC|<arcAB<|AD|$。
因為邊長為 1 ，我們可以得到他們的對位：$\sin \theta<\theta<\tan \theta$。
同除 $\sin \theta\implies 1< \frac{\theta}{\sin \theta}< \frac{1}{\cos \theta}\implies \cos \theta< \frac{\sin \theta}{\theta}<1$ 
因為 $\lim_{ \theta \to 0 }\cos \theta=1$ 且 $\lim_{ \theta \to 0 }1=1$，根據夾擠定理，我們有 $\lim_{ \theta \to 0 } \frac{\sin \theta}{\theta}=1$。

$$
\boxed{\lim_{ x \to 0 } \frac{\cos x-1}{x}=0}
$$

proof:
我們上下同乘 $\cos x+1$：
$\lim_{ x \to 0 } \frac{\cos^{2}x-1}{x(\cos x+1)}=\lim_{ x \to 0 } \frac{-\sin^{2}x}{x(\cos x+1)}=-\lim_{ x \to 0 } \frac{\sin x}{x} \times \lim_{ x \to 0 } \frac{\sin x}{\cos x+1}$ 
$=-1 \times \frac{0}{2}=0$ 

由上，我們可以推出 $\sin x$ 的導數：

$$
\boxed{\frac{d}{dx}(\sin x)=\cos x}
$$

proof:
$f(x)=\sin x$, 我們要找 $f$ 的導數。
$f'(x)=\lim_{ h \to 0 } \frac{\sin(x+h)-\sin x}{h}=\lim_{ h \to 0 } \frac{\sin x\cos h+\sin h \cos x-\sin x}{h}=\lim_{ h \to 0 } \frac{\sin x(\cos h-1)}{h}+\lim_{ h \to 0 } \frac{\sin h \cos x}{h}$ 
$=\sin x\lim_{ h \to 0 } \frac{\cos h-1}{h}+\cos x \lim_{ h \to 0 } \frac{\sin h}{h}=\cos x$ 

利用類似的方法，我們可以得到：

$$
\boxed{\frac{d}{dx} (\cos x)=-\sin x}
$$

我們還有：

$$
\boxed{\frac{d}{dx}(\tan x)=\sec^{2}x}
$$

proof:
$\frac{d}{dx}(\tan x)=\frac{d}{dx}\left( \frac{\sin x}{\cos x} \right)= \frac{\cos x\cos x-\sin x(-\sin x)}{\cos^{2} x}$ 
$= \frac{\cos^{2}x+\sin^{2}x}{\cos^{2x}} = \frac{1}{\cos^{2}x}=\sec^{2}x$ 

剩下的幾個三角函數 $\csc, \sec, \cot$ 可以輕易的使用 The Quotient Rule 導出：

$$
\boxed{\frac{d}{dx}(\csc x)=-\csc x\cot x}
$$

$$
\boxed{\frac{d}{dx}(\sec x)=\sec x\tan x}
$$

$$
\boxed{\frac{d}{dx}(\cot)=-\csc^{2}x}
$$

# The Chain Rule

如果 $g$ 在 $x$ 可微，且 $f$ 在 $g(x)$ 可微，並令 $F(x)=f\circ g$ 那麼有：

$$
\boxed{\begin{align}
 & F'(x)=f'(g(x))g'(x)
\end{align}}
$$

如果使用萊布尼茲的方式表達，令 $y = f(u), \ u=g(x)$，則：

$$
\boxed{\frac{dy}{dx} = \frac{dy}{du} \frac{du}{dx}}
$$

讓我們嘗試用 Chain Rule 推導一遍指數函數的導數。

$$
\boxed{b^{x}=b^{x}\ln b}
$$

proof:
$\frac{d}{dx} (b^{x})=\frac{d}{dx} (e^{x\ln b})=e^{x\ln b} \frac{d}{dx}(x\ln b)=b^{x}\ln b$ 

接下來重頭戲就開場了，讓我們證明 Chain Rule 吧！

誒，在重場戲開始之前，讓我們先來熱個身，推導一個可以幫助 Chain Rule 的東西叭～

我們知道：

$$
\Delta y=f(a+\Delta x)-f(a)
$$

以及：

$$
\lim_{ x \to 0 } \frac{\Delta y}{\Delta x}=f'(a)
$$

我們令 $\epsilon= \frac{\Delta y}{\Delta x}-f'(a)$，那麼：

$$
\lim_{ \Delta x \to 0 } \epsilon=f'(a)-f'(a)=0
$$

如果我們定義 $\epsilon$ 在 $x=0$ 時 $\epsilon=0$，那麼 $\epsilon$ 就會是一個對 $x$ 連續的函數。

又因為 $\epsilon= \frac{\Delta y}{\Delta x}-f'(a)$，所以我們可以改寫：

$$
\Delta y= f'(a)\Delta x + \epsilon\Delta x \quad\text{where} \quad \epsilon\to 0\text{ as } \Delta x\to0
$$

那麼捏，這個性質可以幫助我們證明 Chain Rule ！重頭戲上場～

讓我們假設 $u=g(a)$ 在 $a$ 可導，且 $y=f(u)$ 在 $b=g(a)$ 處可導。

我們有：

$$
\Delta u=g'(a)\Delta x-\epsilon\Delta x=[g'(a)-\epsilon_{1}]\Delta x
$$

與

$$
\Delta y=f'(b)\Delta u-\epsilon\Delta u=[f'(b)-\epsilon_{2}]\Delta u
$$

我們將上上式帶入上式，可得：

$$
\Delta y=[f'(b)-\epsilon_{2}][g'(a)-\epsilon_{1}]\Delta x\implies \frac{\Delta y}{\Delta x}=[f'(b)-\epsilon_{2}][g'(a)-\epsilon_{1}]
$$

取極限：

$$
\lim_{ \Delta x \to 0 } \frac{\Delta y}{\Delta x}=f'(a)=f'(b)g'(a)=f'(g(a))g'(a)
$$

太棒啦，你成功證明了 Chain Rule 了誒！真有實力～

# Implicit Differentiation

如果我們想要對一個隱式定義的函數微分，我們就可以使用隱微分。也就是，同時對等號左右兩邊微分。

需要注意的是，在隱微分中，我們將 $y$ 視為一個由 $x$ 隱式表達的函數，所以在對 $y$ 微分時會需要使用到 Chain Rule。

我們使用一個例子來講解隱微分的做法。

Ex: 
(a) Find $y'$ if $x^{3}+y^{3}=6xy$. 
(b) At what point in the first quadrant is the tangent line horizontal? 

Sol:
(a)
對左右微分：
$\frac{d}{dx}(x^{3})+\frac{d}{dx}(y^{3})=6\frac{d}{dx}(xy)$ 
$3x^{2}+3y^{2} \frac{dy}{dx}=6\left( 1\cdot y + x \cdot 1 \cdot \frac{dy}{dx} \right)\implies 3x^{2}+3y^{2}y'=6y+6xy'\implies x^{2}+y^{2}y'=2y+2xy'$ 
$\implies y' = \frac{x^{2}-2y}{x-y^{2}}$ 

(b)
$y'=0\implies x^{2}-2y=0\implies y=\frac{1}{2}x^{2}$ 
帶回原方程式：$x^{3}+\left( \frac{1}{2}x^{2} \right)^{3}=6x\left( \frac{1}{2}x^{2} \right)\implies x^{6}=16x^{3}$ 
因為 $x\neq 0$ 所以可以同除 $x^{3}$，$x^{3}=16\implies x=2^{4/3},\ y=2^{5/3}$。

如果想要計算多次隱微分，可以直接對一次微分後的結果再多次微分，裡面可能會出現 $y'$，只要使用之前計算的 $y'$ 帶入就好。

# Derivatives of Logarithmic and Inverse Trigonometric

## Derivatives of Logarithmic Functions

我們知道，一個可導的一對一函數的反函數照樣可導。(除去有水平切線的點，因為變成反函數後，該切線會變為鉛直切線)

我們有：

$$
\boxed{\frac{d}{dx}(\log_{b}x)=\frac{1}{x\ln b}}
$$

proof:
令 $y=\log_{b}x$，我們有 $b^{y}=x$。
我們對 $x$ 隱微分，得到：$(b^{y}\ln b) \frac{dy}{dx}=1\implies \frac{d}{dx}(\log_{b}x)=\frac{1}{x\ln b}$。

在此，如果我們取 $b=e$，則有：

$$
\boxed{\frac{d}{dx}(\ln x)= \frac{1}{x}}
$$

利用 Chain Rule，我們還有：

$$
\frac{d}{dx}(\ln g(x))=\frac{g'(x)}{g(x)}
$$

最後，我們還有：

$$
\boxed{\frac{d}{dx}(\ln|x|)=\frac{d}{dx}(\ln x)=\frac{1}{x}}
$$

proof:
$f(x)=\begin{cases}\ln x & \text{if }x>0 \\ \ln(-x) & \text{if }x<0\end{cases}$ ，所以 $f'(x)=\begin{cases} \frac{1}{x} & \text{if }x>0 \\ \frac{1}{(-x)}(-1)=\frac{1}{x} & \text{if }x<0\end{cases}$ 。

所以勒，在某些不知道是正還是負的函數我們都不用加絕對值啦！很方便叭～ 原書裡面說，這個結論很 worth remembering 喔～

寫完題目後評：嗯，我認可。確實 worth remembering。

## Logarithmic Differentiation

一些很複雜的函數的微分(比如乘法與除法)，可以使用對數來化減。

例如：微分 $y= \frac{x^{3/4}\sqrt{ x^{2}+1 }}{(3x+2)^{5}}$。

直接套用 Product Rule / Quotient Rule 實在太變態了，我們對等號左右取 $\ln$。

$\ln y = \frac{3}{4}\ln x + \frac{1}{2}\ln(x^{2}+1)-5\ln(3x+2)$，然後再解是不是簡單多啦！

步驟如下：
- 對 $y=f(x)$ 左右取 $\ln$，然後使用對數律展開。
- 兩邊隱微分。
- (!) 把隱微分結果中的 $y$ 用 $f(x)$ 代替。誒！要記得做啦！

而且，對於 $\frac{d}{dx}[f(x)]^{g(x)}$ 形式的問題，也可以使用對數解決。

現在，我們還可以用 $\ln$ 來重新證明 $\frac{d}{dx}(x^{n})=nx^{n-1}$。

proof:
令 $y=x^{n}$。
因為我們不知道 $x^{n}$ 會不會小於零，所以我們需要加上絕對值。
$\ln|y|=\ln|x|^{n}=n\ln|x|$。
由上，我們知道對絕對值取對數後的導數不變，所以：
$\frac{y'}{y}=n \frac{1}{x}\implies y'=n \frac{y}{x}=n \frac{x^{n}}{x}=nx^{n-1}$。

## The Number $e$ as Limit

$$
\boxed{e=\lim_{ x \to 0 } (1+x)^{1/x}=\lim_{ n \to \infty } \left( 1+\frac{1}{n} \right)^{n}}
$$

proof:
我們從 $\frac{d}{dx}(\ln x)=\frac{1}{x}$ 出發。如果 $f(x)=\ln x$，那麼 $f'(1)=1$。
寫成極限形式：
$f'(1)=\lim_{ x \to 0 } \frac{f(1+x)-f(1)}{x}=\lim_{ x \to 0 } \frac{\ln(1+x)-\ln{1}}{x}=\lim_{ x \to 0 } \frac{1}{x}\ln(1+x)$ 
$=\lim_{ x \to 0 }\ln(1+x)^{1/x}=1$ 
那麼，因為 $e=e^{1}=e^{\lim_{ x \to 0 }\ln(1+x)^{1/x}}=\lim_{ x \to 0 }e^{\ln(1+x)^{1/x}}=\lim_{ x \to 0 }(1+x)^{1/x}$ 。
令 $n=\frac{1}{x}$，那麼 $x\to0^{+}$ 則 $n\to \infty$。所以有 $e=\lim_{ n \to \infty }\left( 1+\frac{1}{n} \right)^{n}$。

最後，我們可以計算：

$$
\boxed{e \approx 2.7182818}
$$

## Derivatives of Inverse Trigonometric Functions

$$
\boxed{\frac{d}{dx}(\sin^{-1}x)=\frac{1}{\sqrt{ 1-x^{2} }}}
$$

proof:
回想反三角函數的定義，$y=\sin^{-1}x$ 代表了 $\sin y=x$ 且 $y \in \left[ -\frac{\pi}{2}, \frac{\pi}{2} \right]$。
使用隱微分：$\cos y \frac{dy}{dx}=1\implies \frac{dy}{dx}=\frac{1}{\cos y}=\frac{1}{\sqrt{ 1-x^{2} }}$。 ($\cos y \geq 0$ 因為 $y \in \left[ -\frac{\pi}{2}, \frac{\pi}{2} \right]$)

$$
\boxed{\frac{d}{dx}(\tan^{-1}x)=\frac{1}{1+x^{2}}}
$$

proof:
$\tan y=x$ 且 $y\in \left[ -\frac{\pi}{2}, \frac{\pi}{2} \right]$。
$\sec^{2}y \frac{dy}{dx}=1\implies \frac{dy}{dx}=\frac{1}{\sec^{2}y}=\frac{1}{1+\tan^{2}y}=\frac{1}{1+x^{2}}$ 

其他的證明都大同小異啦，直接給你答案～

$$
\boxed{\frac{d}{dx}(\cos^{-1}x)=- \frac{1}{\sqrt{ 1-x^{2} }}}
$$

$$
\boxed{\frac{d}{dx}(\csc^{-1}x)=- \frac{1}{x\sqrt{ x^{2}-1 }}}
$$

$$
\boxed{\frac{d}{dx}(\sec^{-1}x)= \frac{1}{x\sqrt{ x^{2}-1 }}}
$$

$$
\boxed{\frac{d}{dx}(\cot^{-1}x)= -\frac{1}{1+x^{2}}}
$$

# Linear Approximations and Differentials

## Linearization and Approximation

我們可以使用在 $(a,f(a))$ 的切線來估計 $y=f(x)$，其中， $x$ 很接近 $a$ 。

那麼，在 $(a,f(a))$ 的切線我們可以使用：

$$
L(x)=f(a) + f'(a)(x-a)
$$

這個稱為：Linearization of $f$ at $a$。

那麼估計 $f(x) \approx L(x)$ 可以寫為：

$$
\boxed{f(x) \approx f(a) + f'(a)(x-a)}
$$

這個方程稱作 linear approximation 或 tangent line approximation of $f$ at $a$。

這樣可以推導出很經典的：當 $\theta$ 很接近 $0$ 時，$\sin \theta \approx \theta$ 與 $\cos \theta \approx 1$。

$f(x)\approx L(x)=\sin0+\cos0(x-0)=x$ 

與

$f(x)\approx L(x)=\cos0-\sin 0(x-0)=1$ 

## Differentials

考慮 $y=f(x)$，其中 $f$ 為可導函數。此時，$dx$ 為獨立變量，$dy$ 則依賴於 $dx$ 的值。

$$
\boxed{dy=f'(x)dx}
$$

需要知道的是，$dx$ 不必趨近於零，而可以是任意數字。而 $dy$ 則是經由 $f'(x)$ 線性預估出來的值，與 $\Delta y$ 存在誤差。

可以使用下圖來理解 $dy$ 與 $\Delta y$ 的差別：

![[Pasted image 20251022141233.png]]

因為 $dx$ 為 $x$ 的變化量，所以 $dx=\Delta x$。

但是因為 $dy$ 基於斜率為 $f'(x)$ 且經過 $(x,f(x))$ 所做的 linear approximation 預估，所以與真正的 $\Delta y$ 存在誤差。

真正的 $\Delta y$ 如下：$\Delta y=f(x+\Delta x)-f(x)$。

可以觀察出來，當 $dx$ 越小，$\Delta y$ 越接近 $dy$。

由於 $f(x) \approx f(a) + f'(a)(x-a)$，我們可以有：$f(a+dx)\approx f(a)+f'(a)(dx)=f(a)+dy$

$$ 
\boxed{f(a+dx)\approx (a)+dy}
$$

例如，我們想尋找 $\sqrt{ 4.05 }$，那麼，可以藉助 $f(x)=\sqrt{ x+3 }$。
(I)
$f(x)\approx f(1)+f'(1)(x-1)=2+\frac{1}{4}(x-1)=\frac{7}{4}+\frac{x}{4}$ ($x$ 在 $1$ 附近時成立)
取 $x=1.05$，$f(1.05)\approx \frac{7}{4}+\frac{1.05}{4} =2.0125$。

(II)
使用上述的 $dy$ 與 $dx$ 的關係。
$dy=f'(x)dx$ ，此處取 $dx=0.05\implies dy=0.0125$。
取 $a=1$，套用 $f(a+dx)\approx f(a)+dy$。$f(1+0.05)=f(1)+dy=2.0125$。

# Tips

- $x^{n}-a^{n}=(x-a)\sum_{k=0}^{n-1}x^{n-1-k}a^{k}=(x-a)(x^{n-1}+x^{n-2}a+\dots+xa^{n-2}+a^{n-1})$ 
- 對於簡單的 $\frac{d}{dx} \frac{a}{x^{2}}$，我們可以先化為 $\frac{d}{dx} (ax^{-2})=-2ax^{-3}$，避免腦子壞掉犯錯。
- 如何求某多項式函數在哪點有垂直切線？先對該函數求導，然後觀察其導數在哪點不存在。通常是分母為零。
- 想求某分段函數是否可導，可以先對每段求導，然後確認在邊界時導數值是否一致。
- $\sec^{2}x=\tan^{2}x+1$。
- 當你不會微分某個函數時，想想他的反函數會不會比較好算。
- 對於 $\frac{d}{dx}[f(x)]^{g(x)}$ 形式的問題，可以使用對數解決。例如：$\frac{d}{dx}(x^{\sqrt{ x }})$。
- 大會考好像蠻喜歡考 Chain Rule + implicit differentiation 的。如果有那種給你 $f(x)$ 讓你求 $(f^{-1})'(n)$ 的題目，就列 $f^{-1}(f(x))=x$ 然後隱微分 $(f^{-1})'(f(x))= \frac{1}{f'(x)}$ 就好。例如：底下大會考第一題。
- 注意題目要求。若 Find the "derivative" of y，是求 $y'$。若 Find the "differential" of y，是求 $dy$。
# 重要例題

1. Differentiate the function $f(v)= v^{-2/3}-2e^{v}$ 

Sol:
需要注意的是，$\frac{d}{dv} 2e^{v}=2e^{v}$。
所以 $f'(v)=-\frac{2}{3}v^{-5/3}-2e^{v}$。

2. Show that the curve $y=2e^{x}+3x+5x^{3}$ has no tangent line with slope 2. 

Sol:
$y'=2e^{x}+3+15x^{2}$ 
然後你會發現，誒？沒教過啊，怎麼解？？
然後你就會去翻解答，然後就會發現原來不用解。
$\because 2e^{x}> 0$ and $15x^{2}\geq 0 \therefore\text{min}\{y'\}=3$ 

3. Let $f(x)=\begin{cases}x^{2} & \text{if }x\leq 2 \\ mx+b & \text{if} x>2\end{cases}$. Find the values of $m$ and $b$ that make $f$ differentiable everywhere.

Sol:
若 $f$ 可導，我們可以得到 $f'(x)=\begin{cases}2x & \text{if }x<2 \\ m & \text{if }x>2\end{cases}$ 。
想要可導需要滿足兩個條件：
1. 在此處連續。
2. 從左逼近其導數值等於從右逼近其導數值。
先滿足 (2)，所以 $2\times {2}=m=4$。
再滿足 (1)，所以 $2^{2}=4(2)+b\implies b=-4$。

3. Two perpendicular lines that intersect on the y-axis and are both tangent to the parabola $y=x^{2}$. Where do these lines intersect? 

Sol:
這題還行，之後可以寫看看，看還會不會。
假設兩條垂直的切線與函數圖形交於 $(a,a^{2}), (-a,a^{2})$。
我們還有 $y'=2x$。
所以我們可以知道兩條切線的斜率：$m_{1}=2a,m_{2}=-2a$。
兩條切線垂直，所以斜率相乘等於負一：$-4a^{2}=-1\implies a=\pm \frac{1}{2}$。(取 $a=\frac{1}{2}$)
接下來我們要算兩條線的交點：$l_{1}:y-\frac{1}{4}=x-\frac{1}{2}$, $l_{2}:y-\frac{1}{4}=-\left( x+\frac{1}{2} \right)$。
解聯立得到：$x=0,y=-\frac{1}{4}\implies\left( 0,-\frac{1}{4} \right)$。

4. Do you think there is a line that is tangent to both $y=x^{2}$ and $y=x^{2}-2x+2$? If so, find its equation. If not, why not?

Sol:
一開始我錯誤的以為，直接使用 $y_{1}'=y_{2}'$ 然後說無解就好。但是，哈哈，還是太年輕太天真了。
假設兩個函數上的點：$(a, a^{2})$ 與 $(b,b^{2}-2b+2)$。
想要尋找公切線，需要使得：在 $m_{a}=m_{b}=m_{ab}$。
我們有：$y_{1}'=2x, y_{2}'=2x-2$
所以有：$2a=2b-2= \frac{a^{2}-b^{2}+2b-2}{a-b}\implies a=\frac{1}{2},b=\frac{3}{2}$。
然後，過 $a$ 做切線：$l:y-\frac{1}{4}=x-\frac{1}{2}$。

5. If $c> \frac{1}{2}$, how many lines through the point $(0,c)$ are **normal lines** to the parabola $y=x^{2}$? What if $c\leq \frac{1}{2}$?

Sol:
感覺跟不是在考微積分...
通過微分，我們可以知道切線斜率，然後就可以知道法線斜率是：$-\frac{1}{2a}$。
(!) 過 $(a,a^{2})$ 做法線：$y-a^{2}=-\frac{1}{2a}(x-a)$。`<-- key`
帶入 $(0,c)$：$c-a^{2}=-\frac{1}{2a}(-a)\implies a=\pm \sqrt{ c-\frac{1}{2} }$。
所以，對於 $c> \frac{1}{2}$ 我們會有兩個 $a\implies$ 兩個法線。還需要加上一個過 $x=0$ 的法線共三條～
對 $c\leq \frac{1}{2}$ $\implies a=0$ 或不存在。所以只有一條法線：$x=0$。

6. Find the limit $\lim_{ \theta \to 0 } \frac{\cos \theta-1}{2\theta^{2}}$ 

Sol:
讓我們先來示範一下**錯誤**做法。
$\lim_{ \theta \to 0 } \frac{\cos \theta-1}{\theta}\times \frac{1}{2\theta}=0\times \lim_{ \theta \to 0 } \frac{1}{2\theta}=0$ 是不正確的，因為我們首先需要明確 Limit product Law 適用範圍。想要可以使用 Limit Laws，則兩者極限應該接存在。顯然 $\lim_{ \theta \to 0 } \frac{1}{2\theta}$ 不存在。
我們稱 $0 \times \infty$ 的形式為不定形，他也不一定等於零，這取決於二者趨近的速度。
正確應該上下同乘 $\cos \theta+1$：
$\lim_{ \theta \to 0 } \frac{\cos \theta-1}{2\theta^{2}}=\lim_{ \theta \to 0 } \frac{\cos^{2}\theta-1}{2\theta^{2}(\cos \theta+1)}=\lim_{ \theta \to 0 } \frac{-\sin^{2}\theta}{2\theta^{2}(\cos \theta+1)}$ 
$-\lim_{ \theta \to 0 }\frac{\sin \theta}{\theta} \times \frac{\sin \theta}{2\theta(\cos \theta+1)}=-1 \times \lim_{ \theta \to 0 } \frac{\sin \theta}{\theta} \times \frac{1}{2} \times \frac{1}{(\cos \theta+1)}$ 
$=-1\times 1\times \frac{1}{2} \times \frac{1}{2}=-\frac{1}{4}$ 

7. Find the limit $\lim_{ x \to \frac{\pi}{4} } \frac{1-\tan x}{\sin x-\cos x}$ 

Sol:
這題應該還好，但是第一次我解的時候粗心解錯，所以希望你在後面複習的時候重新寫寫看。
答案是：$-\sqrt{ 2 }$。

8. The figure shows a circular arc of length $s$ and a chord of length $d$, both subtended by a central angle $\theta$. Find $\lim_{ \theta \to 0^{+} } \frac{s}{d}$. 

![[Pasted image 20251015133344.png]]

Sol:
我們可以觀察出 $s=r\theta$，$d=2r\sin \frac{\theta}{2}$。
那麼 $\lim_{ \theta \to 0^{+} }= \frac{\theta}{2\sin \frac{\theta}{2}}=1$ 。

9. Find all points on the graph of the function $f(x)=2\sin x+\sin^{2}x$ at which the tangent line is horizontal. 

Sol:
先微分：$f'(x)=2\cos x+2\sin x\cos x$ 
然後微分等於零，解 $x$：$f'(x)=2\cos x(\sin x+1)=0\implies 2\cos x=0\text{ or }\sin x+1=0$ 。
$\implies x=\frac{\pi}{2}+k\pi, \frac{3\pi}{2}+2k\pi \quad k \in \mathbb{Z}$ 
$\implies y=3,-1\implies\left( \frac{\pi}{2}+2k\pi,3 \right)\text{ or }\left( \frac{3\pi}{2}+2k\pi, -1 \right)\text{ and } k\in \mathbb{Z}$ 

10. 已知 $\frac{d}{dx}(|x|)=\frac{x}{|x|}$，求 $f(x)=|\sin x|$ 的導數，並說明在哪不可導。

Sol:
$f'(x)= \frac{\sin x}{|\sin x|}\cos x=\begin{cases}\cos x & \text{if }\sin x>0 \\ -\cos x & \text{if }\sin x<0\end{cases}$ 
所以，$f(x)$ 在 $|\sin x|=0$ 時不可導，即 $x=k\pi \quad k \in \mathbb{Z}$ 時不可導。

11. Let $c$ be the x-intercept of the tangent line to the curve $y=b^{x}$ ($b>0, b\neq 1$) at the point $(a,b^{a})$. Show that the distance between the points $(a,0)$ and $(c,0)$ is the same for all values of $a$. 

Sol:
$y'=b^{x}\ln b\implies m_{a}=b^{a}\ln b\implies l: y-b^{a}=(b^{a}\ln b)(x-a)$ 
$\implies-b^{a}=(b^{a}\ln b)(c-a)\implies a-c= \frac{1}{\ln b}\implies |a-c|= \frac{1}{|\ln b|}$ 
$(a,0)$ 到 $(c,0)$ 的距離為 $|a-c|$，而此距離為定值 $\frac{1}{|\ln b|}$。所以對任意 $a$ 值，二者距離不變。

12. If $g(x)+x\sin g(x)=x^{2}$, find $g'(0)$. 

Sol:
這題超簡單的誒，竟然第一次有矇逼到。
反正隱微分可以得到 $g'(0)=-\sin g(0)$。
啊第一次看到這個就想說題目沒給 $g(0)$ 然後就不會，沒想到可以解解看 $g(0)$。
反正 $x$ 帶 0 進去解就知道 $g'(0)=-\sin g(0)=0$ 就好。

13. Show by implicit differentiation that the tangent line to the ellipse $\frac{x^{2}}{a^{2}}+ \frac{y^{2}}{b^{2}}=1$ at the point $(x_{0},y_{0})$ has equation $\frac{x_{0}x}{a^{2}}+\frac{y_{0}y}{b^{2}}=1$. 

Sol:
首先上一波隱微分，需要注意，不要把 $a,b$ 當成變量，它們是常量。
可以輕易的得到直線方程：$y-y_{0}= -\frac{b^{2}x_{0}}{a^{2}y_{0}}(x-x_{0})$。
然後捏，左右同乘 $\frac{y_{0}}{b^{2}}$ 得到 $\frac{x_{0}x}{a^{2}} + \frac{y_{0}y}{b^{2}}=\frac{x_{0}^{2}}{a^{2}}+\frac{y_{0}^{2}}{b^{2}}=1$ 
`~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^ 因為在圖形上，所以等於一喔`

14. Show that the given families of curve ar orthogonal trajectories of each other.
    $y=cx^{2}$           $x^{2}+2y^{2}=k$。

Sol:
首先求第一個方程式的導數：$y'=2cx$。
帶入 $c=\frac{y}{x^{2}}$ 消去常數 $\implies y'=\frac{2y}{x}$ 。
然後，隱微分第二個方程得到：$y'=-\frac{x}{2y}$。
因為 $m_{1}\times m_{2}=\frac{2y}{x} \times \left( - \frac{x}{2y} \right)=-1$ 所以命題成立。
(課本的方法爛)

15. Show that $\lim_{ n \to \infty }\left( 1+\frac{x}{n} \right)^{n}=e^{x}$ for any $x>0$. 

Sol:
(I)
此法簡潔有力，適合考試書寫。
令 $m=\frac{n}{x}$，則 $n=mx$ 且 $m\to \infty$ as $n \to \infty$。
則 $\lim_{ n \to \infty }\left( 1+\frac{x}{n} \right)^{n} = \lim_{ m \to \infty }\left( 1+\frac{1}{m} \right)^{mx}= \lim_{ m \to \infty }\left[ \left( 1+\frac{1}{m} \right)^{m} \right]^{x} =e^{x}$。

(II)
此法無需依賴，顯現扎實功底。
令 $f(x)=\ln x$，那麼 $f'\left( \frac{1}{x} \right)=x$。
利用定義展開：$f'\left( \frac{1}{x} \right)=\lim_{ h \to 0 } \frac{\ln\left( \frac{1}{x}+h \right)-\ln\left( \frac{1}{x} \right)}{h}=\lim_{ h \to 0 }\ln(1+xh)^{1/h}=\ln(\lim_{ h \to 0 }(1+xh)^{1/h})$ 。
`~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^ 因為 ln 在(0, infty) 連續`
又 $e^{x}=e^{\ln(\lim_{ h \to 0 }(1+xh)^{1/h})}=\lim_{ h \to 0 }(1+xh)^{1/h}$。
令 $n=\frac{1}{h}$ 則，$n\to \infty$ as $h\to 0^{+}\implies \lim_{ n \to \infty }\left( 1+\frac{x}{n} \right)^{n}=e^{x}$。

16. Estimate $\cos29^{\circ}$. 

Sol:
(I)
令 $f(x)=\cos\left( \frac{\pi}{6}-x \right)$。則在 $x=0$ 附近的 linearization 為：$L(x)= \frac{\sqrt{ 3 }}{2}-\frac{x}{2}$ 。
取 $x=\frac{\pi}{180}$，則 $f\left( -\frac{\pi}{180} \right)=\cos29^{\circ}\approx L\left( -\frac{\pi}{180} \right)=\frac{\sqrt{ 3 }}{2}+\frac{\pi}{360}$ 

(II)
令 $y=f(x)=\cos x$，則 $dy=-\sin x \ dx$
取 $x=\frac{\pi}{6}$，$dx=-\frac{\pi}{180}$，則 $dy=\frac{\pi}{360}$。
$f\left( \frac{\pi}{6}-\frac{\pi}{180} \right)=\cos29^{\circ} \approx f\left( \frac{\pi}{6} \right)+dy= \frac{\sqrt{ 3 }}{2}+\frac{\pi}{180}$ 

17.   The circumference(圓周長) of a sphere was measured to be 84 cm with a possible error of 0.5 cm. (a) Use differentials to estimate the maximum error in the calculated surface area. What is the relative error? (b) Use differentials to estimate the maximum error in the calculated volume. What is the relative error?

Sol:
(a)
我們有 $2\pi r=84\implies r=\frac{84}{2\pi}$ 與 $dr=\Delta r=\frac{0.5}{2\pi}=\frac{1}{4\pi}$ 
$S=4\pi r^{2}$ 
$dS=8\pi r \ dr$ 
$\frac{\Delta S}{S}\approx \frac{dS}{S}=\frac{8\pi r \ dr}{4\pi r^{2}}= \frac{2dr}{r}= \frac{1}{2\pi}\times \frac{2\pi}{84}\approx 1.12\%$ 

(b)
$V=\frac{4}{3}\pi r^{3}$ 
$dV=4\pi r^{2}dr$ 
$\frac{\Delta V}{V}\approx \frac{dV}{V}= \frac{4\pi r^{2}dr}{\frac{4}{3}\pi r^{3}}=\frac{3dr}{r}=\frac{3}{4\pi}\times \frac{2\pi}{84}\approx 1.8\%$ 

18. If a current I passes through a resistor with resistance R, Ohm’s Law states that the voltage drop is V− RI. If V is constant and R is measured with a certain error, use differentials to show that the relative error in calculating I is approximately the same (in magnitude) as the relative error in R.

Sol:
$V=IR\implies I=\frac{V}{R}\implies dI=-\frac{V}{R^{2}}dR$ 
The relative error in I is: $\frac{\Delta I}{I}\approx \frac{dI}{I}=-\frac{V}{R^{2}}dR \times \frac{R}{V}=-\frac{dR}{R}$ 
The relative error in R is: $\frac{\Delta R}{R}\approx \frac{dR}{R}$ 
所以，the relative error in I 與 the relative error in R 大小大約相同。

# 大會考

1. Let $f\left( \frac{1+x}{1-x} \right)=x$ . Find $f'(2)$. 

Sol:
令 $g(x)=\frac{1+x}{1-x}$，則 $f(g(x))=x$。
隱微分：$f'(g(x))g'(x)=1\implies f'(g(x))=\frac{1}{g'(x)}$。
對 $g(x)$ 微分： $g'(x)=\frac{2}{(1-x)^{2}}$。
我們要找 $f'(2)$，令 $g(x)= \frac{1+x}{1-x}=2\implies x=\frac{1}{3}$。
那麼 $f'(2)=\frac{1}{g'\left( \frac{1}{3} \right)}=\frac{2}{9}$。