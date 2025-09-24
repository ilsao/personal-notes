
# Row Echelon Form (REF)

1. 任何非零 row 開頭第一個非零的數字必為1。
2. 任何非零 row 開頭第一個非零的數字必在上一 row 開頭第一個非零數字之後的 column 上。
3. 所有全零 row 必置於矩陣底部。

The process of transform a matrix into REF is called **Guassian elimination**.

- 方程式數 < 變量數 $\implies$ 無限多組解
- 矛盾(ex: 0 = 3) $\implies$ 無解
- 其他狀況 $\implies$ 單一組解
# Reduced Row Echelon Form (RREF)

If a system in row echelon form and all the entries above the leading 1 in each column have been eliminated, it's **reduced row echelon form**. 

1. 矩陣為 REF。
2. 對於任意 row，開頭第一個非零數字是該 column 上唯一的非零數字。

The process of transform a matrix into RREF is called **Gauss-Jordan reduction**.

# Overdetermined(超定)/Undetermined(欠定) Systems

Overdetermined Systems: If there're **more** equations than unknows, it's an **overdetermined** system. 

Undetermined Systems: If there're **fewer** equations than unknows, it's an **undetermined** system. 

# Homogeneous Systems

A system of linear equations is said to be **homogeneous(齊次的)** if the constant on the right-hand side are all zero.

1. Homogeneous systems are always consistent. 
2. If an homogeneous system have an unique solution, it must be a trival solution = $(0, 0, \dots, 0)$. 
3. An $m \times n$ homogeneous system of linear equations has a nontrival solution if $m < n$. 

# 列運算表示法

交換列：$R_{1} \leftrightarrow R_{2}$ (Row 1 和 Row 2 交換)

乘實數：$(-2)R_{1}\to R_{1}$

乘實數後加到另一列：$(-2)R_{1} + R_{3} \to R_{3}$

# 矩陣相等

矩陣 $A=B$ 需要滿足以下條件：
- $A、B$ 大小相等。
- $a_{ij}=b_{ij}$。

# 轉置矩陣

$$
a_{ij} = (A^{T})_{ji}
$$

$$
(a^{i})^{T}=(A^{T})_{i}
$$

$$
(A+B)^{T}=A^{T}+B^{T}
$$

$$
(cA)^{T} = c(A^{T})
$$

$$
 ^{*} (AB)^{T} = B^{T}A^{T}
$$

# 矩陣乘法

- 矩陣乘法沒有交換律：$AB \neq BA$。
- 矩陣乘法沒有消去律：$AC = BC \centernot\implies A=B$。

當 $AB=C$ 時：
$$
c_{ij}=\sum_{k}^{n} a_{ik} \cdot b_{kj}
$$

兩種看待矩陣乘法的方式：
1. 
   回想，向量 $(x, y)$ 可以表示為 $x\hat{i} + y\hat{j}$。
   而想要將原向量變換到新座標，我們只需要變換 $\hat{i}$ 和 $\hat{j}$ ，然後重新用 $x \cdot \hat{i} + y \cdot \hat{j}$ 表示即可。
   若 $A、B$ 矩陣相乘，將 $A$ 視為變換過的基向量 (即 $\hat{i}、\hat{j}$ 等)，$B$ 視為一或多組需要從原座標系統變換為新座標系統的座標。
   那麼，$AB$ 可以表示為：
$$
A_{m \times 2} \begin{bmatrix}
x \\
y
\end{bmatrix}
=xa_{1}+xa_{2}
$$
   若 $m>2$ 則可將乘法視為將向量 $(x, y)$ 映射到 $m$ 維空間中。
   例子：
$$
\begin{bmatrix}
1 & 0 \\
0 & 1 \\
0 & 0
\end{bmatrix}
\begin{bmatrix}
x \\
y
\end{bmatrix}
=x\begin{bmatrix}
1 \\
0 \\
0
\end{bmatrix}
+y\begin{bmatrix}
0 \\
1 \\
0
\end{bmatrix}
=
\begin{bmatrix}
x \\
y \\
0
\end{bmatrix}
$$
   可以看成將二維 $\hat{i}、\hat{j}$ 映射到三維 $\hat{i}=(1, 0, 0), \hat{j}=(0, 1, 0)$ 上，然後利用映射後的 $\hat{i}、\hat{j}$ 對 $(x, y)$ 變換。
2. 
   若 $A、B$ 矩陣相乘，將 $a^{i}$ 中的每項視為對 $B$ 中的每組向量做拉伸
   那麼，$AB$ 可以表示為：
$$
\begin{bmatrix}
x & y
\end{bmatrix}B_{2 \times n}
=xb^{1}+yb^{2}
$$
   若 $n>2$ 則視為對多組向量同時拉伸。
   例子：
$$
\begin{bmatrix}
x & y
\end{bmatrix}
\begin{bmatrix}
1 & 2 \\
1 & 3
\end{bmatrix}
=x\begin{bmatrix}
1 & 2
\end{bmatrix}+
y\begin{bmatrix}
1 & 3
\end{bmatrix}
$$

# 轉置矩陣

一個 $m \times n$ 矩陣 $A$ 轉置為一個 $n \times m$ 矩陣 $B$，則 $A$ 與 $B$ 的關係定義為

$$
b_{ji}=a_{ij}
$$

其中， $i \leq n, j \leq m$。且矩陣 $A$ 的轉置記作 $A^{T}$。

若 $A^{T}=A$，則此 $n \times n$ 的矩陣 $A$ **對稱(symmetric)**。

以下列出一些 Algebraic Rules for Transposes
1. $(\alpha A)^{T}=\alpha A^{T}$ 
2. $(A+B)^{T}=A^{T}+B^{T}$ 
3. $(AB)^{T}=B^{T}A^{T}$ 
4. $(A^{n})^{T}=(A^{T})^{n}$ 

以下我們證明 $(AB)^{T}=B^{T}A^{T}$.

proof:
想證明這條等式，只需要證明其乘積中的每一項皆相同即可。
其中，$(AB)^{T}$ 的每項可以表達為： $\vec{a}_{j}b_{i} = a_{j 1}b_{1 i} + \dots + a_{j n}b_{n i}$
而 $B^{T}A^{T}$ 的每項可以表達為：$b_{i}^{T} \vec{a}_{j}^{T}=b_{1i}a_{j 1} + \dots +b_{n i} a_{j n}$
因為二者中的每項皆相同，所以二者相等。

# 單位矩陣(The Identity Matrix)

對於 $n\times n$ 單位矩陣 $I=(\delta_{ij})$定義如下：

$$
\delta_{ij}=
\begin{cases}
1 & \text{if i = j} \\
0 & \text{if i } \neq \text{j}
\end{cases}
$$

需要注意的是，想表示 $I$ 的第 $j$ column，不是使用 $i_{j}$，而使用 $e_{j}$。所以可以使用 $I=(e_{1}, e_{2}, \dots e_{n})$ 來表示一個 $n \times n$ 單位矩陣。

# 矩陣的逆運算

一個矩陣只能擁有一個乘法逆元，以下為證明：

Proof:
假設 $B, C$ 為 $A$ 的乘法逆元，則
$$
B = BI = B(AC) = (BA)C = IC = C
$$

**singular(奇異的)**：當一個矩陣沒有乘法逆元，則稱為 singular。即， $\det(A)=0$。

注意，**singular不可以用在非方陣上**，因為一個非方陣總是沒有乘法逆元。

如何求一個矩陣的乘法逆元？

我們以如下例子說明。

現有 $A=\begin{bmatrix} 2 & 1 \\ 3 & 2 \end{bmatrix}$ ，求$A^{-1}$。

令 $A^{-1}=\begin{bmatrix} x_{11} & x_{12} \\ x_{21} & x_{22} \end{bmatrix}$ ，我們有：

$$
\begin{bmatrix}
2 & 1 \\
3 & 2
\end{bmatrix}
\begin{bmatrix}
x_{11} & x_{12} \\
x_{21} & x_{22}
\end{bmatrix}
=
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}
$$

等於解：

$$
\begin{bmatrix}
2 & 1 \\
3 & 2
\end{bmatrix}
\begin{bmatrix}
x_{11} \\
x_{21}
\end{bmatrix}=
\begin{bmatrix}
1 \\
0
\end{bmatrix}
$$

與

$$
\begin{bmatrix}
2 & 1 \\
3 & 2
\end{bmatrix}
\begin{bmatrix}
x_{12} \\
x_{22}
\end{bmatrix}
=\begin{bmatrix}
0 \\
1
\end{bmatrix}
$$

也就是解以下增廣矩陣(化為 Reduced Row Echelon Form)：

$$
\begin{bmatrix}
2 & 1 & | \text{ }1 & 0 \\
3 & 2 & | \text{ }0 & 1
\end{bmatrix}
$$

$$
\begin{bmatrix}
2 & 1 & 1 & 0 \\
1 & 1 & -1 & 1
\end{bmatrix}
\to
\begin{bmatrix}
1 & 1 & -1 & 1 \\
2 & 1 & 1 & 0
\end{bmatrix}
\to
\begin{bmatrix}
1 & 1 & -1 & 1 \\
0 & -1 & 3 & -2
\end{bmatrix}
\to
\begin{bmatrix}
1 & 0 & 2 & -1 \\
0 & 1 & -3 & 2
\end{bmatrix}
$$

即，$A^{-1}=\begin{bmatrix}2 & -1 \\ -3 & 2\end{bmatrix}$。

若兩個可逆矩陣相乘，得出的結果仍為可逆的。

proof:
$(B^{-1}A^{-1})AB=I$
$AB(B^{-1}A^{-1})=I$

# 鄰接矩陣

無向圖的鄰接矩陣定義如下：

$$
\begin{cases}
1  & \text{if }\{V_{i}, V_{j}\} \text{ is an edge of the graph} \\
0 & \text{if there is no edge joining } V_{i} \text{ and } V_{j}
\end{cases}
$$

若有鄰接矩陣 $A$，取 $A^{k}$ 中的 $a^{(k)}_{ij}$ 表示在圖中 $V_{i}\to V_{j}$ 且所經長度為 $k$ 的路徑數。

# 初等矩陣(Elementary Matrices)

基本列運算(Elementary row operation) 包括以下三個操作：
- 交換兩 row
- 某一 row 乘一個非零數
- 某一 row 乘一個非零數並加到另一 row

初等矩陣便是由單位矩陣經過「一個」基本列運算得出的矩陣，且初等矩陣總是可逆的。

以上性質可以用以下兩個方法證明：
- 每個基本列運算都有其逆操作，所以每個初等矩陣都有其逆矩陣。
- 所有基本列運算對行列式值的操作都不會使其等於零，所以初等矩陣總是可逆。

當某個矩陣左乘一個初等矩陣，則會將對該初等矩陣應用的基本列運算應用到該矩陣上。

所以，我們如下定義，若矩陣 $B$ 與矩陣 $A$ 行等價，則：

$$
B=E_{k}E_{k-1}\dots E_{1}A
$$

其中，$E_{n}$ 為初等矩陣。

所以，若增廣矩陣 $(A|\vec{b})$ 和 $(B| \vec{c})$ 行等價，則 $Ax=\vec{b}$ 與 $Bx=\vec{c}$ 為等價方程組。

由上，我們還可以得知，若 $B$ 處於 RREF(此時 $B$ 為單位矩陣)，則：

$$
E_{k}E_{k-1}\dots E_{1}=A^{-1}
$$
$$
E_{1}^{-1}\dots E_{k-1}^{-1}E_{k}^{-1}=A
$$

$A$ 為一個 $n \times n$ 矩陣，則下列敘述互相等價：
- $A$ 可逆
- $Ax=\vec{b}$ 有唯一解
- $Ax=0$ 有唯一零解
- $A$ 與單位矩陣行等價
- $A$ 可以寫成一系列初等矩陣相乘

想證明以上五點等價，可以先假設第一點成立，然後遞推到第五點也成立，最後由第五點推第一點成立即可。

我們還可以推論，如果 $Ax=\vec{b}$ 有唯一解，則 $A$ 必為非奇異的。

proof:
如果 $A$ 是非奇異的，則 $x$ 有唯一解 $A^{-1}\vec{b}$。
誠然，若 $A$ 為奇異的，則 $Ax=0$ 會有解 $z \neq 0$。但這也表明 $Ax=\vec{b}$ 會有不僅單一組解，取 $\vec{x} + z$ 為第二組解也是可以的，因為 $A(\vec{x}+z)=A\vec{x}+Az=\vec{b}+0=\vec{b}$。此假設與前提矛盾，所以 $A$ 必為非奇異的。

# LU分解(LU Factorization)

一個 $n \times n$ 矩陣 $A$ 可能可以表達為兩個三角矩陣相乘：$LU=A$。

其中，$L$ 表示下三角矩陣，$U$ 表示上三角矩陣。

我們可以使用基本列運算：將某 row 乘一個非零數加到另一 row 來構建其中一個三角矩陣，且另一三角矩陣為構建此三角矩陣所使用的初等矩陣的乘積的逆矩陣。

# 例題

1. Assume $\vec{u} = (u_{1}, u_{1}\dots u_{n})$ and $\vec{v}= (v_{1}, v_{2} \dots v_{n})$ are two solutions of $a_{1}x_{1}+a_{2}x_{2}+ \dots +a_{n}x_{n}=b$. **Prove** that for any real number $C$, $\vec{u}+c(u-v)$ is the solution of $a_{1}x_{1}+a_{2}x_{2}+ \dots +a_{n}x_{n}=b$. 

Sol 1:

$\because$ We have $a_{1}u_{1}+a_{2}u_{2}+ \dots a_{n}u_{n} = b$ and $a_{1}v_{1}+a_{2}v_{2}+ \dots +a_{n}v_{n} = b$ 
$\therefore$ We have $a_{1}(u_{1}-v_{1})+a_{2}(u_{2}-v_{2})+ \dots +a_{n}(u_{n}-v_{n})=0$. i.e., $\vec{u}-\vec{v}$ is one of the solution of $a_{1}x_{1}+a_{2}x_{2}+\dots+a_{n}x_{n}=0$.
$\implies$ $c(\vec{u}-\vec{v})$ is also the one of the solution of $a_{1}x_{1}+a_{2}x_{2}+\dots+a_{n}x_{n}=0$. 
Then, we add $\vec{u}$ to $c(\vec{u}-\vec{v})$. i.e., $\vec{u} + c(\vec{u}-\vec{v})$, it's the solution of $a_{1}x_{1}+a_{2}x_{2}+ \dots +a_{n}x_{n}=b$. 

Sol 2:

$a⋅(u+c(u−v))=a⋅u+c(a⋅u−a⋅v)=b+c(b−b)=b$.

2. 給定一個 overdetermined 的齊次方程系統，討論解的情況。

Sol:
因為是齊次系統，所以該系統就算 overdetermined 也會有解(最少也有全零解)。
分為：單一解(全零解)，無限多組解。

3. 給定一個 underdetermined 的非齊次方程，討論解的情況。

Sol:
因為 underdetermined，所以若沒有矛盾情況出現，則必有 free variable 出現，導致無限多組解。
因為限制不足，所以無法出現單一解的情況。
無解僅在矛盾出現時發生。

統整：

![[Pasted image 20250914165104.png]]

$$
\begin{align}
 - & i_{1} + i_{2} - i_{3} = 0 \text{ (node A)} \\
 & i_{1} - i_{2} + i_{4} = 0 \text{ (node B)} \\
 & i_{3} - i_{5} + i_{6} = 0 \text{ (node C)} \\
- & i_{4} + i_{5} - i_{6} = 0 \text{ (node D)} \\
 & 4i_{1} + 2i_{2} = 8 \text{ (top loop)} \\
 & 2i_{2} - 4i_{5} = \text{ (medium loop)} \\
 & 4i_{5} + 5i_{6} = 10 \text{ (bottom loop)}
\end{align}
$$

4. $Ax=b$ be a linear system whose augmented matrix $(A|b)$ has reduced row echelon form $\begin{bmatrix}1 & 2 & 0 & 3 & 1  | &-2 \\ 0 & 0 & 1 & 2 & 4| & 5 \\ 0 & 0 & 0 & 0 & 0| & 0 \\ 0 & 0 & 0 & 0 & 0| & 0 \end{bmatrix}$
   (a) Find all solutions to the system.
   (b) If $a_{1}=\begin{bmatrix}1 \\ 1 \\ 3 \\ 4\end{bmatrix}$ and $a_{3}=\begin{bmatrix}2 \\ -1 \\ 1 \\ 3\end{bmatrix}$ determine $b$. 

Sol:
(a)
It's easy to find out that $\begin{cases}x_{1}=-2-2s-3k-t \\ x_{2}=s \\ x_{3}=5-2k-4t \\x_{4}=k \\ x_{5}=t\end{cases}$

(b)
Let's recall the definition of $Ax=b$. 
Actually, $b$ is the linear combination of $A$. 
In this case, we can express as $b = x_{1}a_{1}+x_{2}a_{2}+x_{3}a_{3}+x_{4}a_{4}+x_{5}a_{5}$. 
Since $a_{1}, a_{3}$ are given, let's find a special solution of $x$. 
Take $x_{2}=x_{4}=x_{5}=0$, we have $x_{1}=-2, x_{3}=5$. 
Thus, we can express $b$ as follow linear combination $Ax=b=-2a_{1}+5a_{3}$. 
So, $b$ will be $\begin{bmatrix}8 \\ -7 \\ -1 \\ 7\end{bmatrix}$. 

5. Is it possible for a nonzero symmetric $2\times 2$ matrix $A$ to have the property that $A^{2}=O$? Prove your answer. 

Sol:
Assume $A=\begin{bmatrix}a & b \\ b & c\end{bmatrix}$ , thus $A^{2}=\begin{bmatrix}a^{2}+b^{2} & ab+bc \\ ab+bc & b^{2}+c^{2}\end{bmatrix}=\begin{bmatrix}0 & 0 \\ 0 & 0\end{bmatrix}$.
$\begin{cases} a^{2}+b^{2}=0 \\ ab+bc=0 \\ b^{2}+c^{2}=0 \end{cases}\implies \begin{cases}a=b=c=0\end{cases}$. 
Therefore, it is impossible for a nonzero symmetric $2\times 2$ matrix to have this property.

6. Let $A$ and $B$ be symmetric n times n matrices. For each of the following, determine whether the given matrix must be symmetric or could be nonsymmetric.
   (a)A+B
   (b)$A^2$
   (c)AB
   (d)ABA
   (e)AB+BA
   (f)AB-BA

Sol:
(a) $(A+B)^T$=$A^{T}+B^{T}=A+B$ 
(b) $(A^{2})^{T}=(A^{T})^{2}=A^{2}$ 
...
Use the method above to prove each option.

7. Prove that if $A$ is nonsingular, then $A^{T}$ is nonsingular and $(A^{T})^{-1}=(A^{-1})^{T}$ 

Sol:
Since $A$ is nonsingular, then $AA^{-1}= A^{-1}A = I$. And we know $I^{T}=I$.
$(AA^{-1})^{T}=(A^{-1})^{T}A^{T}=I$ 
$(A^{-1}A)^{T}=A^{T}(A^{-1})^{T}=I$ 
Thus, we have $A^{T}$ is nonsingular and $(A^{-1})^{T}$ is the inverse of $A^{T}$.

$(A^{k+1})^{-1}=(A^{k}A)^{-1}=A^{-1}(A^{k})^{-1}=A^{-1}(A^{-1})^{k}=(A^{-1})^{k+1}$ 

8. Let $A$ be a nonsingular $n \times n$ matrix. Use mathematical induction to prove that $A^{m}$ is nonsingular and $(A^{m})^{-1}=(A^{-1})^{m}$ for $m=1,2,3,\dots$

Sol:
(Declare: If you have no extra time, just skip this problem. Since I actually solve this after a few minutes of thinking)
當 $m = 1$ 時
因為 Ａ 可逆，所以 $(A^{1})^{-1}=(A^{-1})^{1}$ 成立。
設當 $m=k(k\geq 1)$ 時
$(A^{k})^{-1}=(A^{-1})^{k}$ 亦成立。
當 $m=k+1$ 時
$(A^{k+1})^{-1}=(A^{k}A)^{-1}=A^{-1}(A^{k})^{-1}=A^{-1}(A^{-1})^{k}=(A^{-1})^{k+1}$ 成立。
所以，由數學歸納法，結論對 $m \geq 1$ 皆成立。

9. Let $D$ an $n \times n$ diagonal matrix whose diagonal entries are either 0 or 1.Show that $D$ is idempotent($D^{2}=D$).

Sol:
設 $D=\text{diag}(d_{1},d_{2},\dots,dn), d_{i}\in\{0,1\}$。
對角矩陣相乘仍為對角矩陣，則 $D^{2}=\text{diag}(d_{1}^{2},d_{2}^{2},\dots,d_{n}^{2})$。
因為 $d_{i}\in \{0,1\}$ 所以 $d_{i}^{2}=d_{1}$
$\implies D^{2}=\text{diag}(d_{1}^{2},d_{2}^{2},\dots,d_{n}^{2})=\text{diag}(d_{1},d_{2},\dots,dn)=D, d_{i}\in\{0,1\}$ 

10. Let $A$ and $B$ be symmetric $n \times n$ matrices. Prove that $AB=BA$ if and only if $AB$ is also symmetric .

Sol:
紀錄此題僅為練習 if and only if 的雙向證明法。
($\implies$) If $AB = BA$ then
$(AB)^{T}=B^{T}A^{T}=BA=AB$ 
Thus, $AB$ is symmetric.
($\impliedby$) If $AB$ is symmetric then
$AB=(AB)^{T}=BA$
Thus, $AB=BA$ 
Hence,  $AB=BA$ if and only if $AB$ is also symmetric .