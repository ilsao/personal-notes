
# The Determinant of a Matrix

我們已經知道，$\det(A)\neq 0$ 代表 $A$ 矩陣擁有乘法逆元。我們藉助這點嘗試推導行列式公式：

考慮一個 $2\times 2$ 矩陣 $A=\begin{bmatrix}a_{11} & a_{12} \\ a_{21} & a_{22}\end{bmatrix}$。

通過基本列運算我們可以將其轉化成行等價的 REF：$\begin{bmatrix}a_{11} & a_{12} \\ 0 & a_{11}a_{12}-a_{21}a_{22}\end{bmatrix}$。

想要讓此 REF 可逆，則此 REF 應與單位矩陣行等價。若 $a_{11}\neq 0$ 的情況下，必須有 $a_{11}a_{12}-a_{21}a_{22} \neq 0$ 才可與單位矩陣行等價。

所以，我們定義 $2\times 2$ 矩陣的行列式為 $\det(A)=a_{11}a_{12}-a_{21}a_{22}$ 。

以下嘗試推導 $3\times 3$ 矩陣 $A$ 的行列式公式：

我們可以將矩陣通過基本列運算轉化成行等價的矩陣 $\begin{bmatrix}a_{11} & a_{12} & a_{13} \\ 0 & \frac{a_{11}a_{22}-a_{21}a_{12}}{a_{11}} & \frac{a_{11}a_{23}-a_{21}a_{13}}{a_{11}} \\ 0 & \frac{a_{11}a_{32}-a_{31}a_{12}}{a_{11}} & \frac{a_{11}a_{33}-a_{31}a_{13}}{a_{11}}\end{bmatrix}$ 。

想要此矩陣與單位矩陣行等價，則有 $a_{11}\begin{vmatrix}\frac{a_{11}a_{22}-a_{21}a_{12}}{a_{11}} & \frac{a_{11}a_{23}-a_{21}a_{13}}{a_{11}} \\\frac{a_{11}a_{32}-a_{31}a_{12}}{a_{11}} & \frac{a_{11}a_{33}-a_{31}a_{13}}{a_{11}}\end{vmatrix} \neq 0$ 。

由上，我們可以定義行列式的計算公式。

首先我們定義 $M_{ij}$ 是將矩陣 $A$ 的第 $i$ row 與第 $j$ column 刪除後的矩陣。而 $\det(M_{ij})$ 是 $a_{ij}$ 的 minor(子式)，$A_{ij}=(-1)^{i+j}\det(M_{ij})$ 是 $a_{ij}$ 的 cofactor(餘子式)。

行列式計算公式如下定義：

$$
\begin{align}
 & \det(A)=
 &  & \begin{cases}
a_{11} & \text{if n = 1} \\
a_{11}A_{11}+a_{12}A_{12}+\dots+a_{1n}A_{1n} & \text{if n > 1}
\end{cases} \\
 & \text{Where} \\
 &  &  & A_{1j}=(-1)^{1+j}\det(M_{1j}) \quad j=1,\dots,n
\end{align}
$$

我們稱此計算行列式的方法為：**拉普拉斯展開(cofactor expansion)** 

需要注意的是，我們可以選擇使用任意 row 或 column 對行列式展開。

行列式還有以下性質：
- 如果 $A$ 矩陣有某行或某列全部為零，則行列式值為零。
- 如果 $A$ 矩陣有兩相同的列或行，則行列式為零。

proof:
因為將行列式某列乘一個非零數加到另一列上後，行列式值不變。所以只要將兩相同的列的其中一個乘以負一加到另一個上，就會造成某列全零，行列式為零。

- $^{*}\det(A^{T})=\det(A)$。

proof:
我們使用數學歸納法證明。
當矩陣大小為 $1\times 1$ 時，該式顯然成立。假設命題對 $k\times k$ 的矩陣成立。對 $(k+1) \times (k+1)$ 大小矩陣 $A$ 按第一 **row** 做拉普拉斯展開：
$\det(A)=\sum_{j=1}^{k+1}a_{1j}(-1)^{1+j}\det(M_{1j})$ 
對 $A^{T}$ 按第一 **column** 做展開：
$\det(A^{T})=\sum_{j=1}^{k+1}a_{j1}^T(-1)^{1+j}\det((M^T)_{j 1})=\sum_{j=1}^{k+1}a_{1j}(-1)^{1+j}\det((M_{1j})^T)$ 
由於假設對 $k\times k$ 大小的矩陣命題成立，所以 $\det((M_{1j})^{T})=\det(M_{1j})$，帶回可得 $\det(A^{T})=\det(A)$。

- 如果 $A$ 是三角矩陣，則其行列式值為其對角線元素的乘積。

proof:
我們還是使用數學歸納法證明。
在此我們只需要證明對下三角矩陣成立即可，因為已經有結論 $\det(A^{T})=\det(A)$ ，只需要對下三角矩陣轉置就可以得到上三角矩陣的行列式值。
讓我們假設一個大小為 $n \times n$ 的矩陣 $A$。
對於 $n=1$ ，命題顯然成立。
假設 $n=k$ 時命題亦成立，那麼當 $n=k+1$ 時，我們對該下三角矩陣的第一 row 展開：
$\det(A)=\sum_{j=1}^{k+1}a_{1j}(-1)^{1+j}\det(M_{1j})$ 。
同時，因為是下三角矩陣，所以除了第一項其他項都為零。所以式子可以簡化為：
$\det(A)=a_{11}\det(M_{11})$ 。
又因為 $M_{11}$ 是 $k \times k$ 大小的下三角矩陣，所以由 $n=k$ 時的假設可以得知，$\det(M_{11})=a_{22}\times a_{33}\times\dots \times a_{k+1,k+1}$ 。
所以，$\det(A)=a_{11}a_{22}\dots a_{nn}$ 。由數學歸納法，得證。

# Properties of Determinants

我們由一個引理來開啟此章節。

令 $A$ 為一個 $n\times n$ 矩陣，$A_{ij}$ 為 $a_{ij}$ 的 cofactor。

$$
\sum_{k=1}^{n}a_{ik}A_{jk}=\begin{cases}
\det(A) & \text{if }i=j \\
0 & \text{if }i\neq j
\end{cases}
$$

proof:
這個證明很神奇。
當 $i=j$ 的時候這條式子顯然就是該矩陣的拉普拉斯展開。
讓我們來看看 $i\neq j$ 的情況。
我們首先構建一個矩陣 $A^{*}$ ，其第 $j$ row 的值被第 $i$ row 替代。
那麼，$\sum_{k=1}^{n}a_{ik}A^{*}_{jk}$ 就是 $\det(A^{*})=0$，因為行列式中有兩相等的 row。
現在我們來講解為何此時 $\det(A^{*})=\det(A)$。
因為 $A^{*}$ 會將第 $j$ row 的值刪掉，計算剩下的行列式值，所以將 $i$ 複製過來不會改變 cofactor 的值。
所以，$\sum_{k=1}^{n}a_{ik}A^{*}_{jk}=\sum_{k=1}^{n}a_{ik}A_{jk}=0$ 當 $i \neq j$ 時。

## 列運算 I

將兩 row 交換。

如果 $E$ 為將換兩 row 的初等矩陣，則 $\det(EA)=-\det(A)$。

因為 $\det(E)=\det(EI)=-\det(I)=-1$，所以 $\det(EA)=\det(E)\det(A)$ 。

## 列運算 II

將某 row 乘某非零數。

令 $E$ 為此運算的初等矩陣，則：

$\det(EA)=\sum_{k=1}^{n}\alpha a_{1k}(-1)^{1+k}M_{1k}=\alpha\left( \sum_{k=1}^{n}a_{1k}(-1)^{1+k}M_{1k} \right)=\alpha \det(A)$ 。

因為 $\det(E)=\det(EI)=\alpha \det(I)$，所以 $\det(EA)=\det(E)\det(A)$ 。

## 列運算 III

將某 row 乘以某非零數加到另一 row 上。

令 $E$ 為此運算的初等矩陣，我們將第 $i$ row 乘 $c$ 加到 $j$ row，並對 $j$ row 展開：

$\det(EA)$ 
$=\sum_{k=1}^{n}(a_{jk}+ca_{ik})A_{jk}=\sum_{k=1}^{n}a_{jk}A_{jk}+c\sum_{k=1}^{n}a_{ik}A_{jk}$ 
$=\det(A)+0=\det(A)$ 
`~~~~~~~~~^`
此處使用最開始的那個引理可以得知。

我們可以得到：$\det(EA)=\det(A)=\det(E)\det(A)$。

## 總整

由以上三個列運算，我們可以得出以下結論。

$$
\det(EA)=\det(E)\det(A)
$$

其中，

$$
\det(E)=\begin{cases}
-1 & \text{if E is of type I} \\
\alpha\neq 0 & \text{if E is of type II} \\
1 & \text{if E is of type III}
\end{cases}
$$

同樣的結論也對 column operations 成立：

$\det(AE)=\det((AE)^{T})=\det(E^{T}A^{T})=\det(E^{T})\det(A^{T})=\det(E)\det(A)$ 

## 主要結論

$$
一個 \ n\times n \ 矩陣 \ A \ 奇異 \Leftrightarrow \det(A)=0
$$
proof：
若 $A$ 不可逆，則會有一行等價的矩陣 $B$ 的某列全為零 $\implies \det(B)=\det(E_{k}\dots E_{1})\det(A)=0\implies \det(A)=0$。

$$
\det(EA)=\det(E)\det(A)=\det(AE)
$$

當 $A,B$ 為大小 $n \times n$ 大小的矩陣時：

$$
^{*}\det(AB)=\det(A)\det(B)
$$

proof:
當 $B$ 不可逆時，$AB$ 也不可逆。
($Bx=0\implies (AB)x=0$ 且 $x\neq 0$)
所以此時 $\det(AB)=0=\det(A)\det(B)$ 
若 $B$ 可逆，則：
$\det(AB)=\det(AE_{1}\dots E_{n})=\det(A)\det(E_{1}\dots E_{n})$ 
$=\det(A)\det(B)$ 

# Additional Topics and Applications

## 伴隨矩陣(The Adjoint of a Matrix)

給定一個 $n \times n$ 大小的矩陣 ，我們如下定義伴隨矩陣(其中，$A_{ij}$ 是矩陣 $A$ 的餘子式)：

$$\text{adj}A=\begin{bmatrix}A_{11} & A_{21} & \dots & A_{n_{1}} \\ A_{12} & A_{22} & \dots & A_{n_{2}} \\ \vdots \\ A_{n 1} & A_{n 2} & \dots & A_{nn}\end{bmatrix}$$

即，$(\text{adj}A)_{ij}=(A_{ij})^{T}$。

伴隨矩陣會有如下性質：

$$
A(\text{Adj}A)=\det(A)I
$$

proof:
令 $A(\text{Adj}A)=B$，則 $B_{ij}=\sum_{k=1}^{n} a_{ik}A_{jk}$。根據最初的引理，僅當 $i=j$ 時 $B_{ij}=\det(A)$，否則 $B_{ij}=0\implies B=\det(A)I$。

若 $A$ 非奇異，則其行列式值永不為零。可以得到 $A\left( \frac{1}{\det(A)}\text{Adj}A \right)=I$。

所以，我們可以如下計算 $A$ 的逆：

$$
A^{-1}=\frac{1}{\det(A)}\text{Adj}A \quad \text{when }\det(A)\neq 0
$$

以下性質是我在題目證明中遇到，覺得好用的性質：

$$
\text{adj}(AB)=\text{adj}(A)\text{adj}(B)
$$

proof:
$\text{adj}(AB)=\det(AB)(AB)^{-1}=\det(A)\det(B)B^{-1}A^{-1}=\text{adj}(A)\text{adj(B)}$ 

$$
(\text{adj}A)^{n}=\text{adj}A^{n}
$$

proof:
利用上一個性質，$\text{adj}(A)\text{adj}(B)=adj(AB)\implies (\text{adjA})^{n} = \text{adj}(A)\dots \text{adj}(A)=\text{adj}A^{n}$ 。

## 克拉默法則(Cramer's Rule)

令 $A$ 為一個大小 $n\times n$ 且可逆的矩陣，$\mathbf{b} \in \mathbb{R}^{n}$。定義 $A_{i}$ 為 $A$ 矩陣的第 $i$ column 被 $b$ 替代後的新矩陣。如果 $x$ 是 $A\mathbf{x}=\mathbf{b}$ 的唯一解，則：

$$x_{i}= \frac{\det(A_{i})}{\det(A)} \quad \text{for }i=1,2,\dots,n$$

proof:
$x_{i}=A^{-1}\mathbf{b}$ 
$=\frac{1}{\det(A)}\text{Adj}(A)\mathbf{b}=\frac{\sum _{k=1}^{n}b_{k}A_{ki}}{\det(A)}$ 
$=\frac{\det(A_{i})}{\det(A)}$ (可以回憶 $A_{i}$ 的定義)

## 外積(The Cross Product)

給定兩個向量 $\mathbf{x},\mathbf{y} \in \mathbb{R}^{3}$，則二者的外積：

$$\mathbf{x}\times \mathbf{y}=\begin{bmatrix}x_{2}y_{3}-y_{2}x_{3} \\ y_{1}x_{3}-x_{1}y_{3} \\ x_{1}y_{2}-y_{1}x_{2}\end{bmatrix}$$

若 $C$ 為任意形如：

$$
C=\begin{bmatrix}
w_{1} & w_{2} & w_{3} \\
x_{1} & x_{2} & x_{3} \\
y_{1} & y_{2} & y_{3}
\end{bmatrix}
$$

則：

$$
\mathbf{x}\times \mathbf{y}=C_{11}e_{1}+C_{12}e_{2}+C_{13}e_{3}
$$

如果將 $C$ 的行列式對第一 row 進行拉普拉斯展開：

$$
\det(C)=w_{1}C_{11}+w_{2}C_{12}+w_{3}C_{13}=\mathbf{w}^{T}(\mathbf{x}\times \mathbf{y})
$$

具體來說，如果 $\mathbf{w}=\mathbf{x}$ 或 $\mathbf{w}=\mathbf{y}$，則 $\mathbf{x}^{T}(\mathbf{x}\times \mathbf{y})=\mathbf{y}^{T}(\mathbf{x}\times \mathbf{y})=0$。(行列式中兩列相同)

我們也可以將 $\mathbf{x}=(x_{1},x_{2},x_{3})$ 與 $\mathbf{y}=(y_{1},y_{2},y_{3})$ 視為 row vector。此時，我們如下定義外積：

$$
\mathbf{x}\times \mathbf{y}=(x_{2}y_{3}-y_{2}x_{3})\mathbf{i}-(x_{1}y_{3}-y_{1}x_{3})\mathbf{j}+(x_{1}y_{2}-y_{1}x_{2})\mathbf{k}
$$

其中，$\mathbf{i},\mathbf{j},\mathbf{k}$ 為 $1 \times 3$ 但為矩陣中的 row vector。

同時，外積也可以用行列式表達：

$$
\mathbf{x}\times \mathbf{y}=\begin{vmatrix}
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
x_{1} & x_{2} & x_{3} \\
y_{1} & y_{2} & y_{3}
\end{vmatrix}
$$

或將 row vector 換成 column vector：

$$
\mathbf{x}\times \mathbf{y}=\begin{vmatrix}
\mathbf{e_{1}} & \mathbf{e_{2}} & \mathbf{e_{3}} \\
x_{1} & x_{2} & x_{3} \\
y_{1} & y_{2} & y_{3}
\end{vmatrix}
$$

# Tips

- $\det(A^{T})=\det(A)$ 歸納法可證。
- $\det(\alpha A)=\alpha^{n}\det(A)$。
- $\det(AB)=\det(A)\det(B)$ 將 $B$ 換成初等矩陣可證。
- $\det(-I)=(-1)^{n}\neq-1$。
- $\det(\text{AdjA})=(\det(A))^{n-1}$。
- 基本上很多涉及 $\text{adj}A$ 的證明都要將 $\text{adj}A=\det(A)A^{-1}$ 解。
- 當有一個分塊矩陣 $C=\begin{bmatrix}A & O \\ O & B\end{bmatrix}$ ，則 $\det(C)=\det(A)\det(B)$。
- 若一個全部都是整數的矩陣 $A$ 且 $\det(A)=\pm 1$，則其逆矩陣 $A^{-1}=\text{adj(A)}$ 也全部皆是整數。如果想要構造出這樣的矩陣 $A$，我們可以從單位矩陣出發，對其進行無數個將某列乘以某值加到某列，或進行偶數個交換兩列。
- 計算逆矩陣時，$\text{Adj}A$ 求的是 cofactor，記得正負！
- 給定一個矩陣 $A$，如果想要計算 $A^{-1}$ 的第 $j$ column，可以將其視為解 $A\mathbf{x}=e_{j}$，並利用克拉默法則很快就可以得出答案。

# 重要例題

1. Let $A$ be a symmetric tridiagonal matrix. Let $B$ be the matrix formed from $A$ by deleting the first two rows and columns. Show that $\det(A)=a_{11}\det(M_{11})-a^{2}_{12}\det(B)$.

Sol:
首先跟你說說什麼是 symmetric tridiagonal matrix：
- arbitrary entries on the diagonal ($d_{1},\dots,d_{n}$),
- equal entries $e_{i}$​ on the subdiagonal and superdiagonal,
- zeros everywhere else.

對矩陣做展開：$\det(A)=a_{11}\det(M_{11})-a_{12}\det(M_{12})$。
觀察 $M_{12}$，發現第一 column 只有 $a_{21}$ 非零，用它展開就是 $\det(M_{12})=a_{21}\det(B)$ 。
又因為矩陣為 symmetric tridiagonal matrix，所以 $a_{21}=a_{12}$。所以帶回：
$\det(A)=a_{11}\det(M_{11})-a_{12}^{2}\det(B)$。

2. Let $A$ be a nonsingular matrix. Show that $\det(A^{-1})=\frac{1}{\det(A)}$. 

Sol:
利用性質 $\det(AB)=\det(A)\det(B)$。
因為 $\det(A^{-1}A)=\det(A^{-1})\det(A)=\det(I)=1\implies \det(A^{-1})=\frac{1}{\det(A)}$ 。

3. (!) Let $A$ be an $n \times n$ matrix. Is it possible for $A^{2}+I=O$?

Sol:
$A^{2}+I=O\implies \det(A^{2})=\det(-I)$ 
需要注意的是，$\det(-I)\neq -1$。
因為 $I$ 是對角矩陣，所以 $\det(-I)=(-1)^{n}$！
$\det(A^{2})=(\det(A))^{2}=(-1)^{n}$。當 $n$ 為奇數時，不可能成立。因為一個數字的平方不可能等於負一。

4. Let $A$ be a nonsingular $n \times n$ matrix with a nonzero cofactor $A_{nn}$, and set $c=\frac{\det(A)}{A_{nn}}$. Show that if we subtract $c$ from $a_{nn}$, then the resulting matrix will be singular.

Sol:
對修改過的矩陣 $A'$ 與原本的矩陣對第 $n$ row 展開。
$\det(A')=\sum_{j=1}^{n-1}a_{nj}A_{nj}+(a_{nn}-c)A_{nn}$ 
$\det(A)=\sum_{j=1}^{n-1}a_{nj}A_{nj}+a_{nn}A_{nn}$ 
兩式相減：$\det(A)-\det(A')=cA_{nn}\implies \det(A')=\det(A)-cA_{nn}=0$。

5. Let $A$ be a $k \times k$ matrix and let $B$ be an $(n-k)\times (n-k)$ matrix. Let $E=\begin{bmatrix}I_{k} & O \\ O & B\end{bmatrix},\quad F=\begin{bmatrix}A & O \\ O & I_{n-k}\end{bmatrix}, \quad C=\begin{bmatrix}A & O \\ O & B\end{bmatrix}$ where $I_{k}$ and $I_{n-k}$ are the $k \times k$ and $(n-k)\times (n-k)$ identity matrices. (a) Show that $\det(E)=\det(B)$.  (b) Show that $\det(C)=\det(A)\det(B)$. 

Sol:
(a)
假設 $E^{(r)}=\begin{bmatrix}I_{k-r} & O \\ O & B\end{bmatrix}$ $r=1, 2,\dots,k$ 。對任意 $r \leq k$，我們對第一行第一列進行拉普拉斯展開。得到：
$\det(E)=\det(E^{(0)})=\det(E^{(1)})=\dots=\det(E^{(k)})=\det(B)$。

(b)
通過觀察，我們可以得知：$C=EF$。
由於 $\det(E)=\det(B),\det(F)=\det(A)$，所以 $\det(C)=\det(A)\det(B)$！

6. (!) Show that evaluating the determinant of an $n \times n$ matrix by cofactors involves $(n!-1)$ additions and $\sum_{k=1}^{n-1} \frac{n!}{k!}$ multiplications. 

Sol:
I have no idea how to solve this problem...

7. (!) Let $B_{j}$ denote the matrix obtained by replacing the $j$th column of the identity matrix with a vector $\mathbf{b}=(b_{1},\dots b_{n})^{T}$. Prove that $b_{j}=\det(B_{j})\quad \text{for }j=1,\dots ,n$. 

Sol:
(I) Cramer's Rule
將其視為解 $I\mathbf{x}=\mathbf{b}$。
此時 $\mathbf{x}=\mathbf{b}$，所以 $x_{j}=b_{j}$。
由於克拉默法則，所以：$x_{j}=b_{j}=\frac{\det(B_{j})}{\det(I)}=\det(B_{j})$。

(II) Cofactor expansion
對 $B_{j}$ 的第 $j$ column 做拉普拉斯展開：$\det(B_{j})=\sum_{i=1}^{n}b_{i}(-1)^{i+j}\det(M_{ij})$ 。
因為 $M_{ij}$ 會將對應的 $i$ row 和 $j$ column 刪除，所以對於所有$i \neq j$ 都一定有一 row 為全零 $\implies \det(M_{ij})=0$。
也就是說，只有當 $i = j$ 時 $\det(M_{ij})$ 存在，且 $\det(M_{ij})=1\implies \det(B_{j})=b_{j}$。

8. Let $A$ be a nonsingular $n\times n$ matrix with $n>1$. Show that $\det(\text{Adj}A)=\det(A)^{n-1}$. 

Sol:
我們有 $A^{-1}A=I\implies \frac{1}{\det(A)}(\text{Adj}A)A=I$。
全部取行列式：$[\det(A)]^{-n}\det(\text{AdjA})\det(A)=1\implies \det(AdjA)=\det(A)^{n-1}$ 

9. Suppose that $Q$ is a matrix with the property $Q^{-1}=Q^{T}$. Show that $q_{ij}=\frac{Q_{ij}}{\det(Q)}$. ($Q_{ij}$ is the cofactor of $Q$)

Sol:
$\text{adj}Q=\det(Q)Q^{-1}=\det(Q)Q^{T}$ 
$Q_{ij}=\det(Q)q_{ij}\implies q_{ij}=\frac{Q_{ij}}{\det(Q)}$ 

10. Prove that if $\det(A)=0$ then $\det(\text{adj}A)=0$. 

Sol:
因為 $\det(A)=0$，我們可以得到 $A\text{adj}A=0$。
假設 $\det(\text{adj}A)\neq 0$，則該伴隨矩陣有逆。可以得到 $A=0\cdot(\text{adj}A)^{-1}=O$。
這就表示了 $\text{adjA}=O\implies \det(\text{adjA})=O$，與假設矛盾。
所以 $\det(\text{adjA})=0$。