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

**等高線圖(contour map)**：將所有等高線收集起來繪成的圖，並且我們假設每個 $k$ 的取值間隔相同。等高線越密，圖形越抖。

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

思考方式為：看到不同次方，則優先使用能使同皆的路徑。

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

同理，夾擠定理在此處仍適用。

![[Pasted image 20260417222040.png|655]]
![[Pasted image 20260417222056.png|665]]



## Continuity

當：

$$
\lim_{ (x,y) \to (a,b) } f(x,y)=f(a,b)
$$

我們稱 $f$ 在 $(a,b)$ 連續。若 $f$ 對所有 $(a,b)\in D$ 的點都連續，則 $f$ 在其定義域 $D$ 上連續。

在此我們考慮合成函數。若 $f$ 是一個雙變量連續函數，$g$ 為單變量連續函數，則 $g\circ f$ 連續。

## Functions of Three or More Variables

若 $f$ 定義在 $\mathbb{R}^{n}$ 的子集 $D$ 上，則 $\lim_{ \mathbf{x} \to \mathbf{a} }f(\mathbf{x})=L$ 表示對任意 $\epsilon>0$ 都有對應的 $\delta>0$ 使得：若 $\mathbf{x}\in D$ 且 $0<|\mathbf{x}-\mathbf{a}|<\delta$ 則 $|f(\mathbf{x})-L|<\epsilon$。

