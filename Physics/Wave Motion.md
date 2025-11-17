
# Wavelength, Velocity, Frequency, and Amplitude

其他定義應該都還好，在此我們只提及波速的定義(一秒可以走幾個波長的長度)：

$$
v=\frac{\lambda}{T}=\lambda \nu
$$

以下是定義常用的符號：

波長：$\lambda$ 

波速：$v$ 

頻率：$\nu$ 

週期：$T$ 

振幅：$A$ 

# Traveling Wave in a String

理解這段之前，我們要先知道**時間相位(temporal phase)** 與**空間相位(spatial phase)**。

時間相位：對於固定的 $x$，波的運動根據 $t$ 如何變化，也就是 $\omega t+\phi_{1}$。

空間相位：對於固定的 $t$，波的運動根據 $x$ 如何變化，也就是 $-kx+\phi_{2}$。

當一個波要到達 $x$，需要經過 $t_{0}=\frac{x}{v}$ 的時間。那麼在 $x$ 的時間相位就是：
$\omega(t-t_{0})=\omega t-\frac{\omega}{v}x=\omega t-kx$。(因為在原點時的相位為 $\omega t$)

當我們想表達一個橫波時，需要兩個變量，$x$ 與 $t$。

可以表達成：$y=f(x,t)$。

對於一個正在做簡諧運動的理想彈簧，如果我們在紙上紀錄其運動軌跡，並沿著與擺動垂直的方向向 $+x$ 拉動紙張(波向 $+x$ 移動)，我們可以將此圖形表示成：

$$
y(x,t)=A\sin\left( \omega t - \frac{\omega}{v}x +\phi \right)=A\sin(\omega t-kx+\phi)\quad\text{其中 }\boxed{k=\frac{\omega}{v}}
$$

我們可以考慮一下 $k$。其實，$\boxed{k=\frac{2\pi}{\lambda}}$ 化簡而成。所以，每當 $x$ 位移 $\lambda$ 整個 $\sin$ 就會因為 $-2\pi$ 位移回原點。

考慮一下兩個特殊情況(第二種符合威儀PPT)：

$$
\begin{align}
 & y(x,t)=A\sin(\omega t-kx)\quad\text{if }\phi=0 \\
 & y(x,t)=A\sin(kx-\omega t)\quad\text{if }\phi=\pi
\end{align}
$$

若波向 $-x$ 移動，我們的函數會變成：

$$
y(x,t)=A\sin(kx+\omega t+\phi)
$$

通過固定時間，我們可以發現：

$$
\boxed{\lambda=\frac{2\pi}{k}}
$$

通過固定 $x$，我們可以發現：

$$
\boxed{\nu=\frac{\omega}{2\pi}}
$$

最後，我們還有：

$$
\lambda \nu=\frac{2\pi}{k} \frac{\omega}{2\pi}=\frac{\omega}{k}=v
$$

# Energy Transfer of a Wave

波動會造成能量的轉移，但與那種物體撞過去造成的能量轉移有些許不同：
1. 相對粒子運動來說，波會造成能量轉移但不會造成物質的移動。
2. 粒子運動所攜帶的能量集中在運動中的粒子上(局部化)，但波造成的能量卻分佈在整個波動區域。

我們可以如下計算波的功率：

$$
P=(\text{energy per wavelength})\times \nu
$$

因為波中某個點的能量正比於其振幅的平方，所以波上每個點的能量都相同。

為了計算某點的能量，我們需要求得該點的速度。由於 $x$ 仍在變動，我們對 $y$ 對時間偏微分(將 $x$ 視為常數)。

$$
v_{y}= \frac{\partial y}{\partial t}=\frac{\partial}{\partial t}A\sin(kx-\omega t)=-A\omega \cos(kx-\omega t)
$$
我們可以得到 $\boxed{v_{\text{max}}=A\omega}$。

因為動能守恆，當 $v_{\text{max}}$ 發生時，總能量等於 $\frac{1}{2}mv_{max}^{2}$。

計算一個粒子的動能：

$$
E(\text{for particle})=\frac{1}{2}\Delta m\omega^{2}A^{2}
$$

定義 $\mu$ 為介質單位長度質量，則一個波長的質量為：$\mu \lambda$。

所以：

$$
\text{Energy per wavelength}=\frac{1}{2}\mu \lambda\omega^{2}A^{2}
$$

代回可得功率：

$$
P=\frac{1}{2}\mu \lambda \nu\omega^{2}A^{2}=2\pi^{2}\mu v\nu^{2}A^{2} \propto A^{2}v
$$

最右邊那個等式利用了：$v=\lambda \nu$ 與 $\omega=2\pi \nu$。

最後我們定義**光強度(Intensity)**：

$$
I=\frac{P}{A}
$$

其中，$P$ 是功率，$A$ 是接收面積。光強度的單位為：$\text{W/m}^{2}$。

# 威儀指定習題

1. The speed of sound in air is about $330$ $\text{m/sec}$, whereas the velocity of light is $3 \times 10^{8} \text{m/sec}$. If you see a flash of lightning and count 8 sec before you hear the thunder, how far away was the lightning?

Sol:
因為光速太快，可忽略。
距離 $\approx330\times8=2640\text{ m}$ 

2. The equation of a transverse wave traveling along a very long string is given by $y=6\sin(0.02\pi x+4\pi t)$ where _$x$_ and $y$ are_expressed in centimeters and $t$ in seconds. Find (a) the amplitude, (b) the wavelength, (c) the frequency, (d) the speed of propagation, (e) the direction of propagation of the wave, and (f) the maximum transverse speed of a particle in the string.

Sol:
(a)
6cm
(b)
觀察式子可知 $k=0.02\pi$，$\lambda= \frac{2\pi}{k}=100\text{ cm}$ 
(c)
觀察可知 $\omega=4\pi$，$\nu=\frac{\omega}{2\pi}=2\text{ Hz}$ 
(d)
$v=\lambda \nu=200\text{ cm/sec}$ 
(e)
向 $-x$ 方向傳播
(f)
注意分別此處求的是 particle 的最大速度。
對 $t$ 求偏微分：$\frac{\partial y}{\partial t}=A\omega \cos(kx+\omega t)\implies v_{\text{max}}=A\omega=6\times4\pi=24\pi\text{ cm/sec}$。

3. Write the equation for a wave traveling in the negative direction along the $x$ axis and having an amplitude of $0.010\text{ m}$, a frequency $550\text{ Hz}$, and a speed $330\text{ m/sec}$. 

Sol:
$v=\lambda \nu\implies \lambda=0.6\text{ m}$ 
$k=\frac{2\pi}{\lambda}=\frac{\omega}{v}=\frac{10\pi}{3}\implies\omega=1100\pi$ 
$\implies y=0.010\sin\left( \frac{10\pi}{3}x +1100\pi t\right)$ 

4. A laser produces light pulses of energy $5\text{ J}$ and duration $2 \times 10^{-9}\text{ sec}$. The width of the beam is $1\text{ mm}^{2}$. What is the intensity of the laser light?

Sol:
注意：$1\text{ mm}=10^{-1}\text{ cm}=10^{-3}\text{m}\implies 1\text{ mm}^{2}=10^{-6}\text{m}^{2}$ 
那麼：$I=\frac{P}{A}=\frac{\frac{5}{2\times10^{-9}}}{10^{-6}}=2.5\times 10^{15}\text{ W/m}^{2}$ 

5. A sinusoidal traveling wave of amplitude $2$ $\text{cm}$ and wavelength $50$ $\text{cm}$ moves along a string with velocity $v=6\text{ m/sec}$. (a) What is the maximum transverse velocity of the particles in the string? (b) What is the maximum transverse acceleration of the particles in the string?

Sol:
(a)
(先轉單位到 $m$)
$k=\frac{2\pi}{\lambda}=4\pi$ 
$\omega=kv=24\pi$ 
假設波向 $-x$ 傳播，則：$y=0.02\sin(4\pi x+24\pi t)$。
偏微分即可：$v_{\text{max}}=A\omega=0.02\times24\pi=0.48\pi\text{ m/s}$ 
(b)
$a_{\text{max}}=A\omega^{2}=0.04\times (24\pi)^{2}=11.52\pi^{2}\text{ m/s}^{2}$ 


# 威儀考古

1. At $t=0$, a pulse is described by $y(x)= \frac{A}{B+x^{2}}$. Pulse moves in $+x$ direction at $3\text{ m/s}$. What is the wave function at t?

Sol:
$y(x,t)= \frac{A}{B+(x-vt)^{2}}=\frac{A}{B+(x-3t)^{2}}$ 

2. 指定習題 3