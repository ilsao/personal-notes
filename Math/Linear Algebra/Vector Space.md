
# Definition

## Vector Space Axioms

令 $V$ 為定義了加法與數量積操作的**非空集合**($\mathbf{0} \in V$)。對於 $\mathbf{x}$ 與 $\mathbf{y}$ 在 $V$ 中，我們有 $\mathbf{x}+\mathbf{y}$ 仍在 $V$ 中。如果有數量積 $\alpha$，我們有 $\alpha \mathbf{x}$ 仍在 $V$ 中。我們稱符合以下定義且具有加法與數量積操作的集合 $V$ 為向量空間。

- $\mathbf{x}+\mathbf{y} \in V$ for any x and y in V. 
- $\alpha \mathbf{x} \in V$ for any scalar $\alpha$ and $x$ in V. 
- $\mathbf{x}+\mathbf{y}=\mathbf{y}+\mathbf{x}$ for any x and y in V. 
- $(\mathbf{x+y})+\mathbf{z}=\mathbf{x+(\mathbf{y+z})}$ for any x, y, and z in V. 
- There exists an element $\mathbf{0}$ in V such that $\mathbf{x}+\mathbf{0}=\mathbf{x}$ for each $\mathbf{x} \in V$. 
- For each $\mathbf{x} \in V$, there exists an element $-\mathbf{x}$ in V such that $\mathbf{x}+(-\mathbf{x})=\mathbf{0}$. 
- $\alpha(\mathbf{x}+\mathbf{y})=\alpha \mathbf{x}+\alpha \mathbf{y}$ for each scalar $\alpha$ and any $\mathbf{x}$ and $\mathbf{y}$ in V. 
- $(\alpha\beta)\mathbf{x}=\alpha(\beta \mathbf{x})$ for any scalars $\alpha$ and $\beta$ and any $\mathbf{x} \in V$. 
- $1\mathbf{x}=\mathbf{x}$ for all $\mathbf{x}\in V$. 

以上十條的第一與第二條很重要！我們舉例來跟你說為啥：

假設有一個集合：$W=\{(a,1) | a \text{ real}\}$。

假設兩個元素 $(3,1)$ 與 $(5,1)$ 在集合中。$(3,1)+(5,1)=(8,2) \not\in W$，且數量積也不在 $W$ 中。所以 $W$ 不是一個向量空間。

對於向量空間中的元素，我們就稱為向量。

## The Vector Space $C[a,b]$ 

我們定義 $C[a,b]$ 為所有在區間 $[a,b]$ 皆有定義且連續的實數函數構成的向量空間。所以，我們的向量就是被包含在 $C[a,b]$ 中的函數們。

我們檢查 $(f+g)(x)=f(x)+g(x)$(兩連續函數的和仍為連續函數)，$(\alpha f)(x)=\alpha f(x)$(常數乘以連續函數仍為連續函數) 皆在 $C[a,b]$ 中。

因此，我們可以定義加法操作 $(f+g)(x)=(g+f)(x)$ 滿足 $\mathbf{x}+\mathbf{y}=\mathbf{y}+\mathbf{x}$(因為 $(f+g)(x)=f(x)+g(x)=g(x)+f(x)=(g+f)(x)$)。

我們還可以定義一個函數 $z(x)=0\text{ for all }x\text{ in }[a,b]$，使得 $f+z=f\text{ for all }f\text{ in }C[a,b]$。

哎呀，對於剩下的公理就留給可愛滴讀者證明叭～

## The Vector Space $P_{n}$ 

定義 $P_{n}$ 代表所以最高次係數小於等於 $n$ 的多項式形成的集合。定義 $p+q$ 與 $\alpha p$ 如下：$(p+q)(x)=(q+p)(x)$ 與 $(\alpha p)(x)=\alpha p(x)$ 對於所有 $x \in  \mathbb{R}$ 成立。在這種情況下，零向量等於零多項式。

作者又很欠扁啦～說想證明公理對 $P_{n}$ 都成立非常手拿把掐，所以這個東東是一個向量空間呦！

需要注意的是 $P_{n}$ 的定義，如果定義變成最高次係數為 $n$ 且其係數不為零，那麼這個集合就不是向量空間。舉一個簡單的反例：$x^{n} + (-x^{n})=0 \not\in P'_{n}$。

## Additional Properties of Vector Spaces

$$
\begin{align}
 & \text{If }V\text{ is a vector and }\mathbf{x}\text{ is any element of }V\text{, then} \\
 & (i) \ 0\mathbf{x}=\mathbf{0} \\
 & (ii) \ \mathbf{x+y}=\mathbf{0} \text{ implies that }\mathbf{y=-\mathbf{x}}(\text{i.e., the additive inverse of }\mathbf{x}\text{ is unique}.) \\
 & (iii) \ (-1)\mathbf{x}=\mathbf{-x}
\end{align}
$$

proof:
(i)
$\mathbf{x}=1\mathbf{x}=(1+0)\mathbf{x}=\mathbf{x}+0\mathbf{x}$ 
$-\mathbf{x}+\mathbf{x}=-\mathbf{x}+(\mathbf{x}+0\mathbf{x})=(-\mathbf{x}+\mathbf{x})+0\mathbf{x}$ 
$\mathbf{0}=\mathbf{(-x)+\mathbf{x}}=0+0\mathbf{x}=0\mathbf{x}$ 

(ii)
假設 $\mathbf{x}+\mathbf{y}=0$。
那麼，$-\mathbf{x}=-\mathbf{x}+0=-\mathbf{x}+\mathbf{x}+\mathbf{y}=\mathbf{0}+\mathbf{y}=\mathbf{y}$。

(iii)
證明這條會用到以上兩個定理喔～
$\mathbf{0}=0\mathbf{x}=(1+(-1))\mathbf{x}=1\mathbf{x}+(-1\mathbf{x})$ 
$1\mathbf{x}+(-1\mathbf{x})=0\implies (-1)\mathbf{x}=-\mathbf{x}$ 

# Subspaces

## Definition

我們定義 $S$ 是 $V$ 的子空間：如果 $S$ 是 $V$ 的一個**非空**子集，且 $S$ 符合：
- $a\mathbf{x}\in S$ whenever $\mathbf{x}\in S$ for any scalar $\alpha$. 
- $\mathbf{x}+\mathbf{y} \in S$ whenever $\mathbf{x} \in S$ and $\mathbf{y}\in S$. 
- $\mathbf{0} \in S$. 

也就是說，對 $S$ 裡面的元素應用 $V$ 中定義的加法與數量積操作，仍會在 $S$ 中。

注意：
- 在向量空間 $V$ 中，我們可以知道 $\{\mathbf{0}\}$ 與 $V$ 都是它的子空間。我們將除了 $V$ 自身之外的子空間稱為**真子空間(proper subspaces)** (有元素在大空間裡但不在小空間裡)，而將 $\{\mathbf{0}\}$ 稱為**零子空間(zero subspace)**。

## The Null Space of a Matrix

令 $A$ 為一個 $m \times n$ 大小的矩陣。令 $N(A)$ 為所有 $A\mathbf{x}=\mathbf{0}$ 的解所構成的集合，那麼：

$$
N(A)=\{\mathbf{x} \in \mathbb{R}^{n} \ | \ A\mathbf{x}=\mathbf{0} \}
$$

讓我們證明 $N(A)$ 為 $\mathbb{R}^{n}$ 的子空間。

顯然，$\mathbf{0}\in N(A)$，所以 $N(A)$ 非空。假設 $\mathbf{x} \in N(A)$ 且 $\alpha$ 為一個標量，那麼：

$$
A(\alpha \mathbf{x})=\alpha A\mathbf{x}=\alpha \cdot \mathbf{0}=\mathbf{0}
$$

所以 $\alpha \mathbf{x} \in N(A)$。若 $\mathbf{x}$ 與 $\mathbf{y}$ 都屬於 $N(A)$，那麼：

$$
A(\mathbf{x}+\mathbf{y})=A\mathbf{x}+A\mathbf{y}=\mathbf{0}+\mathbf{0}=\mathbf{0}
$$

所以，$\mathbf{x}+\mathbf{y} \in N(A)$。那麼，$N(A)$ 確實為 $\mathbb{R}^{n}$ 的子空間。我們稱 $N(A)$ 為：**零空間(null space)**。


## The Span of a Set of Vectors

