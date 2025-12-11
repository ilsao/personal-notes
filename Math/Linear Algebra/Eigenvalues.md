
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

# 重要例題

