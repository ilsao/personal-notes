
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

# Tips

- 當 $y$ 高於一次方時，考慮把 $x$ 用 $y$ 表達，然後對 $y$ 積分。 
- 算兩函數交出的面積時，判斷好誰上誰下。
- oi，不要看到 $\cos2x-\sin x$ 就自動換成 $\cos 2x=1-2\sin^{2}x$，思考一下是不是不換的反導函數比較簡單？

# 重要例題

![[Pasted image 20251202181827.png]]

Sol:
不難，主要是提醒你 $c$ 可以是 $\pm 6$。
![[Pasted image 20251202181930.png]]

