
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
y(x,t)=A\sin\left( \omega t - \frac{\omega}{v}x +\phi \right)=A\sin(\omega t-kx+\phi)\quad\text{其中 }k=\frac{\omega}{v}
$$

我們可以考慮一下 $k$。其實，$k=\frac{2\pi}{\lambda}$ 化簡而成。所以，每當 $x$ 位移 $\lambda$ 整個 $\sin$ 就會因為 $-2\pi$ 位移回原點。

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
\lambda=\frac{2\pi}{k}
$$

通過固定 $x$，我們可以發現：

$$
\nu=\frac{\omega}{2\pi}
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

