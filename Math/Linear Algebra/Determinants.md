
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

- $\det(A^{T})=\det(A)$。

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
現在我們來講解為何 $\det(A^{*})=\det(A)$。
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
proof:
我們可以將 $A$ 在有限步驟內化為 REF：$U=E_{k}\dots E_{1}A$。
$\det(U)=\det(E_{k})\dots \det(E_{1})\det(A)$ 。因為所有初等矩陣的行列式值皆不為零，所以 $\det(A)=0\Leftrightarrow\det(U)=0$。當 $\det(A)\neq 0$ 時，因為 $U$ 為上三角矩陣且對角線上的元素值皆為一，所以 $\det(U)=1$。

$$
\det(EA)=\det(E)\det(A)=\det(AE)
$$

當 $A,B$ 為大小 $n \times n$ 大小的矩陣時：

$$
\det(AB)=\det(A)\det(B)
$$

proof:
當 $B$ 不可逆時，$AB$ 也不可逆。
($Bx=0\implies (AB)x=0$ 且 $x\neq 0$)
所以此時 $\det(AB)=0=\det(A)\det(B)$
若 $B$ 可逆，則：
$\det(AB)=\det(AE_{1}\dots E_{n})=\det(A)\det(E_{1}\dots E_{n})$ 
$=\det(A)\det(B)$

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