
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

我們有一個定理 **Fundamental Subspaces Theorem**：若 $A$ 為 $m\times n$ 矩陣，則：

$$N(A)=R(A^{T})^{\perp}\text{ } 且 \text{ }N(A^{T})=R(A)^{\perp}$$

proof:
因為已知 $N(A)\perp R(A^{T})$，所以 $N(A)\subseteq R(A^{T})^{\perp}$。
反過來說，若 $\mathbf{x}$ 為 $R(A^{T})^{\perp}$ 中的任意向量，所以 $\mathbf{x}$ 與 $A^{T}$ 的任意 column vector 都正交，也就是 $A\mathbf{x}=\mathbf{0}$。這要求 $\mathbf{x}\in N(A)$，所以 $N(A)=R(A^{T})^{\perp}$。同理可證 $N(A^{T})=R(A)^{\perp}$。

雖然你不一定想要，但是再送你一些免費的定理～

若 $S$ 是 $\mathbb{R}^{n}$ 的子空間，則：

$$\text{dim }S+\text{dim }S^{\perp}=n$$

此外，若 $\{\mathbf{x_{1}},\dots,\mathbf{x}_{r}\}$ 為 $S$ 的基底，$\{\mathbf{x}_{r+1},\dots,\mathbf{x}_{n}\}$ 為 $S^{\perp}$ 的基底，則 $\{\mathbf{x_{1}},\dots,\mathbf{x}_{r},\dots,\mathbf{x}_{n}\}$ 為 $\mathbb{R}^{n}$ 的一組基底。

proof:
若 $S=\{\mathbf{0}\}$，則 $S^{\perp}=\mathbb{R}^{n}$。滿足 $\text{dim }S+\text{dim }S^{\perp}=n$。
若 $S\neq\{\mathbf{0}\}$，則令 $X$ 為 $r\times n$ 大小的矩陣。$X$ 的第 $i$ 個 row 定義為 $\mathbf{x}_{i}^{T}$。
那麼，$\text{rank}(X)=r$，且 $R(X^{T})=S$。
由上一個定理，我們有：$S^{\perp}=R(X^{T})^{\perp}=N(X)$。
根據 rank-nullity theorem，我們有 $\text{dim }N(X)=n-r$。
想證明  $\{\mathbf{x_{1}},\dots,\mathbf{x}_{r},\dots,\mathbf{x}_{n}\}$ 張出 $\mathbb{R}^{n}$，我們只需要證明 $\{\mathbf{x_{1}},\dots,\mathbf{x}_{r},\dots,\mathbf{x}_{n}\}$ 線性獨立。
設 $c_{1}\mathbf{x_{1}}+\dots+c_{r}\mathbf{x}_{r}+c_{r+1}\mathbf{x}_{r+1}+\dots+c_{n}\mathbf{x}_{n}=\mathbf{0}$。
令 $\mathbf{y}=c_{1}\mathbf{x}_{1}+\dots+c_{r}\mathbf{x}_{r}$，$\mathbf{z}=c_{r+1}\mathbf{x}_{r+1}+\dots+c_{n}\mathbf{x}_{n}$。
則 $\mathbf{y}+\mathbf{z}=\mathbf{0}\implies \mathbf{y}=-\mathbf{z}$。
說明 $\mathbf{y}$ 與 $\mathbf{z}$ $\in S\cap S^{\perp}=\{\mathbf{0}\}\implies \{\mathbf{x_{1}},\dots,\mathbf{x}_{r},\dots,\mathbf{x}_{n}\}$ 線性獨立
$\implies\{\mathbf{x_{1}},\dots,\mathbf{x}_{r},\dots,\mathbf{x}_{n}\}$ 張出 $\mathbb{R}^{n}$。 

來一波定義：若 $U$ 和 $V$ 為 $W$ 的子空間，取 $\mathbf{u}\in U$，$\mathbf{v}\in V$。若任意 $\mathbf{w}\in W$ 都可以被唯一的表示成 $\mathbf{w}=\mathbf{u}+\mathbf{v}$，則稱 $W$ 是 $U$ 和 $V$ 的**直和(direct sum)**，且記為 $W=U\oplus V$。

給你個定理：若 $S$ 是 $\mathbb{R}^{n}$ 的子空間，則：

$$
\mathbb{R}^{n}=S\oplus S^{\perp}
$$

proof:
這個結論在 $S=\{\mathbf{0}\}$ 或 $S=\mathbb{R}^{n}$ 時很 trivial。
當 $\text{dim }S=r$，且 $0<r<n$ 時：
任意 $\mathbf{x}\in \mathbb{R}^{n}$ 都可以被表示為 $\mathbf{x} = c_{1}\mathbf{x_{1}}+\dots+c_{r}\mathbf{x}_{r}+c_{r+1}\mathbf{x}_{r+1}+\dots+c_{n}\mathbf{x}_{n}$ 。
又 $\mathbf{y}=c_{1}\mathbf{x}_{1}+\dots+c_{r}\mathbf{x}_{r}$，$\mathbf{z}=c_{r+1}\mathbf{x}_{r+1}+\dots+c_{n}\mathbf{x}_{n}$ 且 $\mathbf{y}\in S$ 且 $\mathbf{z}\in S^{\perp}$。
所以我們有 $\mathbf{x}=\mathbf{y}+\mathbf{z}$。
來證明唯一性，令 $\mathbf{x}=\mathbf{u}+\mathbf{v}$ 且 $\mathbf{u}\in S$，$\mathbf{v}\in S^{\perp}$。
則 $\mathbf{u}+\mathbf{v}=\mathbf{x}=\mathbf{y}+\mathbf{z}\implies \mathbf{u}-\mathbf{y}=\mathbf{z}-\mathbf{v}$。
因為 $\mathbf{u}-\mathbf{y}\in S$ 且 $\mathbf{z}-\mathbf{v}\in S^{\perp}$，所以 $\mathbf{u}-\mathbf{y}$ 與 $\mathbf{z}-\mathbf{v}$ 都在 $S\cap S^{\perp}=\{\mathbf{0}\}$ 中。
所以 $\mathbf{u}=\mathbf{y}$，$\mathbf{v}=\mathbf{z}$。

都送你一個定理了，那就不吝色的再送你一個叭～

若 $S$ 為 $\mathbb{R}^{n}$ 的子空間，則：

$$
(S^{\perp})^{\perp}=S
$$

proof:
令 $\mathbf{z}\in (S^{\perp})^{\perp}$，$\mathbf{u}\in S$，$\mathbf{v}\in S^{\perp}$。
則因為 $(S^{\perp})^{\perp}\in \mathbb{R}^{n}$，所以 $\mathbf{z}$ 可以被唯一的表達成：$\mathbf{z}=\mathbf{u}+\mathbf{v}$。
因為 $\mathbf{v}\in S^{\perp}$，所以會與 $\mathbf{z}$ 和 $\mathbf{u}$ 都正交。
$0=\mathbf{v}^{T}\mathbf{z}=\mathbf{v}^{T}(\mathbf{u}+\mathbf{v})=\mathbf{v}^{T}\mathbf{u}+\mathbf{v}^{T}\mathbf{v}=\mathbf{v}^{T}\mathbf{v}$ 
所以 $\mathbf{v}=\mathbf{0}$，$\mathbf{z}=\mathbf{u}$。
所以 $S=(S^{\perp})^{\perp}$。

回想 $N(A)=R(A^{T})^{\perp}\text{ } 且 \text{ }N(A^{T})=R(A)^{\perp}$，根據上述定理我們有：

$$
N(A)^{\perp}=R(A^{T})\text{ 且 }N(A^{T})^{\perp}=R(A)
$$

接下來我們要說一個聽起來很牛逼的東西！

若 $A$ 為 $m\times n$ 矩陣，且 $\mathbf{b}\in \mathbb{R}^{m}$。則不是存在 $\mathbf{x}\in \mathbb{R}^{n}$ 使得 $A\mathbf{x}=\mathbf{b}$ 就是存在 $\mathbf{y}\in \mathbb{R}^{m}$ 使得 $A^{T}\mathbf{y}=\mathbf{0}$ 且 $\mathbf{y}^{T}\mathbf{b}\neq 0$。

先搞清楚這個定理在講啥？

很明顯 $A\mathbf{x}=\mathbf{b}$ 是在說明系統有解的情況。

那 $A^{T}\mathbf{y}=\mathbf{0}$ 說明的是什麼？Oh，原來想說明 $\mathbf{y}\in N(A^{T})=R(A)^{\perp}$ 呀！

$R(A)$ 指的是 $A$ 的 column space 對吧？根據上述我們還知道 $\mathbf{y}$ 是 $A$ 的 column space 的正交補，所以如果 $\mathbf{b}$ 與 $\mathbf{y}$ 不正交 ($\mathbf{y}^{T}\mathbf{b}\neq 0$)，就說明 $\mathbf{b}\not\in R(A)=\text{Col}(A)$，也就是系統無解！

希望下圖能幫助你理解：

![[Pasted image 20251123210430.png]]

接下來我們要講一個很厲害的東西，一個 $m\times n$ 的 $A$ 矩陣可以將自己的 column space 一對一對應到自己的 row space 上。

以下我們將 $A$ 視為一個 $\mathbb{R}^{n}$ 到 $\mathbb{R}^{m}$ 上的線性轉換，即 $\mathbf{x}\in \mathbb{R}^{n}\to A\mathbf{x}\in \mathbb{R}^{m}$

因為 $R(A^{T})$ 與 $N(A)$ 為正交補，所以：$\mathbb{R}^{n}=R(A^{T})\oplus N(A)$。

那麼任意 $\mathbf{x}\in \mathbb{R}^{n}$ 都可以寫成 $\mathbf{x}=\mathbf{y}+\mathbf{z}$，其中 $\mathbf{y}\in R(A^{T})$ 且 $\mathbf{z}\in N(A)$。

則：$A\mathbf{x}=A\mathbf{y}+A\mathbf{z}=A\mathbf{y}$。(因為 $\mathbf{z}\in N(A)$)

也就是說 $R(A)=\{A\mathbf{x}|\mathbf{x\in \mathbb{R}^{n}}\}=\{A\mathbf{y}|\mathbf{y}\in R(A^{T})\}$。

如果我們將 $A$ 的定義域限定為 $R(A^{T})$，則 $A$ 將 $R(A^{T})$ 映射到 $R(A)$，且映射是一對一的。

假設 $\mathbf{x}_{1},\mathbf{x}_{2}\in R(A^{T})$，且 $A\mathbf{x}_{1}=A\mathbf{x}_{2}$。

則有 $A(\mathbf{x}_{1}-\mathbf{x}_{2})=\mathbf{0}$。因為 $\mathbf{x_{1}}-\mathbf{x_{2}} \in R(A^{T})\cap N(A)=\{\mathbf{0}\}$ (這裡不要求 $N(A)=\{\mathbf{0}\}$)，所以有 $\mathbf{x_{1}}=\mathbf{x_{2}}$。

因為這種對應是一對一的，所以可將 $A$ 視為在 $R(A)$ 到 $R(A^{T})$ 上的轉換可逆(不論是否在 $\mathbb{R}^{n}$ 上可逆！)。

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