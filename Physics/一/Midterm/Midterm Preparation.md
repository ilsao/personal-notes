
# 重要題目

1. 列出四大作用力與他們的範圍與大小

| 四大作用力名稱及大小排序 | 範圍             |
| ------------ | -------------- |
| 強力           | $10^{-15}$ (!) |
| 電磁力          | $\infty$       |
| 萬有引力         | $\infty$       |
| 弱力           | $10^{-17}$ (!) |

2. (a) 托勒密如何解釋星體忽進忽退？(b) 地心說算不算科學？

雖然我感覺我的答案是對的，但還是列給你看：
(a) 利用大輪小輪的概念。星體繞著小輪轉，小輪的中心繞著地球轉。這樣就可以說明忽進忽退的現象。
(b) 是，只要是利用合理而科學的推理與演繹得來的知識就算是科學，就算在現在已經被證明錯誤仍算科學。

3. 說明 (a) 質量守恆定律 (b) 為何⼀個東⻄的能量是「此物體能給其他物體做功的能⼒」

(a) 一個系統中的能量不會憑空出現或消失，只會從一種形式轉成另一種形式，**總能量和保持不變**。

(b) 作功會造成物體的位能或動能改變，也就是能量的改變。所以，能量就是該物體能給其他物體作功的能力。

4. 說明為何摩擦力與接觸面積大小無關

摩擦力取決於物體與接觸面微突起造成的電磁力。面積變大時，壓力變小，使得物體與微突起接觸較淺。面積變小時壓力變大，使得物體與微突起接觸較深。單位面積電磁力乘以總面積大小即為摩擦力，雖然壓力會影響電磁力，但與面積和壓力的變化互相抵銷，所以摩擦力大小相同。

5. 請⽤理想氣體公式解釋為何在深海潛⽔的⼈突然往海⾯上游是⼀件很危險的事情？

由 $PV=nRT$ 如果短時間內**氣體溫度與莫耳數保持不變**，$P_{1}V_{1}=P_{2}V_{2}$。
我們假設有人從 90m 的深水快速上浮到海平面：(10 公尺水柱壓力 $\approx 1\text{ atm}$)
$\frac{P_{1}}{P_{2}}=\frac{10\text{ atm}}{1\text{ atm}}=\frac{V_{2}}{V_{1}}\implies V_{1}:V_{2}=1:10$ ，氣體會變大十倍，使人的肺部爆炸。

6. The temperature of a room $7\text{m}\times 5\text{m}\times 3\text{m}$ is $27^{\circ}\text{C}$. (a) How much energy is contained in the air of that room? (b) If that energy could be converted to electrical energy, for how long could a $100-W$ bulb be lit? Assume the air behaves as an ideal gas.

臥槽，這題相當有水準啊！但是最後我想出來了，我還是太權威了。
(a)
我們使用公式：$E_{k}=n \times N_{A} \times \frac{3}{2}(k_{B}T)$。
其中，$n= \frac{PV}{RT}$，你會疑惑地發現沒有給壓力。
這時候神奇的來了，你應該直接帶入一大氣壓的值，即 $1.01 \times 10^{5}\text{ N/m}^{2}$。
那麼我們先帶入公式化減一波吧：$E_{k}= \frac{PV}{RT} \times N_{A} \times \frac{3}{2} \times \frac{R}{N_{A}} \times T=PV \times \frac{3}{2}=1.01 \times 10^{5} \times 105 \times \frac{3}{2} \approx 1.5 \times 10^{7}\text{ J}$ 。

(b)
$\frac{1.5 \times 10^{7}}{100\times{8}6400} \approx 1.84\text{ days}$。

7. Derive that the magnitude of the gravity is inversely proportional to the square of the object’s distance from Newton’s second law of motion and Kepler’s third law of planetary motion

首先，利用牛頓第二定律：
$F=ma=m \frac{v^{2}}{r}=m \frac{\left( r \cdot \frac{2\pi}{T} \right)^{2}}{r}=m \frac{4\pi^{2}r}{T^{2}}$ 
然後，因為科普勒第三行星運動定律：$\frac{r^{3}}{T^{2}}=\text{const.}\implies T^{2}=kr^{3}$ ，其中 $k$ 為某個常數。
帶回上式：$F=m \frac{4\pi^{2}r}{kr^{3}}=m \frac{4\pi^{2}}{k} \cdot \frac{1}{r^{2}} \implies F \propto \frac{1}{r^{2}}$ 

8. What is “centrifugal force”? Is centrifugal force a real force from a physical point of view? If centrifugal force doesn’t exist, please explain why lots of people believe in centrifugal force.

離心力是指當物體處於旋轉座標系(非慣性座標)中，讓物體看起來受到向外推的一個假想力力。
離心力不是一種真實存在的力，而是一種假想力。因為處於非慣性坐標中，為了讓牛頓定律成立，必須引入假想力來讓數學看起來平衡。之所以會感覺被向外推，是因為慣性想保持原本與切線同向的移動方向，但卻被向心力向內束縛而產生的感覺。

9. A 20g bullet is shot into a ballistic pendulum with a velocity of $1000\text{ m/s}$. The mass of the wooden block is 2kg. If the bullet remains embedded in the block and 80% of the energy lost in the collision is absorbed as heat by the bullet, what is the increase in the temperature of the bullet? The specific heat of the bullet is $0.1\text{ cal/g-}^{\circ}\text{C}$. 

:(
首先動量守恆得到最終速度：$v \approx 9.9$。
然後分別求動能：
$E_{1}= 0+ \frac{1}{2}\times0.02\times (10^{3})^{2}=10^{4}$ 
$E_{f}=\frac{1}{2} \times (2+0.02) (9.9^{2}) \approx 99$ 
需要注意這邊算的動能變化量是整體系統的動能變化量，如果只算子彈的動能變化，會導致傳遞給木塊的動能也被算到能量損失中，這是非常離譜且錯誤的觀念。
$|\Delta E|=E_{1}-E_{f} \approx 9901$ 
$9901 \times 80\%=20\text{ g} \times 0.1\text{ cal/g-}^{\circ}\text{C} \times 4.18\text{ J/cal} \times T\implies T \approx 945^{\circ}\text{C}$ 
需要注意，此處給的比熱單位為卡路里，我們要手動將其轉成焦耳。

10. (a) 慣性座標的定義？(b) 慣性座標為什麼重要？(c) 在非慣性座標系統，有哪些物理量不會改變大小？

(a) 牛頓**第一**運動定律永遠成立的坐標系。

(b) 可以直接套用牛頓三大運動定律而**無需引入假想力**。

(c) 體積，質量，溫度... 


11. 絕對溫度代表何種物理量？潛熱為何不會影響溫度？

絕對溫度代表 $K$(Kelvin)。潛熱是在相變過程中吸收或放出的熱，其能量用來**增減**粒子間的位能，不會造成動能改變，也就導致溫度不變。

12. A mole of an ideal gas is taken from state A to state C along the path ABC. (a) If 1000cal of heat flow into the gas and the gas does 2100J of work, what is the change in the internal energy of the gas? (b) When the gas is returned from C to A along the path CDA, 700cal of heat flow out of the gas. How much work is done on the gas? (c) What is the change in the temperature of the gas when it is brought back from C to A? (d) If the pressure of the gas in state A is 2 atm, what is the difference in the volume of the gas between stated D and A?

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

(a)
利用 $\Delta E=\Delta Q-\Delta W$ 可以得到 $\Delta E \approx 2080\text{ J}$ 

(b)
利用 (a)
我們要從 C 返回 A，所以 $\Delta E$ 要**取負號**。
$-2080 = -700 \times 4.18 - \Delta W\implies\Delta W = -846\text{ J}$ 
作功為負，代表有外力在壓縮氣體，所以壓縮氣體的力作功為 $846\text{ J}$。

(c)
之前我有一個錯誤觀念，我以為 $\Delta Q=nC_{v}\Delta T$ 會在任意情況下成立。
事實上並不是，此條件**僅在定容的情況下成立，即沒有作功($\Delta W=0$)的條件下才成立**。
其實，應該是 **$\Delta E=nC_{v}\Delta T$ 才對**。
那麼 $-2080 = 1 \times \frac{3}{2}R \times \Delta T \implies\Delta T \approx -167\text{ K}$ 

(d)
本來我想說在 D 的溫度比 A 的高 167K，但實際上，C 到 D 也會降溫，所以我錯得很徹底。
利用能量的觀念想，$W_{CA}=W_{CD}+W_{DA}=0+W_{DA}\implies W_{DA}=-845\text{ J}$ 。之所以 $W_{CD}=0$，因為在此情況下 C 到 D 定容，所以氣體不作功。
那麼，利用：
$\Delta W=P\Delta V\implies-846=2\text{ atm} \times 1.01 \times 10^{5}\text{N/m}^{2}\text{atm }(V_{A}-V_{D})\implies V_{D}-V_{A} \approx 4.17 \times 10^{-3}\text{ m}^{3}$ 。

13. 請問，一個原點固定於地球表面上的參考座標是不是一個慣性座標？如果不是，請問為什麼不是？

不是，因為地球在自轉，有一個向心加速度，所以為非慣性座標。例如，想要解釋颱風的旋轉方向需要引入假想的柯氏力。

14. The radius of a carbon atom is about $2.5 \times 10^{-8}$ cm. Neglect the volume lost in packing the spheres; Answer following questions. 
(a) How many could fit in a row 1-cm long?
(b) How many could fit in a layer one atom deep and area $1cm^{2}$?
(c) How many could fit in a cube 1 cm on each side?
(d) If a crystal of carbon atoms(diamond) had this form, what is the minimum number of impurity atoms that could block the light coming **through** the faces of a 1-$cm^{3}$ cube? Express your answer in both percent and in parts per million. (Hint: Assume as an approximation that a layer of impurity atoms on each of three faces of the cube at right angles to each other could block all the light)

(a)
簡單：$\frac{1}{2 \times 2.5\times 10^{-8}} = 2\times 10^{7}$。
唯一需要注意的是，題目給的長度是半徑，我們需要乘以二用直徑算。

(b)
簡單，$(2\times 10^{7})^{2} = 4\times 10^{14}$。

(c)
簡單，$(2 \times 10^{7})^{3}=8 \times 10^{21}$。

(d)
簡單，讓光透不過去只需要三面：$3 \times 4\times 10^{14}=1.2 \times 10^{15}$。
percentage: $\frac{1.2 \times 10^{15}}{8 \times 10^{21}} \times 10^{2}=1.5 \times 10^{-5}\%$ 
ppm: $1.5 \times 10^{-7} \times 10^{6}=1.5 \times 10^{-1}$ ppm