
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

若此極限存在且對於任意 sample point 都保持定值，則稱 $f$ 在 $[a,b]$ 可積。

我們介紹一個定理來判斷函數是否可積。

若 $f$ 在閉區間 $[a,b]$ **連續或者僅含有限個 jump discontinuities**，則 $f$ 在閉區間內可積。

為了方便，我們通常將 sample points 取右端點，也就是：

$$
\int_{a}^{b}f(x) \ dx=\lim_{ n \to \infty } \sum_{i=1}^{n}f(x_{i})\Delta x
$$

其中，$\Delta x= \frac{b-a}{n}$，$x_{i}= \boxed{a}+i\Delta x$。

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
\int_{a}^{b}f(x) \ dx= \lim_{ n \to \infty } \sum_{i=1}^{n}f(\bar{x_{i}})\Delta x
$$

## Properties of the Definite Integral

介紹一些積分的性質。

$$
\begin{align}
 & \int_{a}^{b}f(x)\ dx=-\int_{b}^{a}f(x) \ dx \\
 & \int_{a}^{a}f(x) \ dx = 0 \\
 & \int_{a}^{b}c \ dx=c(b-a)\quad\quad\quad\quad\quad\quad\text{,where } c\text{ is any constant} \\
 & \int_{a}^{b}[f(x)\pm g(x)] \ dx = \int_{a}^{b}f(x) \ dx\pm\int_{a}^{b}g(x) \ dx \\
 & \int_{a}^{b}cf(x) \ dx =c\int_{a}^{b}f(x) \ dx\quad\quad\text{,where }c\text{ is any constant} \\ \\
 & \int_{a}^{b}f(x) \ dx + \int_{b}^{c}f(x)=\int_{a}^{c}f(x) \ dx
\end{align}
$$

(!以下性質可以拿來考不等式判斷的題目，例如重要例題 3) 上述性質不用考慮 $a,b$ 的大小皆可成立，**但下列性質必須保證 $a\leq b$**。

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

其中，$f(x)$ 在 $[a,b]$ 上**連續**而 $g(x)$ 在 $[a,b]$ 上連續且可導(可導不是條件，而是必然的結果)，並且 $a\leq x\leq b$。(注意，若 $f(x)$ 包含有限個 jump discontinuity 時，$g'(x)$ 在 $f(x)$ 連續的那些點仍等於 $f(x)$，但在 jump discontinuity 的那些點通常不滿足此關係式)

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

# Indefinite Integrals and the Net Change Theorem

## Indefinite Integrals

因為反導函數有很多個，我們定義不定積分就是某個函數的所有反導函數的可能。

$$
\int f(x) \ dx=F(x)\quad \text{means}\quad F'(x)=f(x)
$$

因為常數項在微分後會等於零，所以 $F(x)$ 會有一個常數項 $C$ 代表所有可能的值。

下表列出了常見的不定積分對應表：

![[Pasted image 20251119202513.png]]

需要注意，不定積分所得出來的函數(們)可能只在某個區間內成立。比如某個反導函數為：$-\frac{1}{x}+C$ 在 $x=0$ 時未定義。

## The Net Change Theorem

The Net Change Theorem 說：變化率的積分就是淨變化量。

$$
\int_{a}^{b}F'(x) \ dx = F(b)-F(a)
$$

最好理解的例子就是：將速度對時間積分，所得的值為位移量，也就是最終位置減去初始位置。

# The Substitution Rule

## Substitution Indefinite Integrals

若 $u=g(x)$ 為一個可導函數且其值域為 $I$。若 $f$ 在 $I$ 上連續，則：

$$
\int f(g(x))g'(x) \ dx=\int f(u) \ du
$$

proof:
令 $F'(x)=f(x)$。
則 $\int F'(g(x))g'(x) \ dx=F(g(x))+C=F(u)+C=\int F'(u) \ du$ 

對於如何選擇被換元的函數，我們最好挑那種微分後仍部分存在函數中者。

這部分我們可以推出 $\tan x$ 的反導函數：

$$
\int \tan x \ dx=\ln|\sec x|+C
$$

proof:
令 $u=\cos x$，則 $du=-\sin x \ dx$。
$\int \tan x \ dx=\int \frac{\sin x}{\cos x} \ dx=\int \frac{-1}{u} \ du=-\ln|u|+C$ 
$=-\ln|\cos x|+C=\ln|\sec x|+C$ 

## Substitution Definite Integrals

利用換元法求定積分的值有兩種解法：
- 先算不定積分然後代值。
- 修改定積分的上下界。

若 $g'$ 在 $[a,b]$ 上連續且 $f$ 在 $u=g(x)$ 的值域上連續，則：

$$
\int_{a}^{b}f(g(x))g'(x) \ dx=\int_{g(a)}^{g(b)}f(u) \ du
$$

proof:
令 $F$ 為 $f$ 的反導函數，則有：
$\int_{a}^{b}f(g(x))g'(x) \ dx=F(g(x))|^{b}_{a}=F(g(b))-F(g(a))$ 
且：
$\int_{g(a)}^{g(b)}f(u) \ du=F(u)|^{g(b)}_{g(a)}=F(g(b))-F(g(a))$ 

## Symmetry

若 $f$ 在 $[-a,a]$ 上連續，則：
- 若 $f$ 為偶函數則：$\int_{-a}^{a}f(x) \ dx=2\int_{0}^{a}f(x) \ dx$ 
- 若 $f$ 為奇函數則：$\int_{-a}^{a}f(x) \ dx=0$ 

proof:
$\int_{-a}^{a}f(x) \ dx=-\int_{0}^{-a}f(x) \ dx+\int_{0}^{a}f(x) \ dx$ 
令 $u=-x$，則 $du = -dx$ 且當 $x=-a$ 時 $u=a$。
上式變成：$-\int_{0}^{a}f(-u) \ -du+\int_{0}^{a}f(x) \ dx=\int_{0}^{a}f(-u) \ du+\int_{0}^{a}f(x) \ dx$ 
若 $f$ 為偶函數：$\int_{0}^{a}f(-u) \ du+\int_{0}^{a}f(x) \ dx=2\int_{0}^{a}f(x) \ dx$ 
若 $f$ 為奇函數：$\int_{0}^{a}f(-u) \ du+\int_{0}^{a}f(x) \ dx=0$ 

# Tips

- 使用左右端點法估計積分時，需要注意函數在區間內的**遞增/減**(判斷左端點估計出來的較大還是揍端點估計出來的較大)。(與 $a$，$b$ 的大小)
- 在找 antiderivative 時，如果遇到 $(ax+b)^{n}$ 之類的形式很難找反導函數，可以考慮把括號展開。
- 若 $u$ 為 $x$ 的函數，且 $g(x)=\int_{0}^{u}f(x) \ dx$。則 $g'(x)=f(u) \frac{du}{dx}$。(因爲 $\frac{d}{dx}g(x)=\frac{d}{du}g(x) \frac{du}{dx}$，注意分辨這個還有 substitution rule 的差別)
- $\cos(x^{2})$ 的反導函數**不是** $\frac{\sin(x^{2})}{2x}$。相反，我們(以我們的實力來說)找不到他的反導函數。
- 利用圖形判斷積分大小時，記得看圖表 $y$ 軸值。(例如若 $0<y<1$ 時 $f^{2}$ 可能會比 $f$ 小)
- 不會積的時候試試看用估計的。
- $\tan^{2}\theta=\sec^{2}\theta-1$ 
- 使用換元法前，檢測替換的元素微分後是否仍存在於原式中。(用於 $du=g'(x) \ dx$)
- 如果反導函數是 $\ln|g(x)|$ 的形式，考慮 $g(x)$ 是否恆正。若是，則答案必須處除絕對值。
- $u=2x$，則 $du=2dx$ 而不是 $du=dx$，小菜菜。
- 不定積分得出的 $u$ 需要替換回 $g(x)$，但是定積分如果 $\int_{g(a)}^{g(b)}f(u) \ du$ 就不用替換回 $g(x)$，除非是 $\int_{a}^{b}f(u) \ du$。
- 將 $\int_{0}^{1}\sqrt{ 1-x^{2} } \ dx$ 視為求半徑為 $1$ 的圓的 $\frac{1}{4}$ 面積：$\frac{1}{4}\pi$。

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

4. Use Part 1 of the Fundamental Theorem of Calculus to find the derivative of the function: $y=\int_{e^{x}}^{1}\ln t \ dt$ 

Sol:
注意這題有兩個考點：
1. Chain Rule
2. $\int_{a}^{b}f(x) \ dx=-\int_{b}^{a}f(x) \ dx$ 
(I) (課外寫法)
令 $u=e^{x}$，則 $y=\int_{u}^{1}\ln t \ dt=-\int_{1}^{u}\ln t \ dt$。
又 $\frac{dy}{dx}= \frac{dy}{du} \frac{du}{dx}\implies y'=-\ln u\cdot \frac{du}{dx}=-\ln e^{x}\cdot e^{x}=-xe^{x}$。(By FTC1)
(II) (課內寫法)
令 $u=\ln t$ (因為想令 $u(e^{x})=x$)，則 $du=\frac{1}{t}dt\implies dt=e^{u}du$。
$y = \int^{1}_{e^{x}}\ln t \ dt=\int_{0}^{x}-ue^{u} \ du$ 
$y'=-xe^{x}$ (By FTC1) 注意此處無需帶換回 $\ln t$，有疑慮請回去看 FTC1 的定義。

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
$\int_{0}^{1}1 \ dx\leq\int_{0}^{1}\sqrt{ 1+x^{3} } \ dx\leq \int_{0}^{1}1+x^{3} \ dx$ 
$\implies 1\leq \int_{0}^{1}\sqrt{ 1+x^{3} }\leq1.25$ 

6. Express $\lim_{ n \to \infty }\left( \frac{1}{n^{3}\sqrt{ 4n^{2}+1 }}+\dots+ \frac{n^{3}}{n^{3}\sqrt{ 4n^{2}+n^{2} }} \right)$ as an integral on $[0,1]$. 

Sol:
$\lim_{ n \to \infty }\sum_{i=1}^{n} \frac{i^{3}}{n^{3}\sqrt{ 4n^{2}+i^{2} }}=\lim_{ n \to \infty }\sum_{i=1}^{n} \frac{i^{3}}{n^{4}\sqrt{ 4+\left( \frac{i}{n} \right)^{2} }}=\lim_{ n \to \infty } \frac{1}{n}\sum_{i=1}^{n} \frac{i^{3}}{n^{3}\sqrt{ 4+\left( \frac{i}{n} \right)^{2} }}$ 
$=\lim_{ n \to \infty } \frac{1}{n}\sum_{i=1}^{n} \frac{\left( \frac{i}{n} \right)^{3}}{\sqrt{ 4+\left( \frac{i}{n} \right)^{2} }}=\int_{0}^{1} \frac{x^{3}}{\sqrt{ 4+x^{2} }} \ dx$ 

7. Find the indefinite integral: $\int 2+\tan^{2}\theta \ d\theta$. 

Sol:
發現 $\tan^{2}$，找不到反導函數，於是代換為 $\sec^{2}\theta - 1$。
$\int 2+(\sec^{2}\theta-1) \ d\theta=\int 1+\sec^{2}\theta \ d\theta=\theta+\tan \theta+C$ 

8. Evaluate $\int x\sqrt{ x-2 } \ dx$ 

Sol:
略為思考解決。根號下一坨不好解決，所以換元出去。
令 $u=x-2$，$du=dx$。
$\int x\sqrt{ x-2 }=\int(u+2)\sqrt{ u } \ du=\frac{2}{5}(x+2)^{5/2}-\frac{4}{3}(x+2)^{3/2}+C$ 

9. Evaluate $\int_{0}^{a}x\sqrt{ x^{2}+a^{2} } \ dx$ 

Sol:
令 $u=x^{2}+a^{2}$，則 $du=2xdx$。
$\int_{0}^{a}x\sqrt{ x^{2}+a^{2} } \ dx=\frac{1}{2}\int_{a^{2}}^{2a^{2}}\sqrt{ u } \ du=\frac{1}{2}\left( \frac{2}{3}u^{3/2} \right)|^{2a^{2}}_{a^{2}}$ 
$=\frac{1}{3}[(2a^{2})^{3/2}-(a^{2})^{3/2}]=\frac{1}{3}(2^{3/2}-1)a^{3}=\frac{1}{3}(2\sqrt{ 2 }-1)a^{3}$ 
`~~~~~~~^ 注意此處化簡，不要化簡成 2a^3 了` 

10. Evaluate $\int_{1}^{16} \frac{x^{1/2}}{1+x^{3/4}} \ dx$ 

Sol:
此題重點在於敢代換，並且觀察出可以把分子提出 $x^{3/4}$。(嘿嘿我寫出來了，但是放這讓你複習)
令 $u=1+x^{3/4}$，則 $du= \frac{3}{4}x^{-1/4} \ dx$。
$\int_{1}^{16} \frac{x^{1/2}}{1+x^{3/4}} \ dx=\int_{1}^{16}x^{3/4} \frac{x^{-1/4}}{1+x^{3/4}} \ dx=\frac{4}{3}\int_{2}^{9} \frac{u-1}{u} \ du$ 
$=\frac{4}{3}\left( 7+\ln \frac{2}{9} \right)$ 

10. Use substitution rule to simplify the integral $\int \cos(\ln x) \ dx$. 

Sol:
令 $u=\ln x$，則 $du= \frac{1}{x} \ dx$。
這樣你可能就矇逼了，但是你大意了：$dx = x \ du = e^{u} \ du$。
所以 $\int \cos(\ln x) \, dx=\int e^{t}\cos t \, dt$。

# 大會考

1. Which one of the following statements is TRUE for $\int_{0}^{1}e^{-x^{2}}dx=L$? (ans: $\frac{1}{2}(e^{-1/4}+e^{-1})<L<1$)

Sol:
這題使用**左右端點和估計面積值**。(嘗試代換你會發現換不了一點)
首先判斷函數的遞增/減。
因為 $e^{-x^{2}}$ 在 $[0,1]$ **遞減**，所以 $R_{n}\leq L\leq L_{n}$。
觀察一下題目，決定取 $\Delta x=\frac{1}{2}$。
$L_{n}=\left( f(0)+f\left( \frac{1}{2} \right) \right)\Delta x=\frac{1}{2}(e^{0}+e^{-1/4})=\frac{1}{2}(1+e^{-1/4})<1$ 
$R_{n}=\left( f\left( \frac{1}{2} \right)+f(1) \right)\Delta x=\frac{1}{2}(e^{-1/4}+e^{-1})$ 
$\implies \frac{1}{2}(e^{-1/4}+e^{-1})<L<1$ 

2. Let $I=\lim_{ x \to 0^{+} } \frac{1}{x}\left( \int_{1-x}^{1} \frac{1}{t^{3}+t} \ dt \right)$, find $I$。

Sol:
這題我會，但是感覺很經典所以記錄一下。
這題重點在用洛必達還有利用 FTC1 替換積分。
令 $g(x)=\int_{1-x}^{1} \frac{1}{t^{3}+t} \ dt=-\int_{1}^{u} \frac{1}{t^{3}+t}  \, dt$，則 $g'(x)= \frac{1}{u^{3}+u}= \frac{1}{(1-x)^{3}+(1-x)}$。
那麼 $I=\lim_{ x \to 0^{+} } \frac{g(x)}{x} \stackrel{\left( \frac{0}{0} \right)}{=}\lim_{ x \to 0^{+} } g'(x)=\frac{1}{2}$。

3. Consider $g(x)=\begin{cases} \frac{1}{x}\int_{0}^{\sqrt{ x }} \frac{1}{t^{2}+\sqrt{ t }+1} \ dt & \text{, }x>0 \\ 1 & \text{, }x\leq0\end{cases}$ . Which of the following options are TRUE ? (a) $\lim_{ x \to 0 }g(x)=1$ (b) $\lim_{ x \to \infty }g(x)=0$ (c) $\lim_{ x \to 0 }(\sin x)g(x)=0$ (d) $\lim_{ x \to 1 }g'(x)> 0$. 

Sol:
這題卡在 (c) 忘記換 $\frac{\sin x}{x}$ 還有 (d) 用估計的方式算積分。
令 $f(x)=\int_{0}^{\sqrt{ x }} \frac{1}{t^{2}+\sqrt{ t }+1} \ dt$，則 $f'(x)= \frac{1}{2x^{3/2}+2x^{3/4}+2x^{1/2}}$。
(a)
$\lim_{ x \to 0^{+} }g(x) \stackrel{\left( \frac{0}{0} \right)}{=}\lim_{ x \to 0^{+} }f'(x)=\infty\neq \lim_{ x \to 0^{-} }g(x)=1$ 
(b)
$\lim_{ x \to \infty }g(x)=\lim_{ x \to \infty }f'(x)=0$ 
(c)
$\lim_{ x \to 0 }(\sin x)g(x)=\lim_{ x \to 0 } \frac{\sin x}{x}f(x)=\lim_{ x \to 0 }f(x)=0$ 
(d)
$\lim_{ x \to 1 }g'(x)=\lim_{ x \to 1 } \frac{f'(x)x^{2}-f(x)2x}{x^{2}}=\lim_{ x \to 1 }f'(x)-f(x)$ 
$=\frac{1}{6}-\int_{0}^{1} \frac{1}{t^{2}+\sqrt{ t }+1} \ dt$ 
因為這個積分不好算，我們用估的：$\frac{1}{t^{2}+\sqrt{ t }+1}$ 在 $t\geq0$ 上單調遞減，所以 $\frac{1}{t^{2}+\sqrt{ t }+1}$ 的最小值為 $\frac{1}{3}$。
$\implies \int_{0}^{1}\frac{1}{t^{2}+\sqrt{ t }+1} \ dt \geq \frac{1}{3}$。
$\implies \lim_{ x \to 1 }g'(x)<0$ 
(d) 選項有錯，但是懶得算了。就醬吧。

# 書銘考古

1. Find the limit $\lim_{ n \to \infty } \frac{4}{n^{2}}(\sqrt{ n^{2}-1 }+\sqrt{ n^{2}-4 }+\dots+\sqrt{ n^{2}-n^{2} })$. 

Sol:
$\lim_{ n \to \infty } \frac{4}{n^{2}}(\sqrt{ n^{2}-1 }+\sqrt{ n^{2}-4 }+\dots+\sqrt{ n^{2}-n^{2} })=\lim_{ n \to \infty } \frac{4}{n^{2}}\sum_{i=1}^{n}\sqrt{ n^{2}-i^{2} }$ 
$=\lim_{ n \to \infty } \frac{4}{n^{2}}\sum_{i=1}^{n}n\sqrt{ 1-\left( \frac{i}{n} \right)^{2} }=\lim_{ n \to \infty } \frac{4}{n}\sum_{i=1}^{n}\sqrt{ 1-\left( \frac{i}{n} \right)^{2} }$ 
$=4\int_{0}^{1}\sqrt{ 1-x^{2} } \ dx$ (誒，注意這裡不是 $\int_{0}^{4}\sqrt{ 1-x^{2} } \ dx$ 沒定義誒！！！)
然後注意，這邊還沒學 inverse substitution rule，所以把 $\int_{0}^{1}\sqrt{ 1-x^{2} }$ 視為求半徑為 $1$ 的 $\frac{1}{4}$ 圓面積就好啦。
$\implies4\int_{0}^{1}\sqrt{ 1-x^{2} } \ dx=4\left( \frac{1}{4}\pi \times 1^{2} \right)=\pi$ 

