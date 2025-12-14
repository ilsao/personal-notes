
# Force on Current-Carrying Wires

考慮以下實驗：

![[Pasted image 20251214172356.png]]

由實驗可知：
- 若導線方向與磁場方向相同，則導線不受力。
- $F$ 大小與磁場與導線的夾角 $\theta$ 的 $\sin \theta$ 大小成正比。
- $F$ 與電流大小 $i$ 還有位於導線磁場中的長度 $\Delta l$ 成正比。

所以，我們定義磁場大小為：

$$
B=\frac{F}{i\Delta l\sin \theta}
$$

磁場的單位用 SI 表示為：$N/A\cdot m$，也稱為**特斯拉(tesla, T)**，或者使用另一個較小的單位**高斯(gauss, G)**。其中 $1\text{ tesla}=10^{4}\text{ gauss}$。

地球的磁場大約為 $10^{-4}$ 特斯拉，所以 $1$ 特斯拉很大。

由上式，我們可以將導線受力用外積表示：

$$
F=i\Delta \mathbf{l}\times \mathbf{B}
$$

通常，我們將 $i$ 視為常數，而 $\Delta l$ 視為指向電流流向的向量。

# Torque On a Current Loop

![[Pasted image 20251214173831.png]]

考慮上圖場景，用手比一下就可以知道 2, 4 的力會互相底消。然後 $F_{3}$ 與 $F_{4}$ 的力大小相等，方向相反。

考慮磁場造成的力 (磁場方向與電流方向垂直)：

$$
F=i\Delta \mathbf{l}\times \mathbf{B}=iaB
$$

明顯，這會造成一個力矩。根據力矩公式：

$$
\tau=\mathbf{r}\times \mathbf{F}
$$

這邊我們取 $\mathbf{r}=\frac{b}{2}$，因為 $F_{1}$ 與 $F_{3}$ 大小相等所以有：

$$
\tau=2\cdot\left( \frac{b}{2} \right)\cdot iaB\sin \theta=iabB\sin \theta
$$

注意到 $ab$ 就是該電線圈的面積，令 $ab=A$，有：

$$
\tau=iAB\sin \theta
$$

也就是說，當 $\theta=90^{\circ}$ 時，也就是線圈平面與磁場方向平行時，力矩最大。

當 $\theta=0^{\circ}$ 時，也就是線圈平面與磁場方向垂直時，力矩最小，為零。

注意到，力矩大小可以通過調整電流大小 $i$ 與磁場大小 $B$ 來調整。

# Magnetic Dipole Moment

經由上節，我們可以發現與力矩相關的兩個非常重要的量是：線圈面積與通過的電流大小。

那麼，我們定義一個量為它們倆的乘積，這個量被稱為**磁偶極矩(magnetic dipole moment)** 或稱**磁矩(magnetic moment)**：

$$
\mu=iA
$$

那麼力矩現在就可以被表示為：

$$
\tau=\mu B\sin \theta
$$

通過外積與力矩的定義，我們可以發現 (上圖) 力矩的方向為指向紙面。

我們將 $\mathbf{\mu}$ 定義為一個向量，其方向是根據右手定則，右手四指沿著電流方向彎曲後大拇指指向的方向。可見上圖標示。那麼可以繼續重寫公式：

$$
\tau=\mathbf{\mu}\times \mathbf{B}
$$

# Force On a Moving Charge

根據第十五章，我們知道：

$$
i=qNAv
$$

代入到 $F=i\Delta \mathbf{l}\times\mathbf{B}$：

$$
F=qNAv\Delta \mathbf{l}\times \mathbf{B}
$$

注意到 $NA\Delta {l}$ 正好是整個體積中包含的電荷總數，所以單個電荷所受的力 $F_{q}$ 為：

$$
F_{q}=\frac{F}{NA\Delta {l}}=q\mathbf{v}\times \mathbf{B}
$$

注意，上式假設電流中流動的電荷為正電荷，因為我們假設電流方向與飄移速度同向。

如果流載子實際是負電荷，則受力方向相反。

我們又知道受力方向因為外積總是與速度垂直，所以磁場只會改變電荷的移動方向，而不會改變速度大小。

# The Hall Effect

![[Pasted image 20251214194810.png]]

考慮上圖場景，中間那一大塊是導電金屬薄片。

我們假設 $B$ 是均勻磁場，且電流由正電荷造成。

對每個電荷來說，磁場造成的力為：

$$
F_{B}=q\mathbf{v}\times \mathbf{B}=qvB
$$

且此力使得電荷向金屬片上方移動。

因為整個金屬片必須保持電中性，所以一旦上方積累正電荷，下方必須積累負電荷。

![[Pasted image 20251214195131.png]]

這樣的電場分布會使得上下產生一個點場 $\mathbf{E}_{y}$ 與 $F_{B}$ 抵銷，使得電荷不會偏轉。

因為電場的產生，$CD$ 間必然產生電位差。

$$
V_{H}=V_{D}-V_{C}=\mathbf{E}_{y}d
$$

這個電位差稱為**霍爾電壓(Hall voltage)**，這種現象稱為**霍爾效應(Hall effect)**。

因為電場造成的力與磁場造成的力最終會平衡，所以：

$$
F_{y}=F_{B}\implies q\mathbf{E}_{y}=qvB\implies V_{H}=vBd
$$

回想 $i=qNAv\implies v=\frac{i}{qNA}$，代回就有：

$$V_{H}=\frac{iBd}{qNA}$$

注意到 $A$ 是截面積，所以 $A=td$：

$$
V_{H}=\frac{1}{qN} \frac{iB}{t}
$$

其中 $R_{H}=\frac{1}{qN}$，稱為**霍爾係數(Hall coefficient)**。

因為 $i,B,t$ 都是可測量的量，所以霍爾電壓可以拿來計算載流子密度 $N$。

前面我們假設載流子為正電荷，如果載流子為負電荷，則飄移速度 $\mathbf{v}$ 會與電場方向 $\mathbf{E}_{x}$ 相反。但是因為電荷帶電 $-q$，所以還是向上。

這樣看，上面會充滿負電荷，下面充滿正電荷。因此此時 $D$ 點電位會比 $C$ 點電位低，電場方向 $\mathbf{E}_{y}$ 會與之前假設的相反。

# Electromagnetic Waves: The Nature of Light

電磁波由一個電場 $\mathbf{E}$ 與磁場 $\mathbf{B}$ 組成，且 $\mathbf{E}\perp \mathbf{B}$，且波的傳遞方向同時垂直 $\mathbf{E}$ 與 $\mathbf{B}$。

若一電磁波朝 $x$ 方向傳播，固定時間 $t$，我們可發現 $\mathbf{E}$ 與 $\mathbf{B}$ 都隨 $x$ 呈現正弦變化：

![[Pasted image 20251214203000.png]]

這種電場與磁場的行為可以表示成：

$$
E=E_{0}\sin(kx-\omega t)
$$

$$
B=B_{0}\sin(kx-\omega t)
$$

注意到電磁婆的角頻率 $\omega$ 應該與造成該波的電荷震盪頻率相同。而且，電磁波的傳播不涉及到粒子運動，所以不需要傳播介質。

還有，所有電磁波都以：

$$
c=3\times10^{8}\text{ m/s}
$$

的速度傳播。