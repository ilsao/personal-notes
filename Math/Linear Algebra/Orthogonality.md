
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

至於如何計算某定點 $Q$ 到某平面的距離？

考慮平面 $ax+by+cz=d$ 上任意向量 $\mathbf{P}$，則 $\mathbf{Q}-\mathbf{P}$ 平行 $\mathbf{N}$，且 $Q$ 到平面的距離為 $\mathbf{Q}-\mathbf{P}$ 投影到 $\mathbf{N}$ 上的那個 $\alpha$ 的值。

也就是：

$$
d= \frac{(\mathbf{Q}-\mathbf{P})\cdot \mathbf{N}}{||\mathbf{N}||}= \frac{\mathbf{Q}\cdot \mathbf{N}-\mathbf{P}\cdot \mathbf{N}}{||\mathbf{N}||}= \frac{\mathbf{Q}\cdot \mathbf{N}-d}{||\mathbf{N}||}
$$

需要注意的是，上式中 $d$ 有正負之差，代表該點處於平面的上方還是下方。真正的距離應該為：$|d|$。

通過 $\cos \theta= \frac{\mathbf{x}^{T}\mathbf{y}}{||\mathbf{x}|| \ ||\mathbf{y}||}$ 與 $\sin \theta=\sqrt{ 1-\cos^{2} \theta }$，我們有 $||\mathbf{x}\times\mathbf{y}||=||\mathbf{x}|| \ |\mathbf{y}|\sin \theta$。

## Orthogonality in $\mathbb{R}^{n}$ 

其實這段也沒啥，就是說上述很多東西可以被拓展到 $\mathbb{R}^{n}$。