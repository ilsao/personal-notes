# The Basics of Counting

- 乘法原理

設事件 $A$ 有 $n_{1}$ 種選取方式，$B$ 有 $n_{2}$ 種選取方式。則選取 $A$ 後再選 $B$ 共有 $n_{1}n_{2}$ 種選法。

用集合論說：

設 $A$ 與 $B$ 為兩有限集合，其中 $|A|=n_{1},|B|=n_{2}$。則 $A\times B$ (笛卡爾積) 的個數為：

$$
|A\times B|=|A|\times|B|=n_{1}n_{2}
$$

proof:
若 $n_{1}=0$ 或 $n_{2}=0$ 則等式兩邊均為 $0$，等式成立。
設 $n_{1}>0$ 且 $n_{2}>0$，記 $A=\{ x_{1},x_{2},\dots,x_{n_{1}} \}$ 與 $B=\{ y_{1},y_{2},\dots,y_{n_{2}} \}$。
定義映射：$f:(a_{i},b_{j})\to(i-1)n+j$ 其中 $1\leq i\leq n_{1}$，$1\leq j\leq n_{2}$。
所以 $f$ 是 $A\times B$ 到集合 $\{ 1,2,\dots,n_{1}n_{2} \}$ 的一一映射，等式成立。

![[Pasted image 20260409162852.png|664]]

![[Pasted image 20260409162304.png|652]]



- 加法原理

若任務 $A$ 有 $n_{1}$ 種方式完成，$B$ 有 $n_{2}$ 種，且此二任務不能同時完成，則**只完成其中一個任務**的方式有 $n_{1}+n_{2}$ 種。

用集合論說：

設 $A,B$ 為有限集且 $A\cap B=\phi$，則 $|A\cap B|=|A|+|B|$。 

proof:
若 $A$ 或 $B$ 中有一個為空集，定理顯然成立。
設 $A\neq \phi$ 且 $B\neq \phi$，記 $A=\{ a_{1},a_{2},\dots a_{n_{1}} \}$ $B=\{ b_{1},b_{2},\dots,b_{n_{2}} \}$。
定義映射：$f(x)=\begin{cases}i & \text{if }x=a_{i} \\ n_{1}+j & \text{if }x=b_{j}\end{cases}$ 
因爲 $A\cap B=\phi$，所以 $a_{i}\neq b_{j}$。
因此 $f$ 是 $A\cup B$ 到集合 $1,2,\dots,n_{1}+n_{2}$ 的一一映射，定理成立。

於是：若 $S_{i}\cap S_{j}=\phi\ (1\leq i\neq j\leq n)$ 則 $|\bigcup_{i=1}^{n}S_{i}|=\sum_{i=1}^{n}|S_{i}|$。

![[Pasted image 20260409164653.png|696]]

![[Pasted image 20260409164827.png|680]]

# Inclusion-Exclusion Principle

減法原則、**排容原理(Inclusion-Exclusion Principle)** 本質上是間接的計數方法。

若任務 $A$ 有 $n_{1}$ 種方式完成，$B$ 有 $n_{2}$ 種，則完成任務的方式為 $n_{1}+n_{2}$ 減去 $A$ 與 $B$ 方法相同的部分。

用集合論描述：

設 $A$ 為有限集合 $S$ 的子集，則：$|A|=|S|-|\bar{A}|$。

![[Pasted image 20260409165920.png|704]]

Theorem：設 $S$ 為有限集，$P_{1},P_{2},\dots ,P_{m}$ 是與 $S$ 有關的 $m$ 個性質。設 $A_{i}$ 為 $S$ 中有 $P_{i}$ 性質的元素所構成的集合，則 $S$ 中不具 $P_{i}$ 性質的元素個數為：

$$
\begin{align}
 & |\overline{ A_{1} }\cap \overline{ A_{2} }\cap\dots \cap \overline{ A_{m} }| \\
 = & |S|-\sum_{i=1}^{m} |A_{i}|+\sum_{\{ 1,2,\dots,m \}\text{ 的 2 組合}}|A_{i}\cap A_{j}|-\sum_{\{ 1,2,\dots,m \}\text{ 的 3 組合}}|A_{i}\cap A_{j}\cap A_{k}|+\dots+(-1)^{m}|A_{1}\cap A_{2}\cap\dots \cap A_{m}|
\end{align}
$$

proof:
歸納法

![[Pasted image 20260409171931.png|639]]
![[Pasted image 20260409171954.png|618]]

![[Pasted image 20260409172709.png|630]]
![[Pasted image 20260409172723.png|638]]

之所以說排除了 $2,3,5,7$ 這四個質數，是因為 $2,3,5,7$  會被自己整除，被算成合數減掉了。

![[Pasted image 20260409173359.png|721]]

Sol:
(1)
$|\overline{ A_{1} }\cap \overline{ A_{2} }\cap \overline{ A_{3} }|=12-(8+6+5)+(5+4+3)-3=2$ 
(2)
$(|A_{1}|-(|A_{1}\cap A_{2}|+|A_{1}\cap A_{3}|)+|A_{1}\cap A_{2}\cap A_{3}|)+(\dots)+(\dots)$ 
$=|A_{1}|+|A_{2}|+|A_{3}|-2(|A_{1}\cap A_{2}|+|A_{1}\cap A_{3}|+|A_{2}\cap A_{3}|)+3|A_{1}\cap A_{2}\cap A_{3}|$ 
$=4$ 
(3)
$(|A_{1}\cap A_{2}|+|A_{2}\cap A_{3}|+|A_{1}\cap A_{3}|)-3|A_{1}\cap A_{2}\cap A_{3}|$ 
$=3$ 

# The Pigeonhole Principle

鴿籠原理：如果能把 $k+1$ 或更多的物體放入 $k$ 個盒子，則至少有一個盒子中有兩個或更多的物體。

proof:
設沒有任何盒子裝兩個 (含) 以上的物體，則每個盒子至多裝一個物體。
那麼 $k$ 個盒子的物體加總最多只有 $k$ 個物體。
與總數 $k+1$ 或更多矛盾。

![[Pasted image 20260428211818.png|587]]

![[Pasted image 20260428212126.png|594]]

![[Pasted image 20260428212447.png|666]]

Sol:
先證明：兩個連續整數互質。
***
proof:
設兩個連續整數不互質，即存在 $d>1$ 使得：$d\mid n$ 且 $d\mid (n+1)$ 
$\implies d\mid(n+1-n)=d\mid 1$ 
只可能在 $d=1$ 時存在，與 $d>1$ 矛盾。
所以兩個連續整數互質。
***
我們將 $\{ 1,2,3,\dots,2n \}$ 兩兩分組，則每組的兩數互質，共有 $n$ 組。
因為 $n+1>n$，所以根據鴿籠原理，必定有一組的兩個數都被取到
$\implies$ 必定有兩數互質

![[Pasted image 20260428213428.png|792]]

Sol:
將 $1$ 到 $2n$ 的正整數用 $2$ 的冪次方 $\times$ 奇數表示，即 $a_{i}=q2^{k}$ 其中 $q$ 為奇數，$k\geq 0$。
將所有表示後奇數相同者分到同一組，則每組中的任一對數字總有一個為另一個的倍數。
因為 $1\sim2n$ 間的奇數有 $n$ 個 ($n$ 組)，但取 $n+1$ 個數字。
由鴿籠原理，必有兩個數字從同一個組中取出 $\implies$ 必有兩個數字，其中一個是另一個的倍數。

**廣義鴿籠原理(The Generalized Pigeonhole Principle)**：若把 $N$ 個物體放入 $k$ 個盒子，則至少一個盒子中有最少 $\left\lceil  \frac{N}{k}  \right\rceil$ 或更多的物體。

proof:
假設沒有盒子有比 $\left\lceil  \frac{N}{k}  \right\rceil-1$ 更多的物體。
注：$\left\lceil  \frac{N}{k}  \right\rceil< \frac{N}{k}+1$ 
則 $k\times\left( \left\lceil  \frac{N}{k}  \right\rceil-1 \right)<k\times\left( \left( \frac{N}{k}+1 \right)-1 \right)=N$ 
與前提矛盾。

![[Pasted image 20260428215340.png|611]]

![[Pasted image 20260428215354.png|600]]

> [!note]
> $0\sim 100$ 共有 $101$ 個數字。

![[Pasted image 20260428215505.png|731]]

Sol:
將 $8$ 個數按頭尾依序分組，$\{ 1,8 \},\{ 2,7 \},\{ 3,6 \},\{ 4,5 \}$，共四組每組兩數相加都等於 $9$。
由鴿籠原理，某組一定兩個數都被選到
$\implies$ 一定有兩個整數的和等於 $9$ 

## Ramsey Number

![[Pasted image 20260428220619.png|915]]

Sol:
假設 ABCDEF 為六個人。
將 BCDEF 分為認識 A 與不認識 A 兩類。
則至少有一類有 $\left\lceil  \frac{5}{2}  \right\rceil=3$ 人。
- 有 $3$ 人以上認識 $A$ 
	- 假設 BCD 認識 A
	- 若 BCD 有任意兩人互相認識，再加上 A 就有三人彼此認識
	- 若 BCD 三人沒人認識，此情況本身就是答案
- 有 $3$ 人以上不認識 $A$ 
	- 假設 BCD 不認識 A
	- 若 BCD 有任意兩人互相不認識，再加上 A 就有三人互相不認識
	- 若 BCD 三人全相認，此情況本身就是答案

Ramsey Number：最小的數 $k$，使得 $k$ 人中必定有 $m$ 人相識或 $n$ 人不相識。$k=R(m,n)$ 

$R(3,3)=6$ 
$R(2,n)=n$ (思考一下)
$R(m,n)=R(n,m)$ 

![[Pasted image 20260428221820.png|646]]

# Permutations and Combinations

## Permutation

排列：將集合中不同元素按順序安排

$r$-排列：從集合中取出 $r$ 個物體

![[Pasted image 20260429102046.png|652]]

![[Pasted image 20260429102622.png|623]]

Sol:
(2)
之前錯誤的解法：
$4!\times C(5,2)$ 先排好剩下 $4$ 個，然後插入空隙。但這種做法會漏算 c, e 相鄰的排列。
正確：
$4!\times C(6,2)$ 總共六個字母的位置，先選出兩個位置，剩餘亂排。
![[Pasted image 20260429102919.png|587]]

![[Pasted image 20260429103356.png|806]]

![[Pasted image 20260429103411.png|685]]
![[Pasted image 20260429103433.png|666]]

## 集合的圓排列

考慮 RWLGY 的圓排列，即向右或向左位移 $n$ 步仍屬於同個圓排列。

![[Pasted image 20260429104012.png|319]]

即：
![[Pasted image 20260429104120.png|613]]

於是圓排列數為：$\frac{5!}{5}=4!$ 種

考慮一個 $r$ 圓排列，假設我們從每個元素間將圓形剪開拉直，可以得到 $r$ 種不同的線排列，但同屬一個圓排列。

於是 $n$ 元集合的 $r$ 圓排列數為：

$$
\frac{P(n,r)}{r}=\frac{n!}{r(n-r)!}
$$

## Combination

![[Pasted image 20260429105742.png|699]]

![[Pasted image 20260429110027.png|666]]

![[Pasted image 20260429110104.png|384]]

# Binomial Coefficients and Identities

設 $n$ 為正整數，則對任意 $x$ 與 $y$，有：

$$
\begin{align}
(x+y)^{n} & = \binom{n}{0}x^{n}+\binom{n}{1}x^{n-1}y+\dots+\binom{n}{n}y^{n} \\
 & =\sum_{i=0}^{n} \binom{n}{i}x^{n-i}y^{i}
\end{align}
$$

proof:
將 $(x+y)^{n}$ 展開：$(x+y)(x+y)\dots(x+y)$ 
展開後，每項會從每個括號中選取 $x$ 或 $y$。
假設選了 $i$ 個 $y$，那麼剩下就會是 $n-i$ 個 $x$，且此項為 $x^{n-i}y^{i}$。
此項係數為：$\binom{n}{i}$ 因為從 $n$ 個括號中選 $i$ 個出來，貢獻 $y$。
於是，展開每項就變為：$(x+y)^{n}=\sum_{i=0}^{n}\binom{n}{i}x^{n-i}y^{i}$ 

對任意正整數 $n$，有：

$$
\binom{n}{0} + \binom{n}{1}+\dots+\binom{n}{n}=2^{n}
$$

proof:
(I)
令 $x=y=1$ 套用二項式定理 $(1+1)^{n}=2^{n}$ 展開即可。
(II)
考慮一個 $n$ 元集合 $S$，則其 $r$ 元子集數為 $\binom{n}{r}$。其中 $r=0,1,\dots,n$。
所以 $S$ 的所有子集合數為：$\binom{n}{0} + \binom{n}{1}+\dots+\binom{n}{n}$ 
我們又知 $S$ 的所有子集合數可考慮為，每個元素在某子集或不在：$2^{n}$ 
於是 $\binom{n}{0} + \binom{n}{1}+\dots+\binom{n}{n}=2^{n}$ 

![[Pasted image 20260429111605.png|626]]

![[Pasted image 20260429112406.png|688]]
![[Pasted image 20260429112432.png|280]]
![[Pasted image 20260429112446.png|503]]

## Pascal's Identity

Pascal's Identity：

$$
\binom{n+1}{k}=\binom{n}{k}+\binom{n}{k-1}
$$

proof:
(I)
![[Pasted image 20260429195214.png|500]]
(II)
$\binom{n+1}{k}$ 是 $n+1$ 元集合 $T$ 的 $k$ 組合數。
考慮 $S=T-\{ a \}$ 與 $\{ a \}$，這兩個集合組成了集合 $T$。
考慮 $S$ (為 $n$ 元集合) 的 $k$ 組合數 $\binom{n}{k}$，這代表了 $T$ 所有不包含 $a$ 的 $k$ 組合數。
考慮 $S$ 的 $k-1$ 組合數 $\binom{n}{k-1}$ 並加上 $a$，這代表了 $T$ 所有包含 $a$ 的 $k$ 組合數。
所以 $\binom{n+1}{k}=\binom{n}{k}+\binom{n}{k-1}$ 成立。

![[Pasted image 20260429215100.png|700]]

## Vandermode's Identity

Vandermode's Identity：

$$
\binom{m+n}{r}=\sum_{i=0}^{r} \binom{m}{i}\binom{n}{r-i}
$$

proof:
![[Pasted image 20260429215856.png|647]]

![[Pasted image 20260429220014.png|607]]

Sol:
(I)
共 $m+n$ 個位置，選 $m$ 個出來向上走，剩餘向右走。
$\binom{m+n}{m}$ 
(II)
共 $m+n$ 個操作，$m$ 個相同的向上操作，$n$ 個相同的向右操作。
$\frac{(m+{n})!}{m!n!}$ 

綜合恆等式：

$$
\binom{0}{k}+\binom{1}{k}+\dots+\binom{n}{k}=\binom{n+1}{k+1}
$$

proof:
$\binom{n+1}{k+1}$ 視為 $n+1$ 元子集合 $S=\{ a_{1},a_{2},\dots,a_{n+1} \}$ 的 $k+1$ 元子集合。
$k+1$ 元子集合可以被如下討論：
- 含 $a_{1}$：相當於 $S-\{ a_{1} \}$ 的 $n$ 元集合選 $k$ 個，再與 $a_{1}$ 配。有 $\binom{n}{k}$ 個。
- 不含 $a_{1}$，但含 $a_{2}$：共 $\binom{n-1}{k}$ 個。
- $\dots$ 
- 不含 $a_{1},a_{2},\dots,a_{n}$，但含 $a_{n+1}$ ：共 $\binom{0}{k}$ 個。
於是：$\binom{0}{k}+\binom{1}{k}+\dots+\binom{n}{k}=\binom{n+1}{k+1}$。

> [!note]
> 這個證明不會漏算或重複算，因為所有包含 $a_{1}$ 都在第一類被討論過了。而第二種情況也屏蔽了第一種情況時 $a_{1},a_{2}$ 同時出現的可能。

# Generalized  Permutations and Combination

![[Pasted image 20260429222826.png|743]]

![[Pasted image 20260429222432.png|746]]

Sol:
因為有三個種類的水果，考慮兩根豎線，分隔出 蘋果 | 橘子 | 桃子
所以，總共的組合數為：$C(5,3)$ 

對於 $n$ 個元素的集合允許重複取用的 $r$ 組合數為：

$$
C(n+r-1,r)
$$

![[Pasted image 20260429222810.png|706]]

![[Pasted image 20260429223125.png|697]]

