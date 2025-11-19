
# The Area and Distance Problems

## The Area Problem

將一個曲線水平切成 $n$ 份，如果每塊的高取**右端點(right end point)**，我們將這種估計記為：$R_{n}$。

相反，如果高取**左端點(left end point)**，則記為 $L_{n}$。

若在區間 $[a,b]$ 上定義定義 $\Delta x = \frac{b-a}{n}$，而 $x_{i}$ 為：$a+i\Delta x$。則當 $n\to \infty$ 時，所預估出來的值會等於欲求面積，也就是：

$$
A=\lim_{ n \to \infty } R_{n}=\lim_{ n \to \infty } [f(x_{1})\Delta x+\dots+f(x_{n})\Delta x]=\lim_{ n \to \infty } L_{n}
$$

除了使用左右端點，我們可以在 $[x_{i-1}, x_{i}]$ 之中隨機選擇一個點 $x_{i}^{*}$ 當作 sample point。

那麼，我們有：

$$
A=\lim_{ n \to \infty } [f(x_{1}^{*})\Delta x+\dots+f(x_{n}^{*})\Delta x]
$$

這個東西稱作**黎曼和(Riemann sum)**。

讓我們用求和記號表達這些公式：

$$
A=\lim_{ n \to \infty } \sum_{i=1}^{n}f(x_{i})\Delta x=\lim_{ n \to \infty } \sum_{i=1}^{n}f(x_{i-1})\Delta x=\lim_{ n \to \infty } \sum_{i=1}^{n}f(x_{i}^{*})\Delta x
$$

# The Definite Integral

## The Definite Integral

若函數 $f$ 在 $a\leq x\leq b$ 間**有定義**(實際情況並不要求 $a\leq b$ )，我們將 $[a,b]$ 切割成 $n$ 等份，並將寬度記為 $\Delta x= \frac{b-a}{n}$。令 $(a)=x_{0},x_{1},\dots,x_{n}=(b)$ 為這些子區間的端點，$x_{1}^{*},\dots,x_{n}^{*}$ 為子端點間的 sample point，所以 $x_{i}^{*}$ 會落在 $[x_{i-1},x_{i}]$ 上。

我們定義 $f$ 從 $a$ 到 $b$ 的**定積分(definite integral)** 為：

$$
\int_{a}^{b}f(x) \ dx=\lim_{ n \to \infty } \sum_{i=1}^{n}f(x_{i}^{*})\Delta x
$$

若此極限存在且對於任意 sample point 都保持定值，則稱 $f$ 在 $[a,b]$ 可微。

我們介紹一個定理來判斷函數是否可積。

若 $f$ 在閉區間 $[a,b]$ 連續或者僅含有限個 jump discontinuities，則 $f$ 在閉區間內可積。

為了方便，我們通常將 sample points 取右端點，也就是：

$$
\int_{a}^{b}f(x)=\lim_{ n \to \infty } \sum_{i=1}^{n}f(x_{i})\Delta x
$$

其中，$\Delta x= \frac{b-a}{n}$，$x_{i}= a+i\Delta x$。

## Evaluating Definite Integrals

為了計算定積分的值，我們需要一些求和公式：

$$
\begin{align}
 & \sum_{i=1}^{n}1=n \\
 & \sum_{i=1}^{n}i= \frac{n(n+1)}{2} \\
 & \sum_{i=1}^{n}i^{2}= \frac{n(n+1)(2n+{1})}{6} \\
 & \sum_{i=1}^{n}i^{3}=\left[ \frac{n(n+1)}{2} \right]^{2}
\end{align}
$$

我們還需要知道一些公式：

$$
\begin{align}
 & \sum_{i=1}^{n}ca_{i}=c\sum_{i=1}^{n}a_{i} \\
 & \sum_{i=1}^{n}(a_{i}\pm b_{i})=\sum_{i=1}^{n}a_{i}\pm \sum_{i=1}^{n}b_{i}
\end{align}
$$

## The Midpoint Rule

通常，我們將 sample points 取右端點是因為方便計算。若我們的目標是大略估算積分的值，我們可以將 sample point 取子區間中的中間值，記作 $\bar{x_{i}}$。

也就是：

$$
\int_{a}^{b}f(x) \ dx\approx \lim_{ n \to \infty } \sum_{i=1}^{n}f(\bar{x_{i}})\Delta x
$$

## Properties of the Definite Integral

介紹一些積分的性質。

$$
\begin{align}
 & \int_{a}^{b}f(x)\ dx=-\int_{b}^{a}f(x) \ dx \\
 & \int_{a}^{a}f(x) \ dx = 0 \\
 & \int_{a}^{b}c \ dx=c(b-a)\quad\quad\quad\quad\quad\quad\text{,where } c\text{ is any constant} \\
 & \int_{a}^{b}[f(x)\pm g(x)] \ dx = \int_{a}^{b}f(x) \ dx\pm\int_{a}^{b}g(x) \ dx \\
 & \int_{a}^{b}cf(x) \ dx =c\int_{a}^{b}f(x) \ dx\quad\quad\text{,where }c\text{ is any constan} \\ \\
 & \int_{a}^{b}f(x) \ dx + \int_{b}^{c}f(x)=\int_{a}^{c}f(x) \ dx
\end{align}
$$

(!以下性質可以拿來考不等式判斷的題目，例如重要例題 3) 上述性質不用考慮 $a,b$ 的大小皆可成立，但下列性質必須保證 $a\leq b$。

$$
\begin{align}
 & \text{If }a\leq b\text{ then:} \\
 & \text{If }f(x)\geq0\text{, then }\int_{a}^{b}f(x)\ dx\geq0\text{. } \\
 & \text{If }f(x)\geq g(x)\text{, then }\int_{a}^{b}f(x) \ dx\geq \int_{a}^{b}g(x) \ dx \\
 & \text{If }m\leq f(x)\leq M\text{, then }m(b-a)\leq\int_{a}^{b}f(x) \ dx\leq M(b-a)
\end{align}
$$

想證明最後一個性質，我們可以使用倒數第二個性質幫忙。證明起來很簡單，留給讀者當證明作業。(哇塞，竟然有一天我也可以說出這麼欠揍的話)

最後一個性質可以幫助預估積分的粗略大小範圍。

# The Fundamental Theorem of Calculus

## The Fundamental Theorem of Calculus, Part 1

考慮如下函數：

$$
g(x)=\int_{a}^{x}f(t)\ dt \Leftrightarrow g'(x)=f(x)
$$

其中，$f(x)$ 在 $[a,b]$ 上**連續**而 $g(x)$ 在 $[a,b]$ 上連續且可導(可導不是條件，而是必然的結果)，並且 $a\leq x\leq b$。

proof:
令 $x,x+h$ 在 $(a,b)$ 上。
$g(x+h)-g(x)=\int_{a}^{x+h}f(t)\ dt-\int_{a}^{x}f(t)\ dt=\int_{a}^{x}f(t) \ dt+\int_{x}^{x+h}f(t) \ dt-\int_{a}^{x}f(t) \ dt$ 
$=\int_{x}^{x+h}f(t) \ dt$ 
那麼，對於 $h\neq 0$ 我們有 $\frac{g(x+h)-g(x)}{h}=\frac{1}{h}\int_{x}^{x+h}f(t) \ dt$。
假設 $h>0$，因為 $f$ 在 $[x,x+h]$ 上連續，根據極值定理可以找到兩個數 $u,v$ 使得 $f(u)=m$ 為全局最小值，$f(v)=M$ 為全局最大值。(在 $[x,x+h]$ 上)
也就是：$mh\leq \int_{x}^{x_{h}}f(t) \ dt\leq Mh\implies f(u)\leq \frac{1}{h}\int_{x}^{x_{h}}f(t) \ dt\leq f(v)$ 。
代回 $\frac{g(x+h)-g(x)}{h}=\frac{1}{h}\int_{x}^{x+h}f(t) \ dt$，得到 $f(u)\leq\frac{g(x+h)-g(x)}{h}\leq f(v)$。
同理，對於 $h<0$ 我們也可以得到相同結論。
因為 $f$ 在 $[x,x+h]$ 連續，得到 $\lim_{ h \to 0 }f(u)=\lim_{ u \to x }f(u)=f(x)$ 與 $\lim_{ h \to 0 }f(v)=\lim_{ v \to x }f(v)=f(x)$。
根據夾擠定理，我們有 $\lim_{ h \to 0 } \frac{g(x+h)-g(x)}{h}=f(x)$。

如果用萊布尼茲(Leibniz) 的符號寫，就是：$\frac{d}{dx}\int_{a}^{x}f(t) \ dt=f(x)$。

## The Fundamental Theorem of Calculus, Part 2

若 $F$ 為 $f$ 的反導函數($F'=f$)，且 $f$ 在 $[a,b]$ 上連續，則：

$$
\int_{a}^{b}f(x) \ dx=F(b)-F(a)
$$

proof:
令 $g(x)=\int_{a}^{x}f(t) \ dt$，則有 $g'(x)=f(x)$。
若找到另一個反函數 $F(x)$，我們可知 $F(x)=g(x)+C$，$C$ 為常數。
若取 $g(a)=\int_{a}^{a}f(t) \ dt=0$，我們可以構建：
$F(b)-F(a)=[g(b)+C]-[g(a)+C]=g(b)=\int_{a}^{b}f(t) \ dt$ 

# Tips

- 估計積分時，需要注意函數在區間內的**遞增/減**。
- 在找 antiderivative 時，如果遇到 $(ax+b)^{n}$ 之類的形式很難找反導函數，可以考慮把括號展開。
- 若 $u$ 為 $x$ 的函數，且 $g(x)=\int_{0}^{u}f(t) \ dt$。則 $g'(x)=f(u) \frac{du}{dx}$。(因爲 $\frac{d}{dx}g(x)=\frac{d}{du}g(x) \frac{du}{dx}$)
- $\cos(x^{2})$ 的反導函數**不是** $\frac{\sin(x^{2})}{2x}$。相反，我們(以我們的實力來說)找不到他的反導函數。

# 重要例題

1. When $\int_{-4}^{2}f(x) \ dx=-3$, evaluate $\int_{-4}^{2}[f(x)+2x+5] \ dx$. 

Sol:
這邊需要注意，我在寫題目的時候不知道為啥腦子壞掉了，把問題化簡成 $(-3) + 2x+5$，但不能這樣算。正確算法如下。
$\int_{-4}^{2}[f(x)+2x+5] \ dx=-3+2\int_{-4}^{2}x \ dx+5\times 6=15$ 

2. Use the properties of integrals to verify the inequality without evaluating the integral. (a) $\frac{\pi}{12}\leq \int_{\frac{\pi}{6}}^{\frac{\pi}{3}}\sin x \ dx\leq \frac{\sqrt{ 3 }}{12}$ (b) $\int_{0}^{1}\sqrt{ 1+x^{2} }\leq \int_{0}^{1}\sqrt{ 1+x }$ 

Sol:
(a)
利用函數的極值來解不等式。
因為 $\sin x$ 在 $\left[ \frac{\pi}{6}, \frac{\pi}{3} \right]$ 上的全局最小值為 $\sin \frac{\pi}{6}=\frac{1}{2}$，又全局最大值為 $\sin \frac{\pi}{3}=\frac{\sqrt{ 3 }}{2}$。
所以 $\left( \frac{\pi}{3}-\frac{\pi}{6} \right)\left( \frac{1}{2} \right)\leq\int_{\frac{\pi}{6}}^{\frac{\pi}{3}}\sin x \ dx\leq\left( \frac{\pi}{3}-\frac{\pi}{6} \right)\left( \frac{\sqrt{ 3 }}{2} \right)\implies \frac{\pi}{12}\leq\int_{\frac{\pi}{6}}^{\frac{\pi}{3}}\sin x \ dx\leq \frac{\sqrt{ 3 }}{12}$ 
(b)
利用性質當 $a\leq b$ 時 $f(x)\leq g(x)\implies \int_{a}^{b}f(x) \ dx\leq\int_{a}^{b}g(x)\ dx$。
因為在 $[0,1]$ 上 $x^{2}<x$，所以在 $[0,1]$ 上  $\sqrt{ 1+x^{2} }<\sqrt{ 1+x }$。
根據上述性質，有 $\int_{0}^{1}\sqrt{ 1+x^{2} }\ dx\leq \int_{0}^{1}\sqrt{ 1+x }\ dx$。

3. Use properties of integrals, together with $\int_{a}^{b}x\ dx= \frac{a^{2}-b^{2}}{2}$ and $\int_{a}^{b}x^{2}\ dx=\frac{a^{3}-b^{3}}{3}$, to prove the inequality $\int_{1}^{3}\sqrt{ x^{4}+1 }\ dx\geq \frac{26}{3}$. 

Sol:
這題請通靈。
可以通過觀察 $\frac{26}{3}$ 聯想 $\frac{26}{3}=\int_{1}^{3}x^{2}\ dx$，構建答案。
因為 $\sqrt{ x^{4}+1 }\geq \sqrt{ x^{4} }=x^{2}$，所以 $\int_{1}^{3}\sqrt{ x^{4}+1 }\ dx\geq \int_{1}^{3}x^{2}\ dx=\frac{26}{3}$。

4. Use Part 1 of the Fundamental Theorem of Calculus to find the derivative of the function: $y=\int_{e^{x}}^{-1}\ln t \ dt$ 

Sol:
注意這題有兩個考點：
1. Chain Rule
2. $\int_{a}^{b}f(x) \ dx=-\int_{b}^{a}f(x) \ dx$ 

令 $u=e^{x}$，則 $y=\int_{u}^{-1}\ln t \ dt=-\int_{-1}^{u}\ln t \ dt$。
又 $\frac{dy}{dx}= \frac{dy}{du} \frac{du}{dx}\implies y'=-\ln u\cdot \frac{du}{dx}=-\ln e^{x}\cdot e^{x}=-xe^{x}$。(By FTC1)

5.  (a) Show that $1\leq \sqrt{ 1+x^{3} }\leq1+x^{3}$ for all $x\geq0$.  (b) Show that $1\leq \int_{0}^{1}\sqrt{ 1+x^{3} } \ dx\leq 1.25$ .

Sol:
(a)
這題可以用復合函數的思想解。
令 $f(u)=\sqrt{ u }$，則 $f'(u)=\frac{1}{2\sqrt{ u }}>0\quad \forall u>0\implies f$ 在 $u>0$ 時單調遞增。
代入 $u=1+x^{3}\implies f(1+x^{3})=\sqrt{ 1+x^{3} }$。
因為在 $x\geq0$ 時 $u>0$，所以 $\sqrt{ 1+x^{3} }$ 在 $[0,\infty)$ 單調遞增。
$\implies f(1+0)=1$ 為 $f(1+x^{3})$ 在 $[0,\infty)$ 上的全局最小值 $\implies 1\leq \sqrt{ 1+x^{3} }$。
令 $g(t)=t^{2}-t\implies g'(t)=2t-1\implies g$ 在 $t> \frac{1}{2}$ 時單調遞增，且 $g(1)=0$。
代入 $t=\sqrt{ 1+x^{3} }\implies g(\sqrt{ 1+x^{3} })=1+x^{3}-\sqrt{ 1+x^{3} }$。
因為 $\sqrt{ 1+x^{3} }\geq 1$，所以 $g(\sqrt{ 1+x^{3} })$ 在 $[0,\infty)$ 上單調遞增且 $\geq 0$。
也就是 $1+x^{3}-\sqrt{ 1+x^{3} }\geq0\implies \sqrt{ 1+x^{3} }\leq 1+x^{3}$。
所以，$1\leq \sqrt{ 1+x^{3} }\leq1+x^{3}$。
(b)
$\int_{0}^{1}1 \ dx=\int_{0}^{1}\sqrt{ 1+x^{3} } \ dx\leq \int_{0}^{1}1+x^{3} \ dx$ 
$\implies 1\leq \int_{0}^{1}\sqrt{ 1+x^{3} }\leq1.25$ 

# 大會考

1. Which one of the following statements is TRUE for $\int_{0}^{1}e^{-x^{2}}dx=L$? (ans: $\frac{1}{2}(e^{-1/4}+e^{-1})<L<1$)

Sol:
這題使用左右端點和估計面積值。
首先判斷函數的遞增/減。
因為 $e^{-x^{2}}$ 在 $[0,1]$ **遞減**，所以 $R_{n}<L<L_{n}$。
觀察一下題目，決定取 $\Delta x=\frac{1}{2}$。
$L_{n}=\left( f(0)+f\left( \frac{1}{2} \right) \right)\Delta x=\frac{1}{2}(e^{0}+e^{-1/4})=\frac{1}{2}(1+e^{-1/4})<1$ 
$R_{n}=\left( f\left( \frac{1}{2} \right)+f(1) \right)\Delta x=\frac{1}{2}(e^{-1/4}+e^{-1})$ 
$\implies \frac{1}{2}(e^{-1/4}+e^{-1})<L<1$ 