
# Curves Defined by Parametric Equations

假設 $x$ 與 $y$ 都為第三個變量 $t$ 的函數，則：

$$
x=f(t)\quad y=g(t)
$$

稱為**參數式(parametric equation)**。對於每個 $t$，我們都可以畫出一個點 $(x,y)=(f(t),g(t))$。這些點會形成**參數曲線(parametric curve)**。

有時，如果可以將 $t$ 用 $x$ 或 $y$ 表達，我們有機會把參數式化為一個函數。消去 $t$ 的過程稱為 eliminating the parameter，可以幫助觀察參數式的圖形樣貌。

一個由以下參數式描述的曲線：

$$
x=f(t)\quad y=g(t) \quad a\leq t\leq b
$$

具有**起始點(initial point)** $(f(a),g(a))$ 與**終止點(terminal point)** $(f(b),g(b))$。

以下參數式描述了位於點 $(h,k)$ 且半徑為 $r$ 的圓：

$$
x=h+r\cos t\quad y=k+r\sin t\quad 0\leq t\leq2\pi
$$

## The Cycloid

一個圓周上的點 $P$ 隨著圓的滾動畫出的圖形稱為**擺線(cycloid)**。

![[Pasted image 20251205165714.png]]

![[Pasted image 20251205165858.png]]

因為 $OT$ 代表圓滾過的長度，所以會等於 $\text{arc }PT$。那麼 $P$ 點座標可以寫成：

$$
x=r(\theta-\sin \theta) \quad
y=r(1-\cos \theta) \quad
\theta\in \mathbb{R}
$$

# Calculus with Parametric Curves

## Tangents

當我們想要找參數式 $x=f(t)\quad y=g(t)$ 的斜率，其中 $f,g$ 接連續且 $y$ 為 $x$ 的可導函數。則由 Chain Rule 我們有：

$$
\frac{dy}{dt}= \frac{dy}{dx} \frac{dx}{dt}
$$

若 $\frac{dx}{dt}\neq 0$，則：

$$
\frac{dy}{dx}= \frac{\frac{dy}{dt}}{\frac{dx}{dt}}\quad\text{if } \frac{dx}{dt}\neq 0
$$

可以發現，如果 $\frac{dy}{dt}=0$ 但 $\frac{dx}{dt}\neq{0}$，則為水平切線。(因為 $x$ 仍然在改變)

相反，如果 $\frac{dx}{dt}=0$ 但 $\frac{dy}{dt}\neq 0$，則為鉛直切線。

需要注意的是，如果 $\frac{dy}{dt}=\frac{dx}{dt}=0$ 則為不定型，需要使用其他方法求解。

如果需要計算二次微分，可以將上式的 $y$ 代替為 $\frac{dy}{dx}$：

$$
\frac{d^{2}y}{dx^{2}}=\frac{d}{dx}\left( \frac{dy}{dx} \right)=\frac{\frac{d}{dt}\left( \frac{dy}{dx} \right)}{\frac{dx}{dt}}
$$

注意，這個式子很容易把不等號寫成等號：$\frac{d^{2}y}{dx^{2}}\neq\frac{\frac{d^{2}y}{dt^{2}}}{\frac{d^{2}x}{dt^{2}}}$。

## Areas

一般來說，如果 $y=F(x)$ 且恆正，則 $y$ 從 $a$ 到 $b$ 的面積為 $\int_{a}^{b}F(x) \ dx$。

那麼，參數式 $x=f(t)\quad y=g(t)$ 且 $\alpha\leq t\leq\beta$ 構成的曲線下的面積為：

$$
\int_{a}^{b}y \ dx=\int_{\alpha}^{\beta}g(t)f'(t) \ dt\quad\left[ \text{or }\int_{\beta}^{\alpha}g(t)f'(t) \ dt \right]
$$

因為 $dx=f'(t) \ dt$。

## Arc Length

經由中間值定理，我們可以找到 $\Delta x_{i}=f'(x^{*}_{i})\Delta t$ 與 $\Delta y_{i}=g'(x_{i}^{**})\Delta t$，所以：

如果曲線 $C$ 由 $x=f(t) \quad y=g(t)$ 描述且 $\alpha\leq t\leq\beta$，$f',g'$ 在 $[\alpha,\beta]$ 上連續，且 $C$ 隨著 $t$ 從 $\alpha$ 增加到 $\beta$ 正好被遍歷一次，則 $C$ 的長度為：

$$
L=\int_{\alpha}^{\beta}\sqrt{ \left( \frac{dx}{dt} \right)^{2}+\left( \frac{dy}{dt} \right)^{2} } \ dt
$$

注意，此時 $ds=\sqrt{ \left( \frac{dx}{dt} \right)^{2}+\left( \frac{dy}{dt} \right)^{2} } \ dt$。

而 arc length function 就是：

$$
s(t)=\int_{\alpha}^{t}\sqrt{ \left( \frac{dx}{du} \right)^{2}+\left( \frac{dy}{du} \right)^{2} } \ du
$$

若想求某時刻的速度，且 $s(t)$ 代表沿著曲線走過的距離：

$$
v(t)=s'(t)=\sqrt{ \left( \frac{dx}{dt} \right)^{2}+\left( \frac{dy}{dt} \right)^{2} }
$$

需要注意的是，一般的使用 $\frac{dy}{dx}$ 求速度會用在一維運動計算上。如果使用的是二維運動，且使用參數式表達位置，則要使用上述公式計算！

## Surface Area

好，那接下來就是表面積公式。

在同樣的假設條件下，若 $C$ 對著 $x$ 軸旋轉，則表面積為：

$$
S=\int_{\alpha}^{\beta}2\pi y\sqrt{ \left( \frac{dx}{dt} \right)^{2}+\left( \frac{dy}{dt} \right)^{2} } \ dt
$$

注意到，$S=\int2\pi y \ ds$ 與 $S=\int2\pi x \ ds$ 的公式仍舊存在，只是此時 $ds$ 為在此節定義的那個公式。

# Tips

- 注意，這個式子很容易把不等號寫成等號：$\frac{d^{2}y}{dx^{2}}\neq\frac{\frac{d^{2}y}{dt^{2}}}{\frac{d^{2}x}{dt^{2}}}$。
- 判斷好上下界，對哪個變量積就對那個變量取上下界，然後帶入參數式求解！
- 判斷好對 $x$ 與 $y$ 來說，應不應該加負號！
- 因為求面積是對 $x$ 積分，所以應該考慮 $x$ 的大小 ($x$ 的增長)。但是求 arc length 是對 $t$ 積分，所以應該考慮 $t$ 的大小 (曲線的遍歷方式)。

# 重要例題

Find the point at which the parametric curve intersects itself and the corresponding values of t. 
$x=2t-t^{3}\quad y=t-t^{2}$ 

Sol:
也就是說，我們要找到兩個數 $a,b$ 且 $a< b$ 使得 $x(a)=x(b)$ 且 $y(a)=y(b)$。
從 $y$ 下手：$a-a^{2}=b-b^{2}\implies (a-b)-(a^{2}-b^{2})=0$ 
$\implies(a-b)-(a-b)(a+b)=0\implies(a-b)(1-(a+b))=0\implies a+b=1$ ($\because a\neq b$)
考慮 $x$：$2a-a^{3}=2b-b^{3}\implies2(a-b)-(a^{3}-b^{3})=0\implies2(a-b)-(a-b)(a^{2}+ab+b^{2})=0$ 
$\implies(a-b)(2-(a^{2}+ab+b^{2}))=0\implies a^{2}+ab+b^{2}=2\implies(a+b)^{2}-ab=2\implies ab=-1$ 
$\implies a-a^{2}=-1\implies a=\frac{1}{2}- \frac{\sqrt{ 5 }}{2},b=\frac{1}{2}+ \frac{\sqrt{ 5 }}{2}$ 

Find the area enclosed by the given parametric curve and the y-axis.
![[Pasted image 20251206113546.png]]

Sol:
注意，這裡上下界不能無腦帶 $0,2\pi$！你跑一次就會發現 $0\leq t\leq2\pi$ 會導致曲線跑了兩次。
那又要注意了，直接寫 $\int_{0}^{\pi }x \ dy$ 是不是就對了勒？
天真，會差一個負號。因為我們要從 $y=-1$ 積到 $y=1$，所以要寫 $\int_{-1}^{1}x \ dy$！
那麼代回參數式，可得真正的上下界：$\int_{\pi}^{0}x \ dy$。
繼續解就可得 $=\frac{4}{3}$。

Find the area enclosed by the given parametric curve and the y-axis.
![[Pasted image 20251206115424.png]]
Sol:
注意，此處的 $x$ 因為向左，所以必須加上負號。
$\implies-\int_{0}^{2}(t^{2}-2t)\left( \frac{1}{2}t^{-1/2} \right) \ dt=\frac{8\sqrt{ 2 }}{15}$ 