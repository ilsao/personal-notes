
# Rotational Motion

徑的定義為($s$ 為對應的圓弧)：

$$
\theta=\frac{s}{r}
$$

令 $a,b$ 為圓上相異兩點，則定義切線速度為：

$$
\boxed{v_{T}=\frac{dx}{dt}}
$$

但是，切線速度在同一個旋轉物體的不同半徑上不同。所以我們最好用一個在任意半徑上都會保持同樣的量來代表。

這裡就引入了角速度的概念：

$$
\boxed{\omega= \frac{d \theta}{d t}}
$$

因為當 $t\to 0$ 時，$s\to x$ 所以我們可以將角速度與切線速度關聯起來：

$$
\omega=\frac{d\theta}{dt}=\frac{ds}{dt} \cdot \frac{1}{r}=\frac{dx}{dt}\cdot \frac{1}{r}=\frac{v}{r}\implies \boxed{v_{T}=r\omega}
$$

我們還可以推導切線加速度：

$$
a_{T}= \frac{dv}{dt}
$$

而我們在圓周運動中還有角加速度：

$$
\boxed{\alpha=\frac{d\omega}{dt}}
$$

同樣，我們關聯角加速度與切線加速度：

$$
a_{T}=\frac{dv}{dt}=r \frac{d\omega}{dt}=r\alpha\implies \boxed{a_{T}=r\alpha}
$$

# Equations of Rotational Motion

我們有：

$$
\begin{align}
 & \theta=\bar{\omega}t \\
 & \bar{\omega}= \frac{\omega_{0}+\omega_{f}}{2}
\end{align}
$$

我們還有：

$$
\boxed{\omega=\omega_{0}+\alpha t}
$$

proof:
$\alpha=\frac{d\omega}{dt}\implies \alpha dt=d\omega$ 
$\alpha \int_{0}^{t}dt=\int_{\omega_{0}}^{\omega}dw\implies\alpha t=\omega-\omega_{0}\implies\omega=\omega_{0}+\alpha t$ 

以及：

$$
\boxed{\theta-\theta_{0}=\omega_{0}t+\frac{1}{2}\alpha t^{2}}
$$

proof:
由於 $\omega=\frac{d\theta}{dt}\implies \omega dt=d\theta$ 
利用 $\omega=\omega_{0}+\alpha t$ 替代，$\int_{0}^{t}(\omega_{0}+\alpha t)dt=\int_{\theta_{0}}^{\theta}d\theta\implies\theta-\theta_{0}=\omega_{0}t+\frac{1}{2}\alpha t^{2}$ 。

最後，還有：

$$
\boxed{\omega^{2}-\omega_{0}^{2}=2\alpha(\theta-\theta_{0})}
$$

proof:
使用 chain rule：$\alpha=\frac{d\omega}{dt}=\frac{d\omega}{d\theta} \frac{d\theta}{dt}=\omega \frac{d\omega}{d\theta}\implies\alpha d\theta=\omega d\omega$。
$\int_{\theta_{0}}^{\theta}\alpha d\theta=\int_{\omega_{0}}^{\omega}\omega d\omega\implies\alpha(\theta-\theta_{0})=\frac{1}{2}(\omega^{2}-\omega_{0}^{2})\implies\omega^{2}-\omega_{0}^{2}=2\alpha(\theta-\theta_{0})$。

# Radial Acceleration (逕向加速度)

我們定義逕向加速度(造成旋轉速度改變)為：

$$
a_{R}=\lim_{ \Delta t \to 0 }  \frac{\Delta \mathbf{v}}{\Delta t}=\boxed{r\omega^{2}= \frac{v^{2}}{r}}
$$

proof:
我們將座標表達為三角函數：
$x=r\cos \theta=r\cos \ \omega t$ 
$y = r\sin \ \omega t$ 
那麼，我們可以找到切線速度：
$v_{x}=r \frac{d}{dt}\cos\omega t=-r\omega\sin\omega t$ 
$v_{y}=r \frac{d}{dt}\sin\omega t=r\omega\cos\omega t$ 
接著，就可以找到加速度：
$a_{x}=r\omega \frac{d}{dt}\sin\omega t=-r\omega^{2}\cos\omega t$ 
$a_{y}=r\omega \frac{d}{dt}\sin\omega t=r\omega^{2}\cos\omega t$ 
$\implies a=\sqrt{ a_{x}^{2}+a_{y}^{2}}=\pm r\omega^{2}$。
如果我們代換回去，那就可以得到另一個公式：$a= \frac{v^{2}}{r}$。

# Centripetal Force (向心力)

讓我們簡潔的寫下向心力公式叭~

$$
\boxed{\sum F_{R}=ma_{R}=m \frac{v_{T}^{2}}{r}}
$$

為了解題方便，我們可以自己定義指向圓心的力為正，指出圓心的力為負。

# Orbital Motion and Gravitation

來吧，讓我們寫出那個經典的萬有引力公式：

$$
F= \frac{GMm}{r^{2}}
$$

其中，$G$ 代表萬有引力常數 $6.67 \times 10^{-11} Nm^{2}/kg^{2}$。

對於在地表附近的物體，我們如下列式：

$$
mg= \frac{GMm}{r_{e}^{2}}
$$

對於繞著地球轉的星體，我們如下列式：

$$
m \frac{v^{2}}{r}= \frac{GMm}{r^{2}_{e}}
$$

# 威儀指定習題

1. Assume that the orbit of the earth around the sun is circular and that the period of rotation is 365 days. The earth-sun distance is $1.5\times 10^{11}$m. What is the centripetal acceleration of the earth resulting from its motion around the sun?

Sol:
這裡就靠我們高中使用的公式出場了！
給定週期和距離怎麼求向心加速度 $a=\frac{v^{2}}{r}$ 呢？
先嘗試表達 $v$，$v=r\omega=r \frac{2\pi}{T}\implies v^{2}=\frac{4\pi^{2}r^{2}}{T^{2}}$。
所以，加速度就等於：$a= \frac{4\pi^{2}r^{}}{T^{2}}= \frac{4\pi^{2}(1.5\times 10^{11})}{365\times 24 \times 60 \times 60}\approx 5.9\times 10^{-3}$。

2. A 2kg block is rotating on a frictionless table with angular velocity $\omega=2$rev/sec. The block is connected to a 15kg block by means of a string of total length 2m that passes through a small hole in the table. How far below the tabletop does the 15kg block hang?

Sol:
首先，注意角速度的單位，想要帶進 $v=r\omega$，則單位必須為徑。
然後用吊在下面的物體的重量當作向心加速度即可。

3. A bug sits on a phonograph record 0.18m from the center. if the record turns at 33rev/min, what is the radial acceleration of the bug? If it has a mass of 0.5g, what is the centripetal force acting on it? 

4. (a) What is the centripetal acceleration of a person standing on the earth at a point of latitude $45^\circ$? (b) What is the magnitude and the direction of the force exerted by the ground on that person? Express your answer in terms of the weight $mg$ of the person. The radius of the earth is $6.37\times 10^{6}m$. 

Sol:
這題很難。。。
(a) 
我們知道地球的角速度為：$\omega= \frac{2\pi}{24\times 60\times 60}$。
然後，因為人站在北緯 $45^{\circ}$，所以長軸應該為 $r\cos45^{\circ}$(地球半徑映射到北緯)。
直接帶向心加速度公式：$a=r\cos 45^{\circ} \cdot (\omega)^{2}\approx 2.38\times 10^{-2} m/s^{2}$。

(b)
這個需要有很聰明的腦袋瓜才想得出來。
我們需要向心力映射到與 mg 還有 N 相同的線上：$mg-N=\cos 45^{\circ}ma\implies N=m(g-\cos45^{\circ}a)$。

5. The length of the string of a conical pendulum is 0.6m. The mass of the bob is 1.2kg. The angular velocity of the bob (which moves in a circle in the horizontal plane) is such that the angle between the string and the vertical is $30^{\circ}$ and is constant. (a) What is the tension in the string? (b) What is the angular velocity of the bob?

Sol:
(a)
這個用第三章的方法，$T\cos 30^{\circ}=mg$ 即可。

(b)
這個也還行，注意要求的是 $\omega$ 不是 $v$ 就好。

# 重要例題

1. A pulley of radius $r_{p}=8$cm is connected to the shaft of an electric motor. A belt couples the pulley to a wheel of radius $r_{w}=24$cm. The motor shaft begins to rotate with an angular acceleration $\alpha=25$$rad/sec^2$. (a) What is the angular velocity of the wheel after 3 sec? (b) Through what angle has the wheel rotated when the centripetal acceleration of a point on the rim of the wheel is 100g?

Sol:
(a)
先算出 $\omega_{p}=25 \times 3=75$。
因為用帶子連在一起，所以切線速度相同：$r_{p}\omega_{p}=r_{w}\omega_{w}\implies \omega_{w}=\frac{r_{p}}{r_{w}}\omega_{p}=25$ rad/s

(b)
由上，我們可以得到輪子的角加速度：$\alpha_{w}=\frac{25}{3}$。
利用 $r\omega^{2}=a_{R}$ 列式：$\omega^{2}=\frac{100g}{24}$。
利用位移公式：$\omega^{2}_{f}-\omega_{0}^{2}=2\alpha_{w}\theta\implies \theta=245$ rad