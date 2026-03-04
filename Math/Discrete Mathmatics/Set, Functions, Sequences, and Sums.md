# Sets

**集合(set)** 就是一種將對象**無序**收集在一起的容器，集合中的對象稱為**元素(element)** 或**集合的成員(member of the set)**。

當寫 $x\in A$ 時，表示 $A$ 是一個集合，而 $x$ 為集合中的元素。

集合有兩種標記法：
- 列舉法：在大括弧中列舉出集合中的每個元素。
- 描述法：$\{x  |  \text{attributes of }x\}$。

> [!note]
> 使用列舉法列舉有規律元素時，通常列三個元素後使用 $\dots$。

我們舉例些重要的集合：
- 自然數：$\mathbb{N}=\{0,1,2,\dots\}$。(有些書認為 $0$ 不是自然數)
- 整數：$\mathbb{Z}=\{\dots,-2,-1,0,1,2,\dots\}$。
- 正整數：$\mathbb{Z}^{+}=\{1,2,3,\dots\}=\{x|x\in \mathbb{N}\text{ and }x>0\}$。
- 有理數：$\mathbb{Q}=\left\{ \frac{x}{y}|x\in \mathbb{Z}\text{ and }y\in \mathbb{Z} -\{0\}\right\}$。
- 實數：$\mathbb{R}$。
- 空集合：$\phi=\{\ \}$。

> [!warning] 注意
> $\phi$ 表示的是空集合，不代表不存在。$\phi$ 是一個沒有任何元素的集合。
> 所以，$\{\phi\}$ 不是空集合。

若 $A,B$ 為集合，我們定義：

$$
A=B\iff \forall x(x\in A\leftrightarrow x\in B)
$$

$$
A\subseteq B\iff \forall x(x\in A\to x\in B)
$$

> [!error] 小心
> $\phi \not\in\{0\}$ 因為 $\{0\}$ 不包含空集合 $\{ \ \}$。
> 但是，$\phi \subset\{0\}$，因為 $\phi$ 是任意集合的子集合。

> [!note]
> 使用 $\in$ 時，直接對左側對象判斷是否在右側中出現。
> 使用 $\subset$ 時，先對左側對象拆大括號後，再判斷是否在右側中出現。

若 $S$ 為**有限**集合，則 $S$ 集合的**基數(cardinality)** 表示該集合的元素個數，記為 $|S|$。

若 $S$ 為集合，則 $S$ 的**冪集合(power set)** 是 $S$ 所有子集合形成的集合，記為 $P(S)$。

例如：$S=\{ 1,2 \}$。
則：$|S|=2$，而 $P(S)=\{ \phi,\{ 1 \},\{ 2 \},\{ 1,2 \} \}$。

> [!note]
> $\{ a,\{ a \},\{ a,\{ a \} \} \}$ 的基數為 $3$！因為 $\{ a,\{ a \} \}$ 只被視為一個元素！

這邊有個較 tricky 的東西：$P(P(\phi))=\{ \phi,\{ \phi \} \}$。

綜上所述，通過我們精湛的組合技術，得知 $|P(S)|=2^{|S|}$。

## Cartesian Product

若 $A,B$ 為兩集合，則 $A$ 與 $B$ 的**笛卡爾積(cartesian product)** 表示為 $A\times B$，且定義為：

$$
A\times B=\{ (a,b)|a\in A\text{ and }b\in B \}
$$

我們定義多個集合的笛卡爾積。若 $A_{1},A_{2},\dots,A_{n}$ 為集合，則：

$$
A_{1}\times A_{2}\times\dots \times A_{n}=\{ (a_{1},a_{2},\dots,a_{n})|a_{i}\in A_{i}\text{ for each i} \in \{ 1,2,\dots,n \} \}
$$

> [!warning] 注意
> $(a,b)$ 表示 $a$ 與 $b$ 有順序之分，稱為 ordered pair！

例如：$A=\{ 1,2 \}, \ B=\{ a,b,c \}$，則 $A\times B=\{ (1,a),(1,b),(1,c),(2,a),(2,b),(2,c) \}$。

再次通過精湛的組合技巧，因為 $|A\times B|$ 可以通過 $C^{|A|}_{1}C^{|B|}_{1}$ 計算，所以有：

$$
|A\times B|=|A|\times|B|
$$

> [!note]
> 這裡左側的 $\times$ 為笛卡爾積，右側的 $\times$ 為數字乘法。

> [!note]
> 有個很妙的結論，二維坐標系統 $(x,y)$ 可被視為笛卡爾積 $(x,y)\in X\times Y$ 其中 $X,Y\in \mathbb{R}$。

我們有一個結論：

$$
\phi \times A=\phi
$$

proof:
使用矛盾法。
假設 $\phi \times A\neq \phi$，則存在 $(x,y)\in \phi \times A$，其中 $x\in \phi$。
產生矛盾，所以 $\phi \times A=\phi$。
同理可證 $A\times \phi=\phi$。

另外還有：

$$
A\times B=B\times A\iff A=B\text{, or }A=\phi\text{, or }B=\phi
$$

proof:
($\impliedby$)
$A=B$ 則 $A\times B=A\times A=B\times A$。
$A=\phi$ 則 $\phi \times B=\phi=B\times \phi$。
$B=\phi$ 時同理。
($\implies$)
假設 $A,B$ 為非空集合且 $A\times B=B\times A$。
則對任意 $x\in A,y\in B$ 有 $(x,y)\in A\times B$ 也 $(x,y)\in B\times A$。
那麼，$x\in B$ 且 $y\in A$。
即，$A\subseteq B$ 且 $B\subseteq A$。根據集合相等的定義，有 $A=B$。
若 $A$ 或 $B$ 為空集合，結論自然成立。

## Set Operations

介紹三個基本集合運算：

$$
A\cup B=\{ x|x\in A\text{ or }x\in B \}
$$

$$
A\cap B=\{x|x\in A\text{ and }x\in B\}
$$

$$
A-B=\{ x|x\in A\text{ and }x\not\in B \}
$$

並且，我們如下定義集合 $A$ 與 $B$ **互斥(disjoint)**：

$$
A\cap B=\phi
$$

有一個較為特殊的運算符，**對稱差集(symmetric difference)**：

$$
\begin{align}
A\oplus B & =\{ x|x\in A-B\text{ or }x\in B-A \} \\
 & =(A-B)\cup(B-A) \\
 & =(A\cup B)-(A\cap B)
\end{align}
$$

注：有些書用 $\Delta$ 當作對稱差集的運算符。

我們可以對對稱差集做結合律，即：

$$
A\oplus (B\oplus C)=(A\oplus B)\oplus C
$$

我們嘗試證明：

$$
A\oplus C=B\oplus C\implies A=B
$$

proof:
使用逆否命題，假設 $A\neq B$，並且不失一般性地令 $x\in A-B$。
若 $x\in C$，則 $x\in A, \ x\not\in B,\ x\in C$。
這樣，$x\in A\cap C$，所以 $x\not\in A\oplus C$。但是 $x\not\in B\cap C$，所以 $x\in B\oplus C$。
$\implies A\oplus C\neq B\oplus C$。
若 $x\not\in C$，則 $x\in A,\ x\not\in B, \ x\not\in C$。
這樣，$x\not\in A\cap C$，所以 $x\in A\oplus C$。但是 $x\not\in B\cup C$，所以 $x\not\in B\oplus C$。
$\implies A\oplus C\neq B\oplus C$。
所以 $A\oplus C=B\oplus C\implies A=B$。

若 $U$ 是 $A$ 的宇集，則 $A$ 的補集記做 $A^{c}$ 或 $\bar{A}$，並定義為：

$$
A^{c}=U-A
$$

> [!note]
> 有宇集才可討論補集。

讓我們嘗試證明：

$$
\overline{ A\cap B }=\bar{A}\cup \bar{B}
$$

> [!note]
> 使用邏輯運算拆分集合運算！

proof:
$\overline{ A\cap B }=\{ x|x\in \overline{ A\cap B } \}=\{ x|x\not\in A\cap B \}$ 
$=\{ x|\neg(x\in A\cap B) \}=\{ x|\neg((x\in A)\land (x\in B) \}$ 
=$\{ x|(x\not\in A)\lor(x\not\in B) \}=\{ x|(x\in \bar{A})\lor(x\in \bar{B}) \}$ 
$=\{ x|x\in \bar{A}\cup \bar{B} \}=\bar{A}\cup \bar{B}$ 

緊接著我們來定義連續運算：

$$
\cup^{n}_{i=1}A_{i}=A_{1}\cup A_{2}\cup\dots \cup A_{n}
$$

$$
\cap_{i=1}^{n}A_{i}=A_{1}\cap A_{2}\cap\dots \cap A_{n}
$$

或者，更靈活的令 $I=\{ 1,3,5 \}$：

$$
U_{i\in I}A_{i}=A_{1}\cup A_{3}\cup A_{5}
$$

有一個我們必須學會的東西：**排容原理(Inclusion-Exclusion Principle)**。

$$
|A\cup B|=|A|+|B|-|A\cap B|
$$

