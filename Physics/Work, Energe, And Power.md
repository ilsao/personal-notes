
# Work

$$
\boxed{\Delta W = F \cdot \Delta x}
$$

我們定義一個新單位焦耳(j) 為 牛頓 $\cdot$ 米。$1N \cdot 1J$。

注意，雖然功有分正負，但功並不能表明方向，功是標量。

# Work done by a Variable Force

通過將變動的力劃分為小的間隔，我們可以建立如下等式：

$$
W=\sum_{i=1}^{N}F_{x i}\Delta x
$$

也可以寫成其積分形式：

$$
\boxed{W=\int_{a}^{b}F_{x} \ dx}
$$

也就是說，作功等於 $F-x$ 圖的面積。

# Potential Energy

我們若將一個物體提升到 $h$ 的高度，則放手後重力做功為 $mgh$。我們將這種重力擁有潛在的做功能力稱作位能。重力位能定義如下：

$$
\boxed{E_{p}=mgh}
$$

需要注意的是，位能的大小跟隨我們定義的水平線而定。

以下讓我們來推導彈力位能公式：

因為 $F_{\text{spring}}=-kx$，所以我們施的力與彈簧長度成正比。也就是說 $F=kx$。

則我們將彈簧拉伸所做的功為：

$$
W=\int_{x_{0}}^{x}F \cdot dx = \frac{1}{2}kx^{2}
$$

所以我們定義：

$$
\boxed{E_{\text{p,sp}}=\frac{1}{2}kx^{2}}
$$

# Kinetic Energy

當力使得物體的速度發生改變，我們稱該作功造成該物體失去或獲得動能。

我們可以由兩種方式得到動能公式。

(I) 假設力的大小不變，施力方向平行位移方向。則：

$$
W=Fx=max
$$

使用 $v^{2}-v_{0}^{2}=2ax$ 替換，我們可以得到：

$$
W=m\times \frac{v^{2}-v_{0}^{2}}{2}=\frac{1}{2}mv^{2}-\frac{1}{2}mv_{0}^{2}
$$

所以我們定義動能：

$$
\boxed{E_{k}=\frac{1}{2}mv^{2}}
$$

(II)

我們可以更嚴謹的獲得這個結論，使用積分表達功：

$$
W=\int_{x_{0}}^{x}F \ dx=m\int_{x_{0}}^{x}a \ dx
$$

我們將 $a$ 代換：

$$
a=\frac{dv}{dt}=\frac{dv}{dx} \frac{dx}{dt}=v \frac{dv}{dx}
$$

帶入積分公式：

$$
W=m\int_{x_{0}}^{x} v \frac{dv}{dx} \ dx=m \int_{v_{0}}^{v} v \ dv = \left. m \frac{v^{2}}{2}  \right|^{v}_{v_{0}}=\frac{1}{2}mv^{2}-\frac{1}{2}mv_{0}^{2}
$$

通過觀察，我們可以發現：

$$
\boxed{W_{net}=\Delta E_{k}}
$$

此公式稱為**功能定理**。合力作功等於動能變化量。

# Energy Conservation

我們需要引入**保守力(conservative force)** 與**非保守力(non-conservative force)** 的概念。

保守力：只與位移有關，位移等於零則做功為零。例如，重力，彈力。

非保守力：與路徑有關，位移為零做功不為零。例如，摩擦力。

保守力做功會消耗位能，例如在高度 $h$ 釋放物體。則保守力作功會造成位能減少。即：

$$
\boxed{W_{con}=-\Delta U}
$$

我們可以由合力作功等於動能變化量得到：

$$
W_{net}=W_{con}+W_{non-con}=\Delta K\implies \boxed{W_{non-con}=\Delta K+\Delta U}
$$

同時，由非保守力做功的等式，我們可以推得總能量守恆：

$$
\boxed{K_{i}+U_{i}+E_{in}=K_{f}+U_{f}+E_{out}} \implies \Delta E=-(\Delta K+\Delta U)
$$

因為 $E_{in}, E_{out}$ 必由非保守力做功造成，所以以上邏輯自洽。($\Delta E > 0$ 時，非保守力做負功)

若僅有保守力作功(非保守力作功為零)，我們可以推出**機械能守恆定理**：

$$
\Delta K+\Delta U=0\implies \boxed{\frac{1}{2}mv_{1}^{2}+mgh_{1}=\frac{1}{2}mv_{2}^{2}+mgh_{2}}
$$

# Power

平均功率如下定義：

$$
\boxed{\bar{P}=\frac{W}{t}}
$$

而功率的單位為瓦特(W=J/s)。

我們還可以如下計算瞬時功率：

$$
P=\frac{dW}{dt}=\frac{F \cdot dx}{dt}=F \cdot v
$$

一度電的定義為，1 kwh = $1 \times 10^{3} W \times 3600 s=3.6\times 10^{6} J$。

# Tips

- 1hp = 746W

# 威儀指定習題

1. A boy pulls a 15kg sled at constant speed a distance of 30m along rough level snow that has a coefficient of friction of 0.1. How much work did he do?

Ans:
441J

2. A bead having an initial speed at point A(h=0.7m) of $2m/s^{2}$ slides down a frictionless wire. What are its speeds at point B(h=0m) and C(h=0.3m)?

Ans:
$v_{b}\approx 4.21 m/s^{2},v_{c}\approx 3.44m/s^{2}$ 

3. A pendulum consists of a mass at the end of a string 1.5m long. The mass is pulled sideways until the string makes an angle of $30^{\circ}$ with the vertical; then it is released. What is the speed of the mass as it passes through its lowest point?

$mg(1.5 - 1.5\cos 30^{\circ})=\frac{1}{2}mv^{2}\implies v\approx 1.98 m/s$ 
`~~~~^ 記得減 ^~~~~` 

4. A light rope passing over a frictionless pulley connects two blocks of mass $m_{1}=3kg,m_{2}=5kg$. (a) If the blocks are released from rest in the position $h_{m_{1}}=0m,h_{m_{2}}=6m$ , what will be the velocity of $m_{2}$ as it hits the ground? (b) What is final height reached by $m_{1}$?

Sol:
(a)
因為只受保守力做工，所以機械能守恆。
$m_{2}g(6)=m_{1}g(6)+\frac{1}{2}m_{1}v^{2}+\frac{1}{2}m_{2}v^{2}\implies v \approx 5.42 m/s$ 
不要忘記也要把 $m_{1}$ 的動能考慮進去喔！
還有，因為有繩子綁著，所以 $m_{1},m_{2}$ 的速度一樣喔！

(b)
當 $m_{2}$ 觸地後，$m_{1}$ 持有的動能繼續轉化為位能：
$\frac{1}{2}m_{1}v^{2}=m_{1}gh\implies h=1.5$ 
所以最終高度為 $1.5+6=7m$ 。

5. An 80kg man ascends a 4m high staircase in 12s. What is his horsepower?

Ans:
$\approx 0.35 hp$ (1hp = 746W)

6. A pump is needed to lift 100kg of water per minute from a well 30m deep. The water is ejected with a speed of $5m/s$. What must be the power output of the pump?

Sol:
這題的難點在於看不懂題目...
其實就是抽上去後水要以 5m/s 的速度繼續噴。
先算一秒要抽多少水：$\frac{100}{60}=\frac{5}{3}$ kg/s。
然後需要施加的能量等於增加的位能與動能：$E_{\text{in}}=\frac{5}{3}\times 30 \times g + \frac{1}{2} \times \frac{5}{3} \times 25 \approx 510.8J$ 。
又因為這是一秒所做的功，所以等於需要的功率。

# 重要例題

1. A mass $m_{1}=3kg$ resting on a long table is connected by a light string passing over frictionless pulley to a second mass $m_{2}=5kg$ hanging 2m above the floor. The coefficient of friction between the table and $m_{1}$ is 0.3. The blocks are released from rest. What is the velocity of $m_{2}$ as it hits the floor?

Sol:
此題必須使用 $W_{\text{net}}=\Delta K$ 解。因為同時涉及到保守(重力)與非保守力(摩擦力)作功。
$F_{\text{net}}=m_{2}g-f=4.1g$ 
$W_{\text{net}}=F_{\text{net}}\cdot 2=\Delta K\implies 4.1g \times 2=\frac{1}{2}v^{2}(m_{1}+m_{2})\implies v \approx 4.48m/s$ 。