
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

回想我們定義自然常數 $e$ 在 $x=0$ 時斜率為 $1$。所以，$e$ 的定義如下：

$$
\boxed{\lim_{ h \to 0 } \frac{e^{h}-1}{h}=1 }
$$

而且，我們可以得到 $e$ 的導數：

$$
\boxed{\frac{d}{dx}e^{x}=e^{x}}
$$

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

但是你想喔，$F(x)$ 一定是可導的嘛，那可導是不是必連續呀？說明什麼捏？說明 $x=0$ 是不是根本不在函數的定義域裡面呢？所以可以放心的約掉 $x$ 啦！

# Tips

- $x^{n}-a^{n}=(x-a)\sum_{k=0}^{n-1}x^{n-1-k}a^{k}$ 
- 對於簡單的 $\frac{d}{dx} \frac{a}{x^{2}}$，我們可以先化為 $\frac{d}{dx} (ax^{-2})=-2ax^{-3}$，避免腦子壞掉犯錯。
- 如何求某多項式函數在哪點有垂直切線？先對該函數求導，然後觀察其導數在哪點不存在。通常是分母為零。
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
$\because 2e^{x}\geq 0$ and $15x^{2}\geq 0 \therefore\text{min}\{y'\}=3$ 

