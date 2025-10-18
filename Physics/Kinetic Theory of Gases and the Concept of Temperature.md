
# Molecular Weight

我們如下定義**莫耳(mol)**：一莫耳的物質擁有與 12g 碳原子相同的數量。

通過物理測量，我們可以確定一莫耳的物質有多少個。這個常數稱 Avogadro's number：

$$
N_{A}=6.022 \times 10^{23} \text{ atoms/mol}=6.022\times 10^{26} \text{ atoms/kmol}
$$

用 SI 制來說，我們使用 kmol，即：與 12kg 碳原子相同的數量。

**同位素(isotope)**：相同化學性質，但質量略為不同(相同質子數(atomic number)，不同中子數(neutron number))。

我們使用碳的同位素碳-12作為標準：$12u$。

那麼，可以定義**原子質量單位(atomic mass unit)**：$1u=1.665057\times 10^{-27}kg$。

**原子量(atomic weight)**：某原子的平均質量(相對於我們定義的 碳-12 )。一莫耳某原子的重量就是其原子量。

**莫耳分率(mole fraction)**：在一個混合物中，某成分的莫耳數占總莫耳數的比率。

# Thermometers

這個是這段的重點喔：

$$
^{\circ}F= \frac{9}{5} ^{\circ}C+32
$$

# Ideal Gas Law and Absolute Temperature

我們定義壓力為每單位面積所承受的力：

$$
P= \frac{F}{A}
$$

我們定義：$1\text{Pa}=1\text{N/m}^{2}$。

而一大氣壓大約等於：$\boxed{1.01 \times 10^{5}\text{N/m}^{2}}$。

理想氣題有如下特性：
- 分子體積可忽略不計。
- 分子間的碰撞為彈性碰撞。
- 分子間沒有其他相互作用力。

我們可以在**高溫低壓**的情況下使用稀有氣體(鈍氣)模擬理想氣體。

我們列出理想氣體方程式($n$ 為氣體的莫耳數)：

$$
\boxed{PV=nRT}
$$

其中，$R$ 在物理中通常取 $\boxed{R=8.314\text{ J/mol}\cdot\text{K}}$。

我們定義**絕對零度(absolute zero)**：$-273.15^{\circ}C=0K$。

喔對，偷偷教你一個小技巧。就是說，如果給你一個未知莫耳數的氣體，跟你說他被壓縮幾倍 blablabla 的，然後讓你求最終溫度。你可以利用 $\frac{PV}{T}=nR$ 為定值，然後 $\frac{P_{0}V_{0}}{T_{0}}=\frac{P_{f}V_{f}}{T_{f}}$ 來求呦！

# Kinetic Theory of Gas Pressure

因為理想氣體的碰撞為彈性碰撞，所以運動軌跡應如下圖所示：

![[Pasted image 20251017201252.png]]

觀察上圖，我們可以推導牆壁對粒子施的力為：

$$
\bar{F_{x}}= \frac{mv_{x\text{ final}}-mv_{x\text{ initial}}}{\Delta t}=\frac{2mv_{x}}{\Delta t}
$$

假設理想氣體在一個邊長為 $l$ 的立方體容器中移動，那麼粒子從一個牆面移動到另一個牆面並反彈回來的時間為：

$$
\Delta t=\frac{2l}{v_{x}}
$$

帶回上式，得到：

$$
\bar{F_{x}}= \frac{mv_{x}^{2}}{l}
$$

因為上式為牆面所施的平均力，我們可以展開：

$$
\bar{F_{x}}= \frac{m}{l}(v_{x1}^{2}+v_{x 2}^{2}+\dots+ v_{xN}^{2})
$$

其中，$N$ 為容器中所有粒子的數量。

我們可以將平均速度表示為： $\bar{v_{x}^{2}}= \frac{v_{x 1}^{2}+\dots+ v_{xN}^{2}}{N}$。

帶回上式：

$$
\bar{F_{x}}=\frac{mN}{l}\bar{v^{2}_{x}}
$$

因為理想氣體的移動方向隨機，所以 $\bar{v_{x}}=\bar{v_{y}}=\bar{v_{z}}$。

那麼，$\bar{v^{2}}=\bar{v_{x}^{2}}+\bar{v_{y}^{2}}+\bar{v_{z}^{2}}=3 \bar{v_{x}^{2}}$。

帶回上式，得到：

$$
\bar{F}=\frac{mN}{3l}\bar{v^{2}}
$$

由 $P=\frac{F}{A}$：

$$
\bar{P}= \frac{mN}{3Al} \bar{v^{2}}
$$

因為此容器為立方體，所以 $Al=l^{3}=V$。

最後：

$$
\bar{P}= \frac{mN}{3V} \bar{v^{2}}= \boxed{\frac{2N}{3V}\left( \frac{1}{2}m \bar{v^{2}} \right)}
$$

# Kinetic Theory of Temperature

由理想氣體方程式，帶入上小節推出的公式，可以得到：

$$
\frac{2}{3}N\left( \frac{1}{2}m \bar{v^{2}} \right)=nRT=\frac{N}{N_{A}}RT
$$

這裡我們引入一個常數值 $k_{B}$：

$$
\boxed{k_{B}=\frac{R}{N_{A}}=1.38 \times 10^{-23}\text{ J/K per molecule}}
$$

我們可以將上式改寫為：

$$
\boxed{\frac{1}{2}m \bar{v^{2}}=\frac{3}{2}k_{B}T}\implies \boxed{T= \frac{2 \bar{E_{k}}}{3k_{B}}}
$$

需要小心的是，以上的 $E_{k}=\frac{1}{2}m \bar{v^{2}}$ 為**一個粒子**的動能。

**一團**理想氣體的動能為：

$$
\Delta E_{k}=\frac{3}{2} \frac{R}{N_{a}}\Delta T \times n \times N_{A}=\frac{3}{2}R \times n \Delta T = \boxed{nC_{v}\Delta T}
$$

注：雖然此式由理想氣體方程式推導而來，但是對於液體與固體亦成立。

由上式，我們還可以得到：

$$
\boxed{v_{RMS}= \sqrt{  \frac{3k_{B}T}{m} }}
$$

其中，$m$ 是單一粒子的質量(kg)。

需要注意的是，此處的速度是 root mean square。雖然不是一般的速度的平均值，但是也足夠接近啦～

# Measurement of Heat

**比熱(specific hear)**：使單位質量物體上升 $1^{\circ}C$ 所需的熱量。

我們可以定義溫度的上升量(其中，$\Delta Q$ 為所耗的熱量)：

$$
\boxed{\Delta Q=mc\Delta T}
$$

我們現在知道：熱量其實是能量的一種。我們可以通過那個在水裡轉來轉去然後旁邊釣著一個東西往下(等速)掉的裝置來測量。之所以要等速往下掉，是因為要避免動能變化，使得只使用位能就可以轉換。

我們可以得到以下等式：

$$
mgh=mc\Delta T\implies \boxed{4.184\text{ J}=1\text{ cal}}
$$

上式稱為：**熱的機械當量(mechanical equivalent of heat)**。

# Specific Heats of Gases

我們需要先知道莫耳比熱的概念(比熱每莫耳)：$\boxed{C_{v}=c_{v}M}$。

氣體在定容的情況下(因為無法透過膨脹來作功)：

$$
\Delta Q=\Delta E_{k}
$$

而我們知道：

$$
\boxed{\Delta Q=C_{v}n\Delta T}
$$

且：

$$
\boxed{\Delta E_{k}=(nN_{A})\left( \frac{3}{2}k_{B}\Delta T \right)}
$$

則：

$$
C_{v}n\Delta T=(nN_{A})\left( \frac{3}{2}k_{B}\Delta T \right)\implies \boxed{C_{v}=\frac{3}{2}R}
$$

如果我們轉換一下單位，使用 $\text{cal/mole-K}$ 來表示 $R$，則：

$$
\boxed{C_{v}\approx 3 \text{ cal/mole-K}}
$$

當在產生相變時，吸收的熱量拿來打斷鍵節，所以不會造成溫度上升。

如下圖所示，固體與液體之間的粒子相互作用力(位能)為負，因為其為束縛能，需要我們作功來打斷其鍵節。

![[Pasted image 20251017233410.png]]

# Work Done by a Gas

假設有一個圓柱，圓柱底下有一些理想氣體。在 $h_{1}$ 有一個被氣體支撐起的活塞。那麼當氣體膨脹導致活塞被推到 $h_{2}$ 時，所作的功可以如下推導。

由作功的定義：

$$
dW=F\ dx=PA \ dx=\boxed{P \ dV}
$$

我們定義，如果氣體向上推起活塞，則作正功，否則作負功。

# First Law of Thermodynamics

熱力學中有三個與氣體系統能量變化密切關聯的量：
- $\Delta E$：系統的內能變化量。內能是系統中所有粒子的動能總和，所以當 $\Delta T=0$ 則 $\Delta E=0$。
- $\Delta Q$：系統吸收的熱量。
- $\Delta W$：氣體系統對外所作的功。

那麼，我們有熱力學第一定律：

$$
\boxed{\Delta E=\Delta Q - \Delta W}
$$

此方程利用能量守恆建立，能量變化量等於吸收的能量減去釋出的能量。

# Maxwell-Boltzmann Statistical Distribution

此分佈可以預測速度為 $v$ 的粒子數有多少個。

Maxwell-Boltzmann 分佈的曲線方程如下：

$$
\boxed{f(v)=4\pi\left( \frac{m}{2\pi k_{B}T} \right)^{3/2}v^{2}e^{-\frac{mv^{2}}{2k_{B}T}}}
$$

系統中的粒子總數可以由此曲線積分而來：

$$
N=\int_{0}^{\infty}f(v) \ dv
$$

當溫度上升，平均速度與最高速度均增加，但是曲線較平緩。如下圖所示。

![[Pasted image 20251017232319.png]]

# 威儀指定習題

1. A gas tank contains 10kg of oxygen at a pressure of $10^{7}\text{ N/m}^{2}$ and a temperature of $27^{\circ}$C. As a result of a leak, the pressure drops to $5 \times10^{6}\text{ N/m}^{2}$ and the temperature decreases to $7^{\circ}$C. (a) What is the volume of the tank? (b) How much oxygen has leaked out? 

Ans:
需要注意，我兩個計算都是錯在 $K=273.15$ 加錯？？
(a) $V \approx 7.79 \times 10^{-2}\text{m}^{3}$ 
(b) $\approx 4.65\text{ kg}$ 

2. The temperature of a gas in a closed container at $27^{\circ}$C is raised to $327^{\circ}$C. By what multiple has $v_{RMS}$ changed?($v_{RMS}$ 改變了多少倍)

Ans: $\sqrt{ 2 }$ 倍

3. The temperature of a room $7\text{m}\times 5\text{m}\times 3\text{m}$ is $27^{\circ}\text{C}$. (a) How much energy is contained in the air of that room? (b) If that energy could be converted to electrical energy, for how long could a $100-W$ bulb be lit? Assume the air behaves as an ideal gas.

Sol:
臥槽，這題相當有水準啊！但是最後我想出來了，我也相當有水準啊！
(a)
我們使用公式：$E_{k}=n \times N_{A} \times \frac{3}{2}(k_{B}T)$。
其中，$n= \frac{PV}{RT}$，你會疑惑地發現沒有給壓力。
這時候神奇的來了，你應該直接帶入一大氣壓的值，即 $1.01 \times 10^{5}\text{ N/m}^{2}$。
那麼我們先帶入公式化減一波吧：$E_{k}= \frac{PV}{RT} \times N_{A} \times \frac{3}{2} \times \frac{R}{N_{A}} \times T=PV \times \frac{3}{2}=1.01 \times 10^{5} \times 105 \times \frac{3}{2} \approx 1.5 \times 10^{7}\text{ J}$ 。

(b)
$\frac{1.5 \times 10^{7}}{100\times{8}6400} \approx 1.84\text{ days}$。

4. A 20g bullet is shot into a ballistic pendulum with a velocity of $1000\text{ m/s}$. The mass of the wooden block is 2kg. If the bullet remains embedded in the block and 80% of the energy lost in the collision is absorbed as heat by the bullet, what is the increase in the temperature of the bullet? The specific heat of the bullet is $0.1\text{ cal/g-}^{\circ}\text{C}$. 

Sol:
:(
首先動量守恆得到最終速度：$v \approx 9.9$。
然後分別求動能：
$E_{1}= 0+ \frac{1}{2}\times0.02\times (10^{3})^{2}=10^{4}$ 
$E_{f}=\frac{1}{2} \times (2+0.02) (9.9^{2}) \approx 99$ 
需要注意這邊算的動能變化量是整體系統的動能變化量，如果只算子彈的動能變化，會導致傳遞給木塊的動能也被算到能量損失中，這是非常離譜且錯誤的觀念。
$|\Delta E|=E_{1}-E_{f} \approx 9901$ 
$9901 \times 80\%=20\text{ g} \times 0.1\text{ cal/g-}^{\circ}\text{C} \times 4.18\text{ J/cal} \times T\implies T \approx 945^{\circ}\text{C}$ 
需要注意，此處給的比熱單位為卡路里，我們要手動將其轉成焦耳。

5. A mole of an ideal gas is taken from state A to state C along the path ABC. (a) If 1000cal of heat flow into the gas and the gas does 2100J of work, what is the change in the internal energy of the gas? (b) When the gas is returned from C to A along the path CDA, 700cal of heat flow out of the gas. How much work is done on the gas? (c) What is the change in the temperature of the gas when it is brought back from C to A? (d) If the pressure of the gas in state A is 2 atm, what is the difference in the volume of the gas between stated D and A?

```
Pressure
^
|
|    B   ->   C
|    ^        |
|    |        ˇ
|    A   <-   D
|
|
---------------------> Volume

```

Sol:
(a)
利用 $\Delta E=\Delta Q-\Delta W$ 可以得到 $\Delta E \approx 2080\text{ J}$ 

(b)
利用 (a)
我們要從 C 返回 A，所以 $\Delta E$ 要**取負號**。
$-2080 = -700 \times 4.18 - \Delta W\implies\Delta W = -846\text{ J}$ 
作功為負，代表有外力在壓縮氣體，所以壓縮氣體的力作功為 $846\text{ J}$。

(c)
之前我有一個錯誤觀念，我以為 $\Delta Q=nC_{v}\Delta T$ 會在任意情況下成立。
事實上並不是，此條件僅在定容的情況下成立，即沒有作功($\Delta W=0$)的條件下才成立。
其實，應該是 $\Delta E=nC_{v}\Delta T$ 才對。
那麼 $-2080 = 1 \times \frac{3}{2}R \times \Delta T \implies\Delta T \approx -167\text{ K}$ 

(d)
本來我想說在 D 的溫度比 A 的高 167K，但實際上，C 到 D 也會降溫，所以我錯得很徹底。
利用能量的觀念想，$W_{CA}=W_{CD}+W_{DA}=0+W_{DA}\implies W_{DA}=-846\text{ J}$ 。之所以 $W_{CD}=0$，因為在此情況下 C 到 D 定容，所以氣體不作功。
那麼，利用：
$\Delta W=P\Delta V\implies-846=2\text{ atm} \times 1.01 \times 10^{5}\text{N/m}^{2}\text{atm }(V_{A}-V_{D})\implies V_{D}-V_{A} \approx 4.17 \times 10^{-3}\text{ m}^{3}$ 。
難的是想不到要用作功的式子啦！