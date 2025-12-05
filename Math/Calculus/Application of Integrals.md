
# Areas Between Curves

## Area Between Curves: Integrating With Respect to x

當需要計算 $y=f(x)$ 和 $y=g(x)$ 與 $x=a$ 和 $x=b$ 交出的面積 $A$，且 $f,g$ 在 $[a,b]$ 上連續且 $f\geq g$ $\forall x\in[a,b]$，則：

$$
A=\int_{a}^{b}[f(x)-g(x)] \ dx
$$

若我們想放寬條件，也就是不再要求 $f\geq g$，則需要以下求法。

$y=f(x)$ 和 $y=g(x)$ 與 $x=a$ 和 $x=b$ 交出的面積為：

$$
A=\int_{a}^{b}|f(x)-g(x)| \ dx
$$

## Area Between Curves: Integrating With Respect to y

有時將 $x$ 視為 $y$ 的函數更好計算。注意，是直接移項，而不是交換 $x,y$ 否則會變成求反函數。

想計算 $x=f(y)$ 和 $x=g(y)$ 與 $y=a$ 和 $y=b$ 交出的面積，且 $f,g$ 連續 $f(y)\geq g(y)$  $\forall y\in [a,b]$ ，則：

$$
A=\int_{a}^{b}[f(y)-g(y)] \ dy
$$
有的時後，你需要將圖形切成好幾塊思考，例如以下例題：

![[Pasted image 20251202171051.png]]
![[Pasted image 20251202171127.png]]

# Volumes

## Definition of Volume

我們從**柱體(cylinder)** 開始說，一個柱體的邊界由一個平面區域 $B_{1}$ 與平行的平面 $B_{2}$ 形成，其中 $B_{1}$ 稱為 Base。柱體由所有垂直 $B_{1}B_{2}$ 的點形成。若 Base $B_{1}$ 的面積為 $A$，且高度為 $h$ ($B_{1},B_{2}$ 的距離)，則體積公式為：

$$
V=Ah
$$

對於一個非柱體物體，我們把它切成好多塊小柱體來計算體積。

令 $S$ 為 $x=a$ 與 $x=b$ 之間的固體，若 $S$ 與平面 $P_{x}$ (平面垂直 $x$ 軸，且位於 $x$) 的截面積為 $A(x)$。若 $A(x)$ 是一個連續函數，則 $S$ 的體積為：

$$
V=\lim_{ n \to \infty } \sum_{i=1}^{n}A(x_{i}^{*})\Delta x=\int_{a}^{b}A(x) \ dx
$$

## Volumes of Solids of Revolution

這裡的 Revolution 指的是旋轉體。

若我們將某塊區塊繞著某條線轉一圈，我們就得到了一個旋轉體 (solid of revolution)

如果我們想計算旋轉體的體積，(若對 $x$ 軸繞) 你必須曉得每個截面積會等於把 $f(x)$ 的值當半徑的圓的面積。

![[Pasted image 20251202202632.png]]

所以體積應該為：

$$
V=\int_{a}^{b}\pi[f(x)]^{2} \ dx
$$

那如果更複雜些，用到了兩個函數 ($f$ 當外圓半徑，$g$ 當內圓半徑) 交出來的面繞，體積應該為：

$$
V=\int_{a}^{b}\pi([f(x)]^{2}-[g(x)]^{2}) \ dx
$$

例如：

![[Pasted image 20251202203207.png]]

需要注意的是，當不是繞 $x$ 軸旋轉時，你需要好好判斷誰當外誰當內。

比如說如果對 $y=2$ 旋轉上圖，那麼 $2-x^{2}$ 就會變成外圓半徑，$2-x$ 會是內圓半徑。

![[Pasted image 20251202203511.png]]

# Volumes by Cylindrical Shells

有時想要把一個函數切成內外圓再去繞出體積計算有點難，這就是為啥我們需要下述 method of cylindrical shell。

## The Method of Cylindrical Shells

如果我們想計算下圖這種 cylindrical shell 的體積，可以通過計算：
$\pi r_{2}^{2}h-\pi r_{1}^{2}h=\pi(r_{2}^{2}-r_{1}^{2})h=\pi(r_{2}+r_{1})(r_{2}-r_{1})h=2\pi \frac{r_{2}+r_{1}}{2}h(r_{2}-r_{1})$ 
得到。

![[Pasted image 20251203145251.png]]

如果我們令 $r=\frac{r_{1}+r_{2}}{2}$ 為平均半徑，$\Delta r=r_{2}-r_{1}$，則：

$$
V=2\pi rh\Delta r
$$

可以記憶：

$$
V=[\text{circumference}][\text{height}][\text{thickness}]
$$

現在考慮一個 $y=f(x)$ 與 $x=a$ 和 $x=b$ 形成的區域繞 $y$ 軸旋轉：

![[Pasted image 20251203150017.png]]

則體積為：

$$
V=\lim_{ n \to \infty } 2\pi \bar{x}f(\bar{x})\Delta x=\int_{a}^{b}2\pi xf(x) \ dx\quad\text{where }0\leq a<b
$$

## Disks and Washers versus Cylindrical Shells

你需要知道啥時候用啥技巧。

判斷：若一個函數必須被切成兩塊算的時候，好切否？

![[Pasted image 20251203151535.png]]

考慮上圖場景，我們分別使用：
1. 對 $x$ 積分。
2. 對 $y$ 積分。

對 $x$ 積分，顯然要使用本節的 method of cylindrical shell：$V=\int_{0}^{2}2\pi(1+x)(2x-x^{2}) \ dx$。

對 $y$ 積分，要使用之前的 Disk：$V=\int_{0}^{4}\pi\left( [\sqrt{ y }+1]^{2}-\left[ \frac{1}{2}y+1 \right]^{2} \right) \ dy$。

# Average Value of a Function

我們定義 $f$ 在 $[a,b]$ 的平均值為：

$$
f_{\text{avg}}=\frac{1}{b-a}\int_{a}^{b}f(x) \ dx
$$

## The Mean Value Theorem for Integrals

若 $f$ 在 $[a,b]$ 上連續，則 $[a,b]$ 中存在一個數 $c$ 使得：

$$
f(c)=f_{\text{avg}}= \frac{1}{b-a}\int_{a}^{b}f(x) \ dx
$$

也就是：

$$
\int_{a}^{b}f(x) \ dx = f(c)(b-a)
$$

積分的均值定理的幾何意義就是，存在一個點 $c$ 使得 $f(c)=f_{\text{avg}}$ 且與 $x=a$ 和 $x=b$ 構成的矩形面積會等於 $f(x)$ 與 $x=a$ 和 $x=b$ 構成的面積。

proof:
(I)
因為 $f$ 在 $[a,b]$ 上連續，根據極值定理有 $x_{1}\in[a,b]$ 與 $x_{2}\in[a,b]$ 使得 $f(x_{1})=m$ 為 $f$ 在 $[a,b]$ 上的最小值 ，$f(x_{2})=M$ 為 $f$ 在 $[a,b]$ 上的最大值。
因為 $m\leq f(x)\leq M$，所以 $\int_{a}^{b}m \ dx\leq \int_{a}^{b}f(x) \ dx\leq \int_{a}^{b}M \ dx$。
因為 $\frac{1}{b-a}>0$，所以同除 $b-a$ 得到 $m\leq \frac{1}{b-a}\int_{a}^{b}f(x) \ dx\leq M$。
因為 $f$ 在 $[a,b]$ 上連續，根據中間值定理，對於任意 $y\in[m,M]$ 都有一個數 $c\in[x_{1},x_{2}]\subseteq[a,b]$ 使得 $f(c)=y$。
當取 $y$ 為 $\frac{1}{b-a}\int_{a}^{b}f(x) \ dx$ 則一定有一個數使得 $f(c)=\frac{1}{b-a}\int_{a}^{b}f(x) \ dx$。
(II)
令 $F(x)=\int_{a}^{x}f(t) \ dt$。
根據導數的均值定理，我們有 $F(b)-F(a)=F'(c)(b-a)$，其中 $c\in[a,b]$。
$\implies \int_{a}^{b}f(x) \ dx=f(c)(b-a)$ 

# Arc Length

## Arc Length of a Curve

想計算一個曲線的長度，我們可以通過在曲線上以 $\Delta x$ 為間隔，取 $P_{i}=(x_{i},f(x_{1}))$。

則曲線的長度為：

$$
L=\lim_{ n \to \infty } \sum_{i=1}^{n}|P_{i-1}P|
$$

但是，這東西不好算。如果我們有 $f$ 曲線在 $[a,b]$ 連續且可導，並且 $f'$ 連續，就可以使用積分公式幫忙啦～

若計算 $y=f(x)$ 在 $a\leq x\leq b$ 上的長度，則：

$$
L=\int_{a}^{b}\sqrt{ 1+[f'(x)]^{2} } \ dx
$$

proof:
令 $\Delta y=y_{i}-y_{i-1}$。
由均值定理，有 $x_{i}^{*}\in[x_{i-1},x_{i}]$ 使得 $f(x_{i})-f(x_{i-1})=f'(x_{i}^{*})(x_{i}-x_{i-1})$。
也就是：$\Delta y=f'(x_{i}^{*})\Delta x$。($\Delta x>0$)
代入 $|P_{i-1}P|=\sqrt{ (\Delta x)^{2}+(\Delta y)^{2} }=\sqrt{ \Delta x^{2}+[f'(x_{i}^{*})]^{2}(\Delta x)^{2} }=\sqrt{ 1+[f'(x_{i}^{*})]^{2} }\Delta x$ 
那麼 $\lim_{ n \to \infty }\sum_{i=1}^{n}\sqrt{ 1+[f'(x_{i}^{*})]^{2} }\Delta x=\int_{a}^{b}\sqrt{ 1+[f'(x)]^{2} } \ dx$。

## The Arc Length Function

若一個 smooth curve $y=f(x)$ 在 $a\leq x\leq b$，令 $s(x)$ 代表從起始 $(a,f(a))$ 到 $(x,f(x))$ 的長度，則 $s(x)$ 稱為 arc length function：

$$
s(x)=\int_{a}^{x}\sqrt{ 1+[f'(t)]^{2} } \ dt
$$
通過 FTC 1，我們有：

$$
\frac{ds}{dx}=\sqrt{ 1+\left( \frac{dy}{dx} \right)^{2} }
$$

也就是說 $s$ 的微分最小值為 $1$，且此時曲線的斜率為 $0$。

而：

$$
ds=\sqrt{ 1+\left( \frac{dy}{dx} \right)^{2} } \ dx
$$

或者我們也可以寫成：

$$
(ds)^{2}=(dx)^{2}+(dy)^{2}
$$

![[Pasted image 20251204184712.png]]

# Area of Surface of Revolution

首先考慮圓錐的表面積：

![[Pasted image 20251204224708.png]]

如上圖所示，表面積為：

$$
A=\frac{1}{2}l^{2}\theta=\frac{1}{2}l^{2} \frac{2\pi r}{l}=\pi rl
$$

為了計算某個較為複雜的封閉曲線繞出來的表面積，我們可以仿造上一單元求 arc length 的方法，把它們切段利用直線逼近，並取極限。

為了計算切段的表面積，每段都會形如：

![[Pasted image 20251204225245.png]]

而通過一系列其實不是很複雜的運算(大圓錐減小圓錐，並利用相似算 $l_{1}$ 與 $l$ 的關係)，我們可以得到這種東西的表面積為：

$$
2\pi rl
$$

其中，$r=\frac{r_{1}+r_{2}}{2}$。

那麼，若 $f$ 為正且 $f'$ 連續，我們定義 $y=f(x)$ 與 $x=a$，$x=b$ 繞 $x$ 軸旋轉出來的體積的表面積為：

$$
S=\lim_{ n \to \infty } \sum _{i=1}^{n}2\pi f(x_{i}^{*})\sqrt{ 1+[f'(x^{*}_{i})]^{2} }\Delta x=\int_{a}^{b}2\pi f(x)\sqrt{ 1+[f'(x)]^{2} } \ dx
$$

我們還可以寫成：

$$
S=\int_{a}^{b}2\pi y \ ds
$$

因為：

$$
ds=\sqrt{ 1+\left( \frac{dy}{dx} \right)^{2} }\ dx\text{ or }\sqrt{ 1+\left( \frac{dx}{dy} \right)^{2} } \ dx
$$

需要注意的是，$ds$ 用兩個版本中哪個都行！只是最後要決定要不要把 $y$ 用 $x$ 表達！(根據最後是 $dx$ 還是 $dy$ 決定)

# Tips

- 當 $y$ 高於一次方時，考慮把 $x$ 用 $y$ 表達，然後對 $y$ 積分。 
- 算兩函數交出的面積時，判斷好誰上誰下。
- oi，不要看到 $\cos2x-\sin x$ 就自動換成 $\cos 2x=1-2\sin^{2}x$，思考一下是不是不換的反導函數比較簡單？
- 不是啊，$1+x^{2}=1+2x^{2}+x^{4}$ 而非 $1+2x+x^{2}$ 好伐！

# 重要例題

![[Pasted image 20251202181827.png]]

Sol:
不難，主要是提醒你 $c$ 可以是 $\pm 6$。
![[Pasted image 20251202181930.png]]

![[Pasted image 20251203141532.png]]

Sol:
我們來算算這東西的體積。
為了方便，我們把這東西逆時針旋轉 $90^{\circ}$。
![[Pasted image 20251203141648.png]]
現在他的截面積長這樣，那我們切成兩部分算。
$f(x)=R+\sqrt{ r^{2}-x^{2} }$ 與 $g(x)=R-\sqrt{ r^{2}-x^{2} }$，其中 $f$ 當外圓半徑，$g$ 當內圓半徑。
那麼體積就是：$\int_{-r}^{r}\pi([f(x)]^{2}-[g(x)]^{2}) \ dx$ ！

![[Pasted image 20251203142516.png]]

Sol:
四分之一個橫截面長成這樣：
![[Pasted image 20251203142902.png]]
之所以為正方形，是因為所有邊都垂直。
我們有 $\bar{PQ}^{2}=r^{2}-x^{2}$。
那麼體積為：$4\int_{-r}^{r}(r^{2}-x^{2}) \ dx= \frac{16}{3}r^{3}$。

![[Pasted image 20251203175124.png]]

Sol:
這題不好用 method of cylindrical shell，因為要分三段。
![[Pasted image 20251203175220.png]]
我們對 $y$ 積分並使用 washers：$\int_{0}^{3}\pi([y+1+1]^{2}-[(y-1)+1]^{2}) \ dy= \frac{117}{5}\pi$。

![[Pasted image 20251203231817.png]]

Sol:
要計算這個函數的平均值。
不難，我會但是放這裡以免忘記：
$\frac{1}{3}\int_{1}^{4} \frac{e^{1/z}}{z^{2}} \ dz$ 令 $u= \frac{1}{z}$ 則 $du=-\frac{1}{z^{2}} \ dx$ 
$=-\frac{1}{3}\int_{1}^{1/4}e^{u} \ du=\frac{1}{3}(e-e^{1/4})$ 

![[Pasted image 20251204214600.png]]

Sol:
只能說，這種計算題很噁心，不想寫一點。
$y=(1-x^{2/3})^{3/2}\implies y'=\frac{3}{2}(1-x^{2/3})^{1/2}\left( -\frac{2}{3}x^{-1/3} \right)=-(x^{-2/3}-1)^{1/2}$ 
$(y')^{2}+1=x^{-2/3}$ $\implies 4\int_{0}^{1}\sqrt{ x^{-2/3} } \ dx=6$ 

# 大會考

![[Pasted image 20251204150410.png]]

Sol:
先計算 $(1,1+\sqrt{ 2 })$ 與 $y=x$ 的距離：$d=\frac{|1-1-\sqrt{ 2 }|}{\sqrt{ 2 }}=1$。
所以此圓貼著直線旋轉，那麼體積會等於 $(x-1)^{2}+y^{2}\leq 1$ 繞著 $y$ 軸旋轉。
利用 method of cylindrical shell：$2\int_{0}^{2}2\pi x(\sqrt{ 1-(x-1)^{2} }) \ dx$ 
注意不要化簡 $\sqrt{ 1-(x-1)^{2}}=\sqrt{ -x^{2}+2x }$ 不然不好代換。
令 $u=(x-1)$，則等於 $4\pi \int_{-1}^{1}(u+1)\sqrt{ 1-u^{2} } \ dx=4\pi\left( \int_{-1}^{1}u\sqrt{ 1-u^{2} } \ dx +\int_{-1}^{1}\sqrt{ 1-u^{2} } \ dx\right)$ 
其中 $\int_{-1}^{1}u\sqrt{ 1-u^{2} } \ dx$ 是 odd function 所以等於零，而 $\int_{-1}^{1}\sqrt{ 1-u^{2} } \ dx$ 等於半徑為一的半圓面積，等於 $\frac{\pi}{2}$。
所以答案為 $4\pi \cdot \frac{\pi}{2} = 2\pi^{2}$。

![[Pasted image 20251204152711.png]]

Sol:
哇擦勒，會被騙到。
選 $(A)(D)$，但是很可能會選成 $(C)$。
![[Pasted image 20251204153012.png]]
已知 $x=g(y)$ 嘛，如果想要對 $y$ 積分並使用 method of cylindrical shell，我們要找垂直 $y$ 軸的殼高。
注意上圖，給定一個 $y$，對應的高應該是 $1-y$ 而不是 $y$。
否則，塗色面積應該相反。
所以答案就是 $2\pi\int_{0}^{1} y(1-g(y)) \ dy$ 啦！

![[Pasted image 20251204154915.png]]

Sol:
要分段討論，但不要腦子壞掉右邊函數加一左邊沒加一。
也不要腦子壞掉變成某個積分的兩倍，不能這樣算好嗎？
$\int_{-1}^{0}\pi[(x^{3}+1)^{2}-(x+1)^{2}] \ dx +\int_{0}^{1}\pi[(x+1)^{2}-(x^{3}+1)^{2}] \ dx$ 
$=\pi\left( \left[ \frac{1}{7}x^{7}+\frac{1}{2}x^{4}-\frac{1}{3}x^{3}-x^{2} \right]^{0}_{-1}+\left[ -\frac{1}{7}x^{7}-\frac{1}{2}x^{4}+\frac{1}{3}x^{3}+x^{2} \right]^{1}_{0} \right)$ 注意前者不是直接代 $-1$ 呀！
$=\pi$ 

![[Pasted image 20251204175532.png]]

Sol:
這題難在不知道圖形長啥樣。
長這樣：
![[Pasted image 20251204175603.png]]
首先取第一個與 $x$ 軸交點的 $x$ 座標：$\frac{\sin x}{x}=0\implies x_{1}=\pi$。
所以體積為：$\int_{0}^{\pi}2\pi x \frac{\sin x}{x} \ dx=2\pi[-\cos x]^{\pi}_{0}$ 
$=2\pi \cdot 2=4\pi$ 注意此處 $\cos0=1$，不要以為代 $0$ 啥都等於 $0$ 而忘記算！

![[Pasted image 20251204222312.png]]

Sol:
$(y')^{2}+1=(\ln x)^{2}\implies \int_{e}^{e^{2}} \sqrt{ 1+(y')^{2} } \ dx=\int_{e}^{e^{2}}\ln x \ dx$ 
你可能會想，哇勒這東西沒反導函數可以套吧？
哈，還是太年輕。用 Integration By Part。
令 $u=\ln x$，$dv=dx$，則 $v=x$。
$\int_{e}^{e^{2}}\ln x \ dx=[x\ln x]^{e^{2}}_{e}-\int_{e}^{e^{2}}dx=e^{2}$ 