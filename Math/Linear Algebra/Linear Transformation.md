
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

我們來看看 Matrix Representation Theorem：

若 $E=\{\mathbf{v_{1}},\dots,\mathbf{v_{n}}\}$ $F=\{\mathbf{w_{1}},\dots,\mathbf{w_{n}}\}$ 分別為 $V$ 和 $W$ 的有序基底。

則對於線性變換 $L:V\to W$，一定存在一個 $m\times n$ 矩陣 $A$ 使得：

$$
[L(\mathbf{v})]_{F}=A[\mathbf{v}]_{E} \quad \text{for each }\mathbf{v}\in V
$$

且 $A$ 矩陣可以如下計算：

$$
\mathbf{a}_{j}=[L(\mathbf{v})_{j}]_{F}\quad j=1,\dots,n
$$

