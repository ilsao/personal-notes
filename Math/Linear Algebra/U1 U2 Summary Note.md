
# Matrix and System

## REF / RREF

這個到現在還沒掌握可以掛科了。

## 超定與欠定

對於一個 $m\times n$ 的矩陣 $A$：
- 超定：方程式數量 > 未知數數量 $m>n$ 
- 欠定：方程式數量 < 未知數數量 $m<n$ 

## 齊次系統

形如：$A\mathbf{x}=0$ 的系統。

最少會有一組零解，只有一組零解時稱矩陣 $A$ 非奇異的，且 $\det(A)\neq 0$。如果不只一組解，稱 $A$ 奇異的，且 $\det(A)=0$。

## 列運算表示法

- $R_{1} \leftrightarrow R_{2}$ 
- $(2)R_{1} \to R_{1}$ 
- $(-2)R_{1} + R_{2}\to R_{2}$ 

## 多項式曲線擬合

給定 $n$ 個點，尋找通過所有點的多項式：$p(x)=a_{0}+a_{1}x+\dots+a_{n}x^{n-1}$ 

注意最高次項為 $n-1$ 。

## 矩陣相等

1. 大小相等
2. 各項相同

## 矩陣乘法

若有 $AB=C$

$$
c_{ij}=\sum_{k=1}^{n}a_{ik}b_{kj}
$$

$Ab_{j}= c_{j}$ 

$a_{i}B=\vec{c}_{i}$

## 轉置矩陣

1. $(\alpha A)^{T}=\alpha A^{T}$ 
2. $(A+B)^{T}=A^{T}+B^{T}$ 
3. $(AB)^{T}=B^{T}A^{T}$ 
4. $(A^{n})^{T}=(A^{T})^{n}$ 

第三條的證明方法：展開 $(AB)^{T}$ 的各項並展開 $B^{T}A^{T}$ 的各項，對比發現相同。

第四條的證明方法：使用第三條，遞歸將 $A^{T}$ 從括號拆出去。

## 對稱

$A^{T}=A$ 則稱 $A$ 對稱。

## 單位矩陣

使用**標準基底向量(standard basis vector)** 來標示單位矩陣的 $j$th column。

通常使用 $e_{j}A$ 來提取矩陣的某 column。

## 矩陣逆運算

一個可逆矩陣只有唯一的逆。

證法：假設該矩陣有兩個逆，最後發現這兩個逆相同。

"奇異的" 這個詞不可以用在非方陣上，因為非方陣總是不可逆。

我們有幾種方法求逆：
- 將矩陣寫成**增廣矩陣(augmented matrix)** 形式：$(A|I)$ 然後想辦法通過列運算化成 $(I|A^{-1})$ 即可。
- $E_{k}\dots E_{1}A=I$ 則 $A^{-1}=E^{-1}_{1}\dots E_{k}^{-1}$。
- $A^{-1}=\frac{1}{\det(A)}\text{adj}A$  (由 $A\text{adj}A=\det(A)I$ 得出)

## 鄰接矩陣

如果 $V_{i} 與 V_{j}$ 之間有路徑，則 $a_{ij}=1$ 否則為零。

$A^{k}$ 後，$a_{ij}^{k}$ 表示 $V_{i}\to V_{j}$ 長度為 $k$ 的路徑數。

## 初等矩陣

通過單位矩陣進行一次初等列運算形成的矩陣。

左乘某矩陣，會對該矩陣應用該初等列運算。

右乘某矩陣，會對該矩陣應用對應的初等行運算。

$A$ 為一個 $n \times n$ 矩陣，則下列敘述互相等價：
- $A$ 可逆
- $\det(A)\neq 0$ 
- $Ax=\vec{b}$ 有唯一解 <---|
- $Ax=0$ 有唯一零解 --| 可以用來幫助證明
- $A$ 與單位矩陣行等價
- $A$ 可以寫成一系列初等矩陣相乘

## LU 分解

$U=E_{k}\dots E_{1}A$ 

$L=E_{1}^{-1}\dots E_{k}^{-1}$ 

## 分塊矩陣

### 分塊乘法

$(AB)_{ij}=\sum_{k=1}^{n}A_{ik}B_{kj}$

### 分塊轉置

先將每個分塊位置轉置，然後對每個分塊矩陣內部應用轉置：

$A=\begin{bmatrix}A_{11} & A_{12} \\ A_{21} & A_{22}\end{bmatrix}\implies A^{T}=\begin{bmatrix}A_{11}^{T} & A_{21}^{T} \\ A_{12}^{T} & A_{22}^{T}\end{bmatrix}$ 

## 外積展開(Outer Product Expansion)

$\mathbf{x}\mathbf{y}^{T}=\begin{bmatrix}x_{1} \\ \vdots \\ x_{n}\end{bmatrix}\begin{bmatrix}y_{1} & \dots & y_{n}\end{bmatrix}$ 

$XY^{T}=\begin{bmatrix}x_{1} & \dots & x_{n}\end{bmatrix}\begin{bmatrix}\vec{y}_{1} \\ \vdots \\ \vec{y}_{n}\end{bmatrix}$ 

例如：

$$\begin{align}
 & X=\begin{bmatrix}
3 & 2 \\
2 & 4 \\
1 & 2
\end{bmatrix}\quad Y=\begin{bmatrix}
1 & 2 \\
2 & 4 \\
3 & 1
\end{bmatrix} \\ \\
XY^{T} & =\begin{bmatrix}
3 & 2 \\
2 & 4 \\
1 & 2
\end{bmatrix}\begin{bmatrix}
1 & 2 & 3 \\
2 & 4 & 1
\end{bmatrix} \\
 & =\begin{bmatrix}
3 \\
2 \\
1
\end{bmatrix}\begin{bmatrix}
1 & 2 & 3
\end{bmatrix}+\begin{bmatrix}
2 \\
4 \\
2
\end{bmatrix}\begin{bmatrix}
2 & 4 & 1
\end{bmatrix} \\
 & =\begin{bmatrix}
3 & 6 & 9 \\
2 & 4 & 6 \\
1 & 2 & 3
\end{bmatrix}+\begin{bmatrix}
4 & 8 & 2 \\
8 & 16 & 4 \\
4 & 8 & 2
\end{bmatrix}
\end{align}$$

# Determinants

## 矩陣的行列式

$\det(A)=\sum_{k=1}^{n}a_{1k}(-1)^{1+k}M_{1k}$ 
$= \sum_{k=1}^{n}a_{1k}A_{1k}$ 

- 某行某列全零，$\det(A)=0$ $\implies$ 因為奇異的矩陣 $A$ 化成 RREF 必有一列全零。
- 兩行相同，$\det(A)=0$ 
- 某行爲另一行的 $k$ 倍，$\det(A)=0$ 
- $\det(A^{T})=\det(A)$ (數學歸納法證明，一個按列展開，一個按行展開)
- 三角矩陣行列式值為對角線元素相乘。(數學歸納法證明，且因為有 $\det(A^{T})=\det(A)$，所以只需證明下三角，上三角轉置過去就好)

## 行列式的性質

要先知道一個很重要的引理：$\sum_{k=1}^{n}a_{ik}A_{jk}=\begin{cases}\det(A) & \text{if }i=j \\ 0 & \text{if }i\neq j\end{cases}$ 

這個引理可以用 $j$th row 替換 $i$th row 證明。

交換兩列，行列式變號。

將某列乘 $\alpha$，行列式乘 $\alpha$。

將某列乘 $\alpha$ 加到另一列，行列式不變。

$\det(AB)=\det(A)\det(B)$ 

## 伴隨矩陣

$(\text{adj}A)_{ij}=(A_{ij})^{T}$ 

$A\text{adjA}=\det(A)I$ (可以由乘法展開並套用前述引理證明)

$\text{adj}(AB)=\text{adj}(A)\text{adj}(B)$ 

$(\text{adj}A)^{n}=\text{adj}A^{n}$

## 克拉默法則

$x_{i}=\frac{\det(A_{i})}{\det(A)}$ 

給定一個矩陣 $A$，如果想要計算 $A^{-1}$ 的第 $j$ column，可以將其視為解 $A\mathbf{x}=e_{j}$。利用克拉默法則很快就可以得出答案。

## 外積

假設有矩陣 $C= \begin{bmatrix}w_{1} & w_{2} & w_{3} \\ x_{1} & x_{2} & x_{3} \\ y_{1} & y_{2} & y_{3}\end{bmatrix}$，則：

$\mathbf{x}\times \mathbf{y}=C_{11}e_{1}+C_{12}e_{2}+C_{13}e_{3}$

且

$\det(C)=w_{1}C_{11}+w_{2}C_{12}+w_{3}C_{13}=\mathbf{w}^{T}(\mathbf{x}\times \mathbf{y})$ 

也可以用行列式表達：$\mathbf{x}\times \mathbf{y}=\begin{vmatrix}\mathbf{i} & \mathbf{j} & \mathbf{k} \\ x_{1} & x_{2} & x_{3} \\ y_{1} & y_{2} & y_{3}\end{vmatrix}$。