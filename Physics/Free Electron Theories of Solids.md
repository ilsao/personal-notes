# Recap

回憶歐姆定律：

$$
V=iR
$$

且在長度為 $d$ 的均勻導體中，施加固定電場 $E$ 時電壓為：

$$
V=Ed
$$

因為在給定電位差 (因而給定 $E$) 時，電流大小與導體截面積成正比。

我們想在不受這種關係的情況下觀察，於是定義**電流密度(current density)** $J$：

$$
J=\frac{i}{A}\quad\text{ or }\quad i=AJ
$$

將上兩式代回歐姆定律：

$$
Ed=RAJ\implies E=R \frac{A}{d}J
$$

令**電阻率(electrical resistivity)** $\boxed{\rho=\frac{RA}{d}}$ ($\ohm-m$)，則：

$$
\boxed{E=\rho J}
$$

令**導電率(electrical conductivity)** $\sigma=\frac{1}{\rho}$，則：

$$
\boxed{J=\sigma E}
$$

下列皆為常數：
- $\rho$ 
- $\sigma$ 

固體間的導電性差距可達 $10^{27}$，我們得想個理論解釋歐姆定律與這種差異。

> [!note]
> $J=\sigma E$ 也是歐姆定律喔，展示出電流密度正比於電場。

# Classical Free Electron (CFE) Model

## Assumptions of the Model

CFE 有四個假設：
1. 金屬由離子陣列組成，價電子 (稱為**導電電子(conduction electrons)**，因其負責電流傳導) 可在離子結構中自由移動，但不可離開固體邊界。
2. 忽略電子間的互相作用，並假設由正電離子造成的位能為**常數**。即，電子可被視為理想氣體，滿足 Maxwel-Boltzmann 統計。
3. 不受電場時，電子以隨機熱運動速度移動：
$$
\boxed{\frac{1}{2}m\bar{v}^{2}=\frac{3}{2}k_{B}T}
$$
   其中波茲曼常數 $\boxed{k_{B}=1.38\times 10^{-23}\text{ J/K}=8.61\times 10^{-5}\text{ eV/K}}$。
4. 對固體施加電場 $E$ 時，自由電子會有平均**飄移速度(drift velocity)**，方向與電場相反而形成電流。

![[Pasted image 20260427190633.png|338]]

## Ohm's Laws: Derivation from CFE

考慮一個存在室溫 ($T=300\text{ K}$) 的金屬，其自由電子以熱速度做隨機運動。其均方根速度為：

$$
v_{RMS}=\left( \frac{3k_{B}T}{m} \right)^{1/2}\approx 1.2\times 10^{5}\text{ m/s}
$$

隨機運動意味著：從左穿過某截面與從右穿過的電子數量相同，所以淨流量為零，沒有電流產生。

> [!note]
> 這裡用均方根速度而非平均速度，所以就算方向相反且速度大小相同，一樣可以得到一個速度！
> 均方根：$\sqrt{ \langle v \rangle^{2} }$ 

要產生電流，我們要打破這種隨機對稱性。加入一個電場 $E$，會在原本的隨機運動上疊加一個飄移速度。

![[Pasted image 20260424222020.png|250]]

圖中黑線為隨機運動，藍線為增加飄移速度後的運動軌跡。

由於**電場越大，電子碰撞的機率上升** (從而不繼續加速)。所以**達到平衡狀態時，飄移速度會為定值** (但飄移速度大小會隨電場上升而增快) 而不會是非勻速運動。

現在我們嘗試推導歐姆定律：$J=\sigma E$ 且 $\sigma$ 與 $E$ 無關。

令飄移速度為 $v_{d}$，$N$ 為單位體積電子數。

回顧：
- $\Delta q=qNAv_{d}\Delta t$ 
- $i=\frac{\Delta q}{\Delta t}=qNAv_{d}$ 
- $J=\frac{i}{A}=qNv_{d}$ 
- $\boxed{v_{d}=\frac{J}{qN}}$ 

現在來找 $v_{d}$：

$F=ma=qE\implies a=\frac{qE}{m}$ 
$\implies \frac{dv}{dt}=\frac{qE}{m}\implies dv=\frac{qE}{m}dt$ 
兩邊同時積分：
$\int_{0}^{v}dv=\frac{qE}{m}\int_{0}^{t}dt$ 
於是得到：
$$
\boxed{v_{d}=\frac{qE}{m}t}
$$

> [!note]
> 積分的上下界如下解釋：
> 左邊從初速 $0$ 積累到 $v$，右邊從時間 $0$ 積累到 $t$。

令 $t=\tau$ (平均碰撞時間)，關聯 $E$ 與 $J$ (為了證明 $J=\sigma E$)：

$$
\frac{J}{qN}=\frac{qE}{m}\tau\implies \boxed{J=\frac{q^{2}N\tau}{m}E}
$$

對比發現：

$$
\boxed{\sigma=\frac{q^{2}N\tau}{m}}
$$

現在我們要證明 $\sigma$ 與 $E$ 無關，即 $\tau$ 與 $E$ 無關 (因為 $q,N,m$ 皆為常數)。

令**平均自由程(mean free path)** (即電子碰撞前平均移動距離) $l$，則：

$$
\tau=\frac{l}{\bar{v}}
$$

又 $v_{d}\ll v_{RMS}$，所以 $\bar{v}\approx v_{RMS}$：

$$
\tau=\frac{l}{v_{RMS}}
$$

又 $v_{RMS}$ 與 $E$ 無關，所以我們證明了歐姆定律。

## Failures of the CFE Model

### Specific Heat

CFE 模型假設電子如理想氣體，則理想氣體在定體積下莫耳比熱為：

$$
C_{v}=\frac{3}{2}R
$$

但實際量測為：

$$
C_{v}=10^{-4}RT
$$

數值相差極大，且實際還與溫度有關。

### Temperature Dependence of $\sigma$ 

CFE 中推得：

$$
\sigma \propto T^{-1/2}
$$

但實際測量：

$$
\sigma \propto T^{-1}
$$

# Quantum-Mechanical Free Electron (QMFE) Model

A. Sommerfeld 對自由電子模型做以下修改：
1. 電子由量子力學描述。即電子氣體**能階量子化**。
2. 電子遵守**包力不相容**原理。

對能量分布統計來說：
- 經典氣體遵守 Maxwell-Boltzmann 統計
- 量子氣體遵守 Fermi-Dirac 分佈

A. Sommerfeld 保留以下特性：
1. 價電子在固體中自由移動
2. 除去與離子的碰撞，忽略電子與晶格離子的靜電作用 (在固體中位能為定值)
3. 忽略電子間作用
$\implies$ 此假設使價電子保留理想氣體特徵，但由量子力學處理之。

## Three-Dimensional Infinite Potential Well

一個被原子核束縛的電子可視為落在一個三維無限深位能井中：
- 原子外沒有電子，視為邊界存在一個很大的位能障
- 因為忽略電子與電子、電子與離子間的交互作用，原子內的位能視為均勻常數

考慮：
- 內部：位能為 $0$ 
- 邊界：位能為無限大，電子無法逃出

![[Pasted image 20260425142923.png|191]]

解：$-\frac{\hbar^{2}}{2m}\left( \frac{\partial^{2}\chi}{\partial x^{2}}+\frac{\partial ^{2}\chi}{\partial y^{2}}+\frac{\partial^{2}\chi}{\partial z^{2}} \right)=E\chi$ 

利用變數分離法，解出：$\boxed{\chi(x,y,z)=A\sin(k_{1}x)\sin(k_{2}y)\sin(k_{3}z)}$，其中 $A=B^{3}$ (一維情況的三次方) 。

代入邊界條件連續，即在 $x=a,y=a,z=a$ 時 $\chi=0$。得到：

$$
k_{1}=\frac{n_{1}\pi}{a}\quad k_{2}=\frac{n_{2}\pi}{a}\quad k_{3}=\frac{n_{3}\pi}{a}
$$

從 $k=\sqrt{ \frac{2mE}{\hbar^{2}} }$ 得：

$$
\boxed{E_{n_{1},n_{2},n_{3}}=\frac{\pi^{2}\hbar^{2}}{2ma^{2}}(n_{1}^{2}+n_{2}^{2}+n_{3}^{2})}
$$

## Occupancy Condition at $T=0\text{ K}$ 

能量由三個量子數決定，所以會出現簡併態 (量子數不同，但能量相同)。

在 $T=0\text{ K}$ 時：
- 經典：平均能量為零
- 量子：最低能量為 $3E_{0}$，且根據包利不相容，電子不能處於相同量子態

![[Pasted image 20260425143050.png|302]]

考慮在 ($T=0\text{ K}$) 填一個 34 個電子的氣體：
- $3E_{0}$：填兩個 (電子自旋)
- $6E_{0}$：填六個
- $9E_{0}$：填六個
- $11E_{0}$：填六個
- $12E_{0}$：填兩個
- $14E_{0}$：填十二個

定義**費米能(Fermi Energy)**：最高被填滿的能量。在此例中為 $E_{F}=14E_{0}$。

在 $T=0\text{ K}$ 時：
- $E<E_{F}$：全滿
- $E>E_{F}$：全空

於是令 $F(E)$ 為某能量為 $E$ 的量子態被電子填滿的機率，在 $T=0\text{ K}$ 時：

$$
\boxed{F(E)=\begin{cases}
1 & E<E_{F} \\
0 & E>E_{f}
\end{cases}}
$$

這個分布其實就是 Fermi-Dirac 分布。

![[Pasted image 20260425145848.png|271]]

接下來兩節我們要解決以下兩個問題：
- 如何計算大量電子填入時的 $E_{F}$？
- 在某段能量區間 $\Delta E$ 中，我們可以填入多少電子？

## Calculation of $E_{F}$ at $T=0\text{ K}$ 

將 $n_{1},n_{2},n_{3}$ 作為互相垂直的三根座標軸，對每個整數的 $n_{1},n_{2},n_{3}$ 我們在空間中標記一個點。此點陣就是所有合法的一組 $(n_{1},n_{2},n_{3})$ 值。

![[Pasted image 20260425151256.png|281]]

令 $n^{2}=n_{1}^{2}+n_{2}^{2}+n_{3}^{2}$，則 $n$ 為某點 $(n_{1},n_{2},n_{3})$ 到原點的距離。所有與原點具有相同距離的點，對應到簡併態。

令 $n_{f}$ 為被佔據且離原點最遠的距離。則：

$$
E_{F}(0)=E_{0}n_{f}^{2}
$$

因為我們只允許 $n_{1},n_{2},n_{3}$ 為正值，所以只考慮 $\frac{1}{8}$ 個球。

於是電子總數為 (2 為自旋)：

$$
2\times\left( \frac{1}{8}\times\text{sphere volume} \right)\times(\text{number of points per unit volume})
$$

也可寫為：實空間中單位體積的自由電子數為 $N$，乘以三維位能井的體積 $a^{3}$。

$$
Na^{3}=2\times\left( \frac{1}{8}\times \frac{4}{3}\pi n_{f}^{3} \right)\times 1\implies n_{f}=\left( \frac{3Na^{3}}{\pi} \right)^{1/3}
$$

$$
\boxed{E_{F}(0)=\frac{\hbar^{2}}{2m}(3N\pi^{2})^{2/3}}
$$

Cu：的 $E_{F}= 6.95\text{ eV}$ 

## Density of States

我們考慮相鄰能量間隔：$\Delta E\sim \frac{\hbar^{2}\pi^{2}}{2ma^{2}}$。若取 $a=1\text{ cm}$，則能量差為：

![[Pasted image 20260425154410.png|563]]

是一個極小的值，可視為**準連續(quasicontinuous)**。

令 $g(E)dE$ 表示能量介於 $E$ 與 $E+dE$ 間的能態數，即**能態密度(density of energy states)**。

考慮 $n$ 到 $n+dn$ 間的所有態，其能量範圍：

$$
E=n^{2}E_{0}\quad\text{ to }\quad E+dE=(n+dn)^{2}E_{0}
$$

![[Pasted image 20260425151225.png|250]]

$$
\begin{align}
g(E)dE & =2\times\left( \frac{1}{8}\times\text{sphere shell volume} \right)\times(\text{number of points per unit volume}) \\
 & =2\left( \frac{1}{8}\times4\pi n^{2}dn \right)(1) \\
 & =\pi n^{2}dn
\end{align}
$$

考慮用 $E$ 表示 $g(E)dE$。

$n=\left( \frac{E}{E_{0}} \right)^{1/2}$ 
$\frac{dn}{dE}=\frac{1}{2}\left( \frac{1}{EE_{0}} \right)^{1/2}\implies dn=\frac{1}{2}\left( \frac{1}{EE_{0}} \right)^{1/2}dE$ 

$$
\begin{align}
g(E)dE & = \frac{\pi}{2E_{0}^{3/2}}E^{1/2}dE \\
 & =\boxed{CE^{1/2}dE}\quad\quad\quad\quad \boxed{C=\frac{\pi}{2E_{0}^{3/2}}=\frac{a^{3}(2m)^{3/2}}{2\hbar^{3}\pi^{2}}} \\
 & \implies g(E)dE\propto E^{1/2}
\end{align}
$$

$g(E)$ 給出某能量下可用的能態數，為了得知有多少電子佔據這些能態，必須乘以 Fermi-Dirac 分布：

$$
N(E)dE=g(E)F(E)dE
$$

![[Pasted image 20260425155654.png|302]]![[Pasted image 20260425155707.png|265]]

![[Pasted image 20260427200013.png|533]]

注意到 (單個電子的) 平均能量為：

$$
\boxed{\overline{ E }(T=0)=\frac{3}{5}E_{F}}
$$

## Energy Distribution of Electrons for $T>0\text{ K}$ 

若電子具有約 $k_{B}T$ 的熱能時，就會嘗試躍遷到更高能量的狀態。

**只有能量在 $E_{F}$ 下方約 $k_{B}T$ 範圍內的電子可能躍遷**。若電子能量低於 $E_{F}$ 很多，因為能量比它們高的能階已被佔據，所以無法躍遷。

Fermi-Dirac 分布的精確形式：

$$
\boxed{F(E)=\frac{1}{\text{exp}\left( \frac{E-E_{F}}{k_{B}T} \right)+1}}
$$

當 $E\leq E_{F}-k_{B}T$ 時 $F(E)\approx 1$，又 $E\geq E_{F}+k_{B}T$ 時 $F(E)\approx0$。

![[Pasted image 20260425163724.png|298]]

重新定義 Fermi Energy：**$E_{F}$ 是使電子佔據機率為 $\frac{1}{2}$ 的能量**。

## Failure of CFE Model Revisited

### Specific Heat

對於 $C_{v}$ 的計算：
- 經典：每個電子都可以吸收熱能
- 量子：只有比例約 $\frac{k_{B}T}{E_{F}}$ 的電子可以吸收熱能

回憶到：$\boxed{C_{v}=\frac{dE}{dT}}$ 

對 CFE 來說：$d E=N_{A}\times\left( \frac{3}{2}k_{B}\ d T \right)$ 
$\implies C_{v}=\frac{dE}{dT}=\frac{3}{2}(N_{A}k_{B})=\frac{3}{2}R$ 

對 QMFE 來說：
能量變化 = **被激發的電子數 $\times$ 平均獲得能量** 
$\Delta E=\boxed{N_{A}\times\left( \frac{k_{B}T}{E_{F}} \right)\times(k_{B}\Delta T)}= \frac{N_{A}k_{B}^{2}T^{2}}{E_{F}}$ 
$\implies C_{v}=\frac{dE}{dT}=\frac{2N_{A}k_{B}^{2}}{E_{F}}T=\boxed{\frac{2k_{B}}{E_{F}}RT}$ 
代入 $E_{F}\approx 5\text{ eV}$ 則有 $C_{v}\approx 10^{-4}RT$ 

### Electrical Conductivity

CFE Model 認為：
from:
$\sigma=\frac{q^{2}N\tau}{m}$ 
又唯一與溫度相關的量為 $\tau$。
$\tau \approx \frac{l}{v_{RMS}}$ 
$v_{RMS}=\left( \frac{3k_{B}T}{m} \right)^{1/2}$ 
$\implies\sigma \propto T^{-1/2}$ 

這邊我們想解釋：$\sigma \propto T^{-1}$。

沒有外加電場時，電子速度完全隨機。即，找到速度 $+v_{x}$ 電子的機率等於找到速度 $-v_{x}$ 電子的機率。

從 $E=\frac{1}{2}mv^{2}$，我們有：
- $E^{1/2}=\pm \sqrt{ \frac{m}{2} }v$ 
- $dE=mv\ dv$ 

代入 $g(E)dE=CE^{1/2}dE$，得：

$$
\boxed{g(v)dv\propto v^{2}\ dv}
$$
令 $v_{F}$ 為能量為 $E_{F}$ 時的速度，則：

![[Pasted image 20260425221716.png|500]]

施加一個 $-x$ 朝向的電場，則分布會向 $+x$ 移動。

![[Pasted image 20260425221818.png|481]]

這表示，每個電子都參與導電過程且獲得了能量。

> [!warning]
> 在比熱的討論時，只有接近 $E_{F}$ 的電子獲得了能量。
> 這是因為：
> - 比熱情況：電子獲得的**能量隨機分配**，所以分布不會總體偏移 (包利不相容)。
> - 電場情況：每個電子都**獲得相同的能量**，同時偏移。

雖然每個電子都參與導電，但實際**決定散射時間 $\tau$ 的是接近 $E_{F}$ 的電子**。

因為電子在散射時會損失能量，所以**只有低能態有空位的電子會被散射**，即接近 $E_{F}$ 的電子。

電子不會被無限加速，因為必須要**有高能態空位電子才能加速**，所以會被 $E_{F}$ 附近電子阻擋。

已知：$\tau=\frac{l}{v_{F}}$ 與 $\sigma=\frac{q^{2}N\tau}{m}$。代入得 $\sigma=\frac{q^{2}Nl}{mv_{F}}$。

但在 QMFE 中，$E_{F}$ (因而 $v_{F}$) 與溫度無關。若依照 CFE 假設，$l$ 為原子間距，則 $l$ 也與溫度無關。因而 $\sigma$ 與溫度無關，與實驗相矛盾。

所以，CFE 中 $l$ 的假設錯誤。

讓我們考慮銅：
- $\sigma=5.9\times 10^{7}\ \ohm^{-1}\text{m}^{-1}$ 
- $E_{F}=6.95\text{ eV}$ 
- $N=8.4\times 10^{28}\text{ electrons/m}^{3}$ 
- 求 $l$？

Sol:
$l=v_{F}\tau$ 
$v_{F}=\sqrt{ \frac{2E_{F}}{m} }=1.56\times 10^{6}\text{ m/s}$ 
$\tau=\frac{m\sigma}{q^{2}N}=2.5\times 10^{-14}\text{ s}$ 
$\implies l=390\times 10^{-10}$ 
為原子間距的幾百倍。

我們通過布拉格散射的觀點來修正，已知 $2d\sin \theta=n\lambda$ 時發生散射。若波長過長，則反射 (即布拉格散射) 無法發生。

對銅：
- $\lambda_{F}=\frac{h}{\sqrt{ 2mE_{F} }}\approx 4.65\times 10^{-10}\text{ m}$ ($\lambda=\frac{h}{p}$)
- 晶格間距 $d=2.09\times 10^{-10}\text{ m}$ 

因為 $\lambda_{F}>2d$，電子幾乎不被晶格散射，可以自由穿越晶體。

真正的散射由以下導致：
- 缺陷
- 雜質
- **晶格振動(phonons)** (主要緣由)

當晶格振動時，會產生有效散射截面。有效散射截面越大，散射越強，自由程越短。

於是：

$$
\boxed{l\propto \frac{1}{\pi r^{2}}}
$$

且振動能量：

$$
\boxed{E\propto r^{2}\propto T}
$$

> [!note]
> 能量與振幅平方成正比，且晶格吸收能量為 $k_{B}T$。

所以：

$$
r^{2}\propto T\implies l\propto T^{-1}
$$

代入：

$$
\sigma=\frac{q^{2}Nl}{mv_{F}}\propto T^{-1}
$$

# 威儀指定習題

![[Pasted image 20260427194620.png|695]]

Sol:
電子數 / 莫爾 $\times$ 一立方公尺的莫爾數
$6\times 10^{23}\times\left( \frac{19.3}{197} \right)\times 10^{6}$ 
$\approx 5.87\times 10^{28}\text{ m}^{3}$ 
注：monovalent 一價的

![[Pasted image 20260427195337.png|661]]

Sol:
$V_{H}=R_{H} \frac{iB}{d}=\frac{1}{Nq} \frac{iB}{d}$ 
$\implies 2.6\times 10^{-6}= \frac{1}{N\times 1.6\times 10^{-19}} \frac{20\times 1.2}{10^{-3}}$ 
$\implies N= 5.77\times 10^{28}\text{ m}^{3}$ 

![[Pasted image 20260427201344.png|712]]

Sol:
(a)
因為 $k_{B}T\ll E_{F}$，所以當 $T$ 不大時基本沒啥影響。
雖然 $\overline{ E }(T=0\text{ K})=\frac{3}{5}E_{F}$，但對 $\overline{ E }(T=300\text{ K})\approx \frac{3}{5}E_{F}$ 
銅的 $E_{F}\approx 6.95\text{ eV}$。
$\Delta E=\frac{3}{5}E_{F}-\frac{3}{2}k_{B}T=4.13\text{ eV}$ 
注意：這個是一個電子放出的能量
$\text{E/m}^{3}=4.13\times 8.4\times 10^{28}=3.46\times 10^{29}\text{ eV}$ 
(b)
$t= \frac{3.46\times 10^{29}\times 1.6\times 10^{-19}}{100}=5.54\times 10^{8}\text{ s}$ 

![[Pasted image 20260427202704.png|683]]

Sol:
處於激發態的部分約為：$\frac{k_{B}T}{E_{F}}$ 
$\approx\frac{ 8.63\times 10^{-5}\times 300}{6.95}=3.7\times 10^{-3}$ 

![[Pasted image 20260427202933.png|738]]

Sol:
$\frac{k_{B}T}{E_{F}}\approx \frac{8.63\times 10^{-5}\times 2273}{1}\approx 0.196$ 

![[Pasted image 20260427203659.png|690]]

Sol:
這邊的 show 不是讓你說明，是讓你用數學啦！
能量為 $E$ 的量子態被填滿的機率為：$F(E)=\frac{1}{\text{exp}\left( \frac{E-E_{F}}{k_{B}T} \right)+1}$ 
$F(E_{F}+\Delta E)=\frac{1}{\text{exp}\left( \frac{\Delta E}{k_{B}T} \right)+1}$ 
$F(E-\Delta E)=\frac{1}{\text{exp}\left( -\frac{\Delta E}{k_{B}T} \right)+1}$ 
想說明 $E_{F}+\Delta E$ 的能態被佔據的機率等於 $E_{F}-\Delta E$ 的態空掉的機率，只需相加兩個機率等於 $1$ 即可。
令 $t=\frac{\Delta E}{k_{B}T}$。
$F(E_{F}+\Delta E)+F(E_{F}-\Delta E)=\frac{1}{e^{t}+1}+\frac{1}{e^{-t}+1}$ 
$= \frac{e^{-t}+1+e^{t}+1}{(e^{t}+1)(e^{-t}+1)}=1$ 

# 威儀考古

1. 畫出Fermi-Dirac Distribution的圖形，並標出重要的座標軸及數值

Sol:
![[Pasted image 20260425145848.png|271]]

2. $k_{B}T$ 在 $T=300\text{ K}$ 時的數值為？

Sol:
$\approx 8.63\times 10^{-5}\times 300=2.589\times 10^{-2}\text{ eV}$ 

3. Kronig-Penny Model 有兩個缺點  第一個是 Not much physical insight (只是純粹解數學式而得到結果) 請問第二個是什麼?

Sol:
沒有給出一個能帶中的量子態數

4. 請解釋何謂 Fermi-Dirac Distribution

Sol:
在熱平衡下，能量為 $E$ 的量子態被佔據的機率。