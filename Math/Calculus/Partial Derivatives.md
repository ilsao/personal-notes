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