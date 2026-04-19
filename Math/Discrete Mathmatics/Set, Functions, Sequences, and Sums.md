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

> [!error] 超級無敵大提醒！！！
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
\bigcup^{n}_{i=1}A_{i}=A_{1}\cup A_{2}\cup\dots \cup A_{n}
$$

$$
\bigcap_{i=1}^{n}A_{i}=A_{1}\cap A_{2}\cap\dots \cap A_{n}
$$

或者，更靈活的令 $I=\{ 1,3,5 \}$：

$$
U_{i\in I}A_{i}=A_{1}\cup A_{3}\cup A_{5}
$$

有一個我們必須學會的東西：**排容原理(Inclusion-Exclusion Principle)**。

$$
|A\cup B|=|A|+|B|-|A\cap B|
$$

# Functions

我們定義函數 $f:A\to B$ 為：對**每個** $A$ 中的元素，都可以找到**一個** $B$ 中對應的元素。

其中，我們稱：
- $A$：**定義域(domain)** 
- $B$：**對應域(codomain)** 
- $f(A)$：**值域(range)** 

並且有：$f(A)\subseteq B$。

而從 $A$ 中取一些值作為集合 $S$，則 $f(S)$ 被稱為函數的**映像(image)**，$f(S)\subseteq f(A)$。

> [!warning] 注意
> $f(x)=\frac{1}{x}$ 不是 $\mathbb{R}\to \mathbb{R}$ 的函數，因為 $0\in \mathbb{R}$，但 $f(0)\not\in \mathbb{R}$。
> 而 $f(x)=\pm x$ 不是函數，因為一個輸入對應到多個輸出。

## One-to-one Function

回憶一下 1-1 函數的定義：

若對 $f$ 來說，$x_{1}\neq x_{2}\iff f(x_{1})\neq f(x_{2})$ 則稱 $f$ 為一對一函數。

## Onto and Surjective

若 $f:A\to B$ 中，$\forall b\in B$ 都 $\exists a\in A$ 使得 $f(a)=b$，則 $f$ 被稱為**映成(onto)** 或**蓋射(surjective)**。

> [!note]
> $|A|<|B|$ 時，函數不可能 onto。

例如：$f:\mathbb{Z}^{+}\to S=\{ \text{偶正整數} \}$ 且 $f(x)=2x$，則 $f$ 為映成函數。

因為，對任意 $s\in S$，$s$ 為偶正整數，則 $\frac{s}{2}$ 為正整數。

取 $x=\frac{s}{2}$，有 $f(x)=s\quad\forall s\in S$。

若一個函數同時是映成與一對一函數，則稱其為**雙射(bijection)**。

我們統整一波：

| 1-1              | onto             | bijection     |
| ---------------- | ---------------- | ------------- |
| $\|A\|\leq\|B\|$ | $\|A\|\geq\|B\|$ | $\|A\|=\|B\|$ |

## Compositions of Functions

**若有 $f:A\to B$ 與 $g:C\to A$，則 $f\circ g:C\to B$。**

讓我們試證兩個東西。

若 $f$ 與 $f\circ g$ 都是一對一函數，則 $g$ 是否為一對一函數？

proof:
我們很難從 $f$ 出發，考慮從 $g$ 出發。
設 $g(x)=g(y)$。
因為 $f$ 是一對一函數，所以有 $f(g(x))=f(g(y))$。
因為 $f\circ g$ 是一對一函數，有 $x=y$。
所以，$g$ 是一對一函數。

若 $f$ 與 $f\circ g$ 都是映成函數，則 $g$ 是否為映成函數？

proof:
反例：
$f:\{ -1,1 \}\to \{ 1 \},f(x)=x^{2}$ 
$g:\{ 1 \}\to \{ -1,1 \},g(x)=x$ 
注意， $g$ 的對應域不等於值域。
顯然 $f$ 是映成函數，而 $f\circ g:\{ 1 \}\to \{ 1 \}$ 也是映成函數。
所以此命題不成立。

> [!note]
> 回憶到 onto 是 $|A|\geq |B|$。
> 而 one-to-one 是 $|A|\leq |B|$。

# Inverse Funcitons

一個擁有反函數的函數 $f$，必定是一個一對一函數。並且，$f^{-1}(b)=a$ 與 $f(f^{-1}(x))=x$。

# Sequences and Summations

注意到，數列的通項公式可能會由 $n$ 從零或一開始而不同。

讓我們嘗試證明：$\sum_{k=1}^{n}k^{2}= \frac{n(n+1)(2n+1)}{6}$。

proof:
我們使用歸納法。
當 $k=1$ 時，$\frac{1(2)(3)}{6}=1$ 正確。
假設當 $k=n$ 時命題正確。
當 $k=n+1$ 時，$\sum_{i=1}^{n+1}i^{2}=\sum_{i=1}^{n}i^{2}+(n+1)^{2}= \frac{n(n+1)(2n+1)}{6}+(n^{2}+2n+1)$ 
$= \frac{(n+1)(n+2)(2(n+1)+1)}{6}$ 命題正確。

# Cardinality

$A$ 與 $B$ 集合擁有相同的基數 $\iff$ 兩集合間存在一個函數 $f$ 使得**兩集合一對一對應**。(1-1 與 onto，即雙射 bijection)

我們記為：

$$
|A|=|B|
$$

## Exercise

讓我們來數數吧！問：$\mathbb{N}=\{ 0,1,2,\dots \}$ 和 $\{ 3n|n\in \mathbb{N} \}$，兩集合哪個元素較多？

Sol:
令 $f:\mathbb{N}\to \{ 3n|n\in \mathbb{N} \}$ 為 $f(x)=3x$ 即可。
因為 $f$ 是一對一且映成函數，所以 $|\mathbb{N}|=|\{ 3n|n\in \mathbb{R} \}|$。

> [!note]
> 整數的基數與正整數的基數相同。

## Countable

當一個集合有限，或基數與 $\mathbb{Z}^{+}$ 或 $\mathbb{N}$ 相同，則此集合**可數(countable)**。

> [!note]
> 一個集合是有限，則此集合元素有限，或可以找到一個方法將元素排好，然後按照 $1,2,3,\dots$ 數。
> 能不能數完不影響是否可數，例如，整數是可數集合。

我們可以通過如下方法數整數：

| 數法    | 1   | 2   | 3   | 4   | 5   | ... |
| ----- | --- | --- | --- | --- | --- | --- |
| 整數的排法 | 0   | 1   | -1  | 2   | -2  | ... |

我們也可以嚴謹證明：

proof:
我們要證明 $\mathbb{Z}$ 可數，就是證明 $\mathbb{Z}$ 的基數與 $\mathbb{Z}^{+}$ 相同。
即，存在雙射函數 $f:\mathbb{Z}\to \mathbb{Z}^{+}$。
令 $f(x)=\begin{cases}2x & \text{if }x\in \{ 1,2,3,\dots \} \\ |2x|+1 & \text{if }x\in \{ 0,-1,-2,\dots \}\end{cases}$。
那麼，$f:\mathbb{Z}\to \mathbb{Z}^{+}$ 為雙射函數。
所以，整數集合是可數集合。

## Exercise

證明正奇數是可數集合。

proof:
$f:\mathbb{Z}^{+}\to \{ \text{positive odd intergers} \}$ 
令 $f(x)=2x-1$，則 $f$ 為雙射函數。
所以正奇數是可數集合。

> [!note]
> 注意到，雙射是雙向的，所以可以從 $\mathbb{Z}^{+}$ 出發，也可以從 $\{ \text{positive odd intergers} \}$ 出發。

## Schroder-Bernstein Theorem

在證明兩集合相等時，找出雙射函數有時並不容易。我們使用 Schroder-Bernstein Theorem，來回找一個一對一函數即可。

Schroder-Bernstein Theorem 是這樣描述的：若 $|A|\leq|B|$ 且 $|B|\leq|A|$，則 $|A|=|B|$。也就是說，若存在一對一函數 $f$ 將 $A$ 映射到 $B$，且存在一對一函數 $g$ 將 $B$ 映射到 $A$，則 $A$ 與 $B$ 一一對應。

## Hilbert's Paradox

Hilbert's infinite hotel 擁有無限多個房間，且每個房間都滿人。

此時，分三種情況：
- 有一位客人要入住：將所有客人向後移動一位房間號，這樣 $1$ 號房間空出，那位客人可以注入。即，$\infty+1=\infty$。
- 有 $\infty$ 位可數客人要入住：若此時來了 $\infty$ 位**可數** (注意，此條件必須) 客人，只需要將所有客人移動到房號 $\times2$ 的房間，就空出了正奇數個房間。因為正奇數有無窮多個，所以剛好夠 $\infty$ 個可數客人入住。即，$\infty+\infty=\infty$。
- 有 $\infty$ 組 $\infty$ 位客人入住：注意到**質因數分解結果唯一**，我們將原本住在酒店中的旅客稱為第 $0$ 團。只需將第 $n$ 團第 $k$ 位客人安排在 $2^{n}3^{k}$ 號房間，就可使每人都有房間可住。即，$\infty+\infty+\dots=\infty$。

> [!note]
> 有限與無限集合的情況可能完全相反。
> 例如：$|\{ 1,2,3,\dots,100 \}|>|\{ 2,4,6,\dots,100 \}|$，但 $|\mathbb{Z}|=|\mathbb{Z}^{+}|$。

