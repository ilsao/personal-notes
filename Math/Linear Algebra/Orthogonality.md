
如果 $V$ 是一個向量空間，取兩個 $V$ 中的向量。若二者內積為零，則稱此二向量**直交(orthogonal)**。

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

我們還定義：若 $\mathbf{x},\mathbf{y}$ 為 $\mathbb{R}^{2}$ 或 $\mathbb{R}^{3}$ 中的兩向量且 $\mathbf{x}^{T}\mathbf{y}=0$，則 $\mathbf{x}$ 與 $\mathbf{y}$ 直交。

注意，這麼來說，$\mathbf{0}$ 與任意向量都直交。

## Scalar and Vector Projections

對一個與 $\mathbf{y}$ 不平行的向量 $\mathbf{x}$，我們可能想要將其表示成一個與 $\mathbf{y}$ 平行的向量和一個與 $\mathbf{y}$ 垂直的向量的和。

尋找該與 $\mathbf{y}$ 平行的向量的過稱就稱為 $\mathbf{x}$ 在 $\mathbf{y}$ 上的投影。

尋找投影我們需要 $\mathbf{y}$ 的單位向量 $\mathbf{u}=\frac{1}{||\mathbf{y}||}\mathbf{y}$ 幫忙，也就是表示成：$\alpha \mathbf{u}$ 的形式。

我們如下尋找 $\alpha$：$\alpha=||\mathbf{x}||\cos \theta=\frac{\mathbf{x}^{T}\mathbf{y}}{||\mathbf{y}||}$。

那麼投影就是：

$$
\alpha \mathbf{u}= \frac{\mathbf{x}^{T}\mathbf{y}}{||\mathbf{y}||} \frac{1}{||\mathbf{y}||}\mathbf{y}= \frac{\mathbf{x}^{T}\mathbf{y}}{||\mathbf{y}||^{2}}\mathbf{y}
$$

以下討論中所有向量皆為 $\mathbb{R}^{3}$ 中的向量。若 $\mathbf{N}$ 是一個非零向量，$P_{0}$ 是一個定點。則所有 $P$ 使得 $\vec{P_{0}P}$ 與 $\mathbf{N}$ 直交的集合，會在三維空間中構成一個平面，且 $N=(a,b,c)$ 為該平面的法向量並且 $P_{0}=(x_{0},y_{0},z_{0})$ 與 $P=(x,y,z)$ 會落在該平面上。

$$
(\vec{P_{0}}P)^{T}\mathbf{N}=0\implies a(x-x_{0})+b(y-y_{0})+c(z-z_{0})=0
$$

之前我們討論過兩個線性獨立的向量會在 $\mathbb{R}^{3}$ 中張出一個過原點平面。我們還知道，兩個向量的外積與二向量直交。那麼，就可以取二向量外積作為該平面的法向量。

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

給一波定義：給定兩個 $\mathbb{R}^{n}$ 的子空間 $X$ 和 $Y$，若任意 $\mathbf{x}\in X$ 且 $\mathbf{y}\in Y$ 都有 $\mathbf{x}^{T}\mathbf{y}=0$ 則稱 $X$ 和 $Y$ 直交。計做 $X\perp Y$。

給你個例子：$A$ 為 $m\times n$ 矩陣，而 $\mathbf{x}\in N(A)$，則 $A\mathbf{x}=\mathbf{0}$。所以，對任意 $A^{T}$ 的 column vector，都有 $\mathbf{x}^{T}\mathbf{y}=0$，所以 $N(A)$ 與 $\text{Col}(A^{T})$ 直交。

注意，**$xy$ 平面組成的向量空間與 $yz$ 平面組成的向量空間並不直交**。事實上，只有平面上的某些向量直交。

接下來再給一個定義：令 $Y$ 為 $\mathbb{R}^{n}$ 的子空間。由 $\mathbb{R}^{n}$ 中所有與任意 $Y$ 中向量直交的向量組成的集合被計為 $Y^{\perp}$。

$$
Y^{\perp}=\{\mathbf{x}\in \mathbb{R}^{n} \ | \ \mathbf{x}^{T}\mathbf{y}=0 \ \text{ for every } \ y\in Y\}
$$

$Y^{\perp}$ 稱作**直交補空間(orthogonal complement)**。

若 $X=\text{Span}(\mathbf{e_{1}}), \ Y=\text{Span}(\mathbf{e_{2}}), \ Z=\text{Span}(\mathbf{e_{3}})$，則：

$$
X^{\perp}=\text{Span}(\mathbf{e_{2}},\mathbf{e_{3}})\quad Y^{\perp}=\text{Span}(\mathbf{e_{1}},\mathbf{e_{3}})\quad Z^{\perp}=\text{Span}(\mathbf{e_{1}},\mathbf{e_{2}})
$$

我們有以下性質：
- 若 $X$ 與 $Y$ 都是 $\mathbb{R}^{n}$ 的直交子空間，則 $X\cap Y=\{\mathbf{0}\}$。
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
反過來說，若 $\mathbf{x}$ 為 $R(A^{T})^{\perp}$ 中的任意向量，所以 $\mathbf{x}$ 與 $A^{T}$ 的任意 column vector 都直交，也就是 $A\mathbf{x}=\mathbf{0}$。這要求 $\mathbf{x}\in N(A)$，所以 $N(A)=R(A^{T})^{\perp}$。同理可證 $N(A^{T})=R(A)^{\perp}$。

雖然你不一定想要，但是再送你一些免費的定理～

若 $S$ 是 $\mathbb{R}^{n}$ 的子空間，則：

$$\text{dim }S+\text{dim }S^{\perp}=n$$

此外，若 $\{\mathbf{x_{1}},\dots,\mathbf{x}_{r}\}$ 為 $S$ 的基底，$\{\mathbf{x}_{r+1},\dots,\mathbf{x}_{n}\}$ 為 $S^{\perp}$ 的基底，則 $\{\mathbf{x_{1}},\dots,\mathbf{x}_{r},\dots,\mathbf{x}_{n}\}$ 為 $\mathbb{R}^{n}$ 的一組基底。

proof:
若 $S=\{\mathbf{0}\}$，則 $S^{\perp}=\mathbb{R}^{n}$。滿足 $\text{dim }S+\text{dim }S^{\perp}=n$。
若 $S\neq\{\mathbf{0}\}$，則**令 $X$ 為 $r\times n$ 大小的矩陣。$X$ 的第 $i$ 個 row 定義為 $\mathbf{x}_{i}^{T}$**。
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
因為 $\mathbf{v}\in S^{\perp}$，所以會與 $\mathbf{z}$ 和 $\mathbf{u}$ 都直交。
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

$R(A)$ 指的是 $A$ 的 column space 對吧？根據上述我們還知道 $\mathbf{y}$ 是 $A$ 的 column space 的直交補，所以如果 $\mathbf{b}$ 與 $\mathbf{y}$ 不直交 ($\mathbf{y}^{T}\mathbf{b}\neq 0$)，就說明 $\mathbf{b}\not\in R(A)=\text{Col}(A)$，也就是系統無解！

希望下圖能幫助你理解：

![[Pasted image 20251123210430.png]]

接下來我們要講一個很厲害的東西，一個 $m\times n$ 的 $A$ 矩陣可以將自己的 column space 一對一對應到自己的 row space 上。

以下我們將 $A$ 視為一個 $\mathbb{R}^{n}$ 到 $\mathbb{R}^{m}$ 上的線性轉換，即 $\mathbf{x}\in \mathbb{R}^{n}\to A\mathbf{x}\in \mathbb{R}^{m}$

因為 $R(A^{T})$ 與 $N(A)$ 為直交補，所以：$\mathbb{R}^{n}=R(A^{T})\oplus N(A)$。

那麼任意 $\mathbf{x}\in \mathbb{R}^{n}$ 都可以寫成 $\mathbf{x}=\mathbf{y}+\mathbf{z}$，其中 $\mathbf{y}\in R(A^{T})$ 且 $\mathbf{z}\in N(A)$。

則：$A\mathbf{x}=A\mathbf{y}+A\mathbf{z}=A\mathbf{y}$。(因為 $\mathbf{z}\in N(A)$)

也就是說 $R(A)=\{A\mathbf{x}|\mathbf{x\in \mathbb{R}^{n}}\}=\{A\mathbf{y}|\mathbf{y}\in R(A^{T})\}$。

如果我們將 $A$ 的定義域限定為 $R(A^{T})$，則 $A$ 將 $R(A^{T})$ 映射到 $R(A)$，且映射是一對一的。

假設 $\mathbf{x}_{1},\mathbf{x}_{2}\in R(A^{T})$，且 $A\mathbf{x}_{1}=A\mathbf{x}_{2}$。

則有 $A(\mathbf{x}_{1}-\mathbf{x}_{2})=\mathbf{0}$。因為 $\mathbf{x_{1}}-\mathbf{x_{2}} \in R(A^{T})\cap N(A)=\{\mathbf{0}\}$ (這裡不要求 $N(A)=\{\mathbf{0}\}$)，所以有 $\mathbf{x_{1}}=\mathbf{x_{2}}$。

因為這種對應是一對一的，所以可將 $A$ 視為在 $R(A)$ 到 $R(A^{T})$ 上的轉換可逆(不論是否在 $\mathbb{R}^{n}$ 上可逆！)。

# Least Squares Problems

## Least Squares Solutions of Overdetermined Systems

對於一個 $m\times n$ 超定系統，很可能系統 $A\mathbf{x}=\mathbf{b}$ 無解。

我們首先定義**殘差(residual)**：

$$
r(\mathbf{x})=\mathbf{b}-A\mathbf{x}
$$

我們定義 $\mathbf{b}$ 到 $A\mathbf{x}$ 的距離為：

$$
||\mathbf{b}-A\mathbf{x}||=||r(\mathbf{x})||
$$

如果你想找 $\mathbf{\hat{x}}\in \mathbb{R}^{n}$ 使得 $||b-A\mathbf{\hat{x}}||$ 最小，則此類問題稱為 Least Squares Solution。

閒話少說，直接給定理。

令 $S$ 為 $\mathbb{R}^{m}$ 的子空間。對於任意 $\mathbf{b}\in \mathbb{R}^{m}$ 都有唯一的 $\mathbf{p}\in S$ 最靠近 $\mathbf{b}$，即：

$$
||\mathbf{b}-\mathbf{y}||>||\mathbf{b}-\mathbf{p}||
$$

其中 $\mathbf{y}\in S$ 且 $\mathbf{y}\neq \mathbf{p}$。而且，$\mathbf{p}\in S$ 最靠近 $\mathbf{b}\Leftrightarrow\mathbf{b}-\mathbf{p}\in S^{\perp}$。

proof:
因為 $\mathbb{R}^{m}=S\oplus S^{\perp}$，任意 $\mathbf{b}\in \mathbb{R}^{m}$ 都可以被唯一的表示成 $\mathbf{b}=\mathbf{p}+\mathbf{z}$，其中 $\mathbf{p}\in S$，$\mathbf{z}\in S^{\perp}$。
若 $\mathbf{y}$ 為任意 $S$ 中其他向量，則：$||\mathbf{b}-\mathbf{y}||^{2}=||(\mathbf{b}-\mathbf{p})+(\mathbf{p}-\mathbf{y})||^{2}$。
因為 $\mathbf{b}-\mathbf{p}=\mathbf{z}\in S^{\perp}$ 且 $\mathbf{p-\mathbf{y}}\in S$，由畢氏定理有：$||\mathbf{b}-\mathbf{y}||^{2}=||\mathbf{b}-\mathbf{p}||^{2}+||\mathbf{p}-\mathbf{y}||^{2}$。
($||\mathbf{u}+\mathbf{v}||^{2}=||\mathbf{u}||^{2}+||\mathbf{v}||^{2}$)
所以，$||\mathbf{b}-\mathbf{y}||>||\mathbf{b}-\mathbf{p}||$。也就是說，若 $\mathbf{p}\in S$ 且 $\mathbf{b}-\mathbf{p}\in S^{\perp}$ 則 $\mathbf{p}$ 就是 $S$ 中最靠近 $\mathbf{b}$ 的向量。
反過來說，若 $\mathbf{q}\in S$ 且 $\mathbf{b}-\mathbf{q}\not\in S^{\perp}$，則 $||\mathbf{b}-\mathbf{q}||>||\mathbf{b}-\mathbf{p}||$。

對於上述引理的特殊情況 $\mathbf{b}\in S$，會有 $\mathbf{b}=\mathbf{p}+\mathbf{z}$ 其中 $\mathbf{p}=\mathbf{b}$，$\mathbf{z}=\mathbf{0}$。

當 $\mathbf{\hat{x}}$ 為 least squares problem $A\mathbf{x}=\mathbf{b}$ 的解 $\iff$ $\mathbf{p}=A\mathbf{\hat{x}}$ 是 $R(A)$ 中最靠近 $\mathbf{b}$ 的向量。

其中，向量 $\mathbf{p}$ 被稱為 $\mathbf{b}$ 到 $R(A)$ 的投影。(the projection of $\mathbf{b}$ onto $R(A)$)

並且根據上述定理我們有：

$$
\mathbf{b}-\mathbf{p}=\mathbf{b}-A\mathbf{\hat{x}}=r(\mathbf{\hat{x}})
$$

殘差必須垂直 $R(A)$，也就是：

$$
r(\mathbf{\hat{x}})\in R(A)^{\perp}
$$

那怎麼找 $\mathbf{\hat{x}}$？

我們有 $r(\mathbf{\hat{x}})\in R(A)^{\perp}=N(A^{T})$，也就是 $\mathbf{0}=A^{T}r(\mathbf{\hat{x}})=A^{T}(\mathbf{b}-A\mathbf{\hat{x}})$，也就等於求解 $A^{T}A\mathbf{x}=A\mathbf{b}$。

我們將 $A^{T}A\mathbf{x}=A^{T}\mathbf{x}$ 稱為 **normal equation**。

送你個定理(我不要哇！！！)：

若 $A$ 是一個 $m\times n$ 大小矩陣且秩為 $n$，normal equation：

$$
A^{T}A\mathbf{x}=A^{T}\mathbf{b}
$$

有唯一解：

$$
\mathbf{\hat{x}}=(A^{T}A)^{-1}A^{T}\mathbf{b}
$$

且 $\mathbf{\hat{x}}$ 是 least squares problem $A\mathbf{x}=\mathbf{b}$ 的唯一解。(the unique least squares solution of the system)

proof:
考慮 $A^{T}A\mathbf{x}=\mathbf{0}$。令 $\mathbf{z}$ 為他的解，則 $A\mathbf{z}\in N(A^{T})$ 且 $A\mathbf{z}\in R(A)$。因為 $A\mathbf{z}\in N(A^{T})\cap R(A)=\{\mathbf{0}\}$，所以 $A\mathbf{z}=\mathbf{0}$。
又因為 $A$ 的秩為 $n$，所以 $A$ 的 column vectors 線性獨立 $\implies A\mathbf{z}=\mathbf{0}$ 只有零解 $\mathbf{z}=\mathbf{0}\implies A^{T}A\mathbf{x}=\mathbf{0}$ 只有零解。
$\implies A^{T}A$ 可逆 $\mathbf{\hat{x}}=(A^{T}A)^{-1}A\mathbf{b}$ 唯一且為 least squares solution $A\mathbf{x}=\mathbf{b}$ 的唯一解。

我們可以通過：

$$\mathbf{p}=A\mathbf{\hat{x}}=A(A^{T}A)^{-1}A\mathbf{b}$$

尋找 $R(A)$ 上的  projection vector，使得 $\mathbf{p}$ 與 $\mathbf{b}$ 最近。

我們將 $P=A(A^{T}A)^{-1}A$ 稱為**投影矩陣(projection matrix)**。

如果給定一些數據點，找線性回歸：

$$
y=c_{0}+c_{1}x
$$

我們可以考慮 least squares problem：

$$
\begin{bmatrix}
1 & x_{1} \\
1 & x_{2} \\
\vdots & \vdots \\
1 & x_{m}
\end{bmatrix}\begin{bmatrix}
c_{0} \\
c_{1}
\end{bmatrix}
=\begin{bmatrix}
y_{1} \\
y_{2} \\
\vdots \\
y_{m}
\end{bmatrix}
$$

# Inner Product Spaces

## Definition and Examples

對於向量空間 $V$ 的內積是一個運算使得每一對 $V$ 中的向量 $\mathbf{x}$ 與 $\mathbf{y}$ 都能得到一個實數 $\langle \mathbf{x},\mathbf{y} \rangle$ 滿足下列條件：
1. $\langle \mathbf{x},\mathbf{x} \rangle \geq 0$ 且等號成立 $\iff \mathbf{x}=0$ 
2. $\langle \mathbf{x},\mathbf{y} \rangle = \langle \mathbf{y},\mathbf{x} \rangle\quad\forall \mathbf{x},\mathbf{y}\in V$ 
3. $\langle \alpha \mathbf{x}+\beta \mathbf{y},\mathbf{z} \rangle =\alpha \langle \mathbf{x},\mathbf{z} \rangle+\beta \langle \mathbf{y},\mathbf{z} \rangle\quad\forall \mathbf{x},\mathbf{y},\mathbf{z}\in V$ 與任意標量 $\alpha,\beta$ 

一個有定義內積的向量空間 $V$ 被稱為**內積空間(Inner product space)**。

### The Vector Space $\mathbb{R}^{n}$ 

$\mathbb{R}^{n}$ 上的標準內積就是 scalar product：

$$
\langle \mathbf{x},\mathbf{y} \rangle  =\mathbf{x}^{T}\mathbf{y}
$$

若給定一個向量 $\mathbf{w}$ 為全正數項，我們還可以如下定義內積：

$$
\langle \mathbf{x},\mathbf{y} \rangle =\sum_{i=1}^{n}x_{i}y_{i}w_{i}

$$

其中 $w_{i}$ 項稱為**權重(weights)**。

### The Vector Space $\mathbb{R}^{m\times n}$ 

取 $A,B\in \mathbb{R}^{m\times n}$，我們定義內積：

$$
\langle A,B \rangle =\sum_{i=1}^{m}\sum_{j=1}^{n}a_{ij}b_{ij}
$$

也就是說，把 $A,B$ 的每一項按 row 攤平，然後當成一個 $\mathbb{R}^{mn}$ 的向量做內積。

### The Vector Space $C[a,b]$ 

我們如下定義 $C[a,b]$ 中的內積：

$$
\langle f,g \rangle=\int_{a}^{b}f(x)g(x) \ dx
$$

注意到：

$$
\langle f,f \rangle =\int_{a}^{b}(f(x))^{2}\ dx\geq 0
$$

若在 $x_{0}\in[a,b]$ 時 $f(x_{0})\neq 0$，因為 $(f(x))^{2}$ 連續，所以存在一個區間 $I\in[a,b]$ 使得 $(f(x))^{2}\geq \frac{(f(x_{0}))^{2}}{2}\quad\forall x\in I$ 。若我們令 $I$ 的長度為 $p$，則：

$$
\langle f,f \rangle =\int_{a}^{b}(f(x))^{2} \ dx\geq \int_{I}(f(x))^{2} \ dx \geq \frac{(f(x_{0}))^{2}p}{2}>0
$$

所以，想要 $\langle f,f \rangle=0\iff f(x)=0$。

剩餘兩點定義的驗證就留給你們吧！

若我們令 $w(x)$ 為正的連續函數 $\in [a,b]$，則：

$$
\langle f,g \rangle =\int_{a}^{b}f(x)g(x)w(x) \ dx
$$

同樣定義了內積。

其中 $w(x)$ 稱為**權重函數(weight function)**，所以 $C[a,b]$ 上的內積可以被定義成不同形式。

### The Vector Space $P_{n}$ 

令 $x_{1},x_{2},\dots,x_{n}$ 為相異實數。對於任意一對 $P_{n}$ 中的多項式：

$$
\langle p,q \rangle =\sum_{i=1}^{n}p(x_{i})q(x_{i})
$$

注意到：

$$
\langle p,p \rangle =\sum_{i=1}^{n}(p(x_{i}))^{2}\geq 0
$$

如果 $\langle p,p \rangle=0$ 則 $x_{1},\dots,x_{n}$ 必須為 $p(x)=0$ 的根。因為 $\text{deg }p(x)<n$，最多只能有 $n-1$ 個根，所以此情況下 $p(x)$ 必定等於零多項式。

若 $w(x)$ 為正的函數，則：

$$
\langle p,q \rangle =\sum_{i=1}^{n}p(x_{i})q(x_{i})w(x_{i})
$$

也定義了 $P_{n}$ 上的內積。

## Basic Properties of Inner Product Spaces

所有在 5.1 節的結果都可以被套用到內積空間。

挖草，這裡用內積的定義證明了畢氏定理。

若 $\mathbf{u}$ 和 $\mathbf{v}$ 直交，則：

$$
||\mathbf{u}+\mathbf{v}||^{2}=||\mathbf{u}||^{2}+||\mathbf{v}||^{2}
$$

proof:
$||\mathbf{u}+\mathbf{v}||^{2}=\langle \mathbf{u}+\mathbf{v},\mathbf{u}+\mathbf{v} \rangle=\langle \mathbf{u},\mathbf{u} \rangle+2\langle \mathbf{u},\mathbf{v} \rangle+\langle \mathbf{v},\mathbf{v} \rangle=||\mathbf{u}||^{2}+||\mathbf{v}||^{2}$ 

對於 $\mathbb{R}^{m\times n}$ 向量空間，從內積公式定義的長度稱為 Frobenius norm 且記作 $||\cdot||_{F}$。

若 $A\in \mathbb{R}^{m\times n}$，則 $||A||_{F}=(\langle A,A \rangle)^{1/2}=\left( \sum_{i=1}^{m}\sum_{j=1}^{n}a^{2}_{ij} \right)^{1/2}$。

若 $\mathbf{u}$ 與 $\mathbf{v}$ 在內積空間 $V$ 中且 $\mathbf{v}\neq 0$，則把 $\mathbf{u}$ 投影到 $\mathbf{v}$ 的 scalar projection 為：

$$
\alpha= \frac{\langle \mathbf{u},\mathbf{v} \rangle }{||\mathbf{v}||}
$$

而 vector projection 為：

$$
\mathbf{p}=\alpha\left( \frac{1}{||\mathbf{v}||}\mathbf{v} \right)= \frac{\langle \mathbf{u},\mathbf{v} \rangle }{\langle \mathbf{v},\mathbf{v} \rangle }\mathbf{v}
$$

對於上述定義，有以下性質：
1. $\mathbf{u}-\mathbf{p}$ 和 $\mathbf{p}$ 直交。
2. $\mathbf{u}=\mathbf{p}\iff$ $\mathbf{u}$ 是 $\mathbf{v}$ 的標量積。

proof:
(1)
因為 $\langle \mathbf{p},\mathbf{p} \rangle=\left\langle  \alpha \frac{\mathbf{v}}{||\mathbf{v}||}, \alpha \frac{\mathbf{v}}{||\mathbf{v}||} \right\rangle=\left( \frac{\alpha}{||\mathbf{v}||} \right)^{2}\langle \mathbf{v},\mathbf{v} \rangle=\alpha^{2}$ 
且 $\langle \mathbf{u},\mathbf{p} \rangle=\left\langle  \mathbf{u}, \frac{\langle \mathbf{u},\mathbf{v} \rangle}{\langle \mathbf{v},\mathbf{v} \rangle}\mathbf{v}  \right\rangle=\frac{(\langle \mathbf{u},\mathbf{v} \rangle)^{2}}{\langle \mathbf{v},\mathbf{v} \rangle}=\alpha^{2}$ 
又 $\langle \mathbf{u}-\mathbf{p},\mathbf{p} \rangle=\langle \mathbf{u},\mathbf{p} \rangle-\langle \mathbf{p},\mathbf{p} \rangle=\alpha^{2}-\alpha^{2}=0$ 
所以，$\mathbf{u}-\mathbf{p}$ 與 $\mathbf{p}$ 直交。
(2)
($\implies$)
若 $\mathbf{u}=\mathbf{p}$，則 $\mathbf{u}=\beta \mathbf{v}$，其中 $\beta=\frac{\alpha}{||\mathbf{v}||}$。
($\impliedby$)
若 $\mathbf{u}=\beta \mathbf{v}$，則 $\mathbf{p}= \frac{\langle \beta \mathbf{v},\mathbf{v} \rangle}{\langle \mathbf{v},\mathbf{v} \rangle}\mathbf{v}=\beta \mathbf{v}=\mathbf{u}$。

接下來要證明：

$$
|\langle \mathbf{u},\mathbf{v} \rangle |\leq ||\mathbf{u}|| \ ||\mathbf{v}||
$$

等號在 $\mathbf{u},\mathbf{v}$ 線性相依時成立。

proof:
當 $\mathbf{v}=\mathbf{0}$，等式成立。
當 $\mathbf{v}\neq \mathbf{0}$，令 $\mathbf{p}$ 為 $\mathbf{u}$ 在 $\mathbf{v}$ 上的投影。因為 $\mathbf{p}$ 與 $\mathbf{u}-\mathbf{p}$ 直交，所以：$||\mathbf{p}||^{2}=||\mathbf{u}||^{2}-||\mathbf{u}-\mathbf{p}||^{2}$。
那麼，可以構建：$\frac{(\langle \mathbf{u},\mathbf{v} \rangle)^{2}}{||\mathbf{v}||^{2}}=||\mathbf{p}||^{2}=||\mathbf{u}||^{2}-||\mathbf{u}-\mathbf{p}||^{2}$。
移項可得：$(\langle \mathbf{u},\mathbf{v} \rangle)^{2}=||\mathbf{u}||^{2} \ ||\mathbf{v}||^{2}-||\mathbf{u}-\mathbf{p}||^{2} \ ||\mathbf{v}||^{2}\implies |\langle \mathbf{u},\mathbf{v} \rangle| \leq ||\mathbf{u}|| \ ||\mathbf{v}||$ 
等號成立在 $\mathbf{u}=\mathbf{p}$ 時。根據上面那個東東，可得 $\mathbf{v}$ 與 $\mathbf{u}$ 線性相依時等號成立。

ok 呀，隨著柯西不等式的提出，我們又可以定義兩個向量間的夾角了：

$$
\cos \theta= \frac{\langle \mathbf{u},\mathbf{v} \rangle }{||\mathbf{u}|| \ ||\mathbf{v}||}
$$

其中 $\theta\in[0,\pi]$。

## Norms

一個向量空間稱為 normed linear space 若對每個向量空間 $V$ 中的向量 $\mathbf{v}$ 都有一個對應的實數 $||\mathbf{v}||$ (norm of $\mathbf{v}$)，滿足下列條件：
1. $||\mathbf{v}||\geq 0$，其中等號成立 $\iff \mathbf{v}=\mathbf{0}$。(非負性)
2. $||\alpha \mathbf{v}||=|\alpha| \ ||\mathbf{v}||\quad \forall$ 標量 $\alpha$ 。(齊次性)
3. $||\mathbf{v}+\mathbf{w}||\leq ||\mathbf{v}||+||\mathbf{w}||\quad\forall \mathbf{v},\mathbf{w}\in V$。(三角不等式)

需要注意的是，雖然之前我們用內積定義了 norm，但是 norm 可以不是由內積定義的。

若 $V$ 為一個內積空間，則：

$$
||\mathbf{v}||=\sqrt{ \langle \mathbf{v},\mathbf{v} \rangle  }\quad\forall \mathbf{v}\in V
$$

定義了 $V$ 上的長度(norm)。

proof:
我們這邊只證第三點。
$||\mathbf{u}+\mathbf{v}||^{2}=\langle \mathbf{u}+\mathbf{v},\mathbf{u}+\mathbf{v} \rangle=\langle \mathbf{u},\mathbf{u} \rangle+2\langle \mathbf{u},\mathbf{v} \rangle+\langle \mathbf{v},\mathbf{v} \rangle\leq ||\mathbf{u}||^{2}+2||\mathbf{u}|| \ ||\mathbf{v}||+||\mathbf{v}||^{2}=(||\mathbf{u}||+||\mathbf{v}||)^{2}$ 
$\implies ||\mathbf{u}+\mathbf{v}||\leq ||\mathbf{u}||+||\mathbf{v}||$ 

在給定的向量空間定義許多不同的 norm 是可能的，例如我們可以在 $\mathbb{R}^{n}$ 中定義：

$$
||\mathbf{x}||_{1}=\sum_{i=1}^{n}|x_{i}|
$$

另一個 $\mathbb{R}^{n}$ 中重要的 norm 是 uniform norm 或稱 infinity norm：

$$
||\mathbf{x}||_{\infty}=\text{max}_{1\leq i\leq n}|x_{i}|
$$

更具一般性的，對任意實數 $p\geq1$ 我們可以定義 $\mathbb{R}^{n}$ 的 norm：

$$
||\mathbf{x}||_{p}=\left( \sum_{i=1}^{n}|x_{i}|^{p} \right)^{1/p}
$$

對於 $p=2$，我們有：

$$
||\mathbf{x}||_{2}=\left( \sum_{i=1}^{n}|x_{i}|^{2} \right)^{1/2}=\sqrt{ \langle \mathbf{x},\mathbf{x} \rangle  }
$$

所以，$||\cdot||_{2}$ 就是 inner product 對應的 norm。但是對於其他的 $p$ 定義出來的 norm，沒有對應到任何 inner product。

喔對，對於那些沒有對應到內積的 norm，畢氏定理會失效喔～

喔，這節快結束啦～再給你最後一個定義～

令 $\mathbf{x},\mathbf{y}$ 為 normed linear space 的向量。則 $\mathbf{x},\mathbf{y}$ 之間的距離為 $||\mathbf{y}-\mathbf{x}||$。

# Orthonormal Sets

令 $\mathbf{v_{1}},\dots,\mathbf{v_{n}}$ 為內積空間 $V$ 中的**非零向量**。若 $i\neq j$ 時 $\langle \mathbf{v}_{i},\mathbf{v}_{j} \rangle=0$，則 $\{\mathbf{v_{1}},\dots,\mathbf{v}_{n}\}$ 稱為 orthogonal set。

接一下第一個定理：若 $\{\mathbf{v}_{1},\dots,\mathbf{v}_{n}\}$ 為內積空間 $V$ 中的非零直交集合，則 $\mathbf{v}_{1},\dots,\mathbf{v}_{n}$ 線性獨立。

proof:
假設 $\mathbf{v}_{1},\dots ,\mathbf{v}_{n}$ 兩兩互相直交且非零，且 $c_{1}\mathbf{v_{1}}+\dots+c_{n}\mathbf{v}_{n}=\mathbf{0}$。
令 $1\leq j\leq n$，將上式等號左右同時內積 $\mathbf{v}_{j}$，有：$c_{1}\langle \mathbf{v}_{1},\mathbf{v}_{j} \rangle+\dots+c_{n}\langle \mathbf{v}_{n},\mathbf{v}_{j} \rangle=0$ 
$\implies c_{j}||\mathbf{v}_{j}||^{2}=0$ 
那麼，所有標量 $c_{1},\dots,c_{n}$ 都必須為零等式才會成立。

接下來說明**正交(orthonormal)** 集合：正交集合首先是直交集合，且每個正交集合中的向量都為單位向量。

也就是說，集合 $\{\mathbf{u}_{1},\dots,\mathbf{u}_{n}\}$ 為正交集合 $\iff \langle \mathbf{u}_{i},\mathbf{u}_{j} \rangle=\delta_{ij}$，且 $\delta_{ij}=\begin{cases}1 & \text{if }i=j \\ 0 & \text{if }i\neq j\end{cases}$。

給定一個直交集合 $\{\mathbf{v}_{1},\dots,\mathbf{v}_{n}\}$，我們可以通過定義：$\mathbf{u}_{i}=\left( \frac{1}{||\mathbf{v}_{i}||} \right)\mathbf{v}_{i}$，使得這些集合構成正交集合。

當 $B=\{\mathbf{u}_{1},\dots,\mathbf{u}_{n}\}$ 為內積空間 $V$ 的正交集合，則 $B$ 是子空間 $S=\text{Span}(\mathbf{u}_{1},\dots,\mathbf{u}_{k})$ 的**正交基底(orthonormal basis)**。正交基底很好用呦～

具體怎麼個好用法，參考以下定理。

若 $\mathbf{u}_{1},\dots,\mathbf{u}_{n}$ 是內積空間 $V$ 的正交基底，且 $\mathbf{v}=\sum_{i=1}^{n}c_{i}\mathbf{u}_{i}=c_{1}\mathbf{u_{1}}+\dots+c_{n}\mathbf{u}_{n}$，$\mathbf{u}=\sum_{i=1}^{n}d_{i}\mathbf{u}_{i}$，則 $\langle \mathbf{u},\mathbf{v} \rangle=\sum_{i=1}^{n}c_{i}d_{i}$ 

proof:
$\langle \mathbf{u},\mathbf{v} \rangle=\left\langle  \sum_{i=1}^{n}d_{i}\mathbf{u}_{i},\mathbf{v}  \right\rangle=\sum_{i=1}^{n}c_{i}d_{i}$ (根據之前那個求線性組合的定理)

若 $\mathbf{u}_{1},\dots,\mathbf{u}_{n}$ 是內積空間 $V$ 的正交基底，且 $\mathbf{v}=\sum_{i=1}^{n}c_{i}\mathbf{u}_{i}=c_{1}\mathbf{u_{1}}+\dots+c_{n}\mathbf{u}_{n}$，則 $c_{i}=\langle \mathbf{v},\mathbf{u}_{i} \rangle$。

proof:
$\langle \mathbf{v},\mathbf{u}_{i} \rangle=\sum_{j=1}^{n}c_{j}\mathbf{v}_{j}\cdot \mathbf{u}_{i}=\sum_{j=1}^{n}c_{j}\delta_{ij}=c_{i}$ 

又比如：若 $\mathbf{u}_{1},\dots,\mathbf{u}_{n}$ 是內積空間 $V$ 的正交基底，且 $\mathbf{v}=\sum_{i=1}^{n}c_{i}\mathbf{u}_{i}$，則 $||\mathbf{v}||^{2}=\sum_{i=1}^{n}c_{i}^{2}$。

## Orthonormal Sets and Least Squares (補充)

若 $A$ 的 column vectors 構成 $\mathbb{R}^{m}$ 中的一個正交集合，則 $A^{T}A=I$ 且 least squares solution 為：

$$
\mathbf{\hat{x}}=A^{T}\mathbf{b}
$$

令 $S$ 為內積空間 $V$ 的子空間，且 $\mathbf{x}\in V$。令 $\{\mathbf{u}_{1},\dots,\mathbf{u}_{n}\}$ 為 $V$ 的一組正交基底，若想尋找 $\mathbf{x}$ 在 $S$ 上的投影 $\mathbf{p}$ (尋找 $\mathbf{x}$ 到 $S$ 上的 best least squares approximation，使用 $l(x)=c_{1}\mathbf{u}_{1}+\dots+c_{n}\mathbf{u}_{n}$ 的形式)，則：

$$
\mathbf{p}=\sum_{i=1}^{n}c_{i}\mathbf{u}_{i}
$$

其中，$c_{i}=\langle \mathbf{x},\mathbf{u}_{i} \rangle$。(這邊的 $c_{i}$ 其實是投影 $\mathbf{x}$ 到 $\mathbf{u}_{i}$ 的 scalar projection)

延續上述假設，若 $U=(\mathbf{u}_{1},\dots,\mathbf{u}_{n})$ 也可以表示成：

$$
\mathbf{p}=UU^{T}\mathbf{x}
$$

# Tips

- 做不出來的時候回頭看看題目，說不定會有驚人發現！
- 小菜菜，分清楚 $R(A)$ 等於 $\text{Col}(A)$ 不等於 $\text{Row}(A)$。
- 若已知 $U$ 與 $V$ 為兩向量空間，則想證明 $U$ 是 $V$ 的子空間只需要證明 $U\subseteq V$。
- 若 $U\subseteq V$，則 $V^{\perp}\subseteq U^{\perp}$。
- 對非滿秩 $A$ 求 $A\mathbf{x}=\mathbf{b}$ 的 least square problem 得到的 $\mathbf{\hat{x}}$ 有無限多組解，但是 $\mathbf{b}$ 在 $R(A)$ 上的投影 $A\mathbf{\hat{x}}$ 只有一個。(不管代哪個 $\mathbf{\hat{x}}$ 都會得到相同解)
- $N(A^{T}A)=N(A)$ 
- 對於那些沒有對應到內積的 norm，畢氏定理會失效。
- Norm 定義中 $||\alpha \mathbf{x}||=|\alpha|||\mathbf{x}||$ 小心 $\alpha$ 的絕對值不要掉。

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

![[Pasted image 20251126095445.png]]

Sol:
好啦，我知道這不難。但是複習一下好嗎，你會寫錯。
對 $A$ 找 RREF $=\begin{bmatrix}1 & 0 & 1 \\ 0 & 1 & 1 \\ 0 & 0 & 0\end{bmatrix}$。
$A$ 的 RREF 可以幫助找 $N(A)$ 與 $R(A^{T})$。
顯然，$N(A)=\text{span}((-1,-1,1)^{T})$，$R(A^{T})=\text{span}((1,0,1)^{T},(0,1,1)^{T})$。
對 $A^{T}$ 找 RREF $=\begin{bmatrix}1 & 0 & 1 \\ 0 & 1 & 2 \\ 0 & 0 & 0\end{bmatrix}$。
顯然，$N(A^{T})=\text{span}((-1,-2,1)^{T})$，$R(A)=\text{span}((1,0,1)^{T},(0,1,2)^{T})$。

![[Pasted image 20251126102936.png]]

Sol:
再送你一個超簡單但是我做錯的題目叭～人甚至不能共情之前的自己～
令 $X=\begin{bmatrix}1 \\ -1 \\ 1\end{bmatrix}$，則 $R(X)=\text{span}(\mathbf{x})$。
所以 $S^{\perp}=R(X)^{\perp}=N(X^{T})=\text{span}((1,1,0)^{T},(-1,0,1)^{T})$。(誒，不要只有一個 row 就不會解啊！設 free variable 啊兄弟！)

![[Pasted image 20251126104511.png]]

Sol:
小錯不慌。
有 $\text{dim }R(A)=\text{dim }R(A^{T})=r$。
則有 $\text{dim }N(A)=n-r$，又 $A^{T}$ 為 $n\times m$ 的矩陣 所以 $\text{dim }N(A^{T})=m-r$ By rank-nullity theorem. 

![[Pasted image 20251126114121.png]]

Sol:
(a)
$\mathbf{x}\in N(A^{T}A)\implies A^{T}(A\mathbf{x})=0\implies A\mathbf{x}\in N(A^{T})$ 
又因為 $A\mathbf{x}$ 為 $A$ 的 column vector 的線性組合，所以 $A\mathbf{x}\in R(A)$。
(b)
對於 $\mathbf{x}\in N(A)$，有 $A^{T}A\mathbf{x}=A^{T}\mathbf{0}=\mathbf{0}\implies N(A)\subseteq N(A^{T}A)$。
取任意 $\mathbf{y}\in N(A^{T}A)$ 都有 $A\mathbf{y}\in R(A)\cap N(A^{T})=\{\mathbf{0}\}\implies \mathbf{y}\in N(A)$。
$\implies N(A)=N(A^{T}A)$ 
(c)
$\text{rank}(A)+\text{dim }N(A)=n$ 
$\text{rank}(A^{T}A)+\text{dim }N(A^{T}A)=n$ 
根據 (b) 又有 $\text{dim }N(A)=\text{dim }N(A^{T}A)$，所以 $A$ 與 $A^{T}A$ 有相同的 rank。
(d)
$A$ 的 column vector 線性獨立 $\implies A\mathbf{x}=\mathbf{0}$ 只有 trivial solution $\implies N(A)=\{\mathbf{0}\}$ 。
$A^{T}A\mathbf{x}=\mathbf{0}\implies \mathbf{x}\in N(A^{T}A)=N(A)=\{\mathbf{0}\}\implies$ $A^{T}A\mathbf{x}=\mathbf{0}$ 只有 trivial solution $\implies A^{T}A$ nonsingular. 

證明若$U$ 與 $V$ 為兩向量空間，且 $U\subseteq V$，則 $V^{\perp}\subseteq U^{\perp}$。

Sol:
取任意 $\mathbf{v}\in V^{\perp}$ 與任意 $\mathbf{x}\in V$，則有 $\mathbf{v}\cdot \mathbf{x}=0$。
又因為 $U\subseteq V$，所以對任意 $\mathbf{u}\in U$ 都有 $\mathbf{v}\cdot \mathbf{u}=0$。
也就是說 $\mathbf{v}\in U^{\perp}$。
因為對任意 $\mathbf{v}\in V^{\perp}$ 皆成立，所以 $V^{\perp}\subseteq U^{\perp}$。

![[Pasted image 20251126144353.png]]

Sol:
不難，就是會忘了證明 $A\mathbf{x_{1}},\dots,A\mathbf{x}_{r}$ 線性獨立。
令對任意 $\mathbf{w}\in \mathbb{R}^{n}$，有 $\mathbf{u}\in R(A^{T})$，$\mathbf{v}\in N(A)$ 且 $\mathbf{w}=\mathbf{u}+\mathbf{v}$ 唯一。
$A\mathbf{w}=A\mathbf{u}+A\mathbf{v}=A\mathbf{u}\implies A\mathbf{w}=A\mathbf{u}=A(\alpha_{1}\mathbf{x_{1}}+\dots+\alpha_{r}\mathbf{x}_{r})=\alpha_{1}A\mathbf{x_{1}}+\dots+\alpha_{r}A\mathbf{x}_{r}$ 
又 $A\mathbf{w}=R(A)$，所以 $A\mathbf{x_{1}},\dots,A\mathbf{x}_{r}$ 可能是 $R(A)$ 的一組基底。
現在證明 $A\mathbf{x_{1}},\dots,A\mathbf{x}_{r}$ 線性獨立。
考慮 $A(\alpha_{1}\mathbf{x_{1}}+\dots+\alpha_{r}\mathbf{x}_{r})=\mathbf{0}$，則 $\alpha_{1}\mathbf{x_{1}}+\dots+\alpha_{r}\mathbf{x}_{r}\in N(A)\cap R(A^{T})=\{\mathbf{0}\}$ 
因為 $\mathbf{x_{1}},\dots,\mathbf{x}_{r}$ 線性獨立，所以 $\alpha_{1}=\dots=\alpha_{r}=0\implies A\mathbf{x_{1}},\dots,A\mathbf{x}_{r}$ 線性獨立且張出 $R(A)$。

![[Pasted image 20251126150150.png]]
![[Pasted image 20251126150204.png]]

Sol:
取任意 $\mathbf{u}\in N(A)$，有 $A\mathbf{u}=\mathbf{xy}^{T}\mathbf{u}+\mathbf{yx}^{T}\mathbf{u}=0$。
因為 $\mathbf{x},\mathbf{y}$ 線性獨立，所以 $\mathbf{u}\perp \mathbf{x}$ 與 $\mathbf{u}\perp \mathbf{y}\implies \mathbf{u}\in S^{\perp}$。
所以 $N(A)\subseteq S^{\perp}$。
取任意 $\mathbf{v}\in S^{\perp}$，有 $A\mathbf{v}=\mathbf{xy}^{T}\mathbf{v}+\mathbf{yx}^{T}\mathbf{v}=0$。
所以 $\mathbf{v}\in N(A)\implies S^{\perp}\subseteq N(A)$。
綜合 $N(A)\subseteq S^{\perp}$ 與 $\mathbf{v}\in N(A)\implies S^{\perp}\subseteq N(A)$，我們有 $N(A)=S^{\perp}$。

![[Pasted image 20251128133030.png]]

Sol:
這題其實和 Exercise 7 沒啥大關係。
但是 Exercise 7 給我們了一個方向，考慮 $\bar{x}=0$ 時的狀況較為簡單。
令 $z=x-\bar{x}$，則 $\bar{z}=0$。
那麼 least squares line 為 $y=\bar{y}+dz$。(根據 Exercise 7)
代回 $z=x-\bar{x}$，有 $y=\bar{y}-d\bar{x}+dx$。
此時若代入 $x=\bar{x}$，可得 $y=\bar{y}$。所以 $(\bar{x},\bar{y})$ 在 least squares line 上。

讓我們來練習證明若 $A$ 為 $m\times n$ 大小矩陣且 $P=A(A^{T}A)^{-1}A^{T}$，若 $\mathbf{b}\in \mathbb{R}^{n}$ 則 $P\mathbf{b}\in R(A)$。

Sol:
$P\mathbf{b}=A(A^{T}A)^{-1}A^{T}\mathbf{b}$ 
令 $\mathbf{y}=(A^{T}A)^{-1}A^{T}\mathbf{b}$，則 $\mathbf{y}\in \mathbb{R}^{n}$。
所以 $P\mathbf{b}=A\mathbf{y}\in R(A)$。

![[Pasted image 20251128141139.png]]

Sol:
Explain 太弱了，我們來 Prove。
因為 $\mathbf{b}\in R(A)$，所以 $\mathbf{b}$ 可以被唯一的表達為 $\mathbf{b}=A\mathbf{x}$，其中 $\mathbf{x}\in \mathbb{R}^{n}$。
$P\mathbf{b}=A(A^{T}A)^{-1}A^{T}\mathbf{b}=A(A^{T}A)^{-1}(A^{T}A)\mathbf{x}$ 
$=A\mathbf{x}=\mathbf{b}$ 

![[Pasted image 20251128154324.png]]

Sol:
我會證，但不知道怎麼系統的寫。
設 $A$ 為 $m\times n$ 大小矩陣，則 $\mathbf{b}\in \mathbb{R}^{m}$。
又 $\mathbb{R}^{m}=R(A)\oplus N(A^{T})$，所以 $\mathbf{b}$ 可以被唯一的表示成 $\mathbf{b}=\mathbf{p}+\mathbf{q}$，其中 $\mathbf{p}\in R(A)$，$\mathbf{q}\in N(A^{T})$。
又由題目可得 $A\mathbf{\hat{x}}+\mathbf{r}=\mathbf{b}$ 且 $A^{T}\mathbf{r}=\mathbf{0}\implies \mathbf{r}\in N(A^{T})$ 且 $A\mathbf{\hat{x}}\in R(A)$。
因為 $\mathbf{r}=\mathbf{b}-A\mathbf{\hat{x}}$，所以 $\mathbf{r}$ 為殘差。
因為 $\mathbf{r}\perp R(A)$ ，所以 $A\mathbf{\hat{x}}$ 為 $\mathbf{b}$ 在 $R(A)$ 上的投影 $\implies \mathbf{\hat{x}}$ 是 least squares solution。

![[Pasted image 20251128161036.png]]

Sol:
因為是若且唯若，所以要雙向證明。但是 ($\impliedby$) 的方法很簡單，這邊只說明 $(\implies)$ 的方法。
$(\implies)$ 
令 $\mathbf{y}\in \mathbb{R}^{n}$ 也是 least squares solution，則：
$A^{T}A\mathbf{\hat{x}}=A^{T}A\mathbf{y}=A^{T}\mathbf{b}\implies A^{T}A(\mathbf{y}-\mathbf{\hat{x}})=\mathbf{0}$ 
$\implies \mathbf{y}-\mathbf{\hat{x}}\in N(A^{T}A)=N(A)$ 
$\mathbf{z}:=\mathbf{y}-\mathbf{\hat{x}}$，我們有 $\mathbf{y}=\mathbf{\hat{x}}+\mathbf{z}$ 其中 $\mathbf{z}\in N(A)$。
因為這邊我們只要證明存在這樣的 $\mathbf{z}$ 滿足 $\mathbf{y}=\mathbf{\hat{x}}+\mathbf{z}$ 且 $\mathbf{z}\in N(A)$ 就好，所以我們可以透過定義 $\mathbf{z}:=\mathbf{y}-\mathbf{\hat{x}}$ 得證。

![[Pasted image 20251202235350.png]]

Sol:
只錯了第一個 condition，所以咱只做第一個。
因為 $\langle \mathbf{v},\mathbf{v} \rangle\geq 0$ 且等號成立在 $\mathbf{v}=\mathbf{0}$，所以 $||\mathbf{v}||=\sqrt{ \langle \mathbf{v},\mathbf{v} \rangle }\geq 0$ 且等號成立在 $\mathbf{v}=\mathbf{0}$。
之前寫這題的時候，我錯誤的把 $||\mathbf{v}||^{2}=\langle \mathbf{v},\mathbf{v} \rangle\geq 0$ 寫了出來，但是無論如何平方都是 $\geq 0$ 所以等於啥也沒做。

![[Pasted image 20251203002514.png]]

Sol:
這題我本來從 $A\mathbf{x}\in \mathbb{R}^{n}$ 出發，後來看 GPT 才知道原來有更簡單的寫法。果然要被 AI 取代了。
因為已知 $||\cdot||_{2}$ 是 norm，所以：
(1) $||\mathbf{x}||_{A}=||A\mathbf{x}||_{2}\geq0$ 且等號成立在 $A\mathbf{x}=\mathbf{0}$ 時，因為 $A$ nonsingular，所以 $A\mathbf{x}=\mathbf{0}\iff \mathbf{x}=\mathbf{0}$。
(2) $||\alpha \mathbf{x}||_{A}=||A(\alpha \mathbf{x})||_{2}=||\alpha A\mathbf{x}||_{2}=|\alpha| \ ||A\mathbf{x}||_{2}$ 
(3) $||\mathbf{x}+\mathbf{y}||_{A}=||A(\mathbf{x}+\mathbf{y})||_{2}=||A\mathbf{x}+A\mathbf{y}||_{2}\leq ||A\mathbf{x}||_{2}+||A\mathbf{y}||_{2}=||\mathbf{x}||_{A}+||\mathbf{y}||_{A}$ 

![[Pasted image 20251203105705.png]]

Sol:
$||\mathbf{x}||_{2}=||x_{1}\mathbf{e_{1}}+x_{2}\mathbf{e_{2}}||_{2}\leq ||x_{1}\mathbf{e_{1}}||_{2}+||x_{2}\mathbf{e_{2}}||_{2}$ 
又 $||x_{1}\mathbf{e_{1}}||_{2}=|x_{1}|=||x_{1}\mathbf{e_{1}}||_{1}$ 同理 $||x_{2}\mathbf{e_{2}}||_{2}=||x_{2}\mathbf{e_{2}}||_{1}$ ，且 $||x_{1}\mathbf{e_{1}}+x_{2}\mathbf{e_{2}}||_{1}=||x_{1}\mathbf{e_{1}}||_{1}+||x_{2}\mathbf{e_{2}}||_{1}$ 。
所以 $||\mathbf{x}||_{2}=||x_{1}\mathbf{e_{1}}+x_{2}\mathbf{e_{2}}||_{2}\leq ||x_{1}\mathbf{e_{1}}||_{2}+||x_{2}\mathbf{e_{2}}||_{2}=||x_{1}\mathbf{e_{1}}+x_{2}\mathbf{e_{2}}||_{1}\implies ||\mathbf{x}||_{2}\leq||\mathbf{x}||_{1}$。

![[Pasted image 20251203110406.png]]

Sol:
菜誒，這都想不出來：$(1,0)^{T}$。

![[Pasted image 20251203111410.png]]

Sol:
哇擦勒，我有想到一點點思路，但是沒有寫下去。
$||\mathbf{u}||=||(\mathbf{u}+\mathbf{v})-\mathbf{v}||\leq ||\mathbf{u}+\mathbf{v}||+||-\mathbf{v}||=||\mathbf{u}+\mathbf{v}||+||\mathbf{v}||\implies||\mathbf{u}+\mathbf{v}||\geq ||\mathbf{u}||-||\mathbf{v}||$ 
$||\mathbf{v}||=||(\mathbf{u}+\mathbf{v})-\mathbf{u}||\leq||\mathbf{u}+\mathbf{v}||+||\mathbf{u}||\implies||\mathbf{u}+\mathbf{v}|\geq ||\mathbf{v}||-||\mathbf{u}||$ 
綜合 $\begin{cases}||\mathbf{u}+\mathbf{v}||\geq||\mathbf{v}||-||\mathbf{u}|| \\ ||\mathbf{u}+\mathbf{v}||\geq ||\mathbf{u}||-||\mathbf{v}||\end{cases}\implies||\mathbf{u}+\mathbf{v}||\geq |\ ||\mathbf{u}||-||\mathbf{v}|| \ |$ 

![[Pasted image 20251203113122.png]]

Sol:
很坑，小心。
這邊 $||f||=0$ 只要求 $f(a)=f(b)=0$，而不要求中間所有值都為零，所以不符合。

![[Pasted image 20251208230642.png]]

Sol:
不難，但是典型。怕你忘了放這給你複習呢。
令 $\mathbf{u}=\alpha_{1}\mathbf{u_{1}}+\alpha_{2}\mathbf{u_{2}}$。
則 $\alpha_{1}=\langle \mathbf{u},\mathbf{u_{1}} \rangle=\frac{1}{2}$，$\alpha_{2}=\langle \mathbf{u},\mathbf{u_{2}} \rangle$。
又 $\mathbf{u}$ 是 unit vector，所以 $\alpha_{1}^{2}+\alpha_{2}^{2}=1\implies|\alpha_{2}|=|\mathbf{u}^{T}\mathbf{u}_{2}|=\frac{\sqrt{ 3 }}{2}$ 

![[Pasted image 20251208232020.png]]

Sol:
送分題，怕你忘。
忘記就回去看 5.5 的某個定理。
$\langle f,g \rangle=3\cdot1+2\cdot(-1)=1$ 