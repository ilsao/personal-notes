
# Frequency and Period

頻率常記為 $\nu$，也就是一秒多少次事件。單位為 $\text{Hz}$。

週期常記為 $T$，也就是事件多少秒一次。單位為 $\text{sec}$。

$$
\nu=\frac{1}{T}
$$

若考慮一個逆時針運動等速的質點，則該點座標為：

$$
\begin{align}
 & x=r\cos \theta=r\cos\omega t=r\cos 2\pi \nu t \\
 & y=r\sin \theta=r\sin\omega t=r\sin 2\pi \nu t
\end{align}
$$

# Amplitude and Phase Angle

振幅：最高點距離平衡點的距離。

我們可以用以下公式描述簡諧運動：

$$
\boxed{x=A\sin(\theta+\phi)=A\sin(\omega t+\phi)}
$$

其中，$\phi$ 稱為**相位角(phase angle)**。

# Oscillation of a Spring

由於我們有 $x=A\sin(\omega t+\phi)$，我們可以得到：

$$
\boxed{\begin{align}
 & v=\frac{dx}{dt}=A\omega \cos(\omega t+\phi) \\
 & a = \frac{d^{2}x}{dt^{2}}=-A\omega^{2}\sin(\omega t+\phi)
\end{align}}
$$

代回虎克定律，彈簧對木塊所施的力為：

$$
\begin{align}
 & F=-kx=ma \\
 & F=-kA\sin(\omega t+\phi)=-mA\omega^{2}\sin(\omega t+\phi) \\
 & \implies \boxed{k=m\omega^{2}} \\
 & \implies \boxed{\omega=\sqrt{ \frac{k}{m} }} \\
 & \implies \boxed{\nu=\frac{1}{2\pi}\sqrt{ \frac{k}{m} }} \\
 & \implies \boxed{T=2\pi \sqrt{ \frac{m}{k} }}
\end{align}
$$

如果我們想要解出 $A$ 與 $\phi$，我們需要指定一些邊界條件。

例如，在 $t=0$ 時 $x=x_{0}$，$v_{x}=0$。

可以得到 $x_{0}=A\sin(\phi)$ 且 $v_{x}=0=A\omega \cos(\phi)\implies \begin{cases}\phi=\frac{\pi}{2}\text{ 或 } \frac{3\pi}{2} \\ x_{0}=A\end{cases}$。

我們還有：

$$\boxed{v_{\text{max}}=A\omega}$$

$$\boxed{a_{\text{max}}=A\omega^{2}}$$

# Energy of Oscillation

當一個物體從其平衡位置位移到距離平衡位置 $x$ 的地方，則將該點能量記為 $E_{p}$，且該能量由將該物體移動到該位置的力作的功產生。

所以，當該物體處於偏離平衡位置 $x$ 時，該點的位能記為：

$$
\boxed{E_{p}\text{(spring)}=\frac{1}{2}kx^{2}}
$$

當省略摩擦力時，根據能量守恆，我們有：

$$
\boxed{E_{\text{total}}=E_{k}+E_{p}=\frac{1}{2}mv^{2}+\frac{1}{2}kx^{2}}
$$

若我們想求某點的加速度，可以使用：

$$
\begin{align}
 & F=ma \\
- & kx=ma \\
\implies  & a= -\frac{kx}{m}
\end{align}
$$

# 威儀指定習題

1. When a mass of 0.2 kg is suspended from a spring, it stretches 0.04 m (平衡位置). The mass is pulled down an additional distance 0.1 m (被從平衡位置再拉出來，也就是振幅) from its equilibrium position and released. (a) What is the spring constant? (b) What is the period of oscillation?(c) What is the frequency of oscillation? (d) What will be the maximum velocity?

Sol:
(a)
$0.2g=k\cdot0.04\implies k=5g\approx 4.9\text{ N/m}$ 
(b)
$T=\frac{2\pi}{\omega}=2\pi \sqrt{ \frac{m}{k} }=\frac{2\pi}{5\sqrt{ g }}\approx0.4\text{ sec}$ 
(c)
$\nu=\frac{1}{T}\approx2.5\text{ Hz}$ 
(d)
$v_{\text{max}}=A\omega=2\pi \nu A=2\pi \cdot 2.5\cdot 0.1\approx 1.57\text{ m/sec}$ 
$\frac{1}{2}kx_{\text{max}}^{2}=\frac{1}{2}mv_{\text{max}}^{2}\implies v_{max}=\frac{\sqrt{ g }}{2}\approx1.57\text{ m/sec}$ 

2. Two springs with force constants $k_{1}$ = 100 N/m and $k_{2}$ = 200 N/m are connected to opposite ends of a block of mass 3 kg (see Fig. 10-8). (a) If the block is displaced 0.1 m to the right, what is the net force exerted by the springs on the block? The block is released from that position. (b) What are the frequency and the period of the motion? (c) What is the amplitude of the motion? (d) Find an expression for the position of the particle as a function of time?

![[Pasted image 20251121202029.png]]

Sol:
這題因為木塊移動時，兩根彈簧都被拉伸/壓縮相同的位移量，所以可以視為一根係數為 $k=k_{1}+k_{2}$ 的彈簧。
但是如果是兩個彈簧連在一起，那麼兩個彈簧會被分別拉伸 $x_{1}$ 與 $x_{2}$。
其中 $x_{1}=\frac{F}{k_{1}}$，$x_{2}=\frac{F}{k_{2}}$，且 $x=x_{1}+x_{2}=\frac{F}{k_{1}}+\frac{F}{k_{2}}=F\left( \frac{1}{k_{1}}+\frac{1}{k_{2}} \right)\implies \frac{1}{k_{\text{eq}}}=\frac{1}{k_{1}}+\frac{1}{k_{2}}$ 
(a)
$F=(k_{1}+k_{2})x=30\text{ N}$ 
(b)
$k=k_{1}+k_{2}=300$ 
$T=2\pi \sqrt{ \frac{m}{k} }=0.2\pi$ 
$\nu=\frac{1}{T}=\frac{5}{\pi}$ 
(c)
amplitude = 0.1
(d)
$x(t)=0.1\cos\left( \sqrt{ \frac{300}{3} }t \right)=0.1\cos10t$ 

3. A wooden block of mass 0.8 kg rests on a frictionless table connected to a spring _(k_ = 200 N/m) as shown in Fig. 10-10. A 20-g bullet moving with a velocity _v_ = 500 m/sec is shot into the block and remains embedded in it. What is the amplitude of the ensuing oscillatory motion?

![[Pasted image 20251121203452.png]]

Sol:
$0.02\times500=(0.82)v$ 
$\frac{1}{2}kx^{2}=\frac{1}{2}mv^{2}\implies x\approx0.78\text{ m}$ 

4. A block of mass $m_{1}$ = 3 kg rests on a frictionless surface connected to a spring _(k_ = 150 _N/m)._ A second block of mass $m_{2}$ = 1 kg is launched toward $m_{1}$ with a velocity of 4 m/sec (see Fig. 10-11). After the collision, $m_{2}$ bounces back in the opposite direction with a velocity of 1 m/sec. (a) How much will the spring be compressed? (b) What fraction (部分) of the energy is lost in the collision?

Sol:
(a)
$m_{2}\cdot 4=(m_{1}v)+(-m_{2})\implies v=\frac{5}{3}$ 
$\frac{1}{2}m_{1}v^{2}=\frac{1}{2}kx^{2}\implies x\approx 0.24\text{ m}$ 
(b)
注意，此處 fraction of the energy is lost 指的是：$\frac{\text{lost}}{\text{all}}$ 
也就是：
$\frac{\frac{1}{2}m_{2}\cdot 4^{2}-\frac{1}{2}m_{1}\cdot\left( \frac{5}{3} \right)^{2}-\frac{1}{2}m_{2}\cdot 1^{2}}{\frac{1}{2}m_{2}\cdot 4^{2}}\approx0.42$ 