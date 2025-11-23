
如果 $V$ 是一個向量空間，取兩個 $V$ 中的向量。若二者內積為零，則稱此二向量**正交(orthogonal)**。

# The Scalar Product of $\mathbb{R}^{n}$ 

取 $\mathbb{R}^{n}$ 中兩向量 $\mathbf{x}$ 與 $\mathbf{y}$。

我們定義內積為：$\mathbf{x}^{T}\mathbf{y}$，或者 $\mathbf{x}\cdot \mathbf{y}$。若 $\mathbf{x}=(x_{1},\dots,x_{n})^{T}$ $\mathbf{y}=(y_{1},\dots,y_{n})^{T}$，則 $\mathbf{x}^{T}\mathbf{y}=x_{1}y_{1}+\dots+x_{n}y_{n}$。

## The Scalar Product in $\mathbb{R}^{2}$ and $\mathbb{R}^{3}$ 

對於 $\mathbf{x}$ 為 $\mathbb{R}^{2}$ 或 $\mathbb{R}^{3}$ 的向量，我們有：$||\mathbf{x}||=(\mathbf{x}^{T}\mathbf{x})^{1/2}$。

首先給一個定義：若 $\mathbf{x},\mathbf{y}$ 為 $\mathbb{R}^{2}$ 或 $\mathbb{R}^{3}$ 中的兩向量，則二向量的距離為 $||\mathbf{x}-\mathbf{y}||$。

再來一個高中學過的定理。

若 $\mathbf{x},\mathbf{y}$ 為 $\mathbb{R}^{2}$ 或 $\mathbb{R}^{3}$ 中的兩向量，且 $\theta$ 為兩向量夾角，則：

$$
\mathbf{x}^{T}\mathbf{y}=||\mathbf{x}|| \ ||\mathbf{y}||\cos \theta
$$

proof:
利用餘弦定理。
$\mathbf{x},\mathbf{y},\mathbf{y-x}$ 會構成一個三角形。
我們有：$||\mathbf{y}-\mathbf{x}||=||\mathbf{x}||^{2}+||\mathbf{y}||^{2}-2||\mathbf{x}|| \ ||\mathbf{y}||\cos \theta$。
移項化簡後得證。

我們可以如下計算單位向量：

$$
\mathbf{u}= \frac{1}{||\mathbf{x}||}\mathbf{x}\quad\text{and}\quad\mathbf{v}=\frac{1}{||\mathbf{y}||}\mathbf{y}
$$

並如下計算夾角餘弦值：

$$
\cos \theta=\frac{\mathbf{x}\cdot \mathbf{y}}{||\mathbf{x}|| \ ||\mathbf{y}||}=\mathbf{u}\cdot \mathbf{v}
$$

給出一個引理：Cauchy-Schwarz Inequality (柯西不等式)。

若 $\mathbf{x},\mathbf{y}$ 為 $\mathbb{R}^{2}$ 或 $\mathbb{R}^{3}$ 中的兩向量，則：

$$
|\mathbf{x}^{T}\mathbf{y}|\leq ||\mathbf{x}|| \ ||\mathbf{y}||
$$

其中，等號成立在某一向量為零向量，或者二向量平行。

我們還定義：若 $\mathbf{x},\mathbf{y}$ 為 $\mathbb{R}^{2}$ 或 $\mathbb{R}^{3}$ 中的兩向量且 $\mathbf{x}^{T}\mathbf{y}=0$，則 $\mathbf{x}$ 與 $\mathbf{y}$ 正交。

注意，這麼來說，$\mathbf{0}$ 與任意向量都正交。

## Scalar and Vector Projections

對一個與 $\mathbf{y}$ 不平行的向量 $\mathbf{x}$，我們可能想要將其表示成一個與 $\mathbf{y}$ 平行的向量和一個與 $\mathbf{y}$ 垂直的向量的和。

尋找該與 $\mathbf{y}$ 平行的向量的過稱就稱為 $\mathbf{x}$ 在 $\mathbf{y}$ 上的投影。

尋找投影我們需要 $\mathbf{y}$ 的單位向量 $\mathbf{u}=\frac{1}{||\mathbf{y}||}\mathbf{y}$ 幫忙，也就是表示成：$\alpha \mathbf{u}$ 的形式。

我們如下尋找 $\alpha$：$\alpha=||\mathbf{x}||\cos \theta=\frac{\mathbf{x}^{T}\mathbf{y}}{||\mathbf{y}||}$。

那麼投影就是：

$$
\alpha \mathbf{u}= \frac{\mathbf{x}^{T}\mathbf{y}}{||\mathbf{y}||} \frac{1}{||\mathbf{y}||}\mathbf{y}= \frac{\mathbf{x}^{T}\mathbf{y}}{||\mathbf{y}||^{2}}\mathbf{y}
$$

以下討論中所有向量皆為 $\mathbb{R}^{3}$ 中的向量。若 $\mathbf{N}$ 是一個非零向量，$P_{0}$ 是一個定點。則所有 $P$ 使得 $\vec{P_{0}P}$ 與 $\mathbf{N}$ 正交的集合，會在三維空間中構成一個平面，且 $N=(a,b,c)$ 為該平面的法向量並且 $P_{0}=(x_{0},y_{0},z_{0})$ 與 $P=(x,y,z)$ 會落在該平面上。

$$
(\vec{P_{0}}P)^{T}\mathbf{N}=0\implies a(x-x_{0})+b(y-y_{0})+c(z-z_{0})=0
$$

之前我們討論過兩個線性獨立的向量會在 $\mathbb{R}^{3}$ 中張出一個過原點平面。我們還知道，兩個向量的外積與二向量正交。那麼，就可以取二向量外積作為該平面的法向量。

至於如何計算某定點 $Q$ 到某平面的距離？(取線上或平面上一點與該定點相連，算該向量與法向量的 scalar projection)

考慮平面 $ax+by+cz=d$ 上任意向量 $\mathbf{P}$，則 $\mathbf{Q}-\mathbf{P}$ 平行 $\mathbf{N}$，且 $Q$ 到平面的距離為 $\mathbf{Q}-\mathbf{P}$ 投影到 $\mathbf{N}$ 上的那個 $\alpha$ 的值。

也就是：

$$
d= \frac{(\mathbf{Q}-\mathbf{P})\cdot \mathbf{N}}{||\mathbf{N}||}= \frac{\mathbf{Q}\cdot \mathbf{N}-\mathbf{P}\cdot \mathbf{N}}{||\mathbf{N}||}= \frac{\mathbf{Q}\cdot \mathbf{N}-d}{||\mathbf{N}||}
$$

需要注意的是，上式中 $d$ 有正負之差，代表該點處於平面的上方還是下方。真正的距離應該為：$|d|$。

通過 $\cos \theta= \frac{\mathbf{x}^{T}\mathbf{y}}{||\mathbf{x}|| \ ||\mathbf{y}||}$ 與 $\sin \theta=\sqrt{ 1-\cos^{2} \theta }$，我們有 $||\mathbf{x}\times\mathbf{y}||=||\mathbf{x}|| \ |\mathbf{y}|\sin \theta$。

統整一下！

對於求直線上最近的點，我們有以下解題步驟：
1. 取線上任一點 $P_{0}$，與線**方向向量** $\vec{v}$。
2. 對於給定的點 $P$，做向量 $\vec{P_{0}P}$ 並將 $\vec{P_{0}P}$ 投影到 $\vec{v}$。
3. **將該投影加上 $\vec{P_{0}}$。**(因為所得為 $\vec{P_{0}Q}$，$Q$ 才是所求的點)

注意，如果想求平面上最近的點，不是取平面上相異兩點當方向向量，因為該點可能不落在你選的直線上！！！

對於求平面上最近的點，我們有以下解題步驟：
1. 取平面上任一點 $P_{0}$，與**法向量** $\vec{n}$。
2. 對於給定的點 $P$，做向量 $\vec{P_{0}P}$ 並將 $\vec{P_{0}P}$ 對 $\vec{n}$ 做 vector projection。
3. **將 $P$ 減去該投影。**(因為所得為 $\vec{QP}$，$Q$ 才是所求的點)

對於線上或平面上求最近距離，我們有以下解題步驟：
1. 取線上任一點 $P_{0}$，與線**法向量** $\vec{n}$。
2. 對於給定的點 $P$，做向量 $\vec{P_{0}P}$ 並將 $\vec{P_{0}P}$ 對 $\vec{n}$ 做 scalar projection。
3. 將 scalar projection 的值取絕對值。

## Orthogonality in $\mathbb{R}^{n}$ 

其實這段也沒啥，就是說上述很多東西可以被拓展到 $\mathbb{R}^{n}$。

# Orthogonal Subspaces

給一波定義：給定兩個 $\mathbb{R}^{n}$ 的子空間 $X$ 和 $Y$，若任意 $\mathbf{x}\in X$ 且 $\mathbf{y}\in Y$ 都有 $\mathbf{x}^{T}\mathbf{y}=0$ 則稱 $X$ 和 $Y$ 正交。計做 $X\perp Y$。

給你個例子：$A$ 為 $m\times n$ 矩陣，而 $\mathbf{x}\in N(A)$，則 $A\mathbf{x}=\mathbf{0}$。所以，對任意 $A^{T}$ 的 column vector，都有 $\mathbf{x}^{T}\mathbf{y}=0$，所以 $N(A)$ 與 $\text{Col}(A^{T})$ 正交。

注意，$xy$ 平面組成的向量空間與 $yz$ 平面組成的向量空間並不正交。事實上，只有平面上的某些向量正交。

接下來再給一個定義：令 $Y$ 為 $\mathbb{R}^{n}$ 的子空間。由 $\mathbb{R}^{n}$ 中所有與任意 $Y$ 中向量正交的向量組成的集合被計為 $Y^{\perp}$。

$$
Y^{\perp}=\{\mathbf{x}\in \mathbb{R}^{n} \ | \ \mathbf{x}^{T}\mathbf{y}=0 \ \text{ for every } \ y\in Y\}
$$

$Y^{\perp}$ 稱作**正交補空間(orthogonal complement)**。

若 $X=\text{Span}(\mathbf{e_{1}}), \ Y=\text{Span}(\mathbf{e_{2}}), \ Z=\text{Span}(\mathbf{e_{3}})$，則：

$$
X^{\perp}=\text{Span}(\mathbf{e_{2}},\mathbf{e_{3}})\quad Y^{\perp}=\text{Span}(\mathbf{e_{1}},\mathbf{e_{3}})\quad Z^{\perp}=\text{Span}(\mathbf{e_{1}},\mathbf{e_{2}})
$$

我們有以下性質：
- 若 $X$ 與 $Y$ 都是 $\mathbb{R}^{n}$ 的正交子空間，則 $X\cap Y=\{\mathbf{0}\}$。
- 若 $Y$ 是 $\mathbb{R}^{n}$ 的子空間，則 $Y^{\perp}$ 也是 $\mathbb{R}^{n}$ 的子空間。

proof:
(1)
取 $\mathbf{x}\in X\cap Y$，因為 $X\perp Y$ 所以 $||\mathbf{x}||^{2}=\mathbf{x}^{T}\mathbf{x}=0\implies \mathbf{x}=\mathbf{0}$。
(2)
令 $\mathbf{x}\in Y^{\perp}$，$\mathbf{y}\in Y$，且 $\alpha$ 為標量。
$(\alpha \mathbf{x})^{T}\mathbf{y}=\alpha(\mathbf{x}^{T}\mathbf{y})=\alpha \cdot0=0\implies\alpha \mathbf{x}\in Y^{\perp}$ 
令 $\mathbf{x_{1}},\mathbf{x_{2}}\in Y^{\perp}$。
$(\mathbf{x_{1}}+\mathbf{x_{2}})^{T}\mathbf{y}=0\implies \mathbf{x_{1}}+\mathbf{x_{2}}\in Y^{\perp}$。
所以 $Y^{\perp}$ 也是 $\mathbb{R}^{n}$ 的子空間。

## Fundamental Subspaces

首先你要知道：$R(A)=\text{Col}(A)$。且 $R(A)$ 表示 $A$ 的 range。

我們有一個定理 **Fundamental Subspaces Theorem**：若 $A$ 為 $m\times n$ 矩陣，則 $N(A)=R(A^{T})^{\perp}$ 且 $N(A^{T})=R(A)^{\perp}$。

proof:
因為已知 $N(A)\perp R(A^{T})$，所以 $N(A)\subseteq R(A^{T})^{\perp}$。
反過來說，若 $\mathbf{x}$ 為 $R(A^{T})^{\perp}$ 中的任意向量，所以 $\mathbf{x}$ 與 $A^{T}$ 的任意 column vector 都正交，也就是 $A\mathbf{x}=\mathbf{0}$。這要求 $\mathbf{x}\in N(A)$，所以 $N(A)=R(A^{T})^{\perp}$。同理可證 $N(A^{T})=R(A)^{\perp}$。

# Tips

- 做不出來的時候回頭看看題目，說不定會有驚人發現！

# 重要例題

![[Pasted image 20251122194244.png]]

Sol:
容易想到柯西不等式。
注意，此處等號不能取，因為有關鍵字**線性獨立**。喔對，記得寫大於等於零。
$0\leq|\mathbf{x}^{T}\mathbf{y}|<6$ 

![[Pasted image 20251122200645.png]]

Sol:
真的是越活越退化了，這種題也要寫筆記了。
取線上一點 $\vec{P_{0}}=(0,1)$。
做 $\vec{P_{0}P}=(5,1)$。
投影到**方向向量** $\vec{v}=(1,2)\implies\left( \frac{7}{5}, \frac{14}{5} \right)$ 
將投影加上 $\vec{P_{0}}\implies\left( \frac{7}{5}, \frac{19}{5} \right)$ 

![[Pasted image 20251122210350.png]]

Sol:
(a)
看到圖片給了 $h$，表示 $h$ 是重要輔助線。
想辦法表明 $h$。
$h=||\mathbf{a_{1}}||\sin\theta\implies h^{2}=||\mathbf{a_{1}}||^{2}\sin^{2}\theta=||\mathbf{a_{1}}||^{2}(1-\cos^{2}\theta)$ 
$=||\mathbf{a_{1}}||^{2}-||\mathbf{a_{1}}||^{2}\left(  \frac{\mathbf{a_{1}}^{T}\mathbf{a_{2}}}{||\mathbf{a_{1}}||||\mathbf{a_{2}}||} \right)^{2}$ 
$\implies h^{2}||\mathbf{a_{2}}||^{2}=||\mathbf{a_{1}}||^{2}||\mathbf{a_{2}}||^{2}-(\mathbf{a_{1}}^{T}\mathbf{a_{2}})^{2}$ 
(b)
展開化簡就好。