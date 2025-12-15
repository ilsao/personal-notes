
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
\boxed{F=i\Delta \mathbf{l}\times \mathbf{B}}
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
\boxed{\tau=iAB\sin \theta}
$$

也就是說，當 $\theta=90^{\circ}$ 時，也就是線圈平面與磁場方向平行時，力矩最大。

當 $\theta=0^{\circ}$ 時，也就是線圈平面與磁場方向垂直時，力矩最小，為零。

注意到，力矩大小可以通過調整電流大小 $i$ 與磁場大小 $B$ 來調整。

# Magnetic Dipole Moment

經由上節，我們可以發現與力矩相關的兩個非常重要的量是：線圈面積與通過的電流大小。

那麼，我們定義一個量為它們倆的乘積，這個量被稱為**磁偶極矩(magnetic dipole moment)** 或稱**磁矩(magnetic moment)**：

$$
\boxed{\mu=iA}
$$

注意，有幾圈就要乘幾喔：$\mu=n\cdot iA$。

那麼力矩現在就可以被表示為：

$$
\tau=\mu B\sin \theta
$$

通過外積與力矩的定義，我們可以發現 (上圖) 力矩的方向為指向紙面。

我們將 $\mathbf{\mu}$ 定義為一個向量，其方向是根據右手定則，右手四指沿著電流方向彎曲後大拇指指向的方向。可見上圖標示。那麼可以繼續重寫公式：

$$
\boxed{\tau=\mathbf{\mu}\times \mathbf{B}}
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
F_{q}=\frac{F}{NA\Delta {l}}=\boxed{q\mathbf{v}\times \mathbf{B}}
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
F_{y}=F_{B}\implies q\mathbf{E}_{y}=qvB\implies \boxed{V_{H}=vBd}
$$

回想 $i=qNAv\implies v=\frac{i}{qNA}$，代回就有：

$$\boxed{V_{H}=\frac{iBd}{qNA}}$$

注意到 $A$ 是截面積，所以 $A=td$：

$$
\boxed{V_{H}=\frac{1}{qN} \frac{iB}{t}}
$$

其中 $\boxed{R_{H}=\frac{1}{qN}}$，稱為**霍爾係數(Hall coefficient)**。

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

注意到電磁波的角頻率 $\omega$ 應該與造成該波的電荷震盪頻率相同。而且，電磁波的傳播不涉及到粒子運動，所以不需要傳播介質。

還有，所有電磁波都以：

$$
c=3\times10^{8}\text{ m/s}
$$

的速度傳播。

# 威儀指定習題

![[Pasted image 20251214235546.png]]

Sol:
equator: 赤道
(a)
這題錯在看不懂題目，沒搞懂到底怎麼掛的。
應該是一根線豎直掛著一個東西向的導線。
由 $F=i\Delta l\times B$，且電流從東流到西與地磁從南到北，可以算出 $F=150\cdot2\cdot 4\times 10^{-5}=1.2\times 10^{-2\text{ N}}$ 且方向向下。
那麼繩張力為：$mg+F=9\times 10^{-3}\cdot 9.8+1.2\times 10^{-2}\approx 10.02\times 10^{-2}\text{ N}$。
(b)
$mg-F=9\times10^{-3}\cdot 9.8-1.2\times 10^{-2}=8.82\times10^{-2}-1.2\times 10^{-2}=7.62\times 10^{-2}\text{ N}$ 

![[Pasted image 20251215001728.png]]

Sol:
(a)
對於水平的兩個 wire，因為電流方向平行磁場，所以受力為零。
對於鉛直兩個 wire，每個 wire 受力 $F=i\Delta l\times B=2\cdot0.6\cdot 0.5=0.6\text{ N}$。
(b)
$\tau=\mathbf{r}\times F=0.15\cdot 2\cdot  0.6=0.18\text{ N}$。

![[Pasted image 20251215002334.png]]

Sol:
(a)
coil: 盤起
$l=2\pi r\cdot n\implies r=\frac{l}{2\pi n}$ 
$\mu=n\cdot i\cdot \pi\left( \frac{l}{2\pi n} \right)^{2}=\frac{il^{2}}{4\pi n}$ 
`~~~^ 注意這邊要乘以 n`
當 $n=1$ 時 $\mu$ 有最大值。
(b)
$\mu=\frac{il^{2}}{4\pi n}$ 

![[Pasted image 20251215003823.png]]

Sol:
公式沒背好：$F_{q}=q\mathbf{v}\times \mathbf{B}$。
所以：$F_{q}=1.6\times 10^{-19}(3\times 10^{5},0,7\times 10^{5})\times(0,0.4,0)=(1.92\mathbf{k}-4.48\mathbf{i})10^{-14\text{ N}}$ 

 ![[Pasted image 20251215012848.png]]
Sol:
要使得粒子不被偏轉，必須有 $F_{B}=F_{E}$。
所以有：$qvB=qE\implies v=\frac{E}{B}=\frac{5\times10^{4}}{10^{-1}}=5\times10^{5}\text{ N/sec}$。

![[Pasted image 20251215013343.png]]![[Pasted image 20251215013358.png]]

Sol:
公式會記不起來，所以可以自己推導。
$F_{E}=F_{B}\implies qE=qvB\implies E=vB$ 
$V_{H}=dE=dvB$ 
$i=qNAv\implies v=\frac{i}{qNA}$ 
$\implies V_{H}=\frac{1}{qN} \frac{idB}{A}=\frac{1}{qN} \frac{iB}{t}$ 
$2\times10^{-6}=\frac{1}{1.6\times 10^{-6}N}\times \frac{50\cdot 0.5}{10^{-3}}\implies N\approx 7.8\times 10^{28}\text{ m}^{3}$ 
(可以注意到按題目這樣說，載流子會是負電荷，但是計算貌似用不上呢)

# 威儀考古

1. 自然界中原子產生磁場的兩個主要原因?

Sol:
電子繞著原子核公轉，產生 atomic current，產生磁場。
電子自轉，自轉電流，產生磁場。

2. 下圖電流中移動的是正電還是負電？
![[Pasted image 20251215123139.png]]

Sol:
負電，因為電流方向與磁場外積後受力向下。而下方積累的是負電荷，所以電流中移動的是負電。

3. 解釋什麼是法拉第定律

Sol:
當磁通量 $\phi$ 產生變化，會產生感應電流 $\epsilon$ 以抵抗磁通量的變化。
$\epsilon=-\frac{\Delta\phi}{\Delta t}$ 