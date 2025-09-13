
# Row Echelon Form (REF)

1. The first nonzero entry in each nonzero row is 1.
2. If row $k$ does not consist entirely of zeros, the number of leading zero entries in row $k+1$ is greater than the number of leading zero entries in row $k$. 
3. If there are rows whose entires are zero,  they're below the rows having nonzero entries. 

The process of transform a matrix into REF is called **Guassian elimination**.

- 方程式數 < 變量數 $\implies$ 無限多組解
- 矛盾(ex: 0 = 3) $\implies$ 無解
- 其他狀況 $\implies$ 單一組解
# Reduced Row Echelon Form (RREF)

If a system in row echelon form and all the entries above the leading 1 in each column have been eliminated, it's **reduced row echelon form**. 

1. The matrix is in row echelon form. 
2. The first nonzero entry in each row is the only nonzero entry in it's column

The process of transform a matrix into RREF is called **Gauss-Jordan reduction**.

# Overdetermined/Undetermined Systems

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
# 例題

1. Assume $\vec{u} = (u_{1}, u_{1}\dots u_{n})$ and $\vec{v}= (v_{1}, v_{2} \dots v_{n})$ are two solutions of $a_{1}x_{1}+a_{2}x_{2}+ \dots +a_{n}x_{n}=b$. **Prove** that for any real number $C$, $\vec{u}+c(u-v)$ is the solution of $a_{1}x_{1}+a_{2}x_{2}+ \dots +a_{n}x_{n}=b$. 

Sol 1:

$\because$ We have $a_{1}u_{1}+a_{2}u_{2}+ \dots a_{n}u_{n} = b$ and $a_{1}v_{1}+a_{2}v_{2}+ \dots +a_{n}v_{n} = b$ 
$\therefore$ We have $a_{1}(u_{1}-v_{1})+a_{2}(u_{2}-v_{2})+ \dots +a_{n}(u_{n}-v_{n})=0$. i.e., $\vec{u}-\vec{v}$ is one of the solution of $a_{1}x_{1}+a_{2}x_{2}+\dots+a_{n}x_{n}=0$.
$\implies$ $c(\vec{u}-\vec{v})$ is also the one of the solution of $a_{1}x_{1}+a_{2}x_{2}+\dots+a_{n}x_{n}=0$. 
Then, we add $\vec{u}$ to $c(\vec{u}-\vec{v})$. i.e., $\vec{u} + c(\vec{u}-\vec{v})$, it's the solution of $a_{1}x_{1}+a_{2}x_{2}+ \dots +a_{n}x_{n}=b$. 

Sol 2:

$a⋅(u+c(u−v))=a⋅u+c(a⋅u−a⋅v)=b+c(b−b)=b$.