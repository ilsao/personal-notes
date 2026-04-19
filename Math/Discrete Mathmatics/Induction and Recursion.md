# Mathematical Induction

![[Pasted image 20260406122946.png]]

Example：令 $H_{k}$ 為 Harmonic Series，利用數學歸納法證明當 $n$ 為非負整數時 $H_{2^{n}}\geq1+\frac{n}{2}$。

Sol:
當 $n=0$ 時，$H_{2^{0}}\geq 1+\frac{0}{2}=1$ 成立。
設當 $n=k$ 時命題成立。
考慮 $n=k+1$：
$H_{2^{k+1}}=H_{2^{k}}+\frac{1}{2^{k}+1}+\frac{1}{2^{k}+2}+\dots +\frac{1}{2^{k+1}}$ 
$\geq 1+ \frac{k}{2}+\frac{1}{2^{k}+1}+\frac{1}{2^{k}+2}+\dots+\frac{1}{2^{k+1}}$ 
$\geq1+\frac{k}{2}+\frac{1}{2^{k}+2^{k}}+\frac{1}{2^{k}+2^{k}}+\dots+\frac{1}{2^{k+1}}=1+\frac{k}{2}+ \frac{2^{k}}{2^{k}+2^{k}}$ 
$=1+\frac{k+1}{2}$ 
命題成立。
所以，By induction 對所有 $n\in \mathbb{Z}^{+}$ 命題成立。

![[Pasted image 20260406124816.png|1016]]

> [!note]
> 留意 $(k^{3}+3k^{2}+3k+1)-(k+1)$ 的整理方法。
> 我們要用歸納法證明，所以會想湊出 $(k^{3}-k)$ 的前項結論，與 $3()$ 可被整除項。

![[Pasted image 20260406125313.png|1035]]
![[Pasted image 20260406125328.png|951]]

> [!note]
> 留意 $T=S\cup \{ a \}$ 那段敘述。

![[Pasted image 20260406125838.png|718]]
![[Pasted image 20260406125857.png|651]]


> [!note]
>  藍色區域為空缺，我們將左上三個空缺用一個 right triominoes 填滿即可。 

# Strong Induction and Well-Ordering

## Strong Induction

Basis step: Show that $P(1)$ is true.

Inductive step: Assume all $P(1),P(2),\dots ,P(k)$ are true. 

> [!note]
> 假設所有 $\leq k$ 的命題皆成立。

Show that $P(k+1)$ is true.

Example：證明若 $n\in \mathbb{Z}$ 且 $n>1$，則 $n$ 可寫為質數的乘積。

proof:
令 $P(n)$ 表示 $n$ 可寫為質數的乘積。
$P(2)$ 成立，因為 $2$ 是質數。
假設 $P(2),P(3),\dots,P(k)$ 都成立。
考慮 $P(k+1)$：
- $k+1$ 為質數：$P(k+1)$ 成立。
- $k+1$ 為合數：存在 $2\leq a\leq b<k+1$ 使得 $k=ab$。根據強歸納法的假設，$a,b$ 都可寫成質數的乘積 $\implies k+1$ 也可寫成質數的乘積。$P(k+1)$ 成立。

> [!note]
> 此證明只能用強歸納法證，普通歸納法無法證明。

![[Pasted image 20260406133758.png|780]]
![[Pasted image 20260406133809.png|812]]

## Well-Ordering 良序性

良序性公理：任意一個**非空**的**非負整數**集合，都有最小元素。

> [!warning] 注意
> 良序性公理不保證唯一性。

Example：證明 $a\in \mathbb{Z}$ 且 $d\in \mathbb{Z}^{+}$，$\exists!\ q,r\in \mathbb{Z}$ 使得 $a=dq+r$ 且 $0\leq r<d$。

Sol:
令 $S$ 為 $a-dq$ 的所有非負整數集合，其中 $q\in \mathbb{Z}$。
顯然，$S$ 不是空集合。
存在性：
由良序性公理，$S$ 有最小元素 $r=a-dq_{0}$。
根據 $S$ 的定義，$r\geq0$。
欲證 $r<d$。
假設 $r\geq d$，則 $r-d\geq 0$。
則 $r-d=a-dq_{0}-d=a-d(q_{0}+1)\geq 0$，代表 $r-d\in S$，$S$ 集合中有比 $r$ 小的數。
產生矛盾。
所以，$r<d$。
唯一性：
假設 $\exists\ q_{1},r_{1}\in \mathbb{Z}$ 使得 $a=dq_{1}+r_{1}$ 且 $0\leq r_{1}<d$。與 $\exists\ q_{2},r_{2}\in \mathbb{Z}$ 使得 $a=dq_{2}+r_{2}$ 且 $0\leq r_{2}<d$。
不失一般性，假設 $q_{1}\geq q_{2}$。
因為 $dq_{1}+r_{1}=a=dq_{2}+r_{2}\implies d(q_{1}-q_{2})=r_{2}-r_{1}\geq 0$。
又 $0\leq r_{1}<d$ 且 $0\leq r_{2}<d$，所以 $0\leq r_{1}-r_{2}<d$。
又 $(q_{1}-q_{2})\in \mathbb{Z}$，所以 $(r_{2}-r_{1})$ 為 $d$ 的整數倍 $\implies r_{2}-r_{1}=0$。
$\implies r_{1}=r_{2}$ 
又 $d(q_{1}-q_{2})=0$ 且 $d\neq 0$，所以 $q_{1}-q_{2}=0\implies q_{1}=q_{2}$。

# Recursive Definitions and Structural Induction

![[Pasted image 20260406141217.png|861]]

於是，解為：$f(n)=\begin{cases}4^{n-1}+2f(n-1) & \text{if }n\geq{2} \\ 3 & \text{if }n=1\end{cases}$ 

Example：令 $f_{n}$ 為第 $n$ 個 Fibonacci number。Show that $f_{n}>\alpha^{n-2}$，其中 $\alpha=\frac{1+\sqrt{ 5 }}{2}$ 且 $n\geq 3$。

Sol:
使用強歸納法。
令 $P(n)$ 為命題 $f_{n}>\alpha^{n-2}$。
則 $f_{3}>\alpha$ 且 $f_{4}>\alpha^{2}$ 顯然成立。
假設 $P(3),P(4),\dots ,P(n)$ 接成立。
$f_{n+1}=f_{n}+f_{n-1}>\alpha^{n-2}+\alpha^{n-3}=\alpha^{n-3}(\alpha+1)=\alpha^{n-3}\alpha^{2}=\alpha^{n-1}$ 命題成立。
所以 $P(n)$ 成立 $\forall \ n\geq3$ By strong MI。
注意到上面用到黃金比例關係，$\alpha+1=\alpha^{2}$。

![[Pasted image 20260406142338.png|733]]

