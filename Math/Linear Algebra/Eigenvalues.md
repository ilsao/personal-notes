
# Eigenvalues and Eigenvectors

令 $A$ 為 $n\times n$ 矩陣，若存在一個標量 $\lambda$ 與一個**非零**向量 $\mathbf{x}$ 使得：

$$
A\mathbf{x}=\lambda \mathbf{x}
$$

則 $\mathbf{x}$ 稱為**特徵向量(eigenvector, characteristic vector)**，$\lambda$ 稱為**特徵值(eigenvalue, characteristic value)**。

而這些特徵向量構成的集合稱為特徵子空間，且必須包含零向量。

需要注意的是，$\mathbf{0}$ 不屬於特徵向量，但是必須含在特徵子空間中(因為子空間必須包含零向量)。

如果有 $\mathbf{x}$ 為單位特徵向量，那麼我們可以通過計算 $\mathbf{x}^{T}A\mathbf{x}=\mathbf{x}^{T}\lambda \mathbf{x}=\lambda||\mathbf{x}||^{2}=\lambda$。

## Finding Eigenvalues and Eigenvectors

通過移項，可得：

$$
(A-\lambda I)\mathbf{x}=\mathbf{0}
$$

因為 $\mathbf{x}$ 非零，所以 $A-\lambda I$ 必為 singular，且 $\mathbf{x}\in N(A-\lambda I)$。

上面說的特徵子空間就是 $N(A-\lambda I)$，但需要注意所有特徵子空間的直和並不是 $A$ 的特徵子空間，因為可以構建出一個向量不是於任意 $\lambda_{i}$ 的特徵子空間！

因為 $A-\lambda I$ 奇異，所以：

$$
\det(A-\lambda I)=0
$$

上面這東西稱作：特徵方程。

而下面這東西稱作：特徵多項式。

$$
p(\lambda)=\det(A-\lambda I)
$$

而對於特徵多項式的任意一個解，都是一個特徵值。

統整一下，則有：

![[Pasted image 20251211164926.png]]

通常來說呀，我們會使用 (e) 來計算 $\lambda$ 的值呦！

一但我們得到了 $\lambda$ 的值，就可以計算 $N(A-\lambda I)$，然後取對應的特徵向量為 null space 的基底喔！

## Independency of Eigenvectors

這個引理課本沒有，是老師補充的耶！(後評：好啦，在課本 6.3 有)

若 $\lambda_{1},\dots \lambda_{k}$ 是 $n\times n$ 矩陣 $A$ 的相異特徵值，且 $\mathbf{x}_{1},\dots \mathbf{x}_{n}$ 為相應的特徵向量。則 $\mathbf{x}_{1},\dots,\mathbf{x}_{n}$ 線性獨立。

proof:
這邊用數學歸納法。
首先，說明 $\{c_{1}\mathbf{x}_{1},c_{2}\mathbf{x}_{2}\}$ 線性獨立。
考慮 $c_{1}\mathbf{x}_{1}+c_{2}\mathbf{x}_{2}=\mathbf{0}$。
將左右同乘 $A$，有 $c_{1}\lambda_{1}\mathbf{x}_{1}+c_{2}\lambda_{2}\mathbf{x}_{2}=\mathbf{0}$。
將第一式乘以 $\lambda_{2}$ 然後用第二式減第一式：$c_{1}(\lambda_{2}-\lambda_{1})\mathbf{x}_{1}=\mathbf{0}$。
因為 $\lambda_{2}$ 與 $\lambda_{1}$ 相異，所以不等於零。又特徵向量不能是零向量，所以只有可能 $c_{1}=0$。
同理，$c_{2}=0$。
假設 $\mathbf{x}_{1},\dots ,\mathbf{x}_{l}$ 線性獨立，考慮 $\mathbf{x}_{1},\dots ,\mathbf{x}_{l},\mathbf{x}_{l+1}$。
接續使用上述方法，把 $\mathbf{x}_{l+1}$ 項消掉，因為 $\mathbf{x}_{1},\dots ,\mathbf{x}_{l}$，所以 $c_{1}=\dots=c_{l}=0$。
這個時候 $c_{l+1}$ 就一定也等於 $0$ 啦！

## The Product and Sum of the Eigenvalues

若 $p(\lambda)$ 式特徵多項式，則 $p(\lambda)=\det(A-\lambda I)=\begin{vmatrix}a_{11}-\lambda & a_{12} & \dots & a_{1n} \\ a_{21} & a_{22}-\lambda & \dots & a_{2n} \\ \vdots \\ a_{n_{1}} & \dots &  & a_{nn}-\lambda\end{vmatrix}$。

若對第一個 column 展開：

$$
p(\lambda)=\det(A-\lambda I)=(a_{11}-\lambda)\det(M_{11})+\sum_{i=2}^{n}a_{i1}(-1)^{i+1}\det(M_{i_{1}})
$$

如果我們用多項式解的角度看，有：

$$
p(\lambda)=(-1)^{n}(\lambda-\lambda_{1})(\lambda-\lambda_{2})\dots(\lambda-\lambda_{n})=(\lambda_{1}-\lambda)(\lambda_{2}-\lambda)\dots(\lambda_{n}-\lambda)
$$

那麼：

$$
\lambda_{1}\cdot \lambda_{2}\dots \lambda_{n}=p(0)=\det(A)
$$

通過我沒聽懂的一個過程，有：

$$
\lambda_{1}+\dots+\lambda_{n}=a_{11}+\dots+a_{nn}
$$

## Similar Matrices

還記得相似矩陣的定義嗎？若 $B$ 與 $A$ 相似，則存在一個矩陣 $S$ 使得 $B=S^{-1}AS$。

這邊有個定理：若 $A$ 與 $B$ 為 $n\times n$ 矩陣且二者相似，則此二矩陣有兩個相同的特徵多項式，相應的具有相同的特徵值。

proof:
$p_{B}(\lambda)=\det(B-\lambda I)=\det(S^{-1}AS-\lambda S^{-1}S)=\det(S^{-1}(A-\lambda I)S)$ 
$\det(S^{-1})\det(A-\lambda I)\det(S)=\det(A-\lambda I)$ 
$=p_{A}(\lambda)$ 

# Diagonalization

先說啥是**可對角化(diagonalizale)**，就是說存在一個可逆矩陣 $X$ 與一個 $n\times n$ 矩陣 $A$ 還有一個對角矩陣 $D$ 使得：

$$
X^{-1}AX=D
$$

那麼，$A$ 就是可對角化的。

給一個定理：$n\times n$ 矩陣 $A$ 可對角化 $\iff$ $A$ 有 $n$ 個線性獨立特徵向量。

proof:
($\implies$)
若 $A$ 可對角化，則存在一個可逆矩陣 $X$ 使得 $AX=XD$，其中 $D$ 為對角矩陣。
令 $D$ 的對角元素為 $d_{jj}=\lambda_{j}$。
若 $\mathbf{x}_{1},\dots,\mathbf{x}_{n}$ 為 $X$ 的 column vectors，則：
$A\mathbf{x}_{j}=\lambda_{j}\mathbf{x}_{j}\quad(d_{jj}=\lambda_{j})$ 
這樣，$\lambda_{j}$ 就是 $A$ 的特徵值，且 $\mathbf{x}_{j}$ 就是 $\lambda_{j}$ 對應的特徵向量。
因為 $X$ 非奇異，所以它的 column vectors 線性獨立。
也就是說 $A$ 有 $n$ 個線性獨立的特徵向量。
($\impliedby$)
若 $A$ 有 $n$ 個線性獨立的特徵向量 $\mathbf{x}_{1},\dots,\mathbf{x}_{n}$，且對應的特徵值為 $\lambda_{i}$ (其中 $\lambda_{i}$ 可能重複)。
令 $X=(\mathbf{x}_{1},\dots,\mathbf{x}_{n})$，則 $A\mathbf{x}_{j}=\lambda_{j}\mathbf{x}_{j}$ 是 $AX$ 的第 $j$ 個 column vector。
所以 $AX=(A\mathbf{x}_{1},\dots,A\mathbf{x}_{n})=(\lambda_{1}\mathbf{x}_{1},\dots,\lambda_{n}\mathbf{x}_{n})$ 
$=(\mathbf{x}_{1},\dots,\mathbf{x}_{n})\begin{bmatrix}\lambda_{1} &  &  &  \\  & \lambda_{2} &  &  \\ &  &  \vdots \\  &  &  & \lambda_{n}\end{bmatrix}$ 
$=XD$ 
因為 $X$ 有 $n$ 個線性獨立 column vectors，所以 $X$ 可逆。
那麼有：$D=X^{-1}AX$。

注意到：
1. $X$ 的 column vectors 由 $A$ 的特徵向量組成。$D$ 的對角線元素由對應的特徵值組成。
2. $X$ 並不唯一，可以交換 column vectors 或乘以標量。
3. 若 $A$ 為 $n\times n$ 矩陣且有 $n$ 個相異特徵值，則 $A$ 可被對角化。若 $A$ 沒有 $n$ 個線性獨立的特徵向量，則 $A$ 不可被對角化，此時我們稱 $A$ 為 defective matrix。(注意到不可能有大於 $n$ 個線性獨立的特徵向量) (注意到有小於 $n$ 個特徵值不可直接斷定 $A$ 不可對角化，因為仍有可能找出 $n$ 個線性獨立的特徵向量)
4. 若 $A$ 可對角化，則 $A$ 可被分解成 $A=XDX^{-1}$。

因為我們注意到了 4，所以有：

$$
A^{k}=XD^{k}X^{-1}=X\begin{bmatrix}
(\lambda_{1})^{k} &  &  &  \\
 & (\lambda_{2})^{k} &  &  \\
 &  & \dots  &  \\
 &  &  & (\lambda_{n})^{k}
\end{bmatrix}X^{-1}
$$

## The Polynomials of Matrices

如果我們定義 $p(x)=a_{m}x^{m}+\dots+a_{0}$ 為一個多項式，且 $A$ 為 $n\times n$ 矩陣，則：

$$
p(A)=a_{m}A^{m}+\dots+a_{0}I
$$

若 $A$ 可對角化，則：

$$
p(A)=a_{m}A^{m}+\dots+a_{0}I=X(a_{m}D^{m}+\dots+a_{0}I)X^{-1}=Xp(D)X^{-1}
$$

其中，

$$
p(D)=\begin{bmatrix}
p(\lambda_{1}) & 0 & \dots & 0 \\
0 & p(\lambda_{2}) & \dots & 0 \\
\vdots \\
0 & 0 & \dots & p(\lambda_{n})
\end{bmatrix}
$$

## The Exponential of a Matrix

給定一個標量 $a$，$e^{a}$ 的值根據泰勒展開可得：

$$
e^{a}=1+a+\frac{1}{2!}a^{2}+\frac{1}{3!}a^{3}+\dots
$$

類似地，給定任意 $n\times n$ 矩陣 $A$，可得：

$$
e^{A}=1+A+\frac{1}{2!}A^{2}+\frac{1}{3!}A^{3}+\dots
$$

若 $A$ 可對角化，則：

$$
e^{A}=X\left( 1+D+\frac{1}{2!}D^{2}+\frac{1}{3!}D^{3} \right)X^{-1}=Xe^{D}X^{-1}
$$

其中，

$$
e^{D}=\begin{bmatrix}
e^{\lambda_{1}} &  &  &  \\
 & e^{\lambda_{2}} &  &  \\
 &  &  \dots  & \\
 &  &  & e^{\lambda_{n}}
\end{bmatrix}
$$

## Markov Chains

啥是馬可夫過程呀？就是滿足以下性質的隨機過程：
1. 產出的結果或狀態組成的集合有限。
2. 此時產出的結果僅依賴於上次產出的結果。
3. 機率不論時間如何變化都保持不變。

有個定理：若一個 $n\times n$ 矩陣 $A$ 的馬可夫鏈收斂到一個**穩定狀態(steady-state)** 向量 $\mathbf{x}$，則：
1. $\mathbf{x}$ 是一個機率向量。
2. $\lambda_{1}=1$ 是 $A$ 的一個特徵值，且 $\mathbf{x}$ 是 $\lambda_{1}$ 對應的特徵向量。(因為 $A\mathbf{x}=1\cdot \mathbf{x}$)

所以，想要求穩定狀態 $\mathbf{x}$，我們可以找到 $A$ 在特徵值等於 $1$ 時的 null space，然後在其中挑選一個分量和為 $1$ 的向量。

再有一個定理：若 $\lambda_{1}=1$ 是 $A$ 的特徵值的絕對值最大者，則 $A$ 會有一個穩定狀態。

# Hermitian Matrices

令 $\mathbb{C}^{n}$ 表示所有 n-tuples 複數的向量空間，$\mathbb{C}$ 為所有可能被選為標量的複數集合。

就之前討論來說，我們已知實數元素矩陣 $A$ 的特徵值可能是複數，所以接下來我們叫討論包含複數的矩陣。

## Complex Inner Products

若 $\alpha=a+bi$ 為一個複數標量，則其長度定義為：

$$
|\alpha|=|a+bi|=\sqrt{ \bar{\alpha}\alpha }=\sqrt{ a^{2}+b^{2} }
$$

其中，$\bar{\alpha}$ 代表對 $\alpha$ 取共軛，也就是 $\bar{\alpha}=a-bi$。

注意到 $(a+bi)(a-bi)=a^{2}-(bi)^{2}=a^{2}-b^{2}(-1)=a^{2}+b^{2}$。

定義向量 $\mathbf{z}=(z_{1},z_{2},\dots,z_{n})^{T}\in \mathbb{C}^{n}$ 的長度為：

$$
\begin{align}
||\mathbf{z}|| & =(|z_{1}|^{2}+|z_{2}|^{2}+\dots+|z_{n}^{2}|)^{1/2} \\
 & =(\bar{z_{1}}z_{1}+\bar{z_{2}}z_{2}+\dots+\bar{z_{n}}z_{n})^{1/2} \\
 & =(\bar{\mathbf{z}}^{T}\mathbf{z})^{1/2}
\end{align}
$$

為了方便啊，我們把取共軛加上轉置這個動作用 $H$ 表達：

$$
\bar{\mathbf{z}}^{T}=\mathbf{z}^{H}\quad\text{and}\quad||\mathbf{z}||=(\mathbf{z}^{H}\mathbf{z})^{1/2}
$$

令 $V$ 為複數向量空間，取 $\mathbf{z},\mathbf{w}\in V$，則 $V$ 上的內積有如下定義：
1. $\langle \mathbf{z},\mathbf{z} \rangle\geq 0$，等號成立 $\iff \mathbf{z}=\mathbf{0}$。
2. $\langle \mathbf{z},\mathbf{w} \rangle= \overline{\langle \mathbf{w},\mathbf{z} \rangle}$ 
3. $\langle \alpha \mathbf{z}+\beta \mathbf{w},\mathbf{u} \rangle=\alpha \langle \mathbf{z},\mathbf{u} \rangle+\beta \langle \mathbf{w},\mathbf{u} \rangle$ 

至於第二點為何正確，我們可以做出如下簡單測驗：
$\langle \mathbf{z},\mathbf{w} \rangle=\sum_{i=1}^{n}z_{i}\overline{w_{i}}$ 與 $\langle \mathbf{w},\mathbf{z} \rangle=\sum_{i=1}^{n}w_{i}\overline{{z}_{i}}$ 
如果對第二個式子整體取共軛，有：$\overline{\langle \mathbf{w},\mathbf{z} \rangle}=\sum_{i=1}^{n}\overline{w_{i}}z_{i}=\sum_{i=1}^{n}z_{i}\overline{w_{i}}=\langle \mathbf{z},\mathbf{w} \rangle$ 

需要注意，第三點只有在標量分配在左邊時成立，如果相反 $\langle \mathbf{u},\alpha \mathbf{z}+\beta \mathbf{w} \rangle$ 則：
$\langle \mathbf{u},\alpha \mathbf{z}+\beta \mathbf{w} \rangle=\overline{\langle \alpha \mathbf{z}+\beta \mathbf{w},\mathbf{u} \rangle}=\overline{\alpha \langle \mathbf{z},\mathbf{u} \rangle}+\overline{\beta \langle \mathbf{w},\mathbf{u} \rangle}=\overline{\alpha}\langle \mathbf{u},\mathbf{z} \rangle+\overline{\beta}\langle \mathbf{u},\mathbf{w} \rangle$ 

綜上所述，我們將內積定義為：

$$
\langle \mathbf{z},\mathbf{w} \rangle =\mathbf{w}^{H}\mathbf{z}
$$

| $\mathbb{R}^{n}$                                                 | $\mathbb{C}^{n}$                                                 |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| $\langle \mathbf{x},\mathbf{y} \rangle=\mathbf{y}^{T}\mathbf{x}$ | $\langle \mathbf{x},\mathbf{y} \rangle=\mathbf{y}^{H}\mathbf{x}$ |
| $\mathbf{x}^{T}\mathbf{y}=\mathbf{y}^{T}\mathbf{x}$              | $\mathbf{x}^{H}\mathbf{y}=\overline{\mathbf{y}^{H}\mathbf{x}}$   |
| $\|\mathbf{x}\|^{2}=\mathbf{x}^{T}\mathbf{x}$                    | $\|\mathbf{x}\|^{2}=\mathbf{x}^{H}\mathbf{x}$                    |

## Hermitian Matrices

令 $M=(m_{ij})$ 為 $m\times n$ 矩陣，且 $m_{ij}=a_{ij}+ib_{ij}$。

我們可以表示成：

$$
M=A+iB
$$

其中，$A=(a_{ij})$，$B=(b_{ij})$ 擁有實數元素。

我們定義 $M$ 個共軛為：

$$
\overline{M}=A-iB
$$

如果 $A,B\in \mathbb{C}^{m\times n}$ 且 $C\in \mathbb{C}^{n\times r}$，則有：
1. $(A^{H})^{H}=A$ 
2. $(\alpha A+\beta B)^{H}=\overline{\alpha}A^{H}+\overline{ \beta }B^{H}$ 
3. $(AC)^{H}=C^{H}A^{H}$ 

第三點我們可以快速證：$(\overline{ AC })^{T} = (\overline{ A }\ \overline{ C })^{T}=\overline{ C^{T} } \ \overline{ A^{T} }=C^{H}A^{H}$ 

矩陣 $M$ 被稱為 Hermitian 若：

$$
M^{H}=M
$$

因為實數取共軛會等於自己，所以如果一個矩陣擁有實數元素，且對稱，則它就會是 Hermitian。

Hermitian 矩陣有很多特性，例如下述定理：
1. Hermitian 矩陣的特徵值必全為實數。
2. Hermitian 矩陣的相異特徵值對應的特徵向量會直交。(不能保證同一特徵值下不同的特徵向量直交)

proof:
(I)
令 $A$ 為 Hermitian 矩陣，且 $\lambda$ 為 $A$ 的特徵值，$\mathbf{x}$ 為 $\lambda$ 對應的特徵向量。
令 $\alpha=\mathbf{x}^{H}A\mathbf{x}$，則 $\overline{ \alpha }=\alpha^{H}=(\mathbf{x}^{H}A\mathbf{x})^{H}=\mathbf{x}^{H}A\mathbf{x}=\alpha$，所以 $\alpha$ 為實數。
又 $\alpha=\mathbf{x}^{H}A\mathbf{x}=\mathbf{x}^{H}\lambda \mathbf{x}=\lambda||\mathbf{x}||^{2}\implies \lambda=\frac{\alpha}{||\mathbf{x}||^{2}}$ 為實數。
(II)
令 $\lambda_{1}$，$\lambda_{2}$ 為 $A$ 的相異特徵值，$\mathbf{x}_{1}$，$\mathbf{x}_{2}$ 為對應的特徵向量。
$(A\mathbf{x}_{1})^{H}\mathbf{x_{2}}=\mathbf{x}_{1}^{H}A\mathbf{x}_{2}=\lambda_{2}\mathbf{x}_{1}^{H}\mathbf{x}_{2}$ 
$(A\mathbf{x}_{1})^{H}\mathbf{x}_{2}=(\mathbf{x}_{2}^{H}A\mathbf{x}_{1})^{H}=(\lambda_{1}\mathbf{x}_{2}^{H}\mathbf{x}_{1})^{H}=\lambda_{1}\mathbf{x}_{1}^{H}\mathbf{x}_{2}$ 
$\implies \lambda_{1}\mathbf{x}_{1}^{H}\mathbf{x}_{2}=\lambda_{2}\mathbf{x}_{1}^{H}\mathbf{x}_{2}$ 
因為 $\lambda_{1}\neq \lambda_{2}$，所以必有 $\mathbf{x}_{1}^{H}\mathbf{x}_{2}=\langle \mathbf{x}_{2},\mathbf{x}_{1} \rangle=0$。

### Unitary Matrix

若一個 $n\times n$ 矩陣 $U$ 被稱為單位矩陣，則 $U$ 的 column vectors 構成一個 orthonormal set $\in \mathbb{C}^{n}$ (每個 column vector 的長度都為一，且兩兩互相正交)。

那麼，$U$ 為單位矩陣 $\iff U^{H}U=I$。

如果 $U$ 為單位矩陣，因為 column vectors 正交，所以 $\text{rank }U=n$。又因為滿秩且為 $n\times n$ 矩陣，所以 $U$ 可逆 $\implies U^{-1}=U^{H}$。

我們將實數單位向量稱為 orthogonal matrix。(但實際上 orthonormal 就是了)

有個引理：如果 $A$ 為 Hermitian 矩陣且 $A$ 的特徵值們相異，則存在一個單位矩陣 $U$ 將 $A$ 對角化。(實際上，如果特徵值們不相異這條也會成立)

proof:
不難證，我們在 6.2 就證過了。只是那時直接帶 $X$ 為特徵向量組成的，現在多一個把特徵向量變成單位向量的操作而已。

## Schur's Theorem

對每個 $n\times n$ 矩陣 $A$，都會存在一個單位矩陣 $U$ 使得 $U^{H}AU$ 為上三角矩陣。

proof:
我們使用數學歸納法證明。
當 $n=1$ 時結論明顯成立，取 $U=\begin{bmatrix}1\end{bmatrix}$ 即可。
若當 $n=k$ 時成立，考慮 $n=k+1$ 時的情況。
令 $A$ 為 $(n+1)\times(n+1)$ 矩陣，且 $\lambda_{1}$ 為 $A$ 的特徵值，$\mathbf{w}_{1}$ 為相應單位特徵向量。
通過 Gram-Schmidt process，可以構成 $\mathbf{w}_{2},\dots,\mathbf{w}_{k+1}$ 使得 $\{\mathbf{w}_{1},\dots,\mathbf{w}_{k+1}\}$ 為 $\mathbb{C}^{k+1}$ 的正交基底。
令 $W=(\mathbf{w}_{1},\dots,\mathbf{w}_{k+1})$，注意到 $W$ 為單位矩陣。
以及，$W^{H}A\mathbf{w}_{1}=\lambda_{1}W^{H}\mathbf{w}_{1}=\lambda_{1}\mathbf{e}$。
所以，$W^{H}AW$ 形如：$\begin{bmatrix}\lambda_{1} & \dots & \dots \\ 0 &  &  \\ \vdots & M &  \\ 0 &  & \end{bmatrix}$ 。
其中，$M$ 為 $n\times n$ 矩陣。根據假設，一定存在一個 $k\times k$ 單位矩陣 $V_{1}$ 使得 $V_{1}^{H}MV=T_{1}$，其中 $T_{1}$ 為三角矩陣。
那麼，令 $V$ 為 $(k+1)\times(k+1)$ 單位矩陣形如：$\begin{bmatrix}1 & 0 & \dots & 0 \\ 0 &  &  &  \\ \vdots &  & V_{1} &  \\ 0\end{bmatrix}$。
則有 $V^{H}W^{H}AWV=\begin{bmatrix}\lambda_{1} & \dots & \dots \\ 0 &  &  \\ \vdots & V_{1}^{H}MV &  \\ 0 &  & \end{bmatrix}=\begin{bmatrix}\lambda_{1} & \dots & \dots \\ 0 &  &  \\ \vdots & T_{1} &  \\ 0 &  & \end{bmatrix}=T$ 。
令 $U=WV$，則 $U$ 也是單位矩陣，因為 $U^{H}U=V^{H}W^{H}W=I$。
而且，$U^{H}AU=T$。

$A=UTU^{H}$ 通常被稱為 Schur decomposition of $A$。

## Spectral Theorem

忙活了一大堆，終於到這了。

定理說：若 $A$ Hermitian，則存在單位矩陣 $U$  使得 $A$ 可被對角化。($A$ 不可能是 defective 的)

proof:
由上述定理，存在一個矩陣 $U$ 使得 $U^{H}AU=T$，其中 $T$ 為三角矩陣。
又有 $T^{H}=(U^{H}AU)^{H}=U^{H}AU=T$，所以 $T$ 也是 Hermitian，且是對角矩陣。

注意到，一個 Hermitian 矩陣 $A$ 可以被分解成 $UDU^{H}$，其中 $U$ 為單位矩陣且 $D$ 為對角矩陣。

我們可以寫成：$AU=UD$，如果我們對某一 column 專心看，有：

$A\mathbf{u}_{i}=d_{i}\mathbf{u}_{i}$，其中 $\mathbf{u}_{i}$ 為特徵向量，$d_{i}$ 為特徵值。(就這樣被定義逼出來啦！)

誒，這個東西好像我們之前講對角化的時候出現過誒。這麼想就對了，那個時候只說可以找到矩陣 $X$ 使得 $A$ 被對角化，但是這個定理告訴我們這個 $X$ 一定可以被化成單位矩陣！

需要注意的是，因為化成單位矩陣的過程需要使用 Gram-Schmidt process，只能在同一個向量空間中作用。而我們 Hermitian 矩陣又保證了不同特徵值對應出來的特徵向量會互相垂直，略過了不同向量空間無法跨空間做 Gram-Schmidt 的限制，所以才可以費盡心思找到這個單位矩陣喔！

總結一下，怎麼找到這個矩陣？
1. 先找 Hermitian 矩陣 $A$ 的特徵值們。
2. 找到特徵值們對應的特徵向量們。
3. 對每個特徵空間的基底做 Gram-Schmidt process，找到正交基底。
4. 把這一堆正交基底構成的向量就是我們想找的矩陣啦！

你會問，找這幹啥呀？方便著呢！

如果 $A$ 有 orthonormal sets of eigenvectors $\{\mathbf{u}_{1},\dots,\mathbf{u}_{n}\}$，且 $\mathbf{x}=c_{1}\mathbf{u}_{1}+\dots+c_{n}\mathbf{u}_{n}$，則：

$$
A\mathbf{x}=\lambda_{1}c_{1}\mathbf{u}_{1}+\dots+\lambda_{n}c_{n}\mathbf{u}_{n}
$$

我們又知道：$c_{i}=\langle \mathbf{x},\mathbf{u}_{i} \rangle=\mathbf{u}_{i}^{H}\mathbf{x}$，則：

$$
A\mathbf{x}=\lambda_{1}(\mathbf{u}_{1}^{H}\mathbf{x})\mathbf{u}_{1}+\dots+\lambda_{n}(\mathbf{u}_{n}^{H}\mathbf{x})\mathbf{u}_{n}
$$

## Normal Matrices

有些 non-Hermitian 矩陣仍然可以擁有完整且由特徵向量構成的正交集合。例如 skew-symmetric 與 skew-Hermitian 矩陣 ($A^{H}=-A^{H}$) 都有這個性質。

若任意 $A$ 矩陣擁有完整且由特徵向量構成的正交集合，則 $A=UDU^{H}$ 其中 $U$ 為單位向量且 $D$ 為對角矩陣 (可能包含複數)。若 $D^{H}\neq D$，則 $A^{H}=UD^{H}U^{H}\neq A$。

然而：

$$
AA^{H}=UDU^{H}UD^{H}U^{H}=UDD^{H}U^{H}
$$

且：

$$
A^{H}A=UD^{H}U^{H}UDU^{H}=UD^{H}DU^{H}
$$

又：

$$
D^{H}D=DD^{H}=\begin{bmatrix}
|\lambda_{1}|^{2} &  &  &  \\
 & |\lambda_{2}|^{2} &  &  \\
 &  & \dots &  \\
 &  &  & |\lambda_{n}|^{2}
\end{bmatrix}
$$

所以：

$$
AA^{H}=A^{H}A
$$

我們定義：如果 $A$ 滿足 $AA^{H}=A^{H}A$ 則稱 $A$ 為 **normal matrix(正規矩陣)**。

然後有個定理請你看一下：矩陣 $A$ 為 normal matrix $\iff$ $A$ 擁有完整的由特徵向量構成的正交集合。

proof:
由上面的說明，我們已經證明了 $\impliedby$，現在我們只需要證明 $\implies$。
($\implies$)
根據上面好久 (也不是很久) 之前的定理，我們知道一定存在一個單位矩陣 $U$ 與三角矩陣 $T$ 使得 $T=U^{H}AU$。
注意到：$TT^{H}=U^{H}AA^{H}U$，$T^{H}T=U^{H}A^{H}AU$。又 $A^{H}A=AA^{H}$，所以 $T$ 也是 normal matrix。
我們對比 $TT^{H}$ 與 $T^{H}T$ 的對角線元素，可以發現當 $i\neq j$ 時 $t_{ij}=0$。
所以 $U$ 將 $A$ 對角化，且 $U$ 的 column vectors 會是 $A$ 的特徵向量。

# The Singular Value Decomposition

此節中，我們假設 $A$ 是 $m\times n$ 矩陣且 $m\geq n$。(注意到這樣假設只是為了方便，所有結論對於 $n>m$ 接成立)

我們想要找到一個方法來將 $A$ 分解成 $A=U\Sigma V^{T}$，其中 $U$ 為 $m\times m$ 單位矩陣，$V$ 為 $n\times n$ 單位矩陣。特別地， $\Sigma$ 為所有非對角元素皆為零的 $m\times n$ 矩陣，並且對角元素滿足：

$$
\sigma_{1}\geq\sigma_{2}\geq\dots\geq\sigma_{n}\geq0
$$
$$
\Sigma=\begin{bmatrix}
\sigma_{1} &  &  &  \\
 & \sigma_{2} &  &  \\
 &  & \dots &  \\
 &  &  & \sigma_{n}
\end{bmatrix}
$$

我們將 $\sigma_{i}$  稱為 $A$ 的**奇異值(singular value)**，而 $A=U\Sigma V^{T}$ 稱為 $A$ 的**奇異值分解(Singular Value Decomposition, SVD)**。

之後我們會說明，$\text{rank } A$ 就是所有非零奇異值的個數。

## The SVD Theorem

我們要證明，對於任意 $m\times n$ 矩陣 $A$，都能被奇異值分解。

構造出 $A^{T}A$，此矩陣為對稱的 $n\times n$ 矩陣。所以，它的所有特徵值都是實數，且可以找到一個矩陣 $V$，其 column vectors 互相正交並可以使得 $A^{T}A$ 被對角化。

不僅如此，$A^{T}A$ 的特徵值必須非負。因為：

$$
||A\mathbf{x}||^{2}=\langle A\mathbf{x},A\mathbf{x} \rangle =(A\mathbf{x})^{T}A\mathbf{x}=\mathbf{x}^{T}A^{T}A\mathbf{x}=\lambda||\mathbf{x}||^{2}
$$

有 $||A\mathbf{x}||^{2}\geq0$ 且 $||\mathbf{x}||^{2}\geq 0$，所以 $\lambda\geq 0$。

我們令 $V$ 的 column 有序，使得相應的 ($A^{T}A$ 的) 特徵值滿足：

$$
\lambda_{1}\geq \lambda_{2}\geq\dots\geq \lambda_{n}\geq 0
$$

而 $A$ 的奇異值為：

$$
\sigma_{j}=\sqrt{ \lambda_{j} }\quad j=1,\dots,n
$$

令 $r$ 表示 $A$ 的秩，則 $A^{T}A$ 的秩也為 $r$。因為 $A^{T}A$ 對稱，所以它的秩會等於非零特徵值的個數。(特徵值為零代表該方向被壓成零，所以沒被壓成零的方向數等於秩)。

所以：

$$
\lambda_{1}\geq \lambda_{2}\geq\dots\geq \lambda_{r}>0\quad\text{ and }\lambda_{r+1}=\lambda_{r+2}=\dots=\lambda_{n}=0
$$

對於奇異值 $\sigma_{i}$ 來說，也有相同的關係。

令 $V_{1}=(\mathbf{v}_{1},\dots,\mathbf{v}_{r})$，$V_{2}=(\mathbf{v}_{r+1},\dots,\mathbf{v}_{n})$，$\Sigma_{1}=\begin{bmatrix}\sigma_{1} &  &  &  \\  & \sigma_{2} &  &  \\  &  & \dots &  \\  &  &  & \sigma_{r}\end{bmatrix}$ 。

那麼，$\Sigma=\begin{bmatrix}\Sigma_{1} & O \\ O & O\end{bmatrix}$。

因為 $V_{2}$ 的 column vectors 是 $A^{T}A$ 的特徵值 $\lambda=0$ 對應的特徵向量，所以：

$$
A^{T}A\mathbf{v}_{j}=\mathbf{0}\quad j=r+1,\dots,n
$$

那麼，$V_{2}$ 的 column vectors 會構成 $N(A^{T}A)=N(A)$ 的正交基底。那麼：

$$
AV_{2}=O
$$

又因為 $V$ 是單位向量，所以：

$$
\begin{align}
 & I=VV^{T}=V_{1}V_{1}^{T}+V_{2}V_{2}^{T} \\
 & A=AI=AV_{1}V_{1}^{T}+AV_{2}V_{2}^{T}=AV_{1}V_{1}^{T}
\end{align}
$$

到目前為止，我們已經構造了 $V$ 與 $\Sigma$。我們現在只需要尋找大小為 $m\times n$ 的單位矩陣 $U$ 使得：

$$
A=U\Sigma V^{T}
$$

移項，我們有：$AV=U\Sigma$。

比對前 $r$ 個 column 項：

$$
A\mathbf{v}_{j}=\sigma_{j}\mathbf{u}_{j}\quad j=1,\dots,r
$$

我們令：

$$
\mathbf{u}_{j}=\frac{1}{\sigma_{j}}A\mathbf{v}_{j}\quad j=1,\dots,r
$$

以及，$U_{1}=(\mathbf{u}_{1},\dots,\mathbf{u}_{r})$。則滿足：$AV_{1}=U_{1}\Sigma_{1}$。如果你想驗證 $U_{1}$ 的 column vectors 組成了 orthonormal set，可以去驗證：$\langle \mathbf{u}_{i},\mathbf{u}_{j} \rangle=\delta_{ij}$。

而且，由上式還可以知道，$\mathbf{u}_{j}, \ 1\leq j\leq r$ 會在 $R(A)$ 裡面。又因為 $R(A)$ 的維度為 $r$ 且 $\mathbf{u}_{1},\dots,\mathbf{u}_{r}$ 線性獨立，所以它們是 $R(A)$ 的一組基底。

我們現在想找 $\mathbf{u}_{r+1},\dots,\mathbf{u}_{m}$ 且與 $\mathbf{u}_{1},\dots,\mathbf{u}_{r}$ 仍兩兩正交，也就是找 $R(A)^{\perp}=N(A^{T})$。令 $\{\mathbf{u}_{r+1},\dots,\mathbf{u}_{m}\}$ 為 $N(A^{T})$ 的一組基底，並令 $U_{2}=(\mathbf{u}_{r+1},\dots,\mathbf{u}_{m})$。

令：

$$
U=\begin{bmatrix}
U_{1} & U_{2}
\end{bmatrix}
$$

就成功找到所求的 $U$ 了。

驗證一下：

$$
\begin{align}
U\Sigma V^{T} & =\begin{bmatrix}
U_{1} & U_{2}
\end{bmatrix}\begin{bmatrix}
\Sigma_{1} & O \\
O & O
\end{bmatrix}\begin{bmatrix}
V_{1}^{T} \\
V_{2}^{T}
\end{bmatrix} \\
 & =U_{1}\Sigma_{1}V_{1}^{T} \\
 & =AV_{1}V_{1}^{T} \\
 & =A
\end{align}
$$

注意到：
1. $A$ 的奇異值 $\sigma_{1},\dots,\sigma_{n}$ 唯一，但是 $U$ 和 $V$ 不唯一。
2. 因為 $V$ 使得 $A^{T}A$ 對角化，所以 $\mathbf{v}_{j}$ 是 $A^{T}A$ 的特徵向量。
3. $\mathbf{v}_{j}$ 被稱為**右奇異向量(right singular vector)**，$\mathbf{u}_{j}$ 被稱為左奇異向量。
4. $A$ 的秩會等於非零奇異值($\sigma=\sqrt{ \lambda }$，但是這裡的 $\lambda$ 是相對於 $A^{T}A$ 的)的個數，但是不等於非零特徵值的個數。
5. 如果我們直接令 $A=U_{1}\Sigma_{1}V_{1}^{T}$，則這種 SVD 稱為 compact form of the singular value decomposition。

我們綜整尋找 SVD 分解的步驟：
1. 計算 $A^{T}A$。
2. 計算 $A^{T}A$ 的特徵值，並由大排到小。
3. 由 $A^{T}A$ 的特徵值計算 $A$ 的奇異值，並由大排到小。
4. 令 $\mathbf{v}_{i}$ 為 $\lambda_{i}$ 對應的特徵向量。
5. 令 $\Sigma_{1}$ 為對角矩陣且對角元素為 $\sigma_{i}$，$\Sigma=\begin{bmatrix}\Sigma_{1} & O \\ O & O\end{bmatrix}$。
6. 令 $\mathbf{u}_{i}=\frac{1}{\sigma_{i}}A\mathbf{v}_{i}\quad 1\leq i\leq r$。
7. 計算 $N(A^{T})$ 的正交基底 $\mathbf{w}_{r+1},\dots,\mathbf{w}_{m}$ 令 $\mathbf{u}_{j}=\mathbf{w}_{j}\quad r<j\leq m$。
8. $A=U\Sigma V^{T}$。

# 重要例題

