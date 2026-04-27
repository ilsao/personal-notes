# Functions of Several Variables

回憶函數的表示方法：
- 通過文字表達
- 通過表對應
- 通過顯式寫出數學式
- 通過圖

## Functions of Two Variables

雙變量函數 $f$ 定義為：為集合 $D$ 中實數對 $(x,y)$ 分配唯一實數的規則，記為 $f(x,y)$。其中 $D$ 為 $f$ 的定義域，其值域為 $\{ f(x,y)|(x,y)\in D \}$。

我們通常將 $f$ 函數為 $(x,y)$ 對應的值寫做 $z=f(x,y)$。

其中，$x$ 與 $y$ 變量為**獨立變量(independent variables)**，$z$ 為**相依變量(dependent variable)**。

![[Pasted image 20260326214507.png|371]]

## Graphs

**圖(Graphs)**：若 $f$ 為定義域 $D$ 的雙變量函數，則 $f$ 的圖為所有 $\mathbb{R}^{3}$ 中滿足 $z=f(x,y)$ 與 $(x,y)\in D$ 的 $(x,y,z)$，為 $\mathbb{R}^{3}$ 上的曲面。

> [!note]
> 一個雙變量函數不可能表達出完整的球體，這表示固定 $(x,y)$ 可對應出兩個 $z$。
> 但我們可以用 $f(x,y)=\sqrt{ 9-x^{2}-y^{2} }$ 表示 $x^{2}+y^{2}+z^{2}=9$ 的上半圓。

若 $f(x,y)=ax+by+c$，則其稱為**線性函數(linear function)**。此類函數的圖具有下列等式：$z=ax+by+c$ 或 $ax+by-z+c=0$。

## Level Curves and Contour Maps

**等高線(level curve)**：函數 $f$ 的等高線由等式 $f(x,y)=k$ 構成的曲線構成，其中 $k$ 為常數且在 $f$ 的值域裡。可看成 $z=k$ 與函數圖形的交線投影到 $xy$ 平面。

**等高線圖(contour map)**：將所有等高線收集起來繪成的圖，並且我們假設每個 $k$ 的取值間隔相同。等高線越密，圖形越陡。

## Functions of Three or More Variables

對更多變量函數的定義，與雙變量函數定義類似。

對三變量函數，我們使用**等值面(level surface)** 來觀察函數，因為此時有四個維度。

我們可從不同視角檢視定義在 $\mathbb{R}^{n}$ 子集上的多變量函數 $f$：
1. 一個有 $n$ 個實數變量 $x_{1},x_{2},\dots,x_{n}$ 的函數
2. 一個接收單個點變量 $(x_{1},x_{2},\dots,x_{n})$ 的函數
3. 一個接收單個向量變量 $\mathbf{x}=\langle x_{1},x_{2},\dots,x_{n} \rangle$ 的函數

> [!note] 補充
> $\frac{x^{2}}{a^{2}}+\frac{y^{2}}{b^{2}}=1$ ($a>b$) 的圖形是一個橢圓。
> 其中，$a$ 為長半軸，$b$ 為短半軸。而焦距 $c$ 滿足 $c^{2}=a^{2}-b^{2}$，且焦點位於 $(\pm c,0)$。
> 若 $b>a$ 則 $c^{2}=b^{2}-a^{2}$ 且焦點位於 $(0,\pm c)$。

# Limits and Continuity

## Limits of Functions of Two Variables

令 $f$ 為雙變量函數，其定義域 $D$ 包含任意接近 $(a,b)$ 的所有點。若對任意 $\epsilon>0$ 都有對應 $\delta>0$ 使得若 $(x,y)\in D$ 且 $0<\sqrt{ (x-a)^{2}+(y-b)^{2} }<\delta$ 則 $|f(x,y)-L|<\epsilon$，我們寫：

$$
\lim_{ (x,y) \to (a,b) } f(x,y)=L
$$

![[Pasted image 20260417215709.png]]

## Showing That a Limit Does Not Exist

我們可以從任意方向逼近點 $(a,b)$，只要任意一個逼近的路徑與其他逼近的路徑不相等，則極限不存在。

常見的檢查為：
- 延 $x$ 軸逼近
- 延 $y$ 軸逼近
- 延直線 $y=mx$ 逼近
- 延曲線 $y=x^{2}$ 逼近

思考方式為：看到不同次方，則優先使用能使同階的路徑。

![[Pasted image 20260417221323.png|619]]
![[Pasted image 20260417221337.png|626]]![[Pasted image 20260417221416.png|280]]

極座標法：先將圖形平移到原點，再用 $x=r\cos \theta$，$y=r\sin \theta$ 代換，則函數變為 $f(r,\theta)$。考慮 $r\to0$ 時，值是否跟 $\theta$ 有關？
- 與 $\theta$ 有關：極限不存在
- 與 $\theta$ 無關：極限存在

## Properties of Limits

![[Pasted image 20260417221454.png]]

並且：

$$
\lim_{ (x,y) \to (a,b) } x=a\quad \lim_{ (x,y) \to (a,b) } y=b\quad \lim_{ (x,y) \to (a,b)}c=c
$$

所以，對於由 $cx^{m}y^{n}$ 項構成的雙變量多項式函數，以及多項式函數相除的有理函數，有：

$$
\lim_{ (x,y) \to (a,b) } p(x,y)=p(a,b)
$$
$$
\lim_{ (x,y) \to (a,b) } q(x,y)=\lim_{ (x,y) \to (a,b) } \frac{p(x,y)}{r(x,y)}=\frac{p(a,b)}{r(a,b)}=q(a,b)
$$

但前提是，$(a,b)$ **在函數的定義域中**。即，$\lim_{ (x,y) \to (a,b) }r(x,y)\neq0$。

> [!note]
> 沒錯，這邊講的就是有理函數分母等於零時候的情況！

同理，夾擠定理在此處仍適用。

![[Pasted image 20260417222040.png|655]]
![[Pasted image 20260417222056.png|665]]

> [!note]
> 處理多變量函數極限時，很常用的手段還是嘗試將分母為零的部分與分子化簡。

> [!Note]
> 看到 $\sin$ 在分子，嘗試湊 $\frac{\sin x}{x}$。

## Continuity

當：

$$
\lim_{ (x,y) \to (a,b) } f(x,y)=f(a,b)
$$

我們稱 $f$ 在 $(a,b)$ 連續。若 $f$ 對所有 $(a,b)\in D$ 的點都連續，則 $f$ 在其定義域 $D$ 上連續。

在此我們考慮合成函數。若 $f$ 是一個雙變量連續函數，$g$ 為單變量連續函數，則 $g\circ f$ 連續。

> [!warning] 注意
> 若考慮區域 $y≥x^{b}$，則需先取邊界點 $(a,a^{b})$，再構造由上方與下方趨近該點的路徑，以判斷極限是否存在。  
> 單純的不等式僅描述範圍，並非一條路徑。

## Functions of Three or More Variables

若 $f$ 定義在 $\mathbb{R}^{n}$ 的子集 $D$ 上，則 $\lim_{ \mathbf{x} \to \mathbf{a} }f(\mathbf{x})=L$ 表示對任意 $\epsilon>0$ 都有對應的 $\delta>0$ 使得：若 $\mathbf{x}\in D$ 且 $0<|\mathbf{x}-\mathbf{a}|<\delta$ 則 $|f(\mathbf{x})-L|<\epsilon$。

# Partial Derivatives

## Partial Derivatives of Functions of Two Variables

當計算雙變量函數 $f(x,y)$ 在點 $(a,b)$ 時對 $x$ 的導數時，定義如下：

$$
f_{x}(a,b)=g'(a)=\lim_{ h \to 0} \frac{f(a+h,b)-f(a,b)}{h} \quad\text{ where }g(x)=f(x,b)
$$

即，將 $y$ 視為常數然後對 $f$ 求導。

> [!note]
> 注意到 $g'(a)$ 不代表一定要先算 $g'(x)$ 再帶入 $a$。
> 有時 $g'(x)$ 可能不好算，我們可以從定義直接下手。

偏導還有很多記號：

$$
f_{x}(a,b)=f_{x}= \frac{\partial f}{\partial x}= \frac{\partial}{\partial x}f(x,y)= \frac{\partial z}{\partial x}=f_{1}=D_{1}f=D_{x}f
$$

偏導也可應用在隱微分：

![[Pasted image 20260419161509.png|607]]

## Functions of Three or More Variables

若 $u$ 是包含 $n$ 個變量的函數 $u=f(x_{1},x_{2},\dots,x_{n})$，則其對 $x_{i}$ 的偏導數記為：

$$
\frac{\partial u}{\partial x_{i}}=\lim_{ h \to 0 } \frac{f(x_{1},x_{2},\dots,x_{i}+h,\dots x_{n})-f(x_{1},x_{2},\dots,x_{i},\dots,x_{n})}{h}= \frac{\partial f}{\partial x_{i}}=f_{x_{i}}=f_{i}=D_{i}f
$$

## Higher Derivatives

注意偏導記號的順序：

$$
\begin{align}
 & (f_{x})_{x}=f_{xx}=f_{11}= \frac{\partial}{\partial x}\left( \frac{\partial f}{\partial x} \right)=\frac{\partial^{2}f}{\partial x^{2}}= \frac{\partial^{2} z}{\partial x^{2}} \\
 & (f_{x})_{y}=f_{xy}=f_{12}= \frac{\partial}{\partial y}\left( \frac{\partial f}{\partial x} \right)= \frac{\partial^{2}f}{\partial y\partial x}= \frac{\partial^{2} z}{\partial y\partial x} \\
 & (f_{y})_{x}=f_{yx}=f_{21}= \frac{\partial}{\partial x}\left( \frac{\partial f}{\partial y} \right)= \frac{\partial^{2}f}{\partial x\partial y}= \frac{\partial^{2} z}{\partial x\partial y} \\
 & (f_{y})_{y}=f_{yy}=f_{22}= \frac{\partial}{\partial y}\left( \frac{\partial f}{\partial y} \right)=\frac{\partial^{2}f}{\partial y^{2}}= \frac{\partial^{2} z}{\partial y^{2}}
\end{align}
$$

Clairaut's Theorem：設 $f$ 定義在 Disk D 上且包含點 $(a,b)$。若 $f_{xy}$ 與 $f_{yx}$ 在 D 上連續，則：

$$
f_{xy}(a,b)=f_{yx}(a,b)
$$

> [!note]
> 滿足前提不代表要先計算出 $f_{xy}$ 與 $f_{yx}$，若 $f$ 為多項式函數則 $f$ 必定連續。
> 有時求導的順序與複雜度息息相關，這個定理可幫助我們減少計算。

> [!warning]
> $\frac{d}{dx}(\arcsin x)= \frac{1}{\sqrt{ 1-x^{2} }}$ 
> $\frac{d}{dx}(\arccos x)=-\frac{1}{\sqrt{ 1-x^{2} }}$ 
> $\frac{d}{dx}(\arctan x)=\frac{1}{1+x^{2}}$
> $\frac{d}{dx}(\tan x)=\sec^{2}x$ 
> $\frac{d}{dx}(\sec x)=\sec x\tan x$

> [!error] 小心
> 對 $f_{xy}(0,0)$ 先計算 $f_{x}(0,y)$，然後計算 $f_{xy}(0,0)$。
> 但對 $f_{x}(0,0)$ 則直接計算 $\lim_{ h \to 0 } \frac{f(h,0)-f(0,0)}{h}$。

> [!note]
> 可微偏導必存在，可微必連續。
> 偏導存在，不一定連續，亦不一定可微。

# Tangent Planes and Linear Approximations

## Tangent Planes

對表面 $S$ 在 $P$ 點的 tangent plane：包含 $x$ 軸方向切線與 $y$ 軸方向切線 (過 $P$ 點) 的平面。

![[Pasted image 20260423145649.png|313]]

若 $f$ 具有**連續的偏導** (因而可微)，則其過 $P(x_{0},y_{0},z_{0})$ 的切平面為：

$$
z-z_{0}=f_{x}(x_{0},y_{0})(x-x_{0})+f_{y}(x_{0},y_{0})(y-y_{0})
$$

解釋：
我們知道平面方程：
$A(x-x_{0})+B(y-y_{0})+C(z-z_{0})=0\implies z-z_{0}=-\frac{A}{C}(x-x_{0})-\frac{B}{C}(y-y_{0})$ 
設上式是 $P$ 點的切平面，則其與平面 $y=y_{0}$ 的交線必為 $T_{1}$。
令 $a=-\frac{A}{C},b=-\frac{B}{C}$，代入 $y=y_{0}$：$z-z_{0}=a(x-x_{0})$。
可看出這是一個斜率為 $a$ 的直線，而之前我們又知道 $T_{1}$ 的斜率由 $f_{x}(x_{0},y_{0})$ 計算
$\implies a=f_{x}(x_{0},y_{0})$ 
同理可知 $b=f_{y}(x_{0},y_{0})$ 

## Linear Approximations

我們可以通過切平面近似某點附近的數值。

通過移項切平面公式，我們有：

$$
L(x,y)=f(x_{0},y_{0})+f_{x}(x_{0},y_{0})(x-x_{0})+f_{y}(x_{0},y_{0})(y-y_{0})
$$

我們稱 $L(x,y)$ 為 linearization of $f$ at $(x_{0},y_{0})$。

且：

$$
f(x,y)\approx f(x_{0},y_{0})+f_{x}(x_{0},y_{0})(x-x_{0})+f_{y}(x_{0},y_{0})(y-y_{0})
$$

稱做 linear approximation 或 tangent plane approximation of $f$ at $(x_{0},y_{0})$。

若 $f$ 在 $(a,b)$ 可導，則 $\Delta z$ 可表為：

$$
\Delta z=f_{x}(a,b)\Delta x+f_{y}(a,b)\Delta y+\epsilon_{1}\Delta x+\epsilon_{2}\Delta y
$$

其中 $(\epsilon_{1},\epsilon_{2})\to(0,0)$ as $(x,y)\to(0,0)$。

即，若 $f_{x},f_{y}$ 在 $(a,b)$ 附近存在，**且偏導在 $(a,b)$ 點連續**，則 $f$ 可微。

## Differentials

定義 total differential 如下：

$$
dz=f_{x}(a,b)\ dx+f_{y}(a,b)\ dy=\frac{\partial z}{\partial x}dx+\frac{\partial z}{\partial y}dy
$$

![[Pasted image 20260423152550.png|520]]

> [!note]
> 前提是可導。
> 注意到這條式子與上面 $\Delta z$ 的很像，但 $\Delta z$ 那條是定義，這條是運用那個定義得出來的結果。
> 其實，$\Delta z-dz=\epsilon_{1}\Delta x+\epsilon_{2}\Delta y$。

> [!note]
> 比對 linear approximation 與 $dz$ 的差別，linear approximation 包含原始值而 $dz$ 只代表變化量。

![[Pasted image 20260423152840.png|600]]

## Functions of Three of More Variables

現考慮 $f(x,y,z)$ 的三變量函數。

其 linear approximation 為：

$$
f(x,y,z)\approx f(a,b,c)+f_{x}(a,b,c)(x-a)+f_{y}(a,b,c)(y-b)+f_{z}(a,b,c)(z-c)
$$

令 $w=f(x,y,z)$，則：

$$
dw= \frac{\partial w}{\partial x}dx+\frac{\partial w}{\partial y}dy+\frac{\partial w}{\partial z}dz
$$

# The Chain Rule

## The Chain Rule

若 $z=f(x,y)$ 是 $x,y$ 的可導函數，其中 $x=g(t),y=h(t)$ 且二者皆為 $t$ 的可導函數。則 $z$ 是 $t$ 的可導函數，且：

$$
\frac{dz}{dt}=\frac{\partial z}{\partial x} \frac{dx}{dt}+\frac{\partial z}{\partial y} \frac{dy}{dt}
$$

proof:
$\Delta t$ 的改變會造成 $\Delta x$ 與 $\Delta y$ 的改變，因而造成 $\Delta z$ 的改變。
$\Delta z= \frac{\partial f}{\partial x}\Delta x+ \frac{\partial f}{\partial y}\Delta y+\epsilon_{1}\Delta x+\epsilon_{2}\Delta y$ 
其中 $\epsilon_{1}\to 0$ 且 $\epsilon_{2}\to 0$ as $(\Delta x,\Delta y)\to(0,0)$。
同除 $\Delta t$ 
$\frac{\Delta z}{\Delta t}= \frac{\partial f}{\partial x} \frac{\Delta x}{\Delta t}+\frac{\partial f}{\partial y} \frac{\Delta y}{\Delta t}+\epsilon_{1} \frac{\Delta x}{\Delta t}+\epsilon_{2} \frac{\Delta y}{\Delta t}$ 
則
$\frac{dz}{dt}=\lim_{ t \to 0 } \frac{\Delta z}{\Delta t}$ 
$=\frac{\partial f}{\partial x} \frac{dx}{dt}+\frac{\partial f}{\partial y} \frac{dy}{dt}+(\lim_{ t \to 0 }\epsilon_{1}) \frac{dx}{dt}+(\lim_{ t \to 0 }\epsilon_{2}) \frac{dy}{dt}$ 
$=\frac{\partial f}{\partial x} \frac{dx}{dt}+\frac{\partial f}{\partial y} \frac{dy}{dt}$ 
這邊 $\Delta t\to 0$，因而 $\Delta x=g(t+\Delta t)-g(t)\to 0$。同理 $\Delta y\to0$。

![[Pasted image 20260424115602.png|629]]
![[Pasted image 20260424115616.png|639]]

若 $u$ 是 $n$ 個變量 $x_{1},x_{2},\dots ,x_{n}$ 的可導函數，且每個 $x_{j}$ 都是 $m$ 個變量 $t_{1},t_{2},\dots,t_{m}$ 的的可導函數，則 $u$ 是 $t_{1},t_{2},\dots,t_{m}$ 的可導函數，且對所有 $i=1,2,\dots,m$ 有：

$$
\frac{\partial u}{\partial t_{i}}= \frac{\partial u}{\partial x_{1}} \frac{\partial x_{1}}{\partial t_{i}}+\frac{\partial u}{\partial x_{2}} \frac{\partial x_{2}}{\partial t_{i}}+\dots+ \frac{\partial u}{\partial x_{n}} \frac{\partial x_{n}}{\partial t_{i}}
$$

![[Pasted image 20260424120601.png|649]]

![[Pasted image 20260424121128.png|552]]

## Implicit Differentiation

對雙變量函數 $F(x,y)=0$ 對 $x$ 做隱微分，可視為 $y$ 是 $x$ implicitly 定義的函數，即 $F(x,f(x))=0$。

$$
\frac{\partial F}{\partial x}+\frac{\partial F}{\partial y} \frac{dy}{dx}=0
$$

好吧這邊其實不用管，就按照之前的理念做就對了。

# 練習題

Show that the limit does not exist. 
![[Pasted image 20260419131310.png|264]]

Sol:
我錯誤的嘗試沿曲線 $y=x^{3/2}$ 逼近 $(0,0)$。
令 $f(x,y)= \frac{x^{2}+xy^{2}}{x^{4}+y^{2}}$ 
於是 $f(x,x^{3/2})=\frac{x^{2}+x^{4}}{x^{4}+x^{3}}$，那時我錯誤的認為此時極限會等於 $1$。
但是，由於是趨近 $(0,0)$ 而非 $(\infty,\infty)$，所以極限應該由最小次方項決定為 $\infty$。
正確的方法是：
1. 延 $x$ 軸逼近 $(0,0)$，得極限 $\infty$。
2. 延 $y=x$ 逼近 $(0,0)$，得極限 $1$。

![[Pasted image 20260419133125.png|375]]

Sol:
我錯誤的嘗試用錯誤的不等式：$\sqrt{ x^{2}+y^{2} }\leq x+y$。
正確的應該是：$\sqrt{ x^{2}+y^{2} }\leq|x|+|y|$。
這邊我們換個法子：$|x|\leq \sqrt{ x^{2}+y^{2} }$ 
$\implies 0\leq| \frac{xy}{\sqrt{ x^{2}+y^{2} }}|\leq \frac{|xy|}{|x|}=|y|$ 
又 $\lim_{ (x,y) \to (0,0) }y=0\implies \lim_{ (x,y) \to  (0,0)}=0$ By the squeeze theorem

![[Pasted image 20260419140151.png|572]]

Sol:
(a)
若 $m\leq0$，則 $y=mx^{a}\leq 0$。 
若 $m>0$，則 $mx^{a}\geq x^{4}$ as $x\to 0$，因為 $0<a<4$。
所以 $\lim_{ (x,y) \to (0,0) }f(x,mx^{a})=0$。
(b)
取 $y=x^{5}$ 且 $x>0$，因為 $x^{5}<x^{4}$ as $x\to 0$。則 $\lim_{ (x,y) \to (0,0) }f(x,x^{5})=1$。
因此，沿 $y=mx^{a}$ 與 $y=x^{5}$ 趨近 $(0,0)$ 得到兩個不同值，所以 $f$ 在 $(0,0)$ 時極限不存在。
(c)
在 $y=0$ 時 $f$ 不連續：
若我們趨近 $(a,0)$ 沿 $x=a$，令 $y\to 0^{+}$ 則 $f(x,y)=1$ for $0<y<a^{4}$。所以 $\lim_{ y \to 0^{+} }f(a,y)=1$。
若沿 $x=a$，令 $y\to0^{-}$ 則 $f(x,y)=0$ 且 $\lim_{ y \to 0^{-} }f(a,y)=0$。
因此極限不存在，且 $f$ 在 $y=0$ 時不連續。
在 $y=x^{4}$ 時 $f$ 不連續：
沿路徑 $x=a$，令 $y\to a^{4+}$ 趨近 $(a,a^{4})$，則 $f(x,y)=0$。因此 $\lim_{ y \to a^{4+} }f(a,y)=0$。
沿路徑 $x=a$，令 $y\to a^{4-}$ 趨近，則 $f(x,y)=1$。因此 $\lim_{ y \to a^{4-} }f(a,y)=1$。
因此極限不存在，且 $f$ 在 $y=x^{4}$ 時不連續。

![[Pasted image 20260419142542.png|891]]

Sol:
因為 $|\mathbf{x}-\mathbf{a}|^{2}=|\mathbf{x}|^{2}+|\mathbf{a}|^{2}-2\mathbf{a}\cdot \mathbf{x}\geq|\mathbf{x}|^{2}+|\mathbf{a}|^{2}-2|\mathbf{x}||\mathbf{a}|=(|\mathbf{x}|-|\mathbf{a}|)^{2}$ 
所以 $||\mathbf{x}|-|\mathbf{a}||\leq|\mathbf{x}-\mathbf{a}|$。
取 $\epsilon>0$ 與 $\delta=\epsilon$，則有若 $|\mathbf{x}-\mathbf{a}|<\delta$ 則 $||\mathbf{x}|-|\mathbf{a}||<\epsilon$。
即，$\lim_{ \mathbf{x} \to \mathbf{a} }f(\mathbf{x})=|\mathbf{x}|=|\mathbf{a}|=f(\mathbf{a})$。
於是 $f$ 在 $\mathbb{R}^{n}$ 上連續。

Find the first partial derivatives of the function:
![[Pasted image 20260419211843.png|341]]

Sol:
提醒你：$\int_{a}^{b}g(x)\ dx=-\int_{b}^{a}g(x)\ dx$ 
$\frac{\partial F}{\partial x}=\cos(e^{x})$ 
$\frac{\partial F}{\partial y}=-\cos(e^{y})$ 

![[Pasted image 20260419221403.png|563]]

Sol:
因為 $\sin^{-1}u$ 在 $u\in(-1,1)$ 時連續。
又 $u=x\sqrt{ z }$ 在 $z>0$ 時連續。
所以 $f_{xzy}$ 在其定義域上連續。
於是 $f_{xzy}=f_{yxz}= \frac{\partial^{2}}{\partial z\partial x}(2xyz^{3})=6yz^{2}$ 

Find the differential of the function: 
![[Pasted image 20260423163615.png|324]]

Sol:
$du= \frac{\partial u}{\partial x}dx+ \frac{\partial u}{\partial y}dy$ 這邊有誤解，$dx,dy$ 只是記號，而不是對偏微分後的東西再微分！
$\frac{\partial u}{\partial x}=x(x^{2}+3y^{2})^{-1/2}$ 
$\frac{\partial u}{\partial y}=3y(x^{2}+3y^{2})^{-1/2}$ 
$\implies du=x(x^{2}+3y^{2})^{-1/2}dx+3y(x^{2}+3y^{2})^{-1/2}dy$ 

![[Pasted image 20260423165839.png|706]]

Sol:
英文的鍋。
$V=\pi r^{2}h$ 
$\frac{\partial V}{\partial r}=2\pi rh, \frac{\partial V}{\partial h}=\pi r^{2}$ 
$\implies dV=2\pi rh\ dr+\pi r^{2}\ dr$ 
又 $\Delta r=0.04$，$\Delta h=0.04\times 2$ (上下各增)
所以 $dV=2\pi(4)(12)(0.04)+\pi(4)^{2}(0.08)\approx16.08\text{ cm}^{3}$ 

![[Pasted image 20260423202651.png|680]]

Sol:
卡點在於，不知道怎麼求 curve 的在 $P(2,1,3)$ 切線斜率。
其實不難，先算得 $t=0,u=1$ 時會令 $\mathbf{r}_{1},\mathbf{r}_{2}$ 到達 $P$。
$\mathbf{r}_{1}'(t)=\langle 3,-2t,2t-4 \rangle$ 
$\mathbf{r}'_{2}(u)=\langle 2u,6u^{2},2 \rangle$ 
求導後代入：
$\mathbf{r}_{1}'(0)=\langle 3,0,-4 \rangle$ 
$\mathbf{r}'_{2}(1)=\langle 2,6,2 \rangle$ 
求法向量：
$\langle 3,0,-4 \rangle\times \langle 4,6,2 \rangle=\langle 24,-14,18 \rangle$ 
$\implies 12x-7y+9z=44$ 

![[Pasted image 20260424134304.png|623]]

Sol:
會在應該給 $G_{u,v}$ 代入什麼值的時候混亂。
令 $x=u(s,t),y=v(s,t)$，則 $G(x,y)=G(u(s,t),v(s,t))$。
$R_{s}= \frac{\partial G}{\partial x} \frac{dx}{ds}+ \frac{\partial G}{\partial y} \frac{dy}{ds}$ 
這邊 $\frac{\partial G}{\partial x}$ 與 $\frac{\partial G}{\partial y}$ 都是 $x,y$ 的函數，所以應該代入 $x=u(1,2),y=v(1,2)$ 
$\implies R_{s}=9\times 4+(-2)\times 2=32$ 
$R_{t}= G_{u} u_{t}+G_{v}v_{t}=9\times(-3)+(-2)\times 6=-39$ 

![[Pasted image 20260424152334.png|800]]

Sol:
已知：$a=20,b=30, \frac{da}{dt}=3, \frac{db}{dt}=-2$ 
保持面積不變：$\frac{1}{2}ab\sin \theta=k$ 
對 $t$ 隱微分：$\frac{1}{2}\left( \frac{da}{dt}b\sin \theta+\frac{db}{dt}a\sin \theta \right)+ab\cos \theta \frac{d\theta}{dt}=0$ 
$\implies \frac{d\theta}{dt}=-\frac{1}{12\sqrt{ 3 }}$ 

![[Pasted image 20260424161155.png|582]]

Sol:
有兩點不會：
1. $f$ is homogeneous of degree $n$ 表示：$f(tx,ty)=t^{n}f(x,y)$ 
2. (b) 那邊對 $t$ 偏導忘記 chain rule 應該對所有包含 $t$ 的變量展開
(a)
用 $f(tx,ty)=t^{n}f(x,y)$ 對 $t$ 隱微分。
令 $u=tx,v=ty\implies f(tx,ty)=f(u,v)$ 
$\frac{\partial f}{\partial t}=\frac{\partial f}{\partial u} \frac{\partial u}{\partial t}+\frac{\partial f}{\partial v} \frac{\partial v}{\partial t}=x \frac{\partial f}{\partial u}+y \frac{\partial f}{\partial v}$ 
$\frac{\partial}{\partial t}(t^{n}f(x,y))=nt^{n-1}f(x,y)$ 
取 $t=1$ 則 $x \frac{\partial f}{\partial x}+y \frac{\partial f}{\partial y}=nf(x,y)$ 
(b)
$\frac{\partial}{\partial t}\left( \frac{\partial f}{\partial t} \right)=x\left( \frac{\partial^{2}f}{\partial^{2}u}x+\frac{\partial^{2}f}{\partial v\partial u}y \right)+y\left( \frac{\partial^{2}f}{\partial v^{2}}y+\frac{\partial^{2}f}{\partial u\partial v}x \right)$ 
$\frac{\partial}{\partial t}(nt^{n-1}f(x,y))=n(n-1)t^{n-2}f(x,y)$ 
取 $t=1$ 並利用 $f_{xy}=f_{yx}$ 有：
$x^{2} \frac{\partial^{2}f}{\partial x^{2}}+2xy \frac{\partial^{2}f}{\partial x\partial y}+y^{2} \frac{\partial^{2}f}{\partial y^{2}}=n(n-1)f(x,y)$ 

# 大會考

![[Pasted image 20260419223228.png]]

Sol:
選 (D)
取 $y=x^{2/3}$：
$f(x,x^{2/3})= \frac{x^{2/3}\sin x^{2/3}}{x^{2}+x^{4/3}}= \frac{x^{2/3}\sin x^{2/3}}{x^{4/3}(x^{2/3}+1)}= \frac{\sin x^{2/3}}{x^{2/3}(x^{2/3}+1)}$ 
$\lim_{ x\to0 } f(x,x^{2/3})= \frac{\sin x^{2/3}}{x^{2/3}} \frac{1}{x^{2/3}+1}=1\cdot 1=1$ 
又 $\lim_{ x \to 0 }f(x,0)=0$ 
所以極限不存在。

![[Pasted image 20260419225458.png|603]]

Sol:
(1)
極座標代入：$\lim_{ r \to 0 } \frac{\cos^{2}\theta \sin \theta}{r}$ 不存在。(不是說無限大而不存在，因為當某些 $\theta$ 使分子為零時則極限為零，否則才為無限大)
(2)
$0<|\frac{x^{2}y}{x^{2}+y^{4}+z^{4}}|<|y| |\frac{x^2}{x^{2}+y^{4}+z^{4}}|$ 
又 $|x^{2}+y^{4}+z^{4}|<|x^{2}|$ 
所以 $0<|\frac{x^{2}y}{x^{2}+y^{4}+z^{4}}|<|y| |\frac{x^2}{x^{2}+y^{4}+z^{4}}|<|y|$ 
夾擠得極限為 $0$。

![[Pasted image 20260422161709.png|680]]

Sol:
雖然我知道，但提醒你一句：偏微分有值不代表連續。
這題主要在不知道怎麼開始。
我們應該先考慮 $f_{x}(0,y)$，然後考慮 $f_{xy}(0,0)$。
$f_{x}(0,y)=\lim_{ h \to 0 } \frac{f(h,y)-f(0,y)}{h}=-y^{b-1}$ 
$f_{xy}(0,0)=\lim_{ h \to 0 } \frac{f(0,h)-f(0,0)}{h}=-\lim_{ h \to 0 }h^{b-2}=-1$ 
$\implies b=2$ 

![[Pasted image 20260422164042.png|438]]

Sol:
選 (B)(D)
(B)
我第一次錯誤的認為直接代入 $f(0,y)=1$ 就說可導。
但不是的，這邊我們也要考慮 $x$ 的擾動。
應該這樣說：
因為 $y\neq 0$，所以 $\frac{y^{2}-x^{2}}{x^{2}+y^{2}}$ 有定義。
又這東西是有理函數，所以可導。
(C)
我曾錯誤的求 $f_{x}(0,y)$ 然後代入 $y=0$。
但這是錯誤的，因為這樣計算假設了 $y\neq 0$，但最終卻代入 $y=0$。
直接計算 $f_{x}(0,0)=\lim_{ h \to 0 } \frac{f(h,0)-f(0,0)}{h}=\lim_{ h \to 0 } -\frac{2}{h}$ 不存在
(D)
$f_{y}(0,0)=\lim_{ h \to 0 } \frac{f(0,h)-f(0,0)}{h}=0$ 存在

![[Pasted image 20260422234229.png|764]]

Sol:
這題重點是不要怕，硬給他用偏導定義微下去。
$f_{x}(0,y)=\lim_{ h \to 0} \frac{f(h,y)-f(0,y)}{h}=\lim_{ h \to 0 } \frac{1}{h}\left( h^{2}\tan^{-1}\left( \frac{y}{h} \right)-y^{2}\tan^{-1}\left( \frac{h}{y} \right) \right)$ 
$=\lim_{ h \to 0 }\left( h\tan^{-1}\left( \frac{y}{h} \right)-\frac{y^{2}}{h}\tan^{-1}\left( \frac{h}{y} \right) \right)$ 
$=-\lim_{ h \to 0 } \frac{\tan^{-1}\left( \frac{h}{y} \right)}{\frac{h}{y^{2}}}=-y$ 
$f_{xy}(0,0)=\lim_{ h \to 0 } \frac{f_{x}(0,h)-f_{x}(0,0)}{h}=\lim_{ h \to 0 } -\frac{h}{h}=-1$ 