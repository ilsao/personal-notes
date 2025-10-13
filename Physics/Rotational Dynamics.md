# Moment of Inertia And Torque

首先，假設 $r$ 為力臂，我們給出力矩的定義：

$$
\mathbf{\tau}=\mathbf{r} \times \mathbf{F}
$$

如果只是表示力矩的大小，我們可以如下取得：

$$
\tau=rF\sin \theta=rma_{T}=mr^{2}\alpha=I\alpha
$$

所以，我們定義轉動慣量：

$$
\boxed{I=mr^{2}}
$$

對於很多質點組成的物體，如果所有質點與旋轉中心點的距離皆相同，我們有：

$$
\boxed{I=Mr^{2}}
$$

其中，$M$ 為所有質點的質量總和。

在此，我們需要注意區分三種加速度：

- rotational acceleration：$\alpha$
- tangential acceleration：$a_{T}=r\alpha$
- radial acceleration：$a_{R}=r\omega^{2}= \frac{v^{2}}{r}$

# Rotational Kinetic Energy

雖然等速圓周運動不作功，但是呢，非等速圓周運動是做功的喔！

$$
\boxed{W_{\theta}=\int_{\theta_{0}}^{\theta_{f}}\tau d\theta}
$$

proof:
首先，我們透過切線力可以得到：$dW=F_{T} \cdot ds\implies dW=F_{T}ds$ 。
又 $dW=F_{T}ds=Fr\sin \phi \ d\theta=\tau d\theta$。
我們對上式積分：$W=\int_{\theta_{0}}^{\theta_{f}}\tau d\theta$。

同樣，對旋轉的物體照樣可以套用功能定理。

$$
\boxed{W_{\theta}=(\Delta E_{k})_{\text{rot}}=\frac{1}{2}I\omega_{f}^{2}-\frac{1}{2}I\omega_{0}^{2}}
$$

其中，物體中所有質點相對位置皆保持不變上式才成立。

proof:
我們替換 $W_{\theta}=\int_{\theta_{0}}^{\theta_{f}}\tau d\theta=\int_{\theta_{0}}^{\theta_{f}}I\alpha d\theta=\int_{\theta_{0}}^{\theta_{f}}I \frac{d\omega}{dt}\omega dt=\int_{\omega_{0}}^{\omega_{f}}I\omega d\omega$。
如果物體中所有質點相對位置皆保持不變，我們可以提出 $I$：$W_{\theta}=I\int_{\omega_{0}}^{\omega_{f}}\omega d\omega=\frac{1}{2}I\omega_{f}^{2}-\frac{1}{2}I\omega_{0}^{2}$。

我們如下定義轉動動能：

$$
\boxed{E_{k}=\frac{1}{2}I\omega^{2}}
$$

proof:
$E_{k}=\frac{1}{2}mv_{T}^{2}=\frac{1}{2}mr^{2}\omega^{2}=\frac{1}{2}I\omega^{2}$

一個物體可以一邊移動一邊旋轉，所以：

$$
\boxed{(E_{k})_{\text{total}}=(E_{k})_{\text{trans}}+(E_{k})_{\text{rot}}=\frac{1}{2}mv^{2}+\frac{1}{2}I\omega^{2}}
$$

# Power

我們來寫下功率的公式：

$$
\text{Power}=\frac{dW}{dt}=\frac{\tau d\theta}{dt}=\boxed{\tau\omega
}
$$

# Angular Momentum

$$
\boxed{\tau=\frac{d}{dt}(\mathbf{r}\times m\mathbf{v})}
$$

proof:
我們從 $F=\frac{d}{dt}(mv)$ 開始下手。
$\tau=Fr=r\times \frac{d}{dt}(mv)$。
想要繼續證明，我們還需要證明 $r\times \frac{d}{dt}(mv)=\frac{d}{dt}(r\times mv)$。
展開即可： $\frac{d}{dt}(r \times mv)=\frac{dr}{dt}\times mv + r \times \frac{d}{dt}mv=v\times mv + r\times \frac{d}{dt}mv=r\times \frac{d}{dt}(mv)$。
所以，我們重新寫下公式：$\tau=\frac{d}{dt}(r\times mv)$。

那麼，我們可以找到轉動動量 $L$ ：

$$
L=r\times mv=rm v\sin \theta=rmv_{T}=mr^{2}\omega=\boxed{I\omega}
$$

而力矩也可以被重新寫成：

$$
\boxed{\tau=\frac{L}{dt}}
$$

# Conservation of Angular Momentum

$$
\boxed{(I\omega)_{0}=(I\omega)_{f}}
$$

proof:
因為動量守恆的條件為沒有外力作工，所以 $\implies \tau=\frac{dL}{dt}=0\implies\Delta\omega=0\implies{(I\omega)_{0}=(I\omega)_{f}}$。

# 威儀指定習題

1. A uniform wooden board of mass 20kg rests on two supports. A 30kg steel block is placed to the right of support A. How far to the right of A can the steel block be placed without tipping the board?

```
<---11---><-3-><---8--->
                   口
------------------------
               i
```

2. A wheel of moment of inertia $60kg-m^2$ and radius 1.5m is rotating about an axis through its center with an angular velocity $\omega=30$rev/s. A brake is applied producing a normal force of 450N agianst the rim. The coefficient of friction between the wheel and the brake is 0.5. (a) How long will it take for the wheel to stop? (b) Calculate the work done by friction and show that this is equal to the change in the kinetic energy of the wheel.

Sol:
需要注意，(b) 中，位移的對位是 $\theta$ ！所以想要算真正的路徑長，需要用 $r\theta$ 求。

3. The torque of the motor is turned at right angles to the wheels by the differential gear. Assume that in low gear the angular velocity of the rear wheels is 0.1 that of the motor. If the motor has 200hp and is turning over at a rate of 1400rev/min, how much torque is delivered to the rear wheels?

Sol:
需要注意的是，這題英文會讀不懂。
首先將 hp 轉 watt：$200hp=200\times 746 W=149200W$。
然後求 $1400rev/min= \frac{140\pi}{3} rad$。
利用公式：$W=\tau\omega\implies{1}49200=\tau \cdot \frac{140\pi}{3}\implies \tau \approx 1018$。
因為傳動過去的功率沒有改變，但是 $\omega$ 變成 0.1 倍，那麼相對應的 $\tau$ 應該變為 10 倍。
所以答案：$\tau'\approx 10180$N-m。

4. A children's merry-go-round of radius 4m and mass 100kg has an 80kg man standing at the rim. The merry-go-round coasts on a frictionless bearing at 0.2rev/sec. The man walks inward 2m toward the center. That is the new rotational speed of the merry-go-round? What is the source of this energy? (The moment of inertia of a solid disk is $I=\frac{1}{2}mr^{2}$).

Sol:
這題有個要注意的地方，旋轉木馬的 $I$ 我們要用 $\frac{1}{2}mr^{2}$ 算，但是人的要當成質點算。
還有，能量的來源是人克服慣性向前施的功，轉變為旋轉的動能。
