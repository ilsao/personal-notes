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