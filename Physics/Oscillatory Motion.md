
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

帶回虎克定律，彈簧對木塊所施的力為：

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

