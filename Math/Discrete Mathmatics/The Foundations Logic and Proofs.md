# Propositions

一個**命題(proposition)** 即一個**非對即錯**的語句。我們使用字母當作**命題變量(propositional variables)**，也就是將某命題用某字母表示。

無法被更簡單的命題表示的命題稱為**原子命題(atomic propositions)**。

以下是常用的邏輯運算符號：
- 非 $p$：$\neg p$ 或 $\bar{p}$。
- $p$ 或 $q$：$p \lor q$。
- $p$ 且 $q$：$p\land q$。
- $p$ 異或 $q$：$p\oplus q$。

# Conditional Statement

**條件命題(conditional statement)** 即 $p\to q$ 命題：

| $p$ | $q$ | $p\to q$ |
| --- | --- | -------- |
| T   | T   | T        |
| T   | F   | F        |
| F   | T   | T        |
| F   | F   | T        |

在此，我們將 $p\to q$ 稱為**假設(hypothesis)**，而將 $q$ 稱為**結論(conclusion)**。

並且我們需要注意一個重要結論：

$$
p\to q\iff \neg q\to \neg p
$$

> [!warning] 注意
> $p$ 與 $q$ 方向對調。

proof:
偷使用後面的恆等式：$p\to q\equiv \neg p\lor q$。
那麼有：$\neg q\to \neg p\equiv \neg(\neg q)\lor \neg p\equiv q\lor \neg p$。
利用邏輯或的交換律，二者相等。

我們使用 $\leftrightarrow$ 表示**雙蘊含(biconditional)**：

$$
p\leftrightarrow q\equiv(p\to q)\land(q\to p)
$$

> [!warning] 注意
> $p\leftrightarrow q$ 僅當 $p$ 與 $q$ 真值相等時為真。

## Exercise

![[Math/Discrete Mathmatics/pic/Logic and Proofs/1.png]]

(a)

| $p$ | $q$ | $p\lor q$ | $p\oplus q$ | $(p\lor q)\to(p\oplus q)$ |
| --- | --- | --------- | ----------- | ------------------------- |
| T   | T   | T         | F           | F                         |
| T   | F   | T         | T           | T                         |
| F   | T   | T         | T           | T                         |
| F   | F   | F         | F           | T                         |

(d)

| $p$ | $q$ | $\neg p$ | $p\leftrightarrow q$ | $\neg p\leftrightarrow q$ | $(p\leftrightarrow q)\oplus(\neg p\leftrightarrow q)$ |
| --- | --- | -------- | -------------------- | ------------------------- | ----------------------------------------------------- |
| T   | T   | F        | T                    | F                         | T                                                     |
| T   | F   | F        | F                    | T                         | T                                                     |
| F   | T   | T        | F                    | T                         | T                                                     |
| F   | F   | T        | T                    | F                         | T                                                     |

(e)

| $p$ | $q$ | $r$ | $p\to q$ | $(p\to q)\land r$ |
| --- | --- | --- | -------- | ----------------- |
| T   | T   | T   | T        | T                 |
| T   | T   | F   | T        | F                 |
| T   | F   | T   | F        | F                 |
| T   | F   | F   | F        | F                 |
| F   | T   | T   | T        | T                 |
| F   | T   | F   | T        | F                 |
| F   | F   | T   | T        | T                 |
| F   | F   | F   | T        | F                 |

# Consistent

若一個由多個命題組成的命題，存在一組 (包含以上) 真值使得命題中所有子命題皆為真，則該命題稱為 consistent。

例如：
- $p\land \neg q$ 
- $q\oplus r$ 
- $p\to r$ 
令 $p\equiv T \ q\equiv F \ r\equiv T$，則所有子命題成立，所以命題 consistent。

> [!warning] 注意
> 考試讓判斷 consistent，需要找出符合的一組解，而不是直接寫成判斷題。

## Exercise

![[Math/Discrete Mathmatics/pic/Logic and Proofs/2.png]] 
並令
![[Math/Discrete Mathmatics/pic/Logic and Proofs/3.png]]

按照題意，我們有：
- $p\to q$ 
- $\neg(q\land r)\equiv \neg q\lor \neg r$  
- $\neg(\neg r\land \neg s)\equiv r\lor s$ 
- $s\to \neg q$ 

令 $p$ 為 T，則 $q$ 為 T。此時 $r$ 必為 F，$s$ 必為 T。
若 $s$ 為 T，則 $q$ 為 F，產生矛盾。
所以令 $p$ 為 F，則 $q$ 可能為 T 或 F。
上面當 $q$ 為 T 會產生矛盾，令 $q$ 為 F，則 $r$ 可為 T 或 F。
若 $r$ 為 T，則 $s$ 可為 T 或 F。否則，$s$ 為 T。
當 $s$ 為 T，$q$ 為 F 成立，若 $s$ 為 F，$q$ 可為 T 或 F。
所以解為：$(p,q,s,r)=(F,F,T,T),(F,F,T,F),(F,F,F,T)$。

# Propositional Equivalences

一個恆真的複合命題稱為**真理(tautology)**，相反，一個恆假的複合命題稱為**矛盾(contradiction)**。

讓我們試著使用真值表證明以下命題為 tautology：$\neg p\to(p\to q)$。

| $p$ | $\neg p$ | $q$ | $p\to q$ | $\neg p\to(p\to q)$ |
| --- | -------- | --- | -------- | ------------------- |
| T   | F        | T   | T        | T                   |
| T   | F        | F   | F        | T                   |
| F   | T        | T   | T        | T                   |
| F   | T        | F   | T        | T                   |

若兩復合命題的真值表結果相同，則二復合命題等價，並使用符號 $\iff$ 表示。

> [!error] 小心
> $\leftrightarrow$ 與 $\iff$ 存在差異。$p\to q\iff \neg q\to \neg p$ 表示宣稱兩命題等價，也就是說 $p\to q\leftrightarrow \neg q\to \neg p$ 是 tautology。
> 我們需要驗證 $\iff$ 的宣稱是否正確，通常使用真值表等方法證明。

> [!note] 
> 回憶到，$\leftrightarrow$ 表示雙蘊含 (biconditional)，僅當 $p$ 與 $q$ 真值相等時為真。

若 $p$ 與 $q$ 在所有情況下真值皆相同，則稱二命題邏輯等價。使用 $p\equiv q$ 或 $p \iff q$ 表示。

## Exercise

試證 $\neg(p\leftrightarrow q)$ 與 $p\leftrightarrow \neg q$ 在邏輯上等價：

| $p$ | $q$ | $p\leftrightarrow q$ | $\neg(p\leftrightarrow q)$ | $p\leftrightarrow \neg q$ |
| --- | --- | -------------------- | -------------------------- | ------------------------- |
| T   | T   | T                    | F                          | F                         |
| T   | F   | F                    | T                          | T                         |
| F   | T   | F                    | T                          | T                         |
| F   | F   | T                    | F                          | F                         |

Show that $p\lor(q\land r)\equiv(p\lor q)\land(p\lor r)$：

| $p$ | $q$ | $r$ | $q\land r$ | $p\lor q$ | $p\lor r$ | $p\lor(q\land r)$ | $(p\lor q)\land(p\lor r)$ |
| --- | --- | --- | ---------- | --------- | --------- | ----------------- | ------------------------- |
| T   | T   | T   | T          | T         | T         | T                 | T                         |
| T   | T   | F   | F          | T         | T         | T                 | T                         |
| T   | F   | T   | F          | T         | T         | T                 | T                         |
| T   | F   | F   | F          | T         | T         | T                 | T                         |
| F   | T   | T   | T          | T         | T         | T                 | T                         |
| F   | T   | F   | F          | T         | F         | F                 | F                         |
| F   | F   | T   | F          | F         | T         | F                 | F                         |
| F   | F   | F   | F          | F         | F         | F                 | F                         |

## Important Logically Equivalences

- Commutative laws 交換律
	- $p\lor q\equiv q\lor p$ 
	- $p\land q\equiv q\land p$ 
- Associative laws 結合律
	- $(p\lor q)\lor r\equiv p\lor(q\lor r)$ 
	- $(p\land q)\land r\equiv p\land(q\land r)$ 
- Distributive laws 分配律
	- $p\lor(q\land r)\equiv(p\lor q)\land(p\lor r)$ 
	- $p\land(q\lor r)\equiv(p\land q)\lor(p\land r)$ 
- De Morgan's laws 笛摩根定律
	- $\neg(p\land q)\equiv \neg p\lor \neg q$ 
	- $\neg(p\lor q)\equiv \neg p\land \neg q$ 
- Others
	- $p\land \neg p=F$ 
	- $p\lor \neg p=T$ 
	- $p\to q\equiv \neg q\to \neg p\equiv \neg p\lor q$ *

## Exercise

證明以下命題為恆真句：
1. $(p\land q)\to p$ 
2. $p\to(p\lor q)$ 

1.
$\equiv\neg(p\land q)\lor p\equiv(\neg p\lor \neg q)\lor p\equiv(p\lor \neg p)\lor \neg q\equiv T\lor \neg q=T$ 

2.
$\equiv \neg p\lor(p\lor q)\equiv T\lor q\equiv T$ 

# Predicates and Quantifiers

**命題函數(propositional function)** 是含有變量的陳述句，只有當變量帶入函數時，才會成為命題。

例如：$P(x):x>3$ 是一個命題函數，但因為不知 $x$ 的值，所以無法判斷對錯。而 $P(5)>3$ 為真，而 $P(1)<3$ 為假。

其中，變量是 $x$，predicate 是 "is greater than 3"。

**量詞(quantifiers)** 用來限定變量的定義域：
- $\forall$：universal quantifiers
- $\exists$：existential quantifiers

| 敘述                 | 為真                   | 為假                   |
| ------------------ | -------------------- | -------------------- |
| $\forall x\ P(x)$  | 所有 $x$ 都使得 $P(x)$ 為真 | 存在一個 $x$ 使 $P(x)$ 為假 |
| $\exists x \ P(x)$ | 存在一個 $x$ 使 $P(x)$ 為假 | 所有 $x$ 都使得 $P(x)$ 為假 |

## Exercise

![[Math/Discrete Mathmatics/pic/Logic and Proofs/4.png]]
$(a,b,c,d,e,f)=(T,T,F,F,T,F)$ 

![[Math/Discrete Mathmatics/pic/Logic and Proofs/5.png]]

$(a,b,c,d)=(T,T,T,T)$ 

![[Math/Discrete Mathmatics/pic/Logic and Proofs/6.png]]

$(a,b,c,d)=(T,F,T,F)$ 

## Negate Quantified Expression

| 否定句                    | 等價命題                   | 為真                   | 為假                   |
| ---------------------- | ---------------------- | -------------------- | -------------------- |
| $\neg \exists x\ P(x)$ | $\forall x\ \neg P(x)$ | 對所有 $x$，$P(x)$ 皆為假   | 存在某 $x$ 使得 $P(x)$ 為真 |
| $\neg \forall x\ P(x)$ | $\exists x\ \neg P(x)$ | 存在某 $x$ 使得 $P(x)$ 為假 | 對所有 $x$，$P(x)$ 皆為真   |

我們使用 $\exists!$ 表示**存在且唯一**，$\exists!x \ P(x)$ 表示存在唯一的 $x$ 使得 $P(x)$ 為真。

# Nested Quantifiers

我們使用**群組量詞(nested quantifiers)** 表示套嵌的量詞。

例如：$\forall x\ \exists y \ (x+y=0)\text{ where }x,y\in \mathbb{R}$。我們從左向右解析，即對所有的 $x$ 都存在對應的 $y$ 使得 $x+y=0$。

> [!warning] 注意
> 群組量詞的順序很重要，順序相反可能導致不同的結果。

## Exercise

![[Math/Discrete Mathmatics/pic/Logic and Proofs/7.png]]

$(a,b,c,d,e,f,g,h,i) = (T,T,T,T,T,F,F,T,F)$ 

# Proof Methods and Strategy

一般來說，我們有五種證明方法：
- 窮舉法
- 直接證明法
- 反證法(逆否命題，contrapositive proof)
- 間接證明(矛盾法，proof by contradiction)
- 數學歸納法

直接證明法 ($P\to Q$)：用已知假設 $P$，然後通過已知定理、定義逐步推進，最後推得 $Q$。

反證法 ($\neg Q\to \neg P$)：將原命題改寫，使用 $\neg Q$ 出發逐步推得 $\neg P$。

間接證明 ($P\land \neg Q\to \perp$)：維持原命題 $P$，並額外假設 $\neg Q$，逐步證明與某個已知事實矛盾。

> [!note]
> 注意區分反證法與矛盾法！

我們使用不同方法證給你看以下題目：

證明若 $a$ 與 $b$ 都是整數，且 $a+b$ 為奇數，則 $a$ 與 $b$ 一奇一偶。

直接證明法：
已知 $a+b$ 為奇數，令 $a+b=2k+1$ 其中 $k$ 是整數。
假設 $a=2m$ 是偶數，則 $b=2k-2m+1=2(k-m)+1$ 是奇數。
假設 $a=2m+1$ 是奇數，則 $b=2k-2m=2(k-m)$ 是偶數。

反證法：
假設 $a$ 與 $b$ 不是一奇一偶。
兩數皆為偶數：$2m+2k=2(m+k)$ 為偶數。
兩數皆為奇數：$2m+1+2k+1=2(m+k+1)$ 為偶數。
所以兩數不是一奇一偶，則和必為偶數。$(\neg Q\to \neg P)$ 

矛盾法：
假設 $a+b$ 為奇數且 $a$ 與 $b$ 不是一奇一偶。
兩數皆為偶數，則 $a+b=2k+2m=2(k+m)$ 為偶數，與 $a+b$ 是奇數矛盾。
兩數皆為奇數，則 $a+b=2k+2m+2=2(k+m+1)$ 為偶數，與 $a+b$ 是奇數矛盾。

數學歸納法有兩種：

第一數學歸納法：
1. 歸納基礎：證明當 $n$ 取第一個值 $n_{0}$ 時命題成立。 
2. 歸納假設：假設當 $\boxed{n=k}$ ($k$ 為大於等於 $n_{0}$ 的自然數) 時 $P(n)$ 成立。
3. 歸納遞推：證明 $P(k+1)$ 成立。

第二數學歸納法：
1. 歸納基礎：證明當 $n$ 取第一個值 $n_{0}$ 時命題成立。 
2. 歸納假設：假設對所有 $\boxed{n\leq k}$ ($k$ 為大於等於 $n_{0}$ 的自然數) 時 $P(n)$ 成立。
3. 歸納遞推：證明 $P(k+1)$ 成立。

讓我們來試試看：假設我們有 2 元與 5 元的硬幣，是否可以用這兩種硬幣喚出任意大於 7 元的硬幣。

1. 歸納基礎：
	- $n=7$：$7=2+5$ 
	- $n=8$：$8=2+2+2+2$ 
2. 歸納假設：假設對所有 $7\leq n<k$ 且 $k\geq9$ 時成立。
3. 歸納遞推：當 $n=k$，有：$k=(k-2)+2$。因為 $7\leq k-2<k$，根據假設可以用 2 與 5 元硬幣組成，所以 $n=(k-2)+2$ 可以用 2 與 5 元硬幣組成。

## Exercise

使用數學歸納法證明對任意 $n\geq1$ 都有：

$$
1^{2}+2^{2}+\dots+n^{2}= \frac{n(n+1)(2n+1)}{6}
$$

proof:
當 $n=1$ 時，$\frac{1(2)(3)}{6}=1$ 成立。
假設當 $n=k$ 時命題成立。
則當 $n=k+1$ 時：
$1^{2}+\dots+k^{2}+(k+1)^{2}= \frac{k(k+1)(2k+1)}{6}+(k+1)^{2}=\frac{k(k+1)(2k+1)+6(k+1)^{2}}{6}$ 
$=\frac{(k+1)(k(2k+1)+6(k+1))}{6}=\frac{(k+1)(2k^{2}+7k+6)}{6}=\frac{(k+1)(k+2)(2k+3)}{6}=\frac{(k+1)((k+1)+1)(2(k+1)+1)}{6}$ 命題成立。
By M.I.