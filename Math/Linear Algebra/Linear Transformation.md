
# Definition and Example

線性轉換的定義如下：

我們把一個將向量空間 $V$ 映射到向量空間 $W$ 的映射 $L$ 稱為**線性轉換(linear transformation)**，若：

$$
L(\alpha \mathbf{v_{1}}+\beta \mathbf{v_{2}})=\alpha L(\mathbf{v_{1}})+\beta L(\mathbf{v_{2}})
$$

$\forall \mathbf{v_{1}},\mathbf{v_{2}}\in V$ 與 $\forall\alpha,\beta$ 為標量。

或者我們也可以分兩步確認：
1. $L(\mathbf{v_{1}}+\mathbf{v_{2}})=L(\mathbf{v_{1}})+L(\mathbf{v_{2}})$ 
2. $L(\alpha \mathbf{v)}=\alpha L(\mathbf{v})$ 

我們將向量空間 $V$ 映射到向量空間 $W$ 的映射 $L$ 記作：

$$
L:V\to W
$$

當 $L:V\to V$ 時，我們將此線性轉換稱為**線性操作(linear operation)**。

## Linear Transformation from $\mathbb{R}^{n}$ to $\mathbb{R}^{m}$ 

如果我們有 $m\times n$ 矩陣 $A$，我們可以如下定義一個將 $\mathbb{R}^{n}$ 映射到 $\mathbb{R}^{m}$ 的線性轉換 $L_{A}(\mathbf{x})$：

$$
L_{A}(\mathbf{x})=A\mathbf{x}
$$

對於任意 $\mathbf{x}\in \mathbb{R}^{n}$，$L_{A}(\mathbf{x})$ 是線性的，因為：

$$
\begin{align}
L_{A}(\alpha \mathbf{v_{1}}+\beta \mathbf{v_{2}}) & =A(\alpha \mathbf{v_{1}}+\beta \mathbf{v_{2}}) \\
 & =\alpha (A\mathbf{v_{1}})+\beta(A\mathbf{v_{2}}) \\
 & =\alpha L_{A}(\mathbf{v_{1}})+\beta L_{A}(\mathbf{v_{2}})
\end{align}
$$

## Linear transformation from $V$ to $W$ 

若 $L$ 是一個將向量空間 $V$ 映射到 $W$ 的線性轉換，則：
1. $L(\mathbf{0}_{V})=\mathbf{0}_{W}$，其中 $\mathbf{0}_{V}$ 與 $\mathbf{0}_{W}$ 分別是 $V$ 和 $W$ 中的零向量。
2. $L(\alpha_{1}\mathbf{v_{1}}+\dots+\alpha_{n}\mathbf{v_{n}})=\alpha_{1} L(\mathbf{v_{1}})+\dots+\alpha_{n}L(\mathbf{v_{n}})$。
3. $L(-\mathbf{v})=-L(\mathbf{v})$ $\forall \mathbf{v}\in V$。

讓我們證明一下 (3)：
從 (1) 出發：$\mathbf{0}_{W}=L(\mathbf{0}_{V})=L(\mathbf{v}-\mathbf{v})=L(\mathbf{v})+L(-\mathbf{v})\implies L(-\mathbf{v})=L(\mathbf{v})$。

## The Image and  Kernel

對於 $L:V\to W$，我們將 **kernel(核)** of $L$ 記為 $\text{ker}(L)$ 並定義：

$$
\text{ker}(L)=\{\mathbf{v}\in V|L(\mathbf{v})=\mathbf{0}_{W}\}
$$

也就是說， $\text{ker}(L)$ 表達了 $V$ 中被 $L$ 映射成 $\mathbf{0}$ 的部分子集合。且，$\text{dim}(\text{ker}(L))=\text{null(L)}$。

若 $S$ 是 $V$ 的子空間， **image(像)** of $S$ 記作 $L(S)$ 並定義：

$$
L(S)=\{\mathbf{w}\in W|\mathbf{w}=L(\mathbf{v}) \quad \text{for some }\mathbf{v}\in S\}
$$

也就是說，$L(S)$ 表達了 $V$ 中的子空間 $S$ 被映射到 $W$ 的範圍。且如果 $L$ 用矩陣 $A$ 表示的話，$\text{dim}(L(S))=\text{rank}(A)$。

image of 整個向量空間 $V$，$L(V)$， 稱作 **range(值域)** of $L$。

如果將本節的內容融合第三張的 The Rank Nullity Theorem，可以表達成：

$$
\text{rank}(L)+\text{null}(L)=\text{dim}(L(V)) + \text{dim}(\text{ker}(L))=\text{dim}(V)
$$

在此迎來本節第一個定理：若 $L:V\to W$ 為一個線性轉換，且 $S\subseteq V$，則：
- $\text{ker}(L)$ 是 $V$ 的子空間。
- $L(S)$ 是 $W$ 的子空間。

# Matrix Representation of Linear Transformations

若 $L$ 為一個將 $\mathbb{R}^{n}$ 映射到 $\mathbb{R}^{m}$ 的線性轉換，則存在一個 $m\times n$ 的矩陣 $A$ 使得對任意 $\mathbf{x}\in \mathbb{R}^{n}$ 都有：

$$
L(\mathbf{x})=A\mathbf{x}
$$

我們可以如下求 $A$：$a_{j}=L(\mathbf{e}_{j})\quad j=1,\dots,n$。

proof:
若定義 $\mathbf{a}_{j}=L(\mathbf{e}_{j})$ for $j=1,\dots,n$，並令 $A=(a_{ij})=(\mathbf{a_{1}},\dots,\mathbf{a_{n}})$。
若 $\mathbf{x}=x_{1}\mathbf{e_{1}}+\dots+x_{n}\mathbf{e}_{n}$ 為 $\mathbb{R}^{n}$ 中的任一向量，則：
$L(\mathbf{x})=x_{1}L(\mathbf{e_{1}})+\dots+x_{n}L(\mathbf{e_{n}})$ 
$=x_{1}\mathbf{a_{1}}+\dots+x_{n}\mathbf{a_{n}}=(\mathbf{a_{1}},\dots,\mathbf{a_{n}})\begin{bmatrix}x_{1} \\ \vdots \\ x_{n}\end{bmatrix}$ 
$=A\mathbf{x}$ 

讓我們回憶一下高中的東西：旋轉矩陣吧~

一個讓向量逆時針選轉 $\theta$ 的旋轉矩陣定義如下：

$$
\begin{bmatrix}
\cos \theta & -\sin \theta \\
\sin \theta & \cos \theta
\end{bmatrix}
$$

推導過程很簡單，對於 $\mathbf{e_{1}}$，想要讓其逆時針旋轉 $\theta$ 則會從 $(1,0)$ 變成 $(\cos \theta,\sin \theta)$。

而對於 $\mathbf{e_{2}}$ 來說，會從 $(0,1)$ 變成 $(-\sin \theta,\cos \theta)$。

所以，這兩個分別為矩陣的第一個 column 和第二個 column。

我們來看看 **Matrix Representation Theorem**：

若 $E=\{\mathbf{v_{1}},\dots,\mathbf{v_{n}}\}$ $F=\{\mathbf{w_{1}},\dots,\mathbf{w_{n}}\}$ 分別為 $V$ 和 $W$ 的有序基底。

則對於線性變換 $L:V\to W$，一定存在一個 $m\times n$ 矩陣 $A$ 使得：

$$
[L(\mathbf{v})]_{F}=A[\mathbf{v}]_{E} \quad \text{for each }\mathbf{v}\in V
$$

且 $A$ 矩陣可以如下計算：

$$
\mathbf{a}_{j}=[L(\mathbf{v})_{j}]_{F}\quad j=1,\dots,n
$$

隨著上一個定理的結束，我們迎來了下一個定理：

令 $E=\{\mathbf{u_{1}},\dots,\mathbf{u_{n}}\}$ 與 $F=\{\mathbf{b_{1}},\dots,\mathbf{b_{m}}\}$ 為 $\mathbb{R}^{n}$ 與 $\mathbb{R}^{m}$ 的有序基底，其中 $B=(\mathbf{b_{1}},\dots,\mathbf{b_{n}})$。若有線性變換 $L:\mathbb{R}^{n}\to \mathbb{R}^{m}$，則此變換基於 $E$ 和 $F$ 的矩陣表達 $A$ 可以如下求得：

$$
\mathbf{a}_{j}=B^{-1}L(\mathbf{u}_{j})\quad \text{for }j=1,\dots ,n
$$

proof:
$L(\mathbf{u}_{j})=a_{1j}\mathbf{b_{1}}+\dots+a_{mj}\mathbf{b_{m}}=B\mathbf{a}_{j}$ 
$\implies \mathbf{a}_{j}=B^{-1}L(\mathbf{u}_{j})\quad j=1,\dots,n$ 

接下來，我們要介紹一個使用以上定理的引理：

若 $A$ 為基於基底  $E=\{\mathbf{u_{1}},\dots,\mathbf{u_{n}}\}$ 與 $F=\{\mathbf{b_{1}},\dots,\mathbf{b_{n}}\}$ 的變換 $L:\mathbb{R}^{n}\to \mathbb{R}^{m}$ 的矩陣表達形式，則 $(\mathbf{b_{1}},\dots,\mathbf{b_{m}}|L(\mathbf{u_{1}}),\dots,L(\mathbf{u_{n}}))$ 的 RREF 形式就是 $(I|A)$。

proof:
$B^{-1}(\mathbf{b_{1}},\dots,\mathbf{b_{m}}|L(\mathbf{u_{1}}),\dots,L(\mathbf{u_{n}}))=(I|B^{-1}L(\mathbf{u_{1}}),\dots,B^{-1}L(\mathbf{u}_{n}))=(I|\mathbf{a_{1}},\dots,\mathbf{a_{n}})$ 
$=(I|A)$ 

## Homogeneous Coordinates

一個齊次座標系統將 $\mathbb{R}^{2}$ 對應到 $\mathbb{R}^{3}$：

$$
\begin{bmatrix}
x_{1} \\
x_{2}
\end{bmatrix}
\leftrightarrow
\begin{bmatrix}
x_{1} \\
x_{2} \\
1
\end{bmatrix}
$$

為啥需要這樣的齊次系統捏？誒，這不得不提到心愛的計算機圖學啦～

在 $\mathbb{R}^{2}$ 中，如果想要位移座標，必須使用加法運算。但是如果拓展到 $\mathbb{R}^{3}$ ，就可以輕鬆的使用矩陣乘法位移二維坐標啦～

例如：

$$
\begin{bmatrix}
1 & 0 & t_{1} \\
0 & 1 & t_{2} \\
0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
x_{1} \\
y_{1} \\
1
\end{bmatrix}
=\begin{bmatrix}
x_{1} +t_{1}\\
y_{1} +t_{2}\\
1
\end{bmatrix}
$$

# Similarity

令 $E=\{\mathbf{u_{1}},\dots,\mathbf{u_{n}}\}$ 與 $F=\{\mathbf{b_{1}},\dots,\mathbf{b_{n}}\}$ 為 $V$ 的兩個有序基底，且令 $L$ 為 $V$ 上的線性操作。令 $S$ 為變換 $F$ 上座標到 $E$ 上座標的矩陣，且 $A$ 為 $L$ 在 $E$ 上的矩陣表達，$B$ 為 $L$ 在 $F$ 上的矩陣表達，則：$B=S^{-1}AS$。

proof:
令 $\mathbf{x}$ 為 $\mathbb{R}^{n}$ 中的任意向量，令 $\mathbf{v}=\{x_{1}\mathbf{w_{1}}+\dots+x_{n}\mathbf{w_{n}}\}$。
那麼：
$$
\mathbf{y}=S\mathbf{x} \quad \mathbf{t}=A\mathbf{y}=[L(\mathbf{v})]_{E}\quad \mathbf{z}=B\mathbf{x}=[L(\mathbf{v})]_{F}
$$
則 $S^{-1}A\mathbf{y}=S^{-1}AS\mathbf{x}=B\mathbf{x}\implies B=S^{-1}AS$ (因為對於 $\forall \mathbf{x}\in \mathbb{R}^{n}$ 都成立)

我們可以如下理解這個觀念：某個向量 $[\mathbf{x}]_{F}$ 左乘 $S$ 變換到 $[\mathbf{x}]_{E}$，左乘 $A$ 變換到 $[L(\mathbf{x})]_{E}$，再左乘 $S^{-1}$ 變換到 $[L(\mathbf{x})]_{F}$。

到此，終於可以給出**相似(similar)** 的定義：給定 $A$ 與 $B$ 兩個 $n\times n$ 矩陣，若存在一個非奇異矩陣 $S$ ，且 $B=S^{-1}AS$ 則稱 $A$ 與 $B$ 相似。

根據本節開頭的引理，兩個相對於不同基底，但表達同一個線性變換的矩陣會相似。

反過來說，如果 $A$ 表示 $L$ 在 $\{\mathbf{v_{1}},\dots,\mathbf{v_{n}}\}$ 上的矩陣表達，且 $B=S^{-1}AS$。其中 $\mathbf{w_{1}},\dots,\mathbf{w_{n}}$ 如下定義：

$$
\begin{align}
 & \mathbf{w_{1}}=s_{11}\mathbf{v_{1}}+\dots+s_{n 1}\mathbf{v_{n}} \\
 & \vdots \\
 & \mathbf{w_{n}}=s_{1 n}\mathbf{v1}+\dots+s_{nn}\mathbf{v_{n}}
\end{align}
$$

則：$\{\mathbf{w_{1}},\dots,\mathbf{w_{n}}\}$ 為 $V$ 的一組基底，且 $B$ 表示 $L$ 在 $\{\mathbf{w_{1}},\dots,\mathbf{w_{n}}\}$ 上的矩陣表達。

# Tips

- 如果要表示一個線性變換的 ker 和 range，可以使用 $\text{span}$！
- 對於 $L(\mathbf{x})=(x_{1},x_{2},0)^{T}$，$\text{ker}(L)=\text{span}((0,0,1)^{T})$。
- 要說明某個線性變換 $L:\mathbb{R}^{3}\to \mathbb{R}^{3}$，利用 $L(\mathbf{e_{1}}),L(\mathbf{e_{2}}),L(\mathbf{e_{3}})$ 的結果線性獨立，且 $\text{Im}(L)=\text{span}(L(\mathbf{e_{1}}),L(\mathbf{e_{2}}),L(\mathbf{e_{3}}))$。

# 重要例題

1. Let $L:\mathbb{R}^{2}\to \mathbb{R}^{2}$ be a linear operator. If $L((2,3)^{T})=(3,-2)^{T}$ and $L((-1,1)^{T})=(1,4)^{T}$, find the value of $L((8,7)^{T})$. 

Sol:
兩種看法，1. 利用第一節的東西拆解。2. 利用第二節的矩陣表達解。
(I)
$(8,7)^{T}=3(2,3)^{T}-2(-1,1)^{T}$ 
$L((8,7)^{T})=L(3(2,3)^{T}-2(-1,1)^{T})=3L((2,3)^{T})-2L((-1,1)^{T})$ 
$=(9,-6)^{T}+(-2,-8)^{T}=(7,-14)^{T}$ 
(II)
因為 $(2,3)^{T}$ 與 $(-1,1)^{T}$ 線性獨立，所以可以作為 $\mathbb{R}^{2}$ 的一組基底 $E$。
又 $(3,-2)^{T}$ 與 $(1,4)^{T}$ 線性獨立，所以可以作為 $\mathbb{R}^{2}$ 的一組基底 $F$。
那麼，對於變換矩陣 $A_{E:F}=([L((2,3)^{T})]_{F}, [L(-1,1)^{T}]_{F})=\begin{bmatrix}1 & 0 \\ 0 & 1\end{bmatrix}$ 
所以，如果將 $[(8,7)^{T}]_{E}$ 應用 $A_{E:F}$ 再轉回標準基底就是解。
令 $V=\{\mathbf{e_{1}},\mathbf{e_{2}}\}$ 
所以：$\begin{bmatrix}3 & 1 \\ -2 & 4\end{bmatrix}_{F\to V}\begin{bmatrix}1 & 0 \\ 0 & 1\end{bmatrix}_{E:F}\begin{bmatrix}2 & -1 \\ 3 & 1\end{bmatrix}_{V\to E}\begin{bmatrix}8 \\ 7\end{bmatrix}=\begin{bmatrix}7 \\ -14\end{bmatrix}$ 就是答案。

2. Use mathematical induction to prove that if $L$ is a linear transformation from $V$ to $W$, then $L(\alpha_{1}\mathbf{v_{1}}+\dots+\alpha_{n}\mathbf{v_{n}})=\alpha_{1}L(\mathbf{v_{1}})+\dots+\alpha_{n}L(\mathbf{v_{n}})$. 

Sol:
其他正常，需要注意的是：
將 $L(\alpha_{1}\mathbf{v_{1}}+\dots+\alpha_{k}\mathbf{v_{k}}+\alpha_{k+1}\mathbf{v_{k+1}}) = L(\alpha_{1}\mathbf{v_{1}}+\dots+\alpha_{k}\mathbf{v_{k}})+L(\alpha_{k+1}\mathbf{v_{k+1}})$ 
再繼續就好。

3. Let $L$ be a linear operator on a vector space $V$. Define $L^{n}$, $n\geq 1$, recursively by $L^{1}=L$ and $L^{k+1}(\mathbf{v})=L(L^{k}(\mathbf{v}))$ for all $\mathbf{v}\in V$. Show that $L^{n}$ is a linear operator on $V$ for each $n\geq 1$. 

Sol:
直接給重點。
因為假設 $L^{k}$ 是 linear operator，所以有(注意檢驗方式)：
$L^{k+1}(\alpha \mathbf{v}+\beta \mathbf{w})=L(L^{k}(\alpha \mathbf{v}+\beta \mathbf{w}))=L(\alpha L^{k}(\mathbf{v})+\beta L^{k}(\mathbf{w}))$ 
$=\alpha L^{k+1}(\mathbf{v})+\beta L^{k}(\mathbf{w})$ 

4. Find the kernel and the range of linear operation on $P_{3}$: $L(p(x))=p(0)x+p(1)$. 

Sol:
這裡我們用課本的定義：設 $p(x)=ax^{2}+bx+c$。
則 $p(0)x+p(1)=cx+a+b+c$。
$p(0)x+p(1)=0\implies \begin{cases}a=-b \\ c=0\end{cases}$ 
$\implies\text{ker}(L)=\text{span}(-x^{2}+x)$ 
`~~~~~~~~~~~~~~~~~~^` 這裡注意，$\text{ker}(L)$ 是**轉換前的向量空間中的子集合**，而不是轉換後的。
$\implies\text{range}(L)=\text{span}(x,1)$ 

5. A linear transformation $L: V → W$ is said to be one-to-one if $L (\mathbf{v_{1}})= L (\mathbf{v_{2}})$ implies that $\mathbf{v_{1}}=\mathbf{v_{2}}$ (i.e., no two distinct vectors $\mathbf{v_{1}},\mathbf{v_{2}}$ in $V$ get mapped into the same vector $w ∈ W$). Show that $L$ is one-to-one if and only if $\text{ker}(L) = {\mathbf{0_{V}} }$. 

Sol:
($\implies$)
取 $\mathbf{v}\in\text{ker}(V)$ 使得 $L(\mathbf{v})=\mathbf{0_{W}}$。
因為 $L(\mathbf{0}_{V})=\mathbf{0}_{W}$，且 $L$ 為 one-to-one，所以 $\mathbf{v}=\mathbf{0}_{V}$。
$\implies\text{ker}(V)=\{\mathbf{0}_{V}\}$ 
($\impliedby$)
取 $\mathbf{v_{1}},\mathbf{v_{2}}\in V$，若 $L(\mathbf{v_{1}})=L(\mathbf{v_{2}})$，則：
$L(\mathbf{v_{1}})-L(\mathbf{v_{2}})=L(\mathbf{v_{1}}-\mathbf{v_{2}})=\mathbf{0}_{W}$ (因為 $\text{ker}(L)=\mathbf{0}_{V}$)
$\implies \mathbf{v_{1}}-\mathbf{v_{2}}=\mathbf{0}_{V}\implies \mathbf{v_{1}}=\mathbf{v_{2}}$ 

