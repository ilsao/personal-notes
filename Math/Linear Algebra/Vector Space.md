
# Definition

## Vector Space Axioms

令 $V$ 為定義了加法與數量積操作的**非空集合**($\mathbf{0} \in V$)。對於 $\mathbf{x}$ 與 $\mathbf{y}$ 在 $V$ 中，我們有 $\mathbf{x}+\mathbf{y}$ 仍在 $V$ 中。如果有數量積 $\alpha$，我們有 $\alpha \mathbf{x}$ 仍在 $V$ 中。我們稱符合以下定義且具有加法與數量積操作的集合 $V$ 為向量空間。

- $\mathbf{x}+\mathbf{y}=\mathbf{y}+\mathbf{x}$ for any x and y in V. 
- $(\mathbf{x+y})+\mathbf{z}=\mathbf{x+(\mathbf{y+z})}$ for any x, y, and z in V. 
- There exists an element $\mathbf{0}$ in V such that $\mathbf{x}+\mathbf{0}=\mathbf{x}$ for each $\mathbf{x} \in V$. 
- For each $\mathbf{x} \in V$, there exists an element $-\mathbf{x}$ in V such that $\mathbf{x}+(-\mathbf{x})=\mathbf{0}$. 
- $\alpha(\mathbf{x}+\mathbf{y})=\alpha \mathbf{x}+\alpha \mathbf{y}$ for each scalar $\alpha$ and any $\mathbf{x}$ and $\mathbf{y}$ in V. 
- $(\alpha+\beta)\mathbf{x}=\alpha \mathbf{x}+\beta \mathbf{x}$. 
- $(\alpha\beta)\mathbf{x}=\alpha(\beta \mathbf{x})$ for any scalars $\alpha$ and $\beta$ and any $\mathbf{x} \in V$. 
- $1\mathbf{x}=\mathbf{x}$ for all $\mathbf{x}\in V$. 
- $\mathbf{x}+\mathbf{y} \in V$ for any x and y in V. 
- $\alpha \mathbf{x} \in V$ for any scalar $\alpha$ and $x$ in V. 

以上十條的最後兩條很重要！我們舉例來跟你說為啥：

假設有一個集合：$W=\{(a,1) | a \text{ real}\}$。

假設兩個元素 $(3,1)$ 與 $(5,1)$ 在集合中。$(3,1)+(5,1)=(8,2) \not\in W$，且數量積也不在 $W$ 中。所以 $W$ 不是一個向量空間。

對於向量空間中的元素，我們就稱為向量。

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

令 $\mathbf{v_{1}}, \mathbf{v_{2}}, \dots, \mathbf{v_{n}}$ 是向量空間 $V$ 中的向量，我們稱 $\alpha \mathbf{v_{1}}+\alpha \mathbf{v_{2}}+\dots+\alpha \mathbf{v_{n}}$ 為 $\mathbf{v_{1}}, \mathbf{v_{2}}, \dots, \mathbf{v_{n}}$ 的線性組合。**所有線性組合組成的集合**就稱為 $\mathbf{v_{1}}, \mathbf{v_{2}}, \dots, \mathbf{v_{n}}$ 的**生成空間(span)**，可以用 $\text{Span}(\mathbf{v_{1}}, \mathbf{v_{2}}, \dots, \mathbf{v_{n}})$ 表示。

$$
如果 \ \mathbf{v_{1}}, \mathbf{v_{2}}, \dots, \mathbf{v_{n}} \ 是向量空間 \ V \ 中的向量，那麼其生成空間必為 \ V \ 的子空間。
$$

proof:
令 $\beta$ 為標量，$\mathbf{v}=\alpha_{1} \mathbf{v_{1}}+\dots+\alpha_{n} \mathbf{v_{2}}$, $\mathbf{w}=\beta_{1} \mathbf{v_{1}}+\dots+\beta_{n} \mathbf{v_{2}}$ 為兩個取自 $\text{Span}(\mathbf{v_{1}}, \mathbf{v_{2}}, \dots, \mathbf{v_{n}})$ 的向量。
因為：
$\beta \mathbf{v}=(\beta_{1}\alpha_{1})\mathbf{v_{1}}+\dots+(\beta_{n}\alpha_{n})\mathbf{v_{n}} \in\text{Span}(\mathbf{v_{1}, \dots, v_{n}})$ 
且：
$\mathbf{v}+\mathbf{w}=(\alpha_{1}+\beta_{1})\mathbf{v_{1}}+\dots+(\alpha_{n}+\beta_{n})\mathbf{v_{n} \in \text{Span}(\mathbf{v_{1}},\dots,\mathbf{v_{n}})}$ 
所以，命題成立。

## Spanning Set for a Vector Space

$\mathbf{v_{1}}, \mathbf{v_{2}}, \dots \mathbf{v_{n}}$ 是 $V$ 的生成集 $\Leftrightarrow$ $V$ 可以被表達為 $\mathbf{v_{1}}, \mathbf{v_{2}}, \dots \mathbf{v_{n}}$ 的線性組合。

這邊有點繞，我們必須清楚的區分 Span 和 Spanning Set。其實，他們互為反向描述。

讓我們舉個例子，想要張出向量空間 $\mathbb{R}^{2}$，我們最少需要兩個向量作為生成集。因為一個向量的生成空間只會是一條直線。

我們可以取 $\{\mathbf{e_{1}}, \mathbf{e_{2}}\}$ 來張出 $\mathbb{R}^{2}$。那麼 $\{\mathbf{e_{1}}, \mathbf{e_{2}}\}$ 就是 $\mathbb{R}^{2}$ 的生成集。

如果我們想檢查 $\mathbf{v}$ 是否為 $S=\text{Span}(\mathbf{v_{1}},\dots,\mathbf{v_{n}})$ 中的向量，可以用增廣矩陣解線性組合，如果沒產生矛盾說明 $\mathbf{v}\in S$，否則 $\mathbf{v}\not\in S$。

如果想檢查 $\text{Span}(\mathbf{v_{1}},\dots,\mathbf{v_{j}})$ 是否張出了 $\mathbb{R}^{n}$：
- 如果 $j=n$，則求 $\det(\mathbf{v_{1}},\dots,\mathbf{v_{j}})$ 是否等於 $0$。不等於零說明線性獨立，可張出 $\mathbb{R}^{n}$，否則不行。
- 如果 $j> n$，則每 $n$ 個 $\mathbf{v_{i}}$ 一組求行列式。如果任意一組不等於零，可張出 $\mathbb{R}^{n}$，否則不行。

## Linear Systems Revisited

考慮一個有解的線性系統 $A\mathbf{x}=\mathbf{b}$。

如果 $\mathbf{b}=\mathbf{0}$，那麼所有解構成的集合 $S=N(A)$，且 $S$ 是 $\mathbb{R}^{n}$ 的子空間。

如果 $\mathbf{b}\neq \mathbf{0}$，那麼所有解構成的集合 $S$ 無法構成 $\mathbb{R}^{n}$ 的子空間，因為 $\mathbf{0} \not\in S$。

我們有：如果給定 $\mathbf{x_{0}}$ 為 $A\mathbf{x}=\mathbf{b}$ 的一組特定解，那麼 $\mathbf{y}$ 也會是一組解 $\Leftrightarrow \mathbf{y}=\mathbf{x_{0}}+\mathbf{z}$，其中 $\mathbf{z} \in N(A)$。

假設 $\mathbf{y}$ 為 $A\mathbf{x}=\mathbf{b}$ 的另一組解，則： 

$$
A\mathbf{z}=A\mathbf{y}-A\mathbf{x_{0}}=\mathbf{b}-\mathbf{b}=\mathbf{0}
$$

所以 $\mathbf{z}\in N(A)$。

又：

$$
A\mathbf{y}=A\mathbf{x_{0}}+A\mathbf{z}=\mathbf{b}+\mathbf{0}=\mathbf{b}
$$

所以，另一個解必為 $\mathbf{y}=\mathbf{x_{0}}+\mathbf{z}$，且 $\mathbf{z} \in N(A)$。

我們可以通過其幾何意含來更深入的了解：

令 $A$ 為一個 $3 \times 3$ 的矩陣。 想像 $N(A)$ 構成了一個通過原點的一條直線或平面。那麼我們找到的那個特定解 $\mathbf{x_{0}}$ 則代表被平移後的 $N(A)$ 中的一點。整個解集合 $S = \mathbf{x_{0}}+N(A)$ 就是 $N(A)$ 形成的直線或平面被使用 $\mathbf{x_{0}}$ 位移後的結果。

可以將解集合視為一個被平移後的子空間，如果 $\mathbf{b}\neq \mathbf{0}$ 則解集合不是 $\mathbb{R}^{3}$ 的子空間。我們稱這種空間叫**仿射子空間(affine subspace)**。

# Linear Independence

如果想要尋找最小生成集(沒有任何多餘的向量)，我們需要了解線性獨立與線性相依的概念。

我們定義：

$$
\text{向量空間 V 中的向量 }\mathbf{v_{1}, \dots,v_{n}}\text{ 如果滿足：}
$$
$$
c_{1}\mathbf{v_{1}} + \dots+c_{n}\mathbf{v_{n}}=\mathbf{0} \implies c_{1},\dots c_{n}\text{ 必須全部為零}
$$
$$
\text{則稱 }\mathbf{v_{1}, \dots, v_{n}}\text{ 線性獨立。}
$$

同時，我們還可以意識到線性相依的含義：向量空間中的某向量可以被寫成向量空間中的其他向量的線性組合。

$$
\text{向量空間 V 中的向量 }\mathbf{v_{1}, \dots,v_{n}}\text{ 如果滿足：}
$$
$$
c_{1}\mathbf{v_{1}} + \dots+c_{n}\mathbf{v_{n}}=\mathbf{0} \implies c_{1},\dots c_{n}\text{ 必須最少有一個非零}
$$
$$
\text{則稱 }\mathbf{v_{1}, \dots, v_{n}}\text{ 線性相依。}
$$

我們可以知道，**一個向量空間的最小生成集必須線性獨立**。因為一些線性相依的向量張出的生成空間，必定等於其減去一個或多個向量使得線性獨立時張出的生成空間。

可以這樣理解：

如果生成集中有 $\{\mathbf{v_{1},\mathbf{v_{2}},\mathbf{v_{3}}}\}$，且 $\mathbf{v_{3}}=c_{1}\mathbf{v_{1}}+c_{2}\mathbf{v_{2}}$。

那麼，這些向量形成的線性組合可以被表達為只有 $\mathbf{v_{1}}$ 與 $\mathbf{v_{2}}$ 的形式：
$\alpha_{1}\mathbf{v_{1}}+\alpha_{2}\mathbf{v_{2}}+\alpha_{3}\mathbf{v_{3}}=(\alpha_{1}+c_{1})\mathbf{v_{1}}+(\alpha_{2}+c_{2})\mathbf{v_{2}}$ 。

也就是說：$\text{Span}(\mathbf{v_{1}},\mathbf{v_{2}},\mathbf{v_{3}})=\text{Span}(\mathbf{v_{1}},\mathbf{v_{2}})$。

我們如下統整觀察到的現象：
1. 如果 $\mathbf{v_{1},\dots,\mathbf{v_{n}}}$ 張出一個向量空間 $V$，且其中某個向量可以被寫成其他 $n-1$ 個向量的線性組合，那麼那 $n-1$ 個向量同樣張出 $V$。
2. 給定 $n$ 個向量 $\mathbf{v_{1}},\dots \mathbf{v_{n}}$。如果有辦法將某個向量寫成其他 $n-1$ 個向量的線性組合 $\Leftrightarrow$ $c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}=\mathbf{0}$ 且 $c_{1},\dots,c_{n}$ 至少有一項 $\neq 0$。

proof (1):
假設 $\mathbf{v_{n}}$ 可以被其他向量的線性組合表達。
令 $\mathbf{v}$ 為向量空間 $V$ 中的向量，因為 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 可以張出 $V$，所以：
$\mathbf{v}=\alpha_{1} \mathbf{v_{1}}+\dots+\alpha _{n} \mathbf{v_{n}}=\alpha_{1}\mathbf{v_{1}}+\dots+\alpha_{n}(\beta_{1}\mathbf{v_{1}}+\dots+\beta_{n-1}\mathbf{v_{n-1}})$ 
$=(\alpha_{1}+\alpha_{n}\beta_{1})\mathbf{v_{1}} + \dots+(\alpha_{n-1}+\alpha_{n}\beta_{n-1})\mathbf{v_{n-1}}$ 
因為向量空間 $V$ 的任意向量 $\mathbf{v}$ 都可以被表達為 $\mathbf{v_{1}},\dots,\mathbf{v_{n-1}}$ 的線性組合，所以這些向量生成 $V$。

proof (2):
($\implies$)
假設 $\mathbf{v_{n}}$ 可以被其他向量的線性組合表達。
$\mathbf{v_{n}}=\alpha_{1}\mathbf{v_{1}}+\alpha_{2}\mathbf{v_{2}+\dots+\alpha_{n-1}\mathbf{v_{n-1}}}$ 
移項可得：$\alpha_{1}\mathbf{v_{1}}+\dots+\alpha_{n-1}\mathbf{v_{n-1}}-\mathbf{v_{n}}=\mathbf{0}$ 
如果我們設對於 $i,\dots,n-1$ 有 $c_{i}=\alpha_{i}$ ，且 $c_{n}=-1$，我們有：$c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}=\mathbf{0}$ 
( $\Leftarrow$ )
如果 $c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}=\mathbf{0}$，那麼一定有一個 $c_{i}\neq 0$ (這裡取 $c_{n}$) 使得：
$\mathbf{v_{n}}= \frac{-c_{1}}{c_{n}}\mathbf{v_{1}}+\dots+ \frac{-c_{n-1}}{c_{n}}\mathbf{v_{n-1}}$ 

由於線性獨立 $\implies$ $c_{1},\dots,c_{n}$ 全為零 $\implies \det(A)\neq 0$。

又有線性相依 $\implies c_{1},\dots,c_{n}$ 不全為零 $\implies \det(A)=0$。

本章的重點有點混亂：
- 線性相依：某向量可以被其他向量表達 $\implies$ $c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}=\mathbf{0}$ 且 $c_{1},\dots c_{n}\neq0$。$\boxed{\det(A)=0}$ 
- 線性獨立：沒有向量可以被其他向量表達 $\implies$  $c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}=\mathbf{0}$ 且 $c_{1},\dots c_{n}=0$。$\boxed{\det(A)\neq 0}$

## Geometric Interpretation

如果我們有 $\mathbb{R}^{3}$ 空間中的三個向量 $\mathbf{x,y,z}$，如果 $\mathbf{x,y}$ 線性相依，那麼：$c_{1}\mathbf{x}+c_{2}\mathbf{y}=\mathbf{0}$ 其中 $c_{1}, c_{2}$ 至少一個不為零。
假設 $c_{1}$ 不為零，那麼：$\mathbf{x}=-\frac{c_{2}}{c_{1}}\mathbf{y}$。說明 $\mathbf{x,y}$ 在三維空間中共線。
相反如果二者線性獨立，那麼 $\mathbf{x},\mathbf{y}$ 可以在三維空間中張出一個平面。
此時($\mathbf{x},\mathbf{y}$ 線性獨立)，如果 $\mathbf{z}$ 與二者線性相依，那麼 $\mathbf{z}$ 會落在該平面上。若線性獨立，則不會落在該平面上。

## Theorems and Examples

誒，我好厲害，他剛要講的 Theorem 我在之前就補充到上上小節了耶～

$$令 \ \mathbf{x_{1}},\dots,\mathbf{x_{n}} \ 為 \ \mathbb{R}^{n} \ 中的 \ n \ 個向量，且 \ X=(\mathbf{x_{1}},\dots,\mathbf{x_{n}})。則 \ \mathbf{x_{1}},\dots,\mathbf{x_{n}} \ 線性相依 \ \Leftrightarrow X \ 奇異。$$

proof:
等式：$c_{1}\mathbf{x_{1}}+\dots+c_{n}\mathbf{x_{n}}$ 可以被寫成以下矩陣方程：$X\mathbf{c}=\mathbf{0}$ 。
此方程有 nontrivial solution $\Leftrightarrow X$ 奇異。

需要注意的是，**待檢測的 $k$ 個 $\mathbb{R}^{n}$ 中的向量如果 $k\neq n$，則不能使用行列式檢測。我們必須將矩陣化成 REF，然後觀察 free variables 是否出現(必有某 row 全零才可使得 free variables 出現)**。(因為 $\det(A)=\det(A^{t})$，所以可以把 column vectors 轉置成 row vectors 思考)如果有，則必定線性相依。相反，則線性獨立。

$$
\text{令 }\mathbf{v_{1}},\dots,\mathbf{v_{n}}\text{ 為向量空間 }V\text{ 中的向量}。\text{對於 } \mathbf{v} \in \text{Span}(\mathbf{v_{1}},\dots,\mathbf{v_{n}})\text{：}
$$
$$
\mathbf{v}\text{ 可以被寫成} \ \mathbf{v_{1}},\dots,\mathbf{v_{n}}\ \text{唯一的線性組合方式} \Leftrightarrow\text{ } \mathbf{v_{1}},\dots,\mathbf{v_{n}}\ \text{ 線性獨立}
$$

proof:
我們有 $\mathbf{v}=\alpha_{1}\mathbf{v_{1}}+\dots+\alpha_{n}\mathbf{v_{n}}$。
假設還有 $\mathbf{v}=\beta_{1}\mathbf{v_{1}}+\dots+\beta_{n}\mathbf{v_{n}}$。
如果 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 線性獨立，那麼我們要證明 $\alpha_{i}=\beta_{i}$。
我們將兩式相減，得到 $(\alpha_{1}-\beta_{1})\mathbf{v_{1}}+\dots+(\alpha_{n}-\beta_{n})\mathbf{v_{n}}=\mathbf{0}$ 。
又因為 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 線性獨立，所以所有係數都應該等於零 $\alpha_{i}-\beta_{i}=0\implies\alpha_{i}=\beta_{i}$。
若 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 線性相依，我們要證明最少有一個 $\beta_{i}$ 不等於 $\alpha_{i}$。
因為 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 線性相依，所以我們可以假設 $c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}=\mathbf{0}$，其中 $c_{1},\dots,c_{n}$ 不全為零。
令 $\beta_{i}=\alpha_{i}+c_{i}$，那麼：
$\beta_{1}\mathbf{v_{1}}+\dots+\beta_{n}\mathbf{v_{n}}=(\alpha_{1}+c_{1})\mathbf{v_{1}}+\dots+(\alpha_{n}+c_{n})\mathbf{v_{n}}=\mathbf{v}+\mathbf{0}=\mathbf{v}$ 
說明一定可以找的 $\beta_{i}=\alpha_{i}+c_{i}$ 使得最少有一個 $\beta_{i}$ 不等於 $\alpha_{i}$ 使得 $\mathbf{v}=\beta_{1}\mathbf{v_{1}}+\dots+\beta_{n}\mathbf{v_{n}}$。

## Vector Spaces of Functions

### The Vector Space $P_{n}$ 

想測試多項式 $p_{1},\dots,p_{n}$ 是否線性獨立在 $P_{n}$ 向量空間中，我們令：$c_{1}p_{1}+c_{2}p_{2}+\dots+c_{n}p_{n}=z$ 。

其中，$z$ 為零多項式。即，$z(x)=0x^{n-1}+0x^{n-2}+\dots+0x+0$。

我們可以將 $c_{1}p_{1}+c_{2}p_{2}+\dots+c_{n}p_{n}$ 寫成 $a_{1}x^{n-1}+\dots+a_{n}$。

那麼，想要 $p_{1},\dots,p_{n}$ 線性獨立，則 $a_{1},\dots,a_{n}$ 必須全部等於零。由於 $a_{i}$ 由 $c_{i}$ 與 $p_{i}$ 構成，也就**說明 $c_{1},\dots,c_{n}$ 必須全部為零**。

### The Vector Space $C^{(n-1)}[a,b]$ 

我們同樣可以利用行列式判斷 $C^{(n-1)}[a,b]$ 中的向量是否線性獨立。

假設對於標量 $c_{1},\dots,c_{n}$ 我們有：$c_{1}f_{1}(x)+\dots+c_{n}f_{n}(x)=0$。

對等式左右一直隱微分，可以得到：

$c_{1}f_{1}(x)+\dots+c_{n}f_{n}(x)=0$ 
$c_{1}f_{1}'(x)+\dots+c_{n}f_{n}'(x)=0$
$\vdots$
$c_{1}f_{1}^{(n-1)}(x)+\dots+c_{n}f_{n}^{(n-1)}(x)=0$ 

所以，可以寫成以下矩陣方程：

$\begin{bmatrix}f_{1}(x) & \dots & f_{n}(x) \\ \vdots \\ f_{1}^{(n-1)}(x) & \dots & f_{n}^{(n-1)}(x)\end{bmatrix}\begin{bmatrix}c_{1} \\ \vdots \\ c_{n}\end{bmatrix}=\begin{bmatrix}0 \\ \vdots \\ 0\end{bmatrix}$ 

同理，如果 $c_{1},\dots,c_{n}$ 不全為零，那麼這些函數線性相依。否則，他們線性獨立。

我們令 $W[f_{1},\dots,f_{n}](x)= \begin{vmatrix}f_{1}(x) & \dots & f_{n}(x) \\\vdots \\f_{1}^{(n-1)}(x) & \dots & f_{n}^{(n-1)}(x)\end{vmatrix}$ ，且這種函數稱作 $\mathbf{Wronskian} \ \text{of} f_{1},\dots,f_{n}$。

$$
令 \ f_{1},\dots,f_{n} \ 為 \ C^{(n-1)}[a,b] \ 中的函數。
$$
$$
如果存在一個點 \ x_{0} \ 在區間 \ [a,b] \ 中使得 \ W[f_{1},\dots,f_{n}](x)\neq 0，那麼 \ f_{1},\dots,f_{n} \ 線性獨立。
$$

proof:
如果 $f_{1},\dots,f_{n}$ 線性相依，則之前說明的矩陣不論 $x$ 為多少必定奇異，也就是
$W[f_{1},\dots,f_{n}](x)=0 \ \forall x \in [a,b]$ 。
所以，只要可以找到任意 $x\in[a,b]$ 使得 $W=[f_{1},\dots,f_{n}](x)\neq 0$ 則 $f_{1},\dots,f_{n}$ 線性獨立。

需要注意，**反向結論是不成立的**。也就是說就算對於所有 $x$ 都有 $W[f_{1},\dots,f_{n}](x)=0$ 並仍**不可保證** $f_{1},\dots,f_{n}$ 線性相依。因為，想要保證線性相依， $c_{i}$ 必須為一個固定常數。但是對於所有 $x$ 都有 $W[f_{1},\dots,f_{n}](x)=0$ 只能保證對於某特定 $x$ 可以找到相對應的 $c_{i}$ 使得等式成立。而這個 $c_{i}$ 有可能是常數也有可能隨著 $x$ 不同而改變。所以無法保證線性相依，但是可以說明有一定可能性這些函數線性相依。

# Basis and Dimension

首先，我們給出 basis 的定義：

$$
\text{向量 }\mathbf{v_{1}},\dots,\mathbf{v_{n}} \text{ 組成向量空間 } V\text{ 的基底(basis) 若且唯若}
$$
$$
\begin{align}
 & 1. \ \mathbf{v_{1}},\dots,\mathbf{v_{n}}\text{ 線性獨立} \\
 & 2. \ \mathbf{v_{1}},\dots,\mathbf{v_{n}} \text{ 生成 }V
\end{align}
$$

$$
\text{若 }\mathbf{v_{1}},\dots,\mathbf{v_{n}} \text{ 是向量空間 }V\text{ 的生成集，且 }m>n \text{，則任意 }m \text{ 個從 } V\text{ 中取得的向量線性相依}
$$

proof:
令 $\mathbf{u_{1}},\dots,\mathbf{u_{m}}$ 為 $m$ 個從 $V$ 中選取的向量。
我們可以將 $\mathbf{u_{i}}$ 表示為：
$\mathbf{u_{i}}=a_{i 1}\mathbf{v_{1}}+\dots+a_{i n}\mathbf{v_{n}}$ ，其中 $i=1,\dots,m$。
那麼，線性組合 $c_{1}\mathbf{u_{1}}+\dots+c_{m}\mathbf{u_{m}}$ 可以表達為：
$c_{1}\mathbf{u_{1}}+\dots+c_{m}\mathbf{u_{m}}=\sum_{i=1}^{m}\left( c_{i}\sum_{j=1}^{n}a_{ij}\mathbf{v_{j}} \right)=\sum_{j=1}^{n}\left( \sum_{i=1}^{m}a_{ij}c_{i} \right)\mathbf{v_{j}}$ 
那麼，考慮系統：
$\sum_{i=1}^{m}a_{ij}c_{i}=0$，其中 $j=1,\dots,n$。
是一個未知數 > 等式 的齊次系統，所以必有 nontrivial solution $(\hat{c_{1}},\dots,\hat{c_{m}})^{T}$。
帶回原式：$\hat{c_{1}}\mathbf{u_{1}}+\dots+\hat{c_{n}}\mathbf{u_{m}}=\sum_{j=1}^{n}0\mathbf{v_{j}}=0$ 。
所以，$\mathbf{u_{1}},\dots,\mathbf{u_{m}}$ 線性相依。

$$
\text{若 }\{\mathbf{v_{1}},\dots,\mathbf{v_{n}}\}\text{ 與 }\{\mathbf{u_{1}},\dots,\mathbf{u_{m}}\} \text{ 都是向量空間 }V\text{ 的基底，則 }n=m。
$$

proof:
令 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 與 $\mathbf{u_{1}},\dots,\mathbf{u_{n}}$ 為 $V$ 的基底。
因為他們都是 $V$ 的基底，所以二者都線性獨立。
為了滿足線性獨立的條件，根據上一個我們證明的性質：
因為 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 是 $V$ 的生成集，所以 $m\leq n$ 可以滿足線性獨立的條件。
又因為 $\mathbf{u_{1}},\dots, \mathbf{u_{m}}$ 是 $V$ 的生成集，所以必須 $n\leq m$。
綜合以上，$n=m$。

以下給出向量空間**維度(dimension)** 的定義：

$$
\text{當向量空間 } V \text{ 由 } n \text{ 個基底張成，則稱 }V\text{ 的維度為 } n \text{。}V\text{ 的子空間 }\{0\}\text{ 擁有維度 }0。
$$
$$
\text{若 }V\text{ 的基底向量有限，}\text{則稱 } V\text{ 有限維度(finite dimension)，否則為無限維度(infinite dimension)。}
$$

有了以上定義，我們來延伸一個引理：

$$
\text{若 }V\text{ 是一個維度 }n>0\text{ 的向量空間，則：} 
$$
$$
\begin{align}
 (I)  & \text{ 任意 }V\text{ 中的 } n\text{ 個線性獨立的向量可以張出 } V。\\
 (II) & \text{ 任意可以張出 }V\text{ 的 }n\text{ 個向量線性獨立。}
\end{align}
$$

proof:
(I)
我們取 $V$ 中 $n$ 個線性獨立的向量 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$，以及一個向量 $\mathbf{v}$。
因為 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 線性獨立，所以：$c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}=\mathbf{0}$ 
那麼，$c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}+c_{n+1}\mathbf{v}=\mathbf{0}$ 中的 $c_{n+1}$ 必不為零，否則 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 不是線性獨立。
$\implies \mathbf{v}=\alpha \mathbf{v_{1}}+\dots+\alpha \mathbf{v_{n}}$ 且 $\alpha_{i}=-\frac{c_{i}}{c_{n+1}}$，其中 $i=1,\dots,n$。
因為 $\mathbf{v}$ 為 $V$ 中的任意向量，所以 $c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}$ 張出 $V$。
(II)
利用反證法：假設 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 張出 $V$ 且線性線性相依。
那麼一定可以在這些向量中找到某個 $\mathbf{v_{i}}$ 可以被其他向量表達，我們可以一直挑出這樣的向量，直到最終 $\mathbf{v_{1}},\dots,\mathbf{v_{k}}$ 線性獨立且張出 $V$，其中 $k<n$。
但是，這與前提 $\text{dim }V=n$ 矛盾，所以 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 必定線性獨立。

讓我們介紹本節最後一個引理：

$$
\text{若 }V\text{ 是一個維度 }n>0\text{ 的向量空間，則：} 
$$
$$
\begin{align}
(i)  & \text{ 任何少於 }n\text{ 個向量的生成集都無法生成 }V。\\
(ii)  & \text{ 任何由少於 }n\text{ 個線性獨立的向量構成的子集都可被擴充成 }V\text{ 的一組基底。}\\
(iii) & \text{ 任何由大於 }n\text{ 個向量構成的集合都可以由刪去某些向量成為 }V\text{ 的一組基底。}
\end{align}
$$

proof:
(i)
利用反證法：假設 $\mathbf{v_{1},\dots,\mathbf{v_{m}}}$ 張出 $V$，其中 $m<n$。
那麼根據 (iii)，可以刪去某些向量使得 $\mathbf{v_{1}},\dots,\mathbf{v_{k}}$ 張出 $V$，其中 $k\leq m$。
這與前提 $\text{dim }V=n$ 矛盾，所以 $\mathbf{v_{1},\dots,\mathbf{v_{m}}}$ 無法張出 $V$。
(ii)
假設 $\mathbf{v_{1},\dots,\mathbf{v_{k}}}$ 線性獨立且 $k<n$。
我們一定可以找到一個向量 $\mathbf{v_{k+1}}$ 在 $V$ 中但不在 $\text{Span}(\mathbf{v_{1}},\dots,\mathbf{v_{k}})$ 中，我們把它加入前面。
會變為：$\mathbf{v_{1},\dots,\mathbf{v_{k}}},\mathbf{v_{k+1}}$ ，並且 $\mathbf{v_{1},\dots,\mathbf{v_{k+1}}}$ 仍線性獨立。
如果 $\mathbf{v_{1},\dots,\mathbf{v_{k+1}}}$ 仍無法張出 $V$，我們可以繼續找到 $\mathbf{v_{k+2}}$，加入到集合中。
週而復始，最終我們一定可以將原集合拓展成 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 並張出 $V$。
(iii)
假設 $\mathbf{v_{1}},\dots,\mathbf{v_{m}}$ 且 $m>n$。由上條引理，我們知道這個集合一定線性相依。
所以我們通過不斷將向量剔出，最終剔除到 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 且線性獨立，那麼該集合張出 $V$。

## Standard Bases

我們稱 $\mathbb{R}^{n}$ 的**標準基底(standard bases)** 為：$\{\mathbf{e_{1}},\dots,\mathbf{e_{n}}\}$。

又稱 $\mathbb{R}^{n\times n}$ 的標準基底為：$\{E_{11},E_{12},E_{21},E_{22}\}$。

又稱 $P_{n}$ 的標準基底為：$\{1,x,x^{2},\dots,x^{n-1}\}$。

# Tips

- 零多項式的 degree 通常沒有定義或者定義為 $\text{deg(0)}=-\infty$。
- $A$ matrix commute with $B$ $\Leftrightarrow$ $AB=BA$。
- $N(A)=\{\mathbf{0}\}\implies$ $A$ 化成 RREF 後沒有自由變數，也就是 $I$。
- 對於 Wronskian，只要能找到一個數 $x$ 使得 $W[f_{1},\dots,f_{n}](x) \neq 0$，則 $f_{1},\dots,f_{n}$ 線性獨立。但是，**反向結論不成立**。

# 重要例題

1. Let $C$ be the set of complex numbers. Define addition on $C$ by $(a+bi)+(c+di)=(a+c)+(b+d)i$ and define scalar multiplication by $\alpha(a+bi)=\alpha a+\alpha bi$ for all real numbers $\alpha$. Show that $C$ is a vector space with these operations.

Sol:
這題很無聊，寫過來只是讓你知道怎麼證。但是如果考試真的讓你證十條正不正確，這邊推薦直接送他分。
![[Pasted image 20251021232959.png]]


2. Show that $\mathbb{R}^{m\times n}$ is also a vector space.

Sol:
這裡只給出思路：假設兩個矩陣 $A$ 與 $B$。對兩個矩陣，我們使用**每個元素的視角**進行驗證與運算，就可以得出結論。

3. Show that the element $\mathbf{0}$ in a vector space is unique.

Sol:
(I) 我的寫法
令 $\mathbf{z_{1}}, \mathbf{z_{2}}$ 皆為零向量。那麼，$\forall \mathbf{x} \in V$ 有 $\mathbf{x+z_{1}}=\mathbf{x}$ 與 $\mathbf{x+z_{2}=x}$ 。
則 $\mathbf{x+z_{1}=x+z_{2}}$。
左右同時加上 $\mathbf{-x}$，得到 $\mathbf{z_{1}=z_{2}}$。
所以，零向量唯一。

(II) AI 漂亮版，考試寫這個吧。前一個會用到下一題才證明的性質。
令 $\mathbf{z_{1}}, \mathbf{z_{2}}$ 皆為零向量。那麼，$\forall \mathbf{x} \in V$ 有 $\mathbf{x+z_{1}}=\mathbf{x}$ 與 $\mathbf{x+z_{2}=x}$ 。
取 $\mathbf{x}=\mathbf{z_{2}}$，得 $\mathbf{z_{2}+z_{1}}=\mathbf{z_{2}}=\mathbf{z_{1}+z_{2}}$。(加法交換律)
取 $\mathbf{x}=\mathbf{z_{1}}$，得 $\mathbf{z_{1}}+\mathbf{z_{2}}=\mathbf{z_{1}}$。
得到，$\mathbf{z_{1}}=\mathbf{z_{2}}$。
所以，零向量唯一。

4. Let $\mathbf{x,y}$ and $\mathbf{z}$ be vectors in a vector space $V$. Prove that if $\mathbf{x+y=x+z}$ then $\mathbf{y=z}$. 

Sol:
左右同時**加上** $\mathbf{-x}$：$(\mathbf{-x+x})+\mathbf{y}=(\mathbf{-x+x})+\mathbf{z}\implies \mathbf{0+y}=\mathbf{0+z}$  
$\implies \mathbf{y=z}$ 

5. Let $V$ be a vector space and let $\mathbf{x} \in V$. Show that (a) $\beta \mathbf{0}=\mathbf{0}$ for each scalar $\beta$. (b) if $\alpha \mathbf{x}=\mathbf{0}$, then either $\alpha=0$ or $\mathbf{x}=\mathbf{0}$. 

(a)
因為 $\beta \mathbf{x}\in V$，可以構造出方程：$\beta \mathbf{x}+\beta \mathbf{0}=\beta(\mathbf{x+0})=\beta \mathbf{x}$。
因為 $\beta \mathbf{x}+\beta \mathbf{0}=\beta \mathbf{x}$，左右同加 $-\beta \mathbf{x}$ 得到 $\beta \mathbf{0}=\mathbf{0}$。

(b)
對於 $\alpha=0$，驗證 $\alpha \mathbf{x}=0\mathbf{x}=\mathbf{0}$。
$0\mathbf{x}=(0+0)\mathbf{x}=0\mathbf{x}+0\mathbf{x}$。
左右同加 $-0\mathbf{x}$，得到 $\mathbf{0}=0\mathbf{x}$。命題成立。
對於 $\alpha\neq 0$，原式左右同乘 $\alpha^{-1}$：$\alpha^{-1}\alpha \mathbf{x}=\alpha^{-1}\mathbf{0}$。
$1\mathbf{x}=\alpha^{-1}\mathbf{0}\implies\mathbf{x}=\alpha^{-1}\mathbf{0}=\mathbf{0}$。(利用 (a) 小題結論)
所以，若 $\alpha \mathbf{x}=0$，則 $\alpha=0$ 或 $\mathbf{x}=\mathbf{0}$。

6. Let $S$ be the set of all ordered pairs of real numbers. Define scalar multiplication and addition on $S$ by $\alpha(x_{1},x_{2})=(\alpha x_{1},\alpha x_{2})$ and $(x_{1},x_{2})\oplus (y_{1},y_{2})=(x_{1}+y_{1},0)$. Show that $s$ is not a vector space. Which of the eight axioms fail to hold? 

Sol:
(僅列出不符合項)
首先，令 $\mathbf{0}=(\alpha,\beta)$ 則 $(x_{1},x_{2})+\mathbf{0}=(x_{1}+\alpha,0)\neq (x_{1},x_{2})$ ，所以 $\mathbf{x}+\mathbf{0}=\mathbf{x}$ 不成立，$s$ 不是一個向量空間。
由上，因為 $\mathbf{x+0=x}$ 不成立，那麼左右同加 $-\mathbf{x}$ 的 $\mathbf{x}+(-\mathbf{x})=\mathbf{0}$ 也不成立。
最後，$(\alpha+\beta)(x_{1},x_{2})=((\alpha+\beta)x_{1},(\alpha+\beta)x_{2}) \neq\alpha(x_{1},x_{2})+\beta(x_{1},x_{2})=((\alpha+\beta)x_{1},0)$ 。

4. Determine the null space of $\begin{bmatrix}2 & 1 & 3 & -3 \\ 1 & 2 & -6 & 6\end{bmatrix}$. 

Sol:
利用增廣矩陣解 $\begin{bmatrix}2 & 1 & 3 & -3 \\ 1 & 2 & -6 & 6\end{bmatrix}$。
$\begin{bmatrix}2 & 1 & 3 & -3 & | & 0 \\ 1 & 2 & -6 & 6 & | & 0\end{bmatrix}\implies \begin{bmatrix}1 & 0 & 4 & -4 & | & 0 \\ 0 & 1 & -5 & 5 & | & 0\end{bmatrix}$ 
所以，$N(A)=\text{Span}((-4,5,1,0)^{T},(4,-5,0,1))$。
**注意 $N(A)$ 的表達方式。** 

5. Determine whether the following are subspaces of $P_{4}$: (a) The set of polynomials in $P_{4}$ of even degree. (b) The set of all polynomials of degree 3. (c) The set of all polynomials $p(x)$ in $P_{4}$ such that $p(0)= 0$. (d) The set of all polynomials in $P_{4}$ having at least one real root. 

Sol:
令每題的集合為 $S$，取集合中任意二相異向量 $p,q$。
(a)
取最高次項為偶數，而不是只能有偶次項。
$\mathbf{0}\not\in S$ (零多項式的最高次項未定義或定義為 $-\infty$)
$\alpha p\in S$ 
但 $p+q$ 不一定 $\in S$。
反例：$p(x)=x^{2},q(x)=-x^{2}$，則 $(p+q)(x)=\mathbf{0}\not\in S$ 

(b)
同 (a)

(c)
所有 $p(0)=0$ 的多項式都滿足 $p(x)=ax^{3}+bx^{2}+cx$，其中 $a,b,c,d \in \mathbb{R}$。
$\because p(x)=0$ 滿足 $p(0)=0$ $\therefore \mathbf{0}\in S$ 
$\alpha p=(\alpha a)x^{3}+(\alpha b)x^{2}+(\alpha c)x \in S$。
$p+q=(a_{1}+a_{2})x^{3}+(b_{1}+b_{2})x^{2}+(c_{1}+c_{2})x\in S$。

(d)
$\because p(x)=0$ 有所有實數作為根 $\therefore\mathbf{0}\in S$。
標量積不引響解的個數，所以 $\alpha p\in S$。
但是，若 $p(x)=1,q(x)=0$，則 $(p+q)(x)=1$ 無解，所以 $p+q$ 不一定 $\in S$。

6. Determine whether the set of functions $f$ in $C[-1,1]$ such that $f(-1)=f(1)$ is subspace of $C[-1,1]$. 

Sol:
此題用來學習如何說明一個子空間成立。
令符合 $f(-1)=f(1)$ 的多項式組成一個集合 $V$，$f,g\in V$，$\alpha\in \mathbb{R}$。
零多項式符合條件，$\mathbf{0}\in V$。
$(\alpha f)(-1)=\alpha f(-1)=\alpha f(1)$，$\alpha f\in V$。
$(f+g)(-1)=f(-1)+g(-1)=f(1)+g(1)=(f+g)(1)$，$f+g\in V$。
所以，$V$ 是 $C[-1,1]$ 的一個子空間。

7. Show that $C^{n}[a,b]$ is a subspace of $C[a,b]$. 

Sol:
注意表達形式。
令 $f,g\in C^{n}[a,b]$，$\alpha\in \mathbb{R}$。
則滿足 $f^{(k)}$ 與 $g^{(k)}$ 對所有  $k\leq n$ 皆連續。
$0$ 函數的所有導數都為 $0$ 且連續，$0\in C^{n}[a,b]$。
$(\alpha f)^{(k)}(x)=\alpha f^{(k)}(x)$ 且連續函數乘以某實數仍為連續函數，所以 $\alpha f\in C^{n}[a,b]$。
$(f+g)^{(k)}(x)=f^{(k)}(x)+g^{(k)}(x)$ 仍連續，所以 $f+g\in C^{n}[a,b]$。

8. Let $A$ be a $4\times3$ matrix and let $\mathbf{b}\in \mathbb{R}^{4}$. How many possible solutions could the system $A\mathbf{x}=\mathbf{b}$ have if $N(A)=\{0\}$? Answer the same question in the case $N(A)\neq \{0\}$. Explain your answers.

Sol:
(a)
假設 $\mathbf{x_{1},x_{2}}$ 為 $A\mathbf{x}=\mathbf{b}$ 的兩個解，則：
$A(\mathbf{x_{1}}-\mathbf{x_{2}})=A\mathbf{x_{1}}-A\mathbf{x_{2}}=\mathbf{b}-\mathbf{b}=\mathbf{0}\implies \mathbf{x_{1}}-\mathbf{x_{2}}=\mathbf{0}\implies \mathbf{x_{1}}=\mathbf{x_{2}}$ 
所以，$A\mathbf{x}=\mathbf{b}$ 有唯一解，或者無解。

(b)
設 $\mathbf{x_{1}}$ 為 $A\mathbf{x}=\mathbf{b}$ 的一個解。
令 $\mathbf{x_{2}}=\mathbf{x_{1}}+t\mathbf{z}$，$t\in \mathbb{R}$，$\mathbf{z}\in N(A)$。
則 $A\mathbf{x_{2}}=A(\mathbf{x_{1}}+t\mathbf{z})=A\mathbf{x_{1}}+tA\mathbf{z}=\mathbf{b}+\mathbf{0}=\mathbf{b}$，$\mathbf{x_{2}}$ 也是 $A\mathbf{x}=\mathbf{b}$ 的一組解。
因為 $t\in \mathbb{R}$，所以 $\mathbf{x_{2}}$ 的個數有無限多個。
所以 $A\mathbf{x}=\mathbf{b}$ 有無限多組解，或者無解。

9. Prove that if $S$ is a subspace of $\mathbb{R}^{1}$, then either $S=\{\mathbf{0}\}$ or $S=\mathbb{R}^{1}$. 

Sol:
當 $S=\{\mathbf{0}\}$ 時，顯然滿足構成子空間的三個條件，所以 $S=\{\mathbf{0}\}$ 是一個子空間。
假設 $S$ 含有非零元素 $\mathbf{x_{0}}\in S$，且 $\alpha\in \mathbb{R}$。
因為 $S$ 是一個子空間，所以必須滿足 $\alpha \mathbf{x_{0}}\in S$。
又因為 $S$ 是 $\mathbb{R}^{1}$ 的子空間，所以 $\mathbf{x_{0}}\in \mathbb{R}$。
取任意 $y\in \mathbb{R}$，令 $\alpha=\frac{y}{\mathbf{x_{0}}}$，則 $\alpha \mathbf{x_{0}}=y\in S$ 。
因為 $y$ 可以是任意實數，所以此情況下 $S=\mathbb{R}^{1}$。
所以，$S=\{\mathbf{0}\}$ 或 $S=\mathbb{R}^{1}$。
(GPT 說這題是很經典的線性代數入門題，但是我覺得一點都不入門...)

10. Let $A$ be an $n\times n$ matrix. Prove that the following statements are equivalent: (a) $N(A)=\{\mathbf{0}\}$ (b) $A$ is nonsingular. (c) For each $\mathbf{b}\in \mathbb{R}^{n}$, the system $A\mathbf{x}=\mathbf{b}$ has a unique solution.

Sol:
注意，這題不要用 $(a)\implies(b)$，不好證明。
$(b)\implies(a)$ 
因為 $A$ 非奇異，所以 $A^{-1}$ 存在。
$A\mathbf{x}=\mathbf{0}$ 左右同乘 $A^{-1}$：$A^{-1}A\mathbf{x}=\mathbf{0}\implies \mathbf{x}=\mathbf{0}$ 
$\implies N(A)=\{\mathbf{0}\}$ 
$(a)\implies(c)$ 
因為 $N(A)=\{\mathbf{0}\}$，所以 $A$ 化成 RREF 後必等於 $I$，所以 $A\mathbf{x}=\mathbf{b}$ 必有解。
令 $\mathbf{x_{1}},\mathbf{x_{2}}$ 為 $A\mathbf{x}=\mathbf{b}$ 的兩個解，則：
$A(\mathbf{x_{1}}-\mathbf{x_{2}})=A\mathbf{x_{1}}-A\mathbf{x_{2}}=\mathbf{b}-\mathbf{b}=\mathbf{0}$ 
所以 $\mathbf{x_{1}}-\mathbf{x_{2}}\in N(A)\implies \mathbf{x_{1}}-\mathbf{x_{2}}=\mathbf{0}\implies \mathbf{x_{1}}=\mathbf{x_{2}}$ 
所以，$A\mathbf{x}=\mathbf{b}$ 有唯一解。
$(c)\implies(b)$ 
因為 $A\mathbf{x}=\mathbf{b}$ 有唯一解，所以 $A$ 可以被化成 RREF，且 $A$ 的 RREF 為 $I$。
令將 $A$ 化成 RREF 的初等矩陣為 $E_{1},\dots,E_{k}$。
則 $A^{-1}$ 存在且 $A^{-1}=E_{k}^{-1},\dots,E_{1}^{-1}$。
所以，$A$ 非奇異。

11. Let $U$ and $V$ be subspaces of a vector space $W$. Prove that their intersection $U\cap V$ is also a subspace of $W$. 

Sol:
因為 $\mathbf{0}\in U$ 且 $\mathbf{0}\in V$，所以 $\mathbf{0}\in U\cap V$。
取 $\mathbf{a},\mathbf{b}\in U\cap V$。
則 $\alpha \mathbf{a}\in U$ 且 $\alpha \mathbf{a}\in V$，所以 $\alpha \mathbf{a}\in U\cap V$。
又 $\mathbf{a}+\mathbf{b}\in U$ 且 $\mathbf{a}+\mathbf{b}\in V$，所以 $\mathbf{a}+\mathbf{b}\in U\cap V$。
所以，$U\cap V$ 也是 $W$ 的子空間。

12. Let $S$ be the subspace of $\mathbb{R}^{2}$ spanned by $\mathbf{e_{1}}$ and let $T$ be the subspace of $\mathbb{R}^{2}$ spanned by $\mathbf{e_{2}}$. Is $S\cup T$ a subspace of $\mathbb{R}^{2}$ ? Explain. 

Sol:
$S=\text{Span}(\mathbf{e_{1}})=\{(x,0)|x\in \mathbb{R}\}$ 
$T=\text{Span}(\mathbf{e_{2}})=\{(0,y)|y\in \mathbb{R}\}$ 
因為 $\mathbf{0}\in S$ 且 $\mathbf{0}\in T$ 所以 $\mathbf{0}\in S\cup T$。
令 $\mathbf{a}\in S, \mathbf{b}\in T$。
因為 $\alpha \mathbf{a}\in S$ 所以 $\alpha \mathbf{a}\in S\cup T$。
又 $\alpha \mathbf{b}\in T$ 所以 $\alpha \mathbf{b}\in S\cup T$。
但是 $\mathbf{a}+\mathbf{b}=(x,y)\quad x,y\in \mathbb{R} \implies \mathbf{a}+\mathbf{b}\not\in S$ 且 $\mathbf{a}+\mathbf{b}\not\in T$，所以 $\mathbf{a}+\mathbf{b}\not\in S\cup T$。
所以，$S\cup T$ 不是 $\mathbb{R}^{2}$ 的子空間。

ASK linear algebra 3.2 exercise 27. 