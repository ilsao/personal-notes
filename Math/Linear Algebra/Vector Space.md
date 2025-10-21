
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

令 $\mathbf{v_{1}}, \mathbf{v_{2}}, \dots, \mathbf{v_{n}}$ 是向量空間 $V$ 中的向量，我們稱 $\alpha \mathbf{v_{1}}+\alpha \mathbf{v_{2}}+\dots+\alpha \mathbf{v_{n}}$ 為 $\mathbf{v_{1}}, \mathbf{v_{2}}, \dots, \mathbf{v_{n}}$ 的線性組合。**所有線性組合組成的集合**就稱為 $\mathbf{v_{1}}, \mathbf{v_{2}}, \dots, \mathbf{v_{n}}$ 的**生成空間(span)**，可以用 $\text{Span}(\mathbf{v_{1}}, \mathbf{v_{2}}, \dots, \mathbf{v_{n}})$ 表示。

$$
如果 \ \mathbf{v_{1}}, \mathbf{v_{2}}, \dots, \mathbf{v_{n}} \ 是向量空間 \ V \ 中的向量，那麼其生成空間必為 \ V \ 的子空間。
$$

proof:
令 $\beta$ 為標量，$\mathbf{v}=\alpha \mathbf{v_{1}}+\dots+\alpha \mathbf{v_{2}}$, $\mathbf{w}=\beta \mathbf{v_{1}}+\dots+\beta \mathbf{v_{2}}$ 為兩個取自 $\text{Span}(\mathbf{v_{1}}, \mathbf{v_{2}}, \dots, \mathbf{v_{n}})$ 的向量。
因為：
$\beta \mathbf{v_{1}}=(\beta\alpha)\mathbf{v}+\dots+(\beta\alpha)\mathbf{v_{n}} \in\text{Span}(\mathbf{v_{1}, \dots, v_{n}})$ 
且：
$\mathbf{v}+\mathbf{w}=(\alpha+\beta)\mathbf{v_{1}}+\dots+(\alpha\beta)\mathbf{v_{n} \in \text{Span}(\mathbf{v_{1}},\dots,\mathbf{v_{n}})}$ 
所以，命題成立。

## Spanning Set for a Vector Space

$\mathbf{v_{1}}, \mathbf{v_{2}}, \dots \mathbf{v_{n}}$ 是 $V$ 的生成集 $\Leftrightarrow$ $V$ 可以被表達為 $\mathbf{v_{1}}, \mathbf{v_{2}}, \dots \mathbf{v_{n}}$ 的線性組合。

這邊有點繞，我們必須清楚的區分 Span 和 Spanning Set。其實，他們互為反向描述。

讓我們舉個例子，想要張出向量空間 $\mathbb{R}^{2}$，我們最少區要兩個向量作為生成集。因為一個向量的生成空間只會是一條直線。

我們可以取 $\{\mathbf{e_{1}}, \mathbf{e_{2}}\}$ 來張出 $\mathbb{R}^{2}$。那麼 $\{\mathbf{e_{1}}, \mathbf{e_{2}}\}$ 就是 $\mathbb{R}^{2}$ 的生成集。

## Linear Systems Revisited

考慮一個有解的線性系統 $A\mathbf{x}=\mathbf{b}$。

如果 $\mathbf{b}=\mathbf{0}$，那麼所有解構成的集合 $S=N(A)$，且 $S$ 是 $\mathbb{R}^{n}$ 的子空間。

如果 $\mathbf{b}\neq \mathbf{0}$，那麼 $S$ 無法構成 $\mathbb{R}^{n}$ 的子空間，因為 $\mathbf{0} \not\in S$。

我們有：如果給定 $\mathbf{x_{0}}$ 為一組特定解，那麼 $\mathbf{y}$ 也會是一組解 $\Leftrightarrow \mathbf{y}=\mathbf{x_{0}}+\mathbf{z}$，其中 $\mathbf{z} \in N(A)$。

要如何理解這個？給定系統的另一個解 $\mathbf{x_{1}}$，並令 $\mathbf{z}=\mathbf{x_{1}-x_{0}}$。那麼：

$$
A\mathbf{z}=A\mathbf{x_{1}}-A\mathbf{x_{2}}=\mathbf{b}-\mathbf{b}=\mathbf{0}
$$

所以，另一個解必為 $\mathbf{x_{1}}=\mathbf{x_{0}}+\mathbf{z}$，且 $\mathbf{z} \in N(A)$。

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
2. 給定 $n$ 個向量 $\mathbf{v_{1}},\dots \mathbf{v_{n}}$。如果有辦法將某個向量寫成其他 $n-1$ 個向量的線性組合 $\Leftrightarrow$ $c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}=\mathbf{0}$ 且 $c_{1},\dots,c_{n} \neq 0$。

proof (1):
假設 $\mathbf{v_{n}}$ 可以被其他向量的線性組合表達。
令 $\mathbf{v}$ 為向量空間 $V$ 中的向量，因為 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 可以張出 $V$，所以：
$\mathbf{v}=\alpha_{1} \mathbf{v_{1}}+\dots+\alpha _{n} \mathbf{v_{n}}=\alpha_{1}\mathbf{v_{1}}+\dots+\alpha_{n}(\beta_{1}\mathbf{v_{1}}+\dots+\beta_{n-1}\mathbf{v_{n-1}})$ 
$=(\alpha_{1}+\beta_{1})\mathbf{v_{1}} + \dots+(\alpha_{n}+\beta_{n})\mathbf{v_{n-1}}$ 
因為向量空間 $V$ 的任意向量 $\mathbf{v}$ 都可以被表達為 $\mathbf{v_{1}},\dots,\mathbf{v_{n-1}}$ 的線性組合，所以這些向量生成 $V$。

proof (2):
($\implies$)
假設 $\mathbf{v_{n}}$ 可以被其他向量的線性組合表達。
$\mathbf{v_{n}}=\alpha_{1}\mathbf{v_{1}}+\alpha_{2}\mathbf{v_{2}+\dots+\alpha_{n-1}\mathbf{v_{n-1}}}$ 
移項可得：$\alpha_{1}\mathbf{v_{1}}+\dots+\alpha_{n-1}\mathbf{v_{n-1}}-\mathbf{v_{n}}=\mathbf{0}$ 
如果我們設對於 $i,\dots,n-1$ 有 $c_{i}=\alpha_{i}$ ，且 $c_{n}=-1$，我們有：$c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}=\mathbf{0}$ 
相反的，如果 $c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}=\mathbf{0}$，那麼一定有一個 $c_{i}\neq 0$ (這裡取 $c_{n}$) 使得：
$\mathbf{v_{n}}= \frac{-c_{1}}{c_{n}}\mathbf{v_{1}}+\dots+ \frac{-c_{n-1}}{c_{n}}\mathbf{v_{n-1}}$ 

本章的重點有點混亂：
- 線性相依：某向量可以被其他向量表達 $\implies$ $c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}=\mathbf{0}$ 且 $c_{1},\dots c_{n}\neq0$。$\det(A)=0$ 
- 線性獨立：沒有向量可以被其他向量表達 $\implies$  $c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}=\mathbf{0}$ 且 $c_{1},\dots c_{n}=0$。$\det(A)\neq 0$

## Geometric Interpretation

如果我們有 $\mathbb{R}^{3}$ 空間中的三個向量 $\mathbf{x,y,z}$，如果 $\mathbf{x,y}$ 線性相依，那麼：$c_{1}\mathbf{x}+c_{2}\mathbf{y}=\mathbf{0}$ 其中 $c_{1}, c_{2}$ 至少一個不為零。
假設 $c_{1}$ 不為零，那麼：$\mathbf{x}=-\frac{c_{2}}{c_{1}}\mathbf{y}$。說明 $\mathbf{x,y}$ 在三維空間中共線。
相反如果二者線性獨立，那麼 $\mathbf{x},\mathbf{y}$ 可以在三維空間中張出一個平面。
此時，如果 $\mathbf{z}$ 與二者線性相依，那麼 $\mathbf{z}$ 會落在該平面上。若線性獨立，則不會落在該平面上。

## Theorems and Examples

誒，我好厲害，他剛要講的 Theorem 我在之前就補充道上上小節了耶～

$$令 \ \mathbf{x_{1}},\dots,\mathbf{x_{n}} \ 為 \ \mathbb{R}^{n} \ 中的 \ n \ 個向量，且 \ X=(\mathbf{x_{1}},\dots,\mathbf{x_{n}})。則 \ \mathbf{x_{1}},\dots,\mathbf{x_{n}} \ 線性相依 \ \Leftrightarrow X \ 奇異。$$

proof:
等式：$c_{1}\mathbf{x_{1}}+\dots+c_{n}\mathbf{x_{n}}$ 可以被寫成以下矩陣方程：$X\mathbf{c}=\mathbf{0}$ 。
此方程有 nontrivial solution $\Leftrightarrow X$ 奇異。

需要注意的是，待檢測的 $k$ 個 $\mathbb{R}^{n}$ 中的向量如果 $k\neq n$，則不能使用行列式檢測。我們必須將矩陣化成 REF，然後觀察 free variables 是否出現。如果有，則必定線性相依。相反，則線性獨立。

$$
\text{令 }\mathbf{v_{1}},\dots,\mathbf{v_{n}}\text{ 為向量空間 }V\text{ 中的向量}。\text{對於 } \mathbf{v} \in \text{Span}(\mathbf{v_{1}},\dots,\mathbf{v_{n}})\text{：}
$$
$$
\mathbf{v}\text{ 可以被寫成} \ \mathbf{v_{1}},\dots,\mathbf{v_{n}}\text{唯一的線性組合方式} \Leftrightarrow\text{ } \mathbf{v_{1}},\dots,\mathbf{v_{n}}\text{ 線性獨立}
$$

proof:
我們有 $\mathbf{v}=\alpha_{1}\mathbf{v_{1}}+\dots+\alpha_{n}\mathbf{v_{n}}$。
假設還有 $\mathbf{v}=\beta_{1}\mathbf{v_{1}}+\dots+\beta_{n}\mathbf{v_{n}}$
如果 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 線性獨立，那麼我們要證明 $\alpha_{i}=\beta_{i}$。
我們將兩式相減，得到 $(\alpha_{1}-\beta_{1})\mathbf{v_{1}}+\dots+(\alpha_{n}-\beta_{n})\mathbf{v_{n}}=\mathbf{0}$ 。
又因為 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 線性獨立，所以所有係數都應該等於零 $\alpha_{i}-\beta_{i}=0\implies\alpha_{i}=\beta_{i}$。
若 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 線性相依，那麼我們要證明最少有一個 $\beta_{i}$ 不等於 $\alpha_{i}$。
因為 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 線性相依，所以我們可以假設 $c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v_{n}}=\mathbf{0}$，其中 $c_{1},\dots,c_{n}$ 不全為零。
令 $\beta_{i}=\alpha_{i}+c_{i}$，那麼：
$\beta_{1}\mathbf{v_{1}}+\dots+\beta_{n}\mathbf{v_{n}}=(\alpha_{1}+c_{1})\mathbf{v_{1}}+\dots+(\alpha_{n}+c_{n})\mathbf{v_{n}}=\mathbf{v}+\mathbf{0}=\mathbf{v}$ 
說明一定可以找的 $\beta_{i}=\alpha_{i}+c_{i}$ 使得最少有一個 $\beta_{i}$ 不等於 $\alpha_{i}$ 使得 $\mathbf{v}=\beta_{1}\mathbf{v_{1}}+\dots+\beta_{n}\mathbf{v_{n}}$。

## Vector Spaces of Functions

### The Vector Space $P_{n}$ 

想測試多項式 $p_{1},\dots,p_{n}$ 是否線性獨立在 $P_{n}$ 向量空間中，我們令：$c_{1}p_{1}+c_{2}p_{2}+\dots+c_{n}p_{n}=z$ 。

其中，$z$ 為零多項式。即，$z(x)=0x^{n-1}+0x^{n-2}+\dots+0x+0$。

我們可以將 $c_{1}p_{1}+c_{2}p_{2}+\dots+c_{n}p_{n}$ 寫成 $a_{1}x^{n-1}+\dots+a_{n}$。

那麼，想要 $p_{1},\dots,p_{n}$ 線性獨立，則 $a_{1},\dots,a_{n}$ 必須全部等於零。由於 $a_{i}$ 由 $c_{i}$ 與 $p_{i}$ 構成，也就說明 $c_{1},\dots,c_{n}$ 必須全部為零。

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

需要注意，反向結論是不成立的。也就是說就算對於所有 $x$ 都有 $W[f_{1},\dots,f_{n}](x)=0$ 並仍**不可保證** $f_{1},\dots,f_{n}$ 線性相依。因為，想要保證線性相依， $c_{i}$ 必須為一個固定常數。但是對於所有 $x$ 都有 $W[f_{1},\dots,f_{n}](x)=0$ 只能保證對於某特定 $x$ 可以找到相對應的 $c_{i}$ 使得等式成立。而這個 $c_{i}$ 有可能是常數也有可能隨著 $x$ 不同而改變。所以無法保證線性相依，但是可以說明有一定可能性這些函數線性相依。