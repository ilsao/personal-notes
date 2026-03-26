# Outline of the Solution of the Schrodinger Equation For the H Atom

電子在原子中位能為：

$$
E_{p}= -\frac{1}{4\pi\epsilon_{0}} \frac{Ze^{2}}{r}
$$

其中 $Z$ 為原子序，對 H 原子來說 $Z=1$。

我們將時間獨立的薛丁格方程：$-\frac{\hbar^{2}}{2m} \frac{d^{2}\chi}{dx^{2}}+E_{p}(x)=E\chi$ 拓展到三維：

$$
-\frac{\hbar^{2}}{2m}\left[ \frac{\partial^{2}\chi}{\partial x^{2}} +\frac{\partial^{2}\chi}{\partial y^{2}}+\frac{\partial^{2}\chi}{\partial z^{2}}\right]+E_{p}=E\chi
$$

因為 $E_{p}$ 僅與 $r$ 有關，我們轉用球座標表示：

$$
\frac{1}{r^{2}} \frac{\partial}{\partial r}\left( r^{2} \frac{\partial\chi}{\partial r} \right)+ \frac{1}{r^{2}\sin \theta} \frac{\partial}{\partial \theta}\left( \sin \theta  \frac{\partial\chi}{\partial \theta} \right)+\frac{1}{r^{2}\sin^{2}\theta} \frac{\partial^{2}\chi}{\partial \phi^{2}}+\frac{2m}{\hbar^{2}}[E-E_{p}(r)]\chi=0
$$

![[Pasted image 20260326234530.png|225]]

使用變數分離法：

$$
\chi(r,\theta,\phi)=R(r)\Theta(\theta)\Phi(\phi)
$$

帶入後整理得：

$$
-\frac{\sin^{2}\theta}{R} \frac{d}{dr}\left( r^{2} \frac{dR}{dr} \right)-\frac{2m}{\hbar^{2}}r^{2}\sin^{2}\theta[E-E_{p}(r)]-\frac{\sin \theta}{\Theta} \frac{d}{d\theta}\left( \sin \theta \frac{d\Theta}{d\theta} \right)= \frac{1}{\Phi} \frac{d^{2}\Phi}{d\phi^{2}}
$$

我們令：

$$
\begin{cases}
\frac{1}{\Phi} \frac{d^{2}\Phi}{d\phi^{2}}=-m_{l}^{2} \\
\frac{m_{l}^{2}}{\sin^{2}\theta}-\frac{1}{\Phi} \frac{1}{\sin \theta} \frac{d}{d\theta}\left( \sin \theta \frac{d\Theta}{d\theta} \right)=l(l+1) \\
\frac{1}{R} \frac{d}{dr}\left( r^{2} \frac{dR}{dr} \right)+ \frac{2mr^{2}}{\hbar^{2}}[E-E_{p}(r)]=l(l+1)
\end{cases}
$$

解上述方程，必須 well-behave 且滿足物理條件。

於是有：

$$
\begin{cases}
m_{l}=0,\pm1,\pm 2,\dots \\
l\geq |m_{l}| \\
l<n
\end{cases}
$$

整理後：

$$
\begin{cases}
n:\text{ principle quantum number (主量子數) (decide)}E_{n} \\
l:\text{orbital quantum number (角量子數) } & 0,1,2,\dots,n-1 \\
m_{l}:\text{magnetic quantum number (磁量子數) } & 0,\pm 1,\pm2,\dots,\pm l
\end{cases}
$$

# Physical Significance of the Results

主量子數 $n$：能量依賴於量子數 $n$。

角量子數 $l$：決定原子角動量大小。

磁量子數 $m_{l}$：決定動量在磁場中的方向。

波函數依賴於三個量子數，記為：

$$
\chi_{nlm_{l}}
$$

對氫原子來說，固定 $n$，另外兩個量子數可以取多個值。這說明電子在相同能量時可有不同狀態。

具有相同能量但不同 $l$ 和 $m_{l}$ 的狀態稱為**簡併態(degenerate states)**。

> [!note]
> 對多電子原子來說，因為電子間互相排斥，所以固定 $n$ 而改變另外兩個量子數可能造成能量改變。

簡併程度取決於 $n$，例如：
- $n=1$，僅有狀態 $\chi_{100}$。
- $n=2$：
	- $\chi_{200}$ 
	- $\chi_{21-1}$ 
	- $\chi_{210}$ 
	- $\chi_{211}$ 

我們稱 $n=2$ 時有**四重簡併(fourfold degeneracy)**。

![[Pasted image 20260327001520.png|390]]

軌域名稱：
- $l=0$: s states
- $l=1$: p states
- $l=2$: d states
- $l=3$: f states

就像 $-i\hbar \frac{\partial}{\partial x}$ 可將動量提取一樣，角動量 $L$ 可以被如下提取：

$$
L^{2}\psi_{nlm_{l}}=l(l+1)\hbar^{2}\psi_{nlm_{l}}\implies L=\sqrt{ l(l+1) }\hbar \approx l\hbar
$$

與波爾做的假設 $mvr=n\hbar$ 近似。

若原子放在沿 $z$ 軸的磁場中，角動量的 $z$ 分量由 $m_{l}$ 決定：

$$
L_{z}=m_{l}\hbar
$$

即，角動量在磁場作用下的方向 (或說電子轉動平面在空間中的變化) 也是跳躍式不連續性變化。這稱為**空間量子化(space quantization)**。

下圖展示 $l=2$ 時空間量子化的現象：

![[Pasted image 20260327003650.png|268]]

> [!warning] 注意
> 若沒有施加磁場，系統沒有參考方向，$m_{l}$ 處於疊加態無法確定。而施加磁場後，觀測 $L_{z}$ 使狀態塌縮到某確定的本徵態 (具體哪個由機率決定)，此時空間量子化才有意義。

> [!note] 
> 本徵態是測量結果已確定的狀態。
# Space Quantization: The Experiments

## The Zeeman Effect

## Stern-Gerlach Experiment

# The Spin

# Some Features of the Atomic Wavefunctions

# The Periodic Table

## Pauli's Exclusion Principle

## Understanding the Periodic Table