
數論：研究整數相關性質

# Divisibility and Modular Arithmetic

## Divides (整除)

**整除(divides)**：設 $a$ 與 $b$ 為整數且 $a\neq 0$。若存在整數 $c$ 使得 $b=ac$，則稱 $a$ 整除 $b$，記做 $a\mid b$。若 $a$ 不整除 $b$，則記做 $a\nmid b$。

我們稱 $a$ 為 $b$ 的**因子(factor)** 或**除數(divisor)**。

Theorem 1: 
1. 若 $a\mid b$ 且 $a\mid c$ 則 $a\mid (b+c)$ 
2. 若 $a\mid b$ 且 $c$ 為整數，則 $a\mid bc$ 
3. 若 $a\mid b$ 且 $b\mid c$，則 $a \mid c$ 

`/* 非常簡單可不看 */`
proof:
(1)
$a\mid b\implies$ 存在整數 $n_{1}$ 使 $b=n_{1}a$ 
$a\mid c\implies$ 存在整數 $n_{2}$ 使 $c=n_{2}a$ 
則 $b+c=n_{1}a+n_{2}a=(n_{1}+n_{2})a$，且 $n_{1}+n_{2}\in \mathbb{Z}$，所以 $a\mid (b+c)$。
(2)
$a\mid b\implies$ 存在整數 $n_{1}$ 使 $b=n_{1}a$ 
則 $bc=cn_{1}a=(cn_{1})a$，因為 $c\in \mathbb{Z}$ 所以 $cn_{1}\in \mathbb{Z}\implies a\mid bc$。
(3)
$a\mid b\implies$ 存在整數 $n_{1}$ 使 $b=n_{1}a$ 
$b\mid c\implies$ 存在整數 $n_{2}$ 使 $c=n_{2}b=n_{2}(n_{1}a)=(n_{2}n_{1})a$ 
由乘法封閉性，$n_{2}n_{1}\in \mathbb{Z}\implies a\mid c$。

Corollary：若 $a,b,c\in \mathbb{Z}$ 且 $a\neq 0$，其中 $a\mid b$ 且 $a\mid c$，則 $a\mid mb+nc$。其中，$m,n$ 為任意整數。

proof:
因為  $a\mid b$ 且 $a\mid c$，由 Theory 1 (2)，有 $a\mid mb$ 與 $a\mid nc$。
因為 $a\mid mb$ 與 $a\mid nc$，由 Theory 1 (1)，有 $a\mid mb+nc$。

Division Algorithm：若 $a$ 為整數且 $d$ 為**正**整數，則存在唯一的整數 $q$ 與 $r$，其中 $0\leq r<d$ 使得 $a=dq+r$。
- $d$ 稱為**除數(divisor)**。
- $a$ 稱為**被除數(dividend)**。
- $r$ 稱為**餘數(remainder)**。$r=a\text{ mod }d$ 
- $q$ 稱為**商(quotient)**。$q=a\text{ div }d$ 

> [!warning] 注意
> 注意範圍是 $0\leq r<d$ 而非 $0\leq r<q$。

## Congruence (同餘)

同餘：設 $a,b$ 為整數，$m$ 為正整數。以下描述等價：
- $m\mid a-b$ 
- $a$ 除以 $m$ 的餘數與 $b$ 除以 $m$ 的餘數相同
- $a$ 模 $m$ 同餘 $b$ 
- $m$ 整除 $a-b$ 
- $a\equiv b\ (\text{mod }m)$ 

試證 $m\mid a-b\iff a\equiv b\ (\text{mod }m)$ 

proof:
$(\implies)$ 
$m\mid a-b\implies \exists\ n\in \mathbb{Z}$ 使得 $a-b=nm$ 
設 $a=qm+r$ 其中 $q\in \mathbb{Z}$ 且 $0\leq r<m$，則 $a\text{ mod }m=r$。
$a-b=qm+r-b=nm\implies b=m(q-n)+r$ 
$\implies b\text{ mod m}=r$ 
$\implies a\equiv b\ (\text{mod }m)$ 

> [!error]
> 設 $a=qm+r_{1}$ 與 $b=pm+r_{2}$，其中 $q,p, r_{1},r_{2}\in \mathbb{Z}$ 且 $0\leq r_{1}<m$，$0\leq r_{2}<m$。
> $m\mid a-b\implies \exists\ n\in \mathbb{Z}$ 使得 $(a-b)=(qm+r_{1})-(pm+r_{2})=m(q-p)+(r_{1}-r_{2})=nm$ 
> $\implies r_{1}-r_{2}=0\implies r_{1}=r_{2}$ 
> $\implies a\equiv b\ (\text{mod }m)$ 
> 是錯誤的證明，因為無法從 $(a-b)=(qm+r_{1})-(pm+r_{2})=m(q-p)+(r_{1}-r_{2})=nm$  推得 $r_{1}-r_{2}=0$。

$(\impliedby)$ 
設 $a=qm+r_{1}$ 與 $b=pm+r_{2}$，其中 $q,p, r_{1},r_{2}\in \mathbb{Z}$ 且 $0\leq r_{1}<m$，$0\leq r_{2}<m$。
$a\equiv b\ (\text{mod }m)\implies r_{1}=r_{2}$ 
於是，$a-b=qm-pm=(q-p)m$ 
因為 $q,p\in \mathbb{Z}$，所以 $q-p\in \mathbb{Z}$。
$\implies m\mid a-b$ 

Theory：$a\equiv b\ (\text{mod }m)\iff a=b+km\quad k\in \mathbb{Z},m\in \mathbb{Z}^{+}$   

proof:
$(\implies)$ 
$a\equiv b\ (\text{mod }m)\implies a\text{ mod }m=b\text{ mod }m$ 
令 $a\text{ mod }m=b\text{ mod }m=r$ 其中 $0\leq r<m$，則 $\exists\ p,q\in \mathbb{Z}$ 使得 $a=pm+r,b=qm+r$ 
則 $r=a-pm=b-qm\implies a=b+(p-q)m$ 
取 $k=p-q$，得證。
$(\impliedby)$ 
設 $b=qm+r$，其中 $q,r\in \mathbb{Z}$ 且 $0\leq r<m$，則 $b\text{ mod }m=r$。
則 $a=b+km=qm+r+km=m(q+k)+r\implies a\text{ mod }m=r$ 
$\implies a\equiv b\ (\text{mod }m)$ 

Theorem：若 $a\equiv b\ (\text{mod }m)$ 與 $c\equiv d\ (\text{mod }m)$ 且 $m\in \mathbb{Z}^{+}$，則
1. $a+c\equiv b+d\ (\text{mod }m)$ 
2. $ac\equiv bd\ (\text{mod }m)$ 

證略。

由上個定理，可推：若 $a\equiv b\ (\text{mod }m)$ 且 $c\in \mathbb{Z}$，則：
- $a\pm c\equiv b\pm c\ (\text{mod }m)$ 
- $ac\equiv bc\ (\text{mod }m)$ 

> [!note] 
> 但是 $\frac{a}{c}$ 與 $\frac{b}{c}$ 不一定同餘。

Theorem：$a,b\in \mathbb{Z}$ 且 $m\in \mathbb{Z}^{+}$ 則：
- $(a+b)\text{ mod }m=((a\text{ mod }m)+(b\text{ mod }m))\text{ mod }m$ 
- $ab\text{ mod }m=((a\text{ mod }m)(b\text{ mod }m))\text{ mod }m$ 

proof:
![[Pasted image 20260331150253.png|585]]

# Arithmetic Modulo $m$ (模 $m$ 運算)

定義：
- 令 $\mathbb{Z}_{m}=\{ 0,1,2,\dots,m-1 \}$ 為所有小於 $m$ 的非負整數集合
- $a+_{m}b=(a+b)\text{ mod }m$ 
- $a\cdot_{m}b=(a\cdot b)\text{ mod }m$ 

模 $m$ 運算具有：
- 封閉性
- 結合律
- 交換律
- 分配律

證明結合律的思路：使用上一個定理展開兩運算並比對結果。

單位元：
- 加法單位元：$0$ 
- 乘法單位元：$1$ 

反元素：與某數運算後得到單位元。
- 加法反元素：
	- 若 $a\neq 0\in \mathbb{Z}_{m}$ 則反元素為 $m-a$。$a+_{m}(m-a)=0$ 
	- 若 $a=0$ 則反元素為 $0$。$0+_{m}0=0$ 

> [!note]
> 乘法反元素不一定存在，因為 $\mathbb{Z}_{m}$ 的要求是非負**整數**。
> 有些數必須乘以分數才會等於 $1$。

![[Pasted image 20260401205927.png|559]]

# Integer Representations and Algorithms

進制轉換參見數電 U1 [[Digital Systems and Binary Numbers#Binary Numbers]] 

將 10 進制數 $b$ 轉 $n$ 進制的偽代碼：

![[Pasted image 20260401210640.png]]

# Primes and Greatest Common Divisors (最大公因數)

Primes：只能被自身與 $1$ 整除的數。

**Composite(合數)**：所有非質數整數。

## The Fundamental Theorem of Arithmetic (算數基本定理)

Theorem：任意大於 $1$ 的整數都可以被唯一的表示為一個或多個質數乘積，其中質數因子以非遞減排列。

Ex: $13=13,100=2^{2}\times5^{2}$ 

Theorem：若 $n$ 為合數，則 $n$ 必有一個質因數 $a$，其中 $a\leq \sqrt{ n }$。

> [!note]
> 想檢驗某數是否為質數，只需檢測是否有除 $1$ 之外且 $\leq \sqrt{ n }$ 的數可整除它。

proof:
因為 $n$ 為合數，所以存在 $1<a\leq n$ 且 $a\in \mathbb{Z}$ 使得 $a\mid n$。
因此 $n=ab$ 且 $1<b< n$。
接下來我們證明 $\text{min}(a,b)\leq \sqrt{ n }$。
假設 $a>\sqrt{ n }$ 且 $b>\sqrt{ n }$，則 $ab>n$ 矛盾。
所以有 $a\leq \sqrt{ n }$ 或 $b\leq \sqrt{ n }$。
不失一般性，假設 $a\leq b$ 且 $a\leq \sqrt{ n }$。
若 $a$ 為質數，定理成立。
若 $a$ 為合數，則根據算數基本定理，$a$ 可被表示成比自己更小的質數的乘積，定理成立。

Theorem：質數有無限個。

proof:
假設存在有限多個質數 $p_{1},p_{2},\dots,p_{k}$。
令 $Q=p_{1}p_{2}\dots p_{k}+1$ 
因為 $Q\not\in \{ p_{1},p_{2},\dots,p_{k} \}$ 根據假設，$Q$ 應該為合數。
但是，根據基本算術定裡，合數應該可被一或多個質數的乘積表達，但 $Q$ 無法被如此表達。
矛盾，所以存在無限多個質數。

## Greatest Common Divisor

Greatest Common Divisor：若 $a,b\in \mathbb{Z}$ 且不全為 $0$，則存在 $d\in \mathbb{Z}$ 使得 $d\mid a$ 且 $d\mid b$。其中，$d$ 中最大者被稱為最大公因數，記為 $\text{gcd}(a,b)$。

**Relatively Prime(互質)**：若 $a,b$ 的最大公因數為 $1$，則 $a$ 與 $b$ 互質。

**Least Common Multiple(最小公倍數)**：能同時被 $a,b$ 整除的最小整數，記為 $\text{lcm}(a,b)$。

![[Pasted image 20260401213111.png|669]]

## Euclidean Algorithm

用歐幾里德算法找最大公因數，即輾轉相除法原理如下。

若 $a\geq b$ 則 $a=bq+r$ 其中 $0\leq r<b$。

如果 $d$ 同時整除 $b$ 與 $r$，則必定整除 $a$。

所以算法如下：
1. 計算 $r=a\text{ mod }b$ 
2. 問題變成 $\text{gcd}(b,r)$ 
3. 重複直到餘數為 $0$，剩下的除數為解。

![[Pasted image 20260401214050.png|551]]

# Solving Congruences

目標：假設 $m\in \mathbb{Z}^{+}$ 且 $a,b\in \mathbb{Z}$，求解下式的 $x$：$ax\equiv b\ (\text{mod }m)$。

Theorem：若 $a,m$ 為**互質的**整數且 $m>1$，則存在 $\bar{a}$ 使得 $a\bar{a}\equiv1\ (\text{mod }m)$，且 $\bar{a}$ 唯一。

我們稱 $\bar{a}$ 是 $a$ 在 $a$ modulo $m$ 的反元素。

> [!note]
> 若 $a,m$ 不互質，則 $\bar{a}$ 不一定存在。
> 例如，$\mathbb{Z}_{4}=\{ 0,1,2,3 \}$，則 $2$ 在 $2\text{ mod }4$ 運算中沒有反元素。

> [!warning] 補充 Bézout 定理
> 若 $a,b\in \mathbb{Z}$，且 $\text{gdc}(a,b)=d$。
> 則 $\exists\ s,t\in \mathbb{Z}$ 使得 $sa+tb=d$。

proof:
存在性：
因為 $a,m$ 互質，所以 $\text{gcd}(a,b)=1$。
則一定存在整數 $s,t$ 使得 $sa+tm=1$。
因為 $sa+tm\equiv 1\ (\text{mod }m)$ 且 $tm\equiv0\ (\text{mod }m)$，所以 $sa\equiv 1\ (\text{mod }m)$。
此處 $s$ 即我們要找的反元素。
唯一性：
設 $b,c$ 是 $a$ modulo $m$ 的**任意**兩反元素。
則有 $ba\equiv ca\equiv{1}\ (\text{mod }m)$。
所以，$ba-ca\equiv0\ (\text{mod }m)$。
又 $a$ 與 $m$ 互質，所以 $b-c\equiv 0\ (\text{mod m})$。
因此 $b\equiv c\ (\text{mod }m)$，所以 $b,c$ 在模 $m$ 上唯一。

![[Pasted image 20260402162928.png|584]]

我們應該如何快速找到 $\bar{a}$，應該反向使用 Euclidean Algorithm。

因為 $a,m$ 互質，所以 $\text{gcd}(a,m)=1$。

必存在 $x,y\in \mathbb{Z}$ 使得 $ax+my=1$，又 $my\equiv 0\ (\text{mod }m)$，所以 $ax\equiv 1\ (\text{mod }m)$。即，$x=\bar{a}$。

![[Pasted image 20260402195014.png|827]]

# 中國餘數定理、中國剩餘定理

Theorem：令 $m_{1},m_{2},\dots ,m_{n}\in \mathbb{Z}^{+}$ 兩兩互質，$a_{1},a_{2},\dots,a_{n}\in \mathbb{Z}$ 則：

$$
\begin{align}
 & x\equiv a_{1}\ (\text{mod }m_{1}) \\
 & x\equiv a_{2}\ (\text{mod }m_{2}) \\
 & \vdots \\
 & x\equiv a_{n}\ (\text{mod }m_{n})
\end{align}
$$

存在解，且在模 $m=m_{1}m_{2}\dots m_{n}$ 下唯一 ($0\leq x<m$，其餘解都與 $x\text{ mod }m$ 同餘)。

proof:
這裡我們只證存在性。
對任意 $k\in \{ 1,2,\dots,n \}$，令 $M_{k}=\frac{m}{m_{k}}$。
則對任意 $i\in \{ 1,2,\dots,n \}$ 有 $\text{gcd}(m_{i},M_{i})=1$。
因此，存在唯一個 $y_{i}=\overline{ M_{i} }$ 使得 $y_{i}M_{i}\equiv 1\ (\text{mod }m_{i})$。
則 $x=a_{1}M_{1}y_{1}+a_{2}M_{2}y_{2}+\dots+a_{n}M_{n}y_{n}$ 為方程的一個解。
因為，對任意 $j\in \{ 1,2,\dots,n \}$ 若：
- $j=k$ 則 $a_{j}M_{j}y_{j}\equiv a_{j}\ (\text{mod }m_{k})$ 
- $j\neq k$ 則 $a_{j}M_{j}y_{j}\equiv M_{j}\equiv0\ (\text{mod }m_{k})$ 

> [!note]
> $j$ 取 $\overline{ M_{i} }$ 而不是 $\overline{ a_{i} }$。

![[Pasted image 20260402201419.png|627]]

