
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

定義 $P_{n}$ 代表所以最高次係數小於 $n$ 的多項式形成的集合 (老師的定義與課本不一樣，他是最高次係數小於或等於 $n$)。定義 $p+q$ 與 $\alpha p$ 如下：$(p+q)(x)=(q+p)(x)$ 與 $(\alpha p)(x)=\alpha p(x)$ 對於所有 $x \in  \mathbb{R}$ 成立。在這種情況下，零向量等於零多項式。

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
( $\impliedby$ )
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
所以，**只要可以找到任意 $x\in[a,b]$ 使得 $W=[f_{1},\dots,f_{n}](x)\neq 0$ 則 $f_{1},\dots,f_{n}$ 線性獨立**。

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

我們有引理：

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
是一個未知數 > 等式數 的齊次系統，所以必有 nontrivial solution $(\hat{c_{1}},\dots,\hat{c_{m}})^{T}$。
帶回原式：$\hat{c_{1}}\mathbf{u_{1}}+\dots+\hat{c_{n}}\mathbf{u_{m}}=\sum_{j=1}^{n}0\mathbf{v_{j}}=0$ 。
所以，$\mathbf{u_{1}},\dots,\mathbf{u_{m}}$ 線性相依。

$$
\text{若 }\{\mathbf{v_{1}},\dots,\mathbf{v_{n}}\}\text{ 與 }\{\mathbf{u_{1}},\dots,\mathbf{u_{m}}\} \text{ 都是向量空間 }V\text{ 的基底，則 }n=m。
$$

proof:
令 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 與 $\mathbf{u_{1}},\dots,\mathbf{u_{n}}$ 為 $V$ 的基底。
因為他們都是 $V$ 的基底，所以二者都線性獨立。
為了滿足線性獨立的條件，**根據上一個我們證明的性質**：
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
那麼，$c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}+c_{n+1}\mathbf{v}=\mathbf{0}$ 中的 **$c_{n+1}$ 必不為零**，否則 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 不是線性獨立。
(若 $c_{n+1}$ 為零，那麼 $c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}+c_{n+1}\mathbf{v}=\mathbf{0}$ 會等於 $c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}=\mathbf{0}$，這隱含了 $\mathbf{v_{1}},\dots \mathbf{v_{n}}$ 線性相關，與前提矛盾)
$\implies \mathbf{v}=\alpha \mathbf{v_{1}}+\dots+\alpha \mathbf{v_{n}}$ 且 $\alpha_{i}=-\frac{c_{i}}{c_{n+1}}$，其中 $i=1,\dots,n$。
因為 $\mathbf{v}$ 為 $V$ 中的任意向量，所以 $c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}$ 張出 $V$。
(II)
利用**反證法**：假設 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 張出 $V$ 且線性相依。
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

# Change of Basis

## Changing Coordinates in $\mathbb{R}^{2}$ 

$\mathbb{R}^{2}$ 的標準基底為 $\{\mathbf{e_{1}},\mathbf{e_{2}}\}$。任何 $\mathbb{R}^{2}$ 中的向量 $\mathbf{x}$ 都可以被表示成：

$$
\mathbf{x}=x_{1}\mathbf{e_{1}}+x_{2}\mathbf{e_{2}}
$$

標量 $x_{1},x_{2}$ 可以被視為 $\mathbf{x}$ 在**標準基底**上的座標。

若我們取 $\mathbb{R}^{2}$ 的任意一組基底 $\{\mathbf{y},\mathbf{z}\}$，則 $\mathbf{x}$ 可以被表達成：

$$
\mathbf{x}=\alpha \mathbf{y}+\beta \mathbf{z}
$$

那麼標量 $\alpha,\beta$ 可以被視為 $\mathbf{x}$ 在 $\{\mathbf{y},\mathbf{z}\}$ 上的座標。

需要注意，我們必須為基底定義順序。因為相同基底，但不同順序的組合會導致 $\mathbf{x}$ 相對於該基底的座標不同。

## Changing Coordinates

考慮 $\mathbb{R}^{2}$ 中的一組基底：

$$
\mathbf{u_{1}}=\begin{bmatrix}
3 \\
2
\end{bmatrix}
\quad 
\mathbf{u_{2}}=\begin{bmatrix}
1 \\
1
\end{bmatrix}
$$

思考以下兩個問題：
1. 給定一向量 $\mathbf{x}=(x_{1},x_{2})^{T}$，找到 $x$ 在 $\mathbf{u_{1}}$ 與 $\mathbf{u_{2}}$ 上的座標。
2. 給定一向量 $c_{1}\mathbf{u_{1}}+c_{2}\mathbf{u_{2}}$ ($(c_{1},c_{2})^{T}$ 是該向量在 $\mathbf{u_{1},u_{2}}$ 上的座標)，找到該向量在 $\mathbf{e_{1}}$ 與 $\mathbf{e_{2}}$ 上的座標。

我們首先考慮問題 $2$，因為較容易解決，只需要將 $\mathbf{u_{1}},\mathbf{u_{2}}$ 用標準基底表達即可：

$$
c_{1}\mathbf{u_{1}}+c_{2}\mathbf{u_{2}}=c_{1}(3\mathbf{e_{1}}+2\mathbf{e_{2}})+c_{2}(\mathbf{e_{1}}+\mathbf{e_{2}})=(3c_{1}+c_{2})\mathbf{e_{1}}+(2c_{1}+c_{2})\mathbf{e_{2}}
$$

於是：

$$
\mathbf{x}=\begin{bmatrix}
3c_{1}+c_{2} \\
2c_{1}+c_{2}
\end{bmatrix}=\begin{bmatrix}
3 & 1 \\
2 & 1
\end{bmatrix}
\begin{bmatrix}
c_{1} \\
c_{2}
\end{bmatrix}
$$

如果我們令 $U=(\mathbf{u_{1}},\mathbf{u_{2}})=\begin{bmatrix}3 & 1 \\ 2 & 1\end{bmatrix}$ ，則：

$$
\mathbf{x}=U\mathbf{c}
$$

我們將這種矩陣 $U$ 稱為**轉移矩陣(transition matrix)**。

讓我們回過頭解決 $1$。

因為 $U$ 矩陣可逆，所以：

$$
\mathbf{c}=U^{-1}\mathbf{x}
$$

考慮另一個新問題：給定 $\{\mathbf{u_{1}},\mathbf{u_{2}}\}$ 與 $\{\mathbf{v_{1}},\mathbf{v_{2}}\}$ 為 $\mathbb{R}^{2}$ 上的兩組不同的基底。假設 $\mathbf{x}$ 是 $\mathbb{R}^{2}$ 上的一個向量，如何將 $\mathbf{x}$ 在 $\mathbf{u}$ 上的座標轉換成 $\mathbf{v}$ 上的左標？

已知 $\mathbf{x}=c_{1}\mathbf{u_{1}}+c_{2}\mathbf{u_{2}}$，想要將其轉換成 $\mathbf{v}$ 上的座標，我們需要找到標量使得：

$$
c_{1}\mathbf{u_{1}}+c_{2}\mathbf{u_{2}}=d_{1}\mathbf{v_{1}}+d_{2}\mathbf{v_{2}}
$$

令 $U=(\mathbf{u_{1}},\mathbf{u_{2}})$ 與 $V=(\mathbf{v_{1}},\mathbf{v_{2}})$，則：

$$
U\mathbf{c}=V\mathbf{d}\implies \mathbf{d}=V^{-1}U\mathbf{c}
$$

我們也可以將其想成：先將 $\mathbf{c}$ 轉為標準基底上的座標 ($U\mathbf{c}$)，然後再轉為 $\mathbf{v}$ 上的座標 ($V^{-1}U\mathbf{c}$)。

## Change of Basis of a General Vector Space

綜上所述，我們給出定義：

令 $V$ 為向量空間並令 $E=\{\mathbf{v_{1}},\dots ,\mathbf{v_{n}}\}$ 為 $V$ 的一組排序過的基底。

取 $V$ 中任意向量 $\mathbf{v}$，則 $\mathbf{v}$ 可被表達為：$\mathbf{v}=c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}$，其中 $c_{1},\dots,c_{n}$ 為標量。

那麼，對於每個 $\mathbf{v}$，我們都可以找到獨有的向量 $c=(c_{1},\dots ,c_{n})^{t}\in \mathbb{R}^{n}$。

我們稱 **$\mathbf{c}$ 是 $\mathbf{v}$ 在有序基底 $E$ 上的座標向量(coordinate vector)，並記作 $[\mathbf{v}]_{E}$**。

$\mathbf{c}$ 的每一項稱為 $\mathbf{v}$ 在 $E$ 上的座標。

注意到：**每個轉移矩陣必定都是可逆的**。

proof:
這個證明有點繞，做好心理準備。
令 $V$ 是一個 $n$ 維的向量空間。令 $E=\{\mathbf{w_{1}},\dots,\mathbf{w_{n}}\}$ 與 $F=\{\mathbf{v_{1}},\dots,\mathbf{v_{n}}\}$。
接下來這步是最重要的一步：將 $\mathbf{w_{j}}$ 用 $\mathbf{v_{i}}$ 表達。
$$
\begin{align}
 & \mathbf{w_{1}}=s_{11}\mathbf{v_{1}}+s_{21}\mathbf{v_{2}}+\dots+s_{n{1}}\mathbf{v_{n}} \\
 & \vdots \\
 & \mathbf{w_{n}}=s_{1n}\mathbf{v_{1}}+s_{2n}\mathbf{v_{2}}+\dots+s_{nn}\mathbf{v_{n}}
\end{align}
$$
在此，$S=([\mathbf{w_{1}}]_{F} \ [\mathbf{w_{2}}]_{F} \ \dots \ [\mathbf{w_{n}}]_{F})$。
也就是說，$S$ 是一個將 $E$ 上座標轉換成 $F$ 座標的 transition matrix。
令 $\mathbf{v}\in V$，且 $\mathbf{x}=[\mathbf{v}]_{E}$，$\mathbf{y}=[\mathbf{v}]_{F}$，則：
$$
\mathbf{y}=S\mathbf{x}
$$
而且 $\mathbf{y}=S\mathbf{x}\Leftrightarrow x_{1}\mathbf{w_{1}}+\dots+x_{n}\mathbf{w_{n}}=y_{1}\mathbf{v_{1}}+\dots+y_{n}\mathbf{v_{n}}$。
令 $\mathbf{y}=\mathbf{0}\implies x_{1}\mathbf{w_{1}}+\dots+x_{n}\mathbf{w_{n}}=\mathbf{0}$。
因為 $\mathbf{w_{1},\dots,w_{n}}$ 線性獨立，所以 $x_{1}=\dots=x_{n}=0$。
那麼：$S\mathbf{x}=\mathbf{0}$ 有唯一零解，所以 $S$ 可逆。

以上，我們證明了所有 transition matrix 都可逆。實際上，我們可以將任何可逆的矩陣都視為 transition matrix。

對於任意給定的可逆矩陣 $A\in \mathbb{R}^{n\times n}$，給定任意一組基底 $V=\{\mathbf{v_{1}},\dots,\mathbf{v_{n}}\}$，定義 $F=\{A\mathbf{v_{1}}, A\mathbf{v_{2}},\dots,A{\mathbf{v_{n}}}\}$，則 $F$ 也會是一組基底(因為 $\{A\mathbf{v_{1}}, A\mathbf{v_{2}},\dots,A{\mathbf{v_{n}}}\}$ 必定線性獨立 ($A$ 非奇異)，下面例題好像有證過)。且 $A$ 為轉換 $V$ 上座標到 $F$ 上座標的 transition matrix。

其實，學完第四章的內容後，我們可以用第四章的內容幫助我們更快速的找到 transition matrix。

假設我們有 $V=\text{span}(\mathbf{v_{1}},\dots,\mathbf{v_{n}})$ 與 $U=\text{span}(\mathbf{u_{1}},\dots,\mathbf{u_{n}})$ 都是某個向量空間的基底，求從 $V\to U$ 的 transition matrix。

令 $A$ 為想求的 transition matrix，則：

$$
\mathbf{a}_{j}=[\mathbf{v}_{j}]_{U}
$$

proof:
對於任意向量，我們有 $A[\mathbf{x}]_{V}=[\mathbf{x}]_{U}$。
帶入 $\mathbf{x}=\mathbf{v}_{j}$，則有 $A\mathbf{e}_{j}=[\mathbf{v}_{j}]_{U}$。

# Row Space and Column Space

首先定義一波：

若 $A$ 是一個 $m\times n$ 的矩陣，則：

**row space**：由 $A$ 的 row vectors 生成的 $\mathbb{R}^{1\times n}$ 子空間。

**column space**：由 $A$ 的 column vectors 生成的 $\mathbb{R}^{m}$ 子空間。

這邊我們有個定理給你介紹一下～

$$
\text{兩個 row equivalent 的矩陣有相同的 row space。}
$$

proof:
因為 $B$ row equivalent $A$，所以 $B$ 的 row vectors 可以由 $A$ 的 row vectors 的線性組合表達。
那麼，$B$ 的 row space 必定為 $A$ 的 row space 的子空間。
同理，$A$ 的 row space 也必為 $B$ 的 row space 的子空間。
所以 $A$ 的 row space 必等於 $B$ 的 row space。

緊接著，我們定義什麼是**秩(rank)**：$A$ 的 row space 的維度。寫成：$\text{rank}(A)$。

想找出 $A$ 的秩，我們可以將 $A$ 化成 REF。

所有非零 row 會構成 $A$ 的 row space 的基底，所以 $\text{rank}(A)=$ nonzero rows 的個數。

## Linear Systems

Consistency Theorem for Linear Systems說：一個線性系統 $A\mathbf{x}=\mathbf{b}$ 有解 $\Leftrightarrow \mathbf{b}$ 在 $A$ 的 column space 中。

這很好理解，因為 $A\mathbf{x}=\mathbf{b}$ 可以寫成：

$$
x_{1}\begin{bmatrix}
a_{11} \\
a_{21} \\
\vdots \\
a_{m1}
\end{bmatrix}
+\dots+
x_{n}\begin{bmatrix}
a_{1n} \\
a_{2n} \\
\vdots \\
a_{mn}
\end{bmatrix}
=\begin{bmatrix}
b_{1} \\
b_{2} \\
\vdots \\
b_{n}
\end{bmatrix}
$$

也就是說，$A\mathbf{x}=\mathbf{b}$ 有解，代表 $\mathbf{b}$ 可以被寫成 $A$ 的 column vectors 的線性組合。

那麼，對於 $A\mathbf{x}=\mathbf{b}$ 有解，解的情況可以如以下討論：
- 無解：$\mathbf{b}\not\in\text{Col}(A)$。
- 唯一解：$\mathbf{b}\in\text{Col}(A)$ 且 $A$ 的 column vectors 線性獨立。
- 無限多組解：$\mathbf{b}\in\text{Col}(A)$ 且 $A$ 的 column vectors 線性相依。

還有一個定理說：若 $A$ 為 $m\times n$ 的矩陣，則 $A\mathbf{x}=\mathbf{b}$ 有解 $\forall \mathbf{b}\in \mathbb{R}^{m}\Leftrightarrow A$ 的 column vectors span $\mathbb{R}^{m}$。若 $\mathbf{b}$ 最多只有一解，則 $A$ 的 column vectors 線性獨立。

proof:
第一點可以簡單的用 Consistency Theorem 證明，所以我們來證第二點。
($\implies$)
$A\mathbf{x}=\mathbf{b}$ 最多只有一解 $\implies A\mathbf{x}=\mathbf{0}$ 只有 trivial solution。
$\implies A$ 的 column vectors 線性獨立。
($\impliedby$)
$A$ 的 column vectors 線性獨立 $\implies A\mathbf{x}=\mathbf{0}$ 只有 trivial solution。
令 $\mathbf{x_{1}},\mathbf{x_{2}}$ 都是 $A\mathbf{x}=\mathbf{b}$ 的解，則 $A(\mathbf{x_{1}}-\mathbf{x_{2}})=\mathbf{0}$。
因為 $A\mathbf{x}=\mathbf{0}$ 只有 trivial solution，所以 $\mathbf{x_{1}}=\mathbf{x_{2}}$，最多只有一解。

我們還有一個引理：$A$ 為一個 $n\times n$ 的可逆矩陣 $\Leftrightarrow$ $A$ 的 column vectors 構成 $\mathbb{R}^{n}$ 的基底。

proof:
假設 $A$ 為 $n\times m$ 的矩陣。
因為 $A$ 的 column vectors 要張出 $\mathbb{R}^{n}$，所以 $m\geq n$。
因為 $A$ 的 column vectors 要線性獨立(基底必線性獨立)，所以 $m\leq n$。
$\begin{cases}m\geq n \\ m\leq n\end{cases}\implies m=n$。

### The Rank-Nullity Theorem

(怕你忘記，nullity 就是 $\text{dim}(N(A))$)

$$
A \text{ 是一個 } m\times n\text{ 矩陣，則 } \text{rank}(A)+\text{null}(A)=n
$$

proof:
令 $U$ 為 RREF 狀態的 $A$。
若 $\text{rank}(A)=r$，則 $U$ 會有 $r$ 行 nonzero rows，以及 $n-r$ 個 free variables。
而 $\text{dim}(N(A))=$ free variables 的個數，所以 $\text{rank}(A)+\text{null}(A)=n$。

## The Column Space

我們需要知道，**兩個 row equivalent 的矩陣的 column vectors 具有相同的 dependency relation。**

那麼，我們可以使用上面通靈得到的定理證明如下定理。

$A$ 為一個 $m\times n$ 矩陣。$A$ 的 row space 的維度 $=$ column space 的維度。

proof:
若 $A$ 為 $m\times n$ 的矩陣且 $\text{rank}(A)=r$。
令 $U$ 為 $A$ 的 REF，令 $U_{L}$ 為刪除了包含 free variables 的 column，$A_{L}$ 也是。
因為 $U$ 有 $n-r$ 個 free variables，所以 $U_{L}$ 與 $A_{L}$ 有 $r$ 個 column
則 $A_{L}$ 與 $U_{L}$ row equivalent，且因為 $U_{L}$ 的 column vectors 線性獨立，所以 $U_{L}\mathbf{x}=\mathbf{0}$ 只有 trivial solution，且 $U_{L}\mathbf{x}=\mathbf{0}$ 的解也是 $A_{L}\mathbf{x}=\mathbf{0}$ 的解。
$\implies$ $A_{L}$ 的 column vectors 線性獨立($A_{L}$ 有 $r$ 個 columns) $\implies$ $A$ 的 column vectors 的維度 $\geq r$。
那麼：
$\text{dim}(\text{row space of }A)\leq\text{dim}(\text{column space of }A)$ 
又
$\text{dim}(\text{row space of }A)=\text{dim}(\text{column space of }A^{T})\geq\text{dim}(\text{row space of }A^{T})=\text{dim}(\text{column space of }A)$ 
所以：$\text{dim}(\text{row space of }A)=\text{dim}(\text{column space of }A)$。

我們可以使用 $U$ 來幫忙尋找 $A$ 的 column space 的 basis。只需要取得 $U_{L}$，則對應的 $A_{L}$ 中的 column vectors 就會是 $A$ 的 column space 的 basis。
(還記得嗎，兩個 row equivalent 的矩陣的 column vectors 具有相同的 dependency relation。所以 $\text{dim}(\text{column space of }U)=\text{dim}(\text{column space of }A)$)

也就是說 $A$ 的 column space 的維度 = $A$ 的 REF 的 leading 1 個數。

# Tips

- 零多項式的 degree 通常沒有定義或者定義為 $\text{deg(0)}=-\infty$。
- $A$ matrix commute with $B$ $\Leftrightarrow$ $AB=BA$。
- $N(A)=\{\mathbf{0}\}\implies$ $A$ 化成 RREF 後沒有自由變數，也就是 $I$。
- 對於 Wronskian，只要能找到一個數 $x$ 使得 $W[f_{1},\dots,f_{n}](x) \neq 0$，則 $f_{1},\dots,f_{n}$ 線性獨立。但是，**反向結論不成立**。
- 取 $\mathbb{R}^{n}$ 中 $U$ 和 $V$ 兩個子向量空間。若 $U\cap V=\{\mathbf{0}\}\implies$ $U$ 和 $V$ 的**基底線性獨立**，若 $U\cap V\neq \{\mathbf{0}\}\implies$ $U$ 和 $V$ 的**基底線性相依**。(例題 21, 22 包含證明)
- 取 $\mathbb{R}^{n}$ 中一向量 $\mathbf{b}$，並給定一個 $n\times k$ 矩陣 $A$。若 $\text{rank}(A)=n$ ($n<k$)，則 $A\mathbf{x}=\mathbf{b}$ 的解永遠有**無限多組解**，不可能無解。
- 判斷 $A\mathbf{x}=\mathbf{b}$ 解的個數，首先判斷 $\mathbf{b}$ 是否 $\in$ $\text{Col}(A)$ ($\text{Col}(A)$ 是否可以完整張出 $\mathbf{b}$ 所在的向量空間？)，然後判斷 $\text{null}(A)$ 是否可能無限多組解。
- 基本矩陣乘以某個矩陣不會改變該矩陣的 rank。
- 想證明 $A$ 的 column vectors 張出 $\mathbb{R}^{m}$，可以取任意 $\mathbf{b}\in\mathbb{R}^{m}$，然後用 $A$ 的 column vectors 線性組合 $\mathbf{b}$ 來證明。

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

13. Show that $1,e^{x}+e^{-x},e^{x}-e^{-x}$ is linear independent on $C[a,b]$. 

Sol:
法一：
首先要證 $1,e^{x},e^{-x}$ 線性獨立。
令 $a,b,c$ 為 scalars，則令 $ae^{x}+be^{-x}+c=0$。
同乘 $e^{x}\implies a(e^{x})^{2}+ce^{x}+b=0$。
令 $t=e^{x}\quad t\in(0,\infty)$，則 $at^{2}+ct+b=0$。
$\implies a=b=c=0\implies1,e^{x},e^{-x}$ 線性獨立。
回到題目：
解 $a(e^{x}+e^{-x})+b(e^{x}-e^{-x})+c=0\implies(a+b)e^{x}+(a-b)e^{-x}+c=0$ 
因為$1,e^{x},e^{-x}$ 線性獨立，所以：
$\begin{cases}a+b=0 \\ a-b=0 \\ c=0\end{cases}\implies a=b=c=0\implies1,e^{x}+e^{-x},e^{x}-e^{-x}$ 線性獨立。
法二：
因為 $e^{x},e^{-x},1$ 都可以微無限次，且 $C^{2}[a,b] \subseteq C[a,b]$。
又因為在子空間線性獨立的向量們，在父向量空間也線性獨立。
那麼，此題本來無法用 Wronskian 解 $3\times2$ 的行列式，可以多微一次變成 $3\times 3$ 的行列式。
只要檢查該行列式是否等於零即可。
$\begin{vmatrix}1 & e^{x}+e^{-x} & e^{x}-e^{-x} \\ 0 & e^{x}-e^{-x} & e^{x}+e^{-x} \\ 0 & e^{x}+e^{-x} & e^{x}-e^{-x}\end{vmatrix}=-4\neq 0\implies$線性獨立。

14. Consider the vector $\cos(x+\alpha)$ and $\sin x$ in $C[-\pi,\pi]$. For what values of $\alpha$ will the two vectors be linear dependent?

Sol:
利用 Wronskian：$\begin{vmatrix}\cos(x+\alpha) & \sin x \\ -\sin(x+\alpha) & \cos x\end{vmatrix}=\cos x\cos(x+\alpha)+\sin x\sin(x+\alpha)$ 
是不是有點矇逼？問題不大，回憶公式 $\cos(a-b)=\cos a\cos b+\sin a\sin b$。
套用到本題：$\cos x\cos(x+\alpha)+\sin x\sin(x+\alpha)=\cos(-\alpha)=\cos\alpha\implies\alpha= \frac{\pi}{2}+k\pi\quad k\in \mathbb{N}$。

15. Given the functions $2x$ and $|x|$, show that (a) these two vectors are linearly independent in $C[-1,1]$. (b) these two vectors are linearly dependent in $C[0,1]$. 

Sol:
(a)
這題不要用 Wronskian，得出的解會找不到 $x$ 使得行列式不等於零。
直接套定義：
嘗試解 $a(2x)+b(|x|)=0$。
當 $x\geq0$：
$2ax+bx=0\implies2a+b=0$ 
當 $x<0$：
$2ax-bx=0\implies2a-b=0$ 
$\implies a=b=0$ 線性獨立。
(b)
當 $x\geq0\implies 2a+b=0$ 有 nontrivial solutions，所以線性相關。

16. Let $A$ be an $m\times n$ matrix. Show that if $A$ has linearly independent column vectors, then $N(A)=\{0\}$. 

Sol:
寫這題主要是為了教你如何證明這種類型的題目。 
令 $\mathbf{x}$ 為 $N(A)$ 中的任意向量。
則 $A\mathbf{x}=\mathbf{0}$。
$A\mathbf{x}=x_{1}\mathbf{a_{1}}+\dots+x_{n}\mathbf{a_{n}}=0$。
因為 column vectors 互相獨立，所以有 $x_{1}=x_{2}=\dots=x_{n}=0$。
因為 $\mathbf{x}$ 為 $N(A)$ 中的任意向量，所以 $N(A)=\{0\}$。

17. Let $\mathbf{x_{1}},\dots,\mathbf{x_{k}}$ be linearly independent vectors in $\mathbb{R}^{n}$ and let $A$ be a nonsingular $n\times n$ matrix. Define $\mathbf{y_{i}}=A\mathbf{x_{i}}$ for $i=1,\dots,k$. Show that $\mathbf{y_{1}},\dots,\mathbf{y_{k}}$ are linearly independent. 

Sol:
這題思考後自己寫了出來，如果有額外時間可以複習。
令 $\alpha_{1},\dots\alpha_{k}$ 為 scalars。
解 $\alpha_{1}(A\mathbf{x_{1}})+\dots+\alpha_{k}(A\mathbf{x_{k}})=0$ 是否只有 trivial solution。
提出 $A$：$A(\alpha_{1}\mathbf{x_{1}}+\dots+\alpha_{k}\mathbf{x_{k}})=0$。
因為 $A$ nonsingular，所以只有 trivial solution $(\alpha_{1}\mathbf{x_{1}}+\dots+\alpha_{k}\mathbf{x_{k}})=0$。
又因為 $\mathbf{x_{1}},\dots,\mathbf{x_{k}}$ 線性獨立，所以 $\alpha_{1},\dots,\alpha_{k}$ 必須 $\alpha_{1}=\dots=\alpha_{k}=0$。

18. Let $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ be the independent vectors in the vector space $V$. Show that $\mathbf{v_{2}},\dots,\mathbf{v_{n}}$ cannot span $V$. 

Sol:
利用反證法。
假設 $\mathbf{v_{2}},\dots,\mathbf{v_{n}}$ 可以張出 $V$。
因為 $\mathbf{v_{1}}\in V$，所以必有 $\mathbf{v_{1}}=\alpha_{2}\mathbf{v_{2}}+\dots+\alpha_{n}\mathbf{v_{n}}$。
$\implies-\mathbf{v_{1}}+\alpha_{2}\mathbf{v_{2}}+\dots+\alpha_{n}\mathbf{v_{n}}=0\implies \mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 線性相關。
與前提矛盾，所以 $\mathbf{v_{2}},\dots,\mathbf{v_{n}}$ 無法張出 $V$。

19. Find a basis for the subspace $S$ of $\mathbb{R}^{4}$ consisting of all vectors of the form $(a+b,a-b+2c,b,c)^{T}$, where $a,b,c$ are all real numbers. What is the dimension of $S$ ?

Sol:
$(a+b,a-b+2c,b,c)^{T}=a(1,1,0,0)^{T}+b(1,-1,1,0)^{T}+c(0,2,0,1)^{T}$ 
所以，$(1,1,0,0)^{T}, (1,-1,1,0)^{T},(0,2,0,1)^{T}$ span $S$。
驗證線性獨立：
考慮 $(a+b,a-b+2c,b,c)^{T}=\mathbf{0}\implies \begin{cases}a+b=0 \\ a-b+2c=0 \\ b=0 \\ c=0\end{cases}\implies a=b=c=0$ 
$\implies(1,1,0,0)^{T}, (1,-1,1,0)^{T},(0,2,0,1)^{T}$ 線性獨立。
所以 $(1,1,0,0)^{T}, (1,-1,1,0)^{T},(0,2,0,1)^{T}$ 為 $S$ 的基底，且 $\text{dim} \ S=3$。

20. Let $S$ be subspace of $P_{3}$ consisting of all polynomials $p(x)$ such that $p(0)=0$, and let $T$ be subspace of all polynomials $q(x)$ such that $q(1)=0$. Find bases for (a) $T$ (b) $S \cap T$. 

Sol:
(a)
不是很懂題目的意思，$T$ 到底是不是 $P_{3}$ 的子空間？這邊假設是好了。
**$q(1)=0\implies$ 可以被 $1$ 整除。**
則 $T=\{(x-1)(ax^{2}+bx+c)|a,b,c \in \mathbb{R}\}$。
展開：$ax^{3}+(-a+b)x^{2}+(-b+c)x-c=a(x^{3}-x^{2})+b(x^{2}-x)+c(x-1)$ 
因為 $x^{3}-x^{2},x^{2}-x,x-1$ 線性獨立，所以一組基底為：$\{x^{3}-x^{2},x^{2}-x,x-1\}$。
(b)
$p(0)=0, q(1)=0\implies$ **可以被 $0,1$ 整除**。
則 $S\cap T=\{x(x-1)(\alpha x+\beta)\}$。
展開：$x(x-1)(\alpha x+\beta)=\alpha x^{3}+(-\alpha+\beta)x^{2}-\beta x=\alpha(x^{3}-x^{2})+\beta(x^{2}-x)$。
因為 $x^{3}-x^{2},x^{2}-x$ 線性獨立，所以一組基底為：$\{x^{3}-x^{2},x^{2}-x\}$。

21. Is it possible to find a pair of two-dimensional subspaces $U$ and $V$ of $\mathbb{R}^{3}$ whose intersection is $\{\mathbf{0}\}$? Prove your answer. (Hint: Let $\{\mathbf{u_{1}},\mathbf{u_{2}}\}$ and $\{\mathbf{v_{1}},\mathbf{v_{2}}\}$ be bases for $U$ and $V$, respectively. Show that $\mathbf{u_{1}},\mathbf{u_{2}},\mathbf{v_{1}},\mathbf{v_{2}}$ are linearly dependent.)

Sol:
因為 $\mathbb{R}^{3}$ 中任意三個線性獨立的向量可以張出整個向量空間，所以不可能存在四個向量屬於 $\mathbb{R}^{3}$ 且線性獨立(第四個向量必定可以被前三個向量表達)。
令 $U=\text{Span}(\mathbf{u_{1}},\mathbf{u_{2}})$ 與 $V=\text{Span}(\mathbf{v_{1}},\mathbf{v_{2}})$。
$\alpha_{1}\mathbf{u_{1}}+\alpha_{2}\mathbf{u_{2}}+\alpha_{3}\mathbf{v_{1}}+\alpha_{4}\mathbf{v_{2}}=\mathbf{0}$ 其中 $\alpha_{1},\alpha_{2},\alpha_{3},\alpha_{4}$ 必定為 nontrivial solutions。
移項：$\alpha_{1}\mathbf{u_{1}}+\alpha_{2}\mathbf{u_{2}}=-\alpha_{3}\mathbf{v_{1}}-\alpha_{4}\mathbf{v_{4}}$ 。
**上式等號左右不為零**。(可以用此反推 $U\cap V\neq \{\mathbf{0}\}\implies$ $U, V$ 的基底必**線性相依**)
因為 $\alpha_{1}\mathbf{u_{1}}+\alpha_{2}\mathbf{u_{2}}\in U$ 且 $-\alpha_{3}\mathbf{v_{1}}-\alpha_{4}\mathbf{v_{4}}\in V$，
所以一定可以找到 $\mathbf{x}=\alpha_{1}\mathbf{u_{1}}+\alpha_{2}\mathbf{u_{2}}=-\alpha_{3}\mathbf{v_{1}}-\alpha_{4}\mathbf{v_{4}}\neq \mathbf{0}$ 使得 $\mathbf{x}\in U\cap V$。
所以 $U\cap V\neq \{\mathbf{0}\}$。

22. Show that if $U$ and $V$ are subspaces of $\mathbb{R}^{n}$ and $U\cap V=\{\mathbf{0}\}$, then $\text{dim}(U+V)=\text{dim} \ U+\text{dim }V$. 

Sol:
我們先來證明性質：$U\cap V=\{\mathbf{0}\}\implies U,V$ 的基底線性獨立。
令 $U=\text{Span}(\mathbf{u_{1}},\dots ,\mathbf{u_{n}})$ 與 $V=\text{Span}(\mathbf{v_{1}},\dots,\mathbf{v_{n}})$。
令 $\alpha_{1},\dots,\alpha_{n}$ 與 $\beta_{1},\dots,\beta_{n}$ 為 scalars。
考慮：$\alpha_{1}\mathbf{u_{1}}+\dots+\alpha_{n}\mathbf{u_{n}}+\beta_{1}\mathbf{v_{1}}+\dots+\beta_{n} \mathbf{v_{n}}=0$。
移項：$\alpha_{1}\mathbf{u_{1}}+\dots+\alpha_{n}\mathbf{u_{n}}=-(\beta_{1}\mathbf{v_{1}}+\dots+\beta_{n}\mathbf{v_{n}})$ 。
因為 $\alpha_{1}\mathbf{u_{1}}+\dots+\alpha_{n}\mathbf{u_{n}} \in U$ 且 $-(\beta_{1}\mathbf{v_{1}}+\dots+\beta_{n}\mathbf{v_{n}}) \in V$，又 $U\cap V=\{\mathbf{0}\}$。
所以，$\mathbf{0}=\alpha_{1}\mathbf{u_{1}}+\dots+\alpha_{n}\mathbf{u_{n}}=-(\beta_{1}\mathbf{v_{1}}+\dots+\beta_{n}\mathbf{v_{n}})$。
因為基底線性獨立，所以 $\alpha_{1}=\dots=\alpha_{n}=\beta_{1}=\dots=\beta_{n}=0$ 
$\implies \mathbf{u_{1}},\dots,\mathbf{u_{n}},\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 線性獨立。
那麼，因為 $\mathbf{u_{1}},\dots,\mathbf{u_{n}},\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 線性獨立，
所以有：
$\text{dim}(U+V)=\text{dim}(\text{Span}(\mathbf{u_{1}},\dots,\mathbf{u_{n}},\mathbf{v_{1}},\dots,\mathbf{v_{n}}))=\text{dim}(\text{Span}(\mathbf{u_{1}},\dots,\mathbf{u_{n}}))+\text{dim}(\text{Span}(\mathbf{v_{1}}, \dots,\mathbf{v_{n}}))$ 
$\implies\text{dim}(U+V)=\text{dim}(U)+\text{dim}(V)$。

23. Given $\mathbf{v_{1}}=\begin{bmatrix}3 \\ 1\end{bmatrix}, \mathbf{v_{2}}=\begin{bmatrix}4 \\ 2\end{bmatrix}, S=\begin{bmatrix}2 & -5 \\ -1 & 3\end{bmatrix}$, find the vector $\mathbf{w_{1}}$ and $\mathbf{w_{2}}$ so that $S$ will be the transition matrix from $\{\mathbf{w_{1}},\mathbf{w_{2}}\}$ to $\{\mathbf{v_{1}},\mathbf{v_{2}}\}$. 

Sol:
首先給波錯誤示範：
令 $W=(\mathbf{w_{1}},\mathbf{w_{2}})$，我**以為**可以寫成 $SW=V$。
但是**不行**！這樣只能解出兩個在 $\{\mathbf{w_{1}}\mathbf{w_{2}}\}$ 上的座標使得映射後等於 $\mathbf{v_{1}},\mathbf{v_{2}}$，但我們要求的是基底而不是座標。
給波正確範例：
令 $V=\begin{bmatrix}3 & 4 \\ 1 & 2\end{bmatrix}$ $W=(\mathbf{w_{1}},\mathbf{w_{2}})$。
根據定義，我們有：$S=V^{-1}W$。
那麼，解 $W=VS=\begin{bmatrix}2 & -3 \\ 0 & 1\end{bmatrix}\implies \mathbf{w_{1}}=(2,0)^{T} \ \mathbf{w_{2}}=(-3,1)^{T}$。

24. Let $A$ be $4\times3$ matrix and suppose the vectors $\mathbf{z_{1}}=\begin{bmatrix}1 \\ 1 \\ 2\end{bmatrix} \ \mathbf{z_{2}}=\begin{bmatrix}1 \\ 0 \\ -1\end{bmatrix}$ forms a basis for $N(A)$. If $\mathbf{b}=a_{1}+2a_{2}+a_{3}$, find all the solutions of the system $A\mathbf{x}=\mathbf{b}$. 

Sol:
這題主要怕漏解，其實不難。
$\mathbf{b}=A\begin{bmatrix}1 \\ 2 \\ 1\end{bmatrix}$ 
$A(\begin{bmatrix}1 \\ 2 \\ 1\end{bmatrix}+t\begin{bmatrix}1 \\ 1 \\ 2\end{bmatrix}+s\begin{bmatrix}1 \\ 0 \\ -1\end{bmatrix})=\mathbf{b}+0+0=\mathbf{b}$  $t,s\in \mathbb{R}$ 
$\implies \mathbf{x}=\begin{bmatrix}1+t+s \\ 2+t \\ 1+2t-s\end{bmatrix} \ t,s\in \mathbb{R}$ 

25. Let $A$ be $4\times4$ matrix with reduced echelon form given by $\begin{bmatrix}1 & 0 & -1 & 1 \\ 0 & 1 & 3 & 2 \\ 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0\end{bmatrix}$. If $\mathbf{a_{1}}=\begin{bmatrix}3 \\ 2 \\ -1 \\ 2\end{bmatrix}$ and $\mathbf{a_{2}}=\begin{bmatrix}1 \\ 1 \\ -1 \\ 3\end{bmatrix}$, find $\mathbf{a_{3}},\mathbf{a_{4}}$. 

Sol:
這題難在我忘記：**兩個 row equivalent 的矩陣，column vectors 的 dependency relations 會相同**。
所以 $\mathbf{u_{3}}=-\mathbf{u_{1}}+3\mathbf{u_{2}}, \ \mathbf{u_{4}}=\mathbf{u_{1}}+2\mathbf{u_{2}}\implies \mathbf{a_{3}}=-\mathbf{a_{1}}+3\mathbf{a_{2}}, \ \mathbf{a_{4}}=\mathbf{a_{1}}+2\mathbf{a_{2}}$。
解解就好。

26. Let $A$ be a $4 × 5$ matrix and let $U$ be the reduced row echelon form of $A$. If $\mathbf{a_{1}}=\begin{bmatrix}2 \\ 1 \\ -3 \\ -2\end{bmatrix}$ $\mathbf{a_{2}}=\begin{bmatrix}-1 \\ 2 \\ 3 \\ 1\end{bmatrix}$ $U=\begin{bmatrix} 1 & 0 & 2 & 0 & -1 \\ 0 & 1 & 3 & 0 & -2 \\ 0 & 0 & 0 & 1 & 5 \\ 0 & 0 & 0 & 0 & 0\end{bmatrix}$ and given that $\mathbf{x_{0}}=\begin{bmatrix} 3 \\ 2 \\ 0 \\ 2 \\ 0\end{bmatrix}$ is a solution to $A\mathbf{x}=\begin{bmatrix}0 \\ 5 \\ 3 \\ 4\end{bmatrix}$. Determine $\mathbf{a_{4}}$. 

Sol:
因為這題的其他問題都還好，我就把卡住的點拿出來問。
因為 $\begin{bmatrix}0 \\ 5 \\ 3 \\ 4\end{bmatrix}=3\mathbf{a_{1}}+2\mathbf{a_{2}}+2\mathbf{a_{4}}\implies \mathbf{a_{4}}=\begin{bmatrix}-2 \\ -1 \\ 4 \\ 4\end{bmatrix}$。
`~~~~~~~~~~~~~~~~~~~~~^ 利用` $\mathbf{x_{0}}$。

27. (!)Let $A$ and $B$ be $m × n$ matrices. Show that $\text{rank}(A+B)\leq\text{rank}(A)+\text{rank}(B)$. 

Sol:
令 $\mathbf{x}\in \mathbb{R}^{n}$，則 $(A+B)\mathbf{x}=A\mathbf{x}+B\mathbf{x} \in\text{Col}(A)+\text{Col}(B)$。
$\implies\text{rank}(A+B)$ 
$=\text{dim}(\text{Col}(A+B))\leq\text{dim}(\text{Col}(A)+\text{Col}(B))\leq\text{dim}(\text{Col}(A))+\text{dim}(\text{Col}(B))=\text{rank}(A)+\text{rank(B)}$ 

27. Let $A$ be an $m × n$ matrix. Show that if $C$ is a nonsingular $n × n$ matrix, then $AC$ and $A$ have the same rank.

Sol:
因為 $C$ 非奇異，所以可以將 $C$ 寫成一系列基本矩陣相乘。
因為將**基本矩陣乘以某個矩陣不會改變該矩陣的 rank**，所以 $\text{rank}(AC)=\text{rank}(AE_{1},\dots,E_{n})=\text{rank}(A)$ 

28. Let $A$ and $B$ be $n × n$ matrices. (a) Show that $AB= O$ if and only if the column space of $B$ is a subspace of the null space of $A$. (b) Show that if $AB= O$, then the sum of the ranks of $A$ and $B$ cannot exceed $n$.

Sol:
(a)
($\implies$)
取 $\mathbf{y}\in\text{Col}(B)$，則有 $\mathbf{x}$ 滿足 $\mathbf{y}=B\mathbf{x}$。
考慮 $A\mathbf{y}=A(B\mathbf{x})=(AB)\mathbf{x}=\mathbf{0}\implies \mathbf{y}\in N(A)$ 
$\implies\text{Col}(B)\subseteq N(A)$ 
($\impliedby$)
取 $B\mathbf{x}\in\text{Col}(B)$ 則 $B\mathbf{x}\in N(A)$，$x\in \mathbb{R}^{n}$。
那麼，$A(B\mathbf{x})=(AB)\mathbf{x}=\mathbf{0}$。
因為 $\forall x \in \mathbb{R}^{n}$ $AB\mathbf{x}=\mathbf{0}$ 都成立，所以 $AB=\mathbf{0}$。

29. Let $\mathbf{x}$ and $\mathbf{y}$ be nonzero vectors in $\mathbb{R}^{m}$ and $\mathbb{R}^{n}$, respectively, and let $A= \mathbf{xy}^{T}$. Show that $\{\mathbf{x}\}$ is a basis for the column space of $A$ and that $\{\mathbf{y}^{T} \}$ is a basis for the row space of $A$.

Sol:
$a_{i}=y_{i}\mathbf{x}$ 
$\implies\text{Col}(A)=\text{Span}(\mathbf{x})$ 且 $\{\mathbf{x}\}$ 線性獨立 $\implies\{\mathbf{x}\}$ 為 column space 的基底。
$a^{j}=x_{y}\mathbf{y}^{T}$ 
$\implies\text{Row}(A)=\text{Span}(\mathbf{y}^{T})$ 且 $\{\mathbf{y}^{T}\}$ 線性獨立 $\implies\{\mathbf{y}^{T}\}$ 為 row space 的基底

30. Let $A\in \mathbb{R}^{m\times n},\ B\in \mathbb{R}^{n\times r}$, and $C=AB$. Show that if $A$ and $B$ both have linearly independent column vectors, then the column vectors of $C$ will also be linearly independent. 

Sol:
本來這題我想用上題那樣分解，但是貌似有更快的解法。
由題意可知：$N(A)=N(B)=\{\mathbf{0}\}$。
取任意 $\mathbf{w}\in \mathbb{R}^{r}$ 使得 $C\mathbf{w}=\mathbf{0}$。
則 $C\mathbf{w}=AB\mathbf{w}=A(B\mathbf{w})=\mathbf{0}$。
因為 $N(A)=\{\mathbf{0}\}$，所以 $B\mathbf{w}=\mathbf{0}$。
又因為 $N(B)=\{\mathbf{0}\}$，所以 $\mathbf{w}=\mathbf{0}$。
那麼，$N(C)=\{\mathbf{0}\}$，所以 column vectors of $C$ 線性獨立。

31. An $m × n$ matrix $A$ is said to have a right inverse if there exists an $n × m$ matrix $C$ such that $AC= I_{m}$. Show that if $A$ has a right inverse, then the column vectors of $A$ span $\mathbb{R}^{m}$.

Sol:
令 $\mathbf{b}\in \mathbb{R}^{m}$ 的任意向量。
$\mathbf{b}=I\mathbf{b}=AC\mathbf{b}=A(C\mathbf{b})$ 
那麼，$\mathbf{b}$ 可以被 $A$ 的 column vectors 線性組合 ($C\mathbf{b}$ 為 $n\times1$ 的向量)。
$\implies \mathbb{R}^{m}\subseteq\text{Col}(A)$ 

32. Prove: If $A$ is an $m × n$ matrix and the column vectors of $A$ span $\mathbb{R}^{m}$, then $A$ has a right inverse. (Hint: Let $\mathbf{e_{j}}$ denote the jth column of $I_{m}$ and solve $A\mathbf{x}=\mathbf{e_{j}}$ for $j=1,\dots,m$. )

Sol:
因為 $\mathbf{e}_{j}\in \mathbb{R}^{m}\subseteq\text{Col(A)}$，所以對於 $A\mathbf{x}=\mathbf{e_{j}}$ 都可以找到解。
將這些解合起來組成一個矩陣，就是 $A$ 的右逆。