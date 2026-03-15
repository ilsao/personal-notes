# De Broglie's Hypothesis And Its Experimental Verification

德布羅意認為，光具有二象性，那麼此性質應該適用於所有粒子。

於是提出：**導波(pilot wave)** 即**物質波(matter wave)** 的概念。其波長與頻率為：

$$
\begin{align}
 & \lambda=\frac{h}{p} \\
 & \nu=\frac{E}{h}
\end{align}
$$

為了證明物質波，我們嘗試使粒子束表現出波的性質。但設計此實現會遇到問題，波長 $\lambda=\frac{h}{p}$，通常因為 $p$ 過大導致 $\lambda$ 過短，難以找到狹縫使得此波展現繞射現象。

因為 $h$ 不能動，只能藉由減輕質量縮小 $p$。顯然，選擇電子當作實驗粒子是個好選項。

![[Pasted image 20260313234758.png]]

1. 電子經由加熱燈絲產生
2. 經過電場 $V$ 加速
3. 通過陽極小孔，形成電子束
4. 撞擊涅晶體並用偵測器偵測電子數量

![[Pasted image 20260313235046.png]]

當波滿足條件：$n\lambda=2d\sin \theta$ 時，就會產生繞射現象。因為我們可以通過 $\lambda=\frac{h}{p}$ 與 $E_{k}=eV$ 來調整電子束的波長，現在我們需要一個參照物來得知 $\theta$。

我們選取 X 光，因為電磁波被證明過為波。

已知：$d=0.91\times 10^{-10}\text{ m}$，X 光波長 $\lambda=1.65\times 10^{-10}\text{ m}$，所以 $\sin \theta= \frac{\lambda}{2d}\implies \theta \approx 65^{\circ}$。

由於 $2\theta+\phi=180^{\circ}$，所以 $\phi=50^{\circ}$。於是，我們固定 $\phi=50^{\circ}$ 並放置偵測器。

改變電壓 $V$，測量散射強度如圖：

![[Pasted image 20260314000344.png]]

可見在 $V=54\text{ V}$ 時，具有最大值。此時電子束的理論波長為：

$$
\lambda=\frac{h}{p}=\frac{h}{\sqrt{ 2mE_{k} }}=\frac{h}{\sqrt{ 2meV }}\approx 1.67\times 10^{-19}\text{ m}
$$

與 X 光波長非常相似。

於是此實驗成功證明物質粒子具有波動性。

# Nature of The Wave

我們使用**強度**連接波與粒子兩種理論，因為強度被定義為單位面積、單位時間通過的能量，在兩種模型中都有定義。

古典物理認為：

$$
I\propto(\text{amplitude})^{2}
$$

即，增加振幅可以增加強度。

在光子模型中，強度為：

$$
I=cN(h\nu)
$$

其中 $c$ 為光速，$N$ 為單位體積內的光子數量，$h\nu$ 為每個光子所攜帶的能量。

即，增加光子數量可以增加強度。

那麼：

$$
N\propto(\text{amplitude})^{2}
$$

當我們討論光子密度 $N$ 時，不應將其視為精確數值。

$N$ 實際上會有波動：
- 每秒到達的光子數不固定，但是總體平均下來會是 $N$。
- 無法預測下一顆光子會落在哪裡，但最終所有區域收到的光子平均後會相同。

這種隨機性來自於光子的發射過程。激發態的半衰期是 $10^{-8}\text{ s}$，有一半的激發原子會在 $10^{-8}\text{ s}$ 內衰變，但我們無法預測某個原子會在 $10^{-8}\text{ s}$ 前還是後衰變。

因為有隨機性，所以我們不能確定在某區域是否可以找到光子，我們只能談論光子出現在該區域內的機率。

因為在某區域內找到光子的機率會正比於光子密度 $N$，那麼也會正比於波函數的振幅平方：

$$
P\propto N\propto(\text{amplitude})^{2}
$$

那麼，現在我們知道所謂物質波，就是一種描述粒子機率密度的函數。我們將其稱為**波函數(wave function)**：

$$
\psi(r,t)
$$

若我們想求得，在時間 $t$ 時，粒子出現在 $r$ 附近小體積 $dV$ 的機率，可以如下計算：

$$
P(r,t)dV=|\psi|^{2}dV
$$

注意到粒子在空間中出現的機率和為 $1$，所以：

$$
\int_{-\infty}^{\infty}|\psi|^{2}dV=1
$$

![[Pasted image 20260314130442.png]]

# The Uncertainty Principle

古典物理有時雖然也會使用機率函數描述系統的行為，但那是因為系統中包含大量粒子難以單個求解。而在量子力學中，就算只有單個粒子，我們也必須使用機率函數描述系統行為。

古典物理認為，只要給定初始條件，通過計算牛頓運動定律，就能預測粒子在任意時刻的位置。此即**決定論(determinisim)**。

在量子力學中，Werner Heisenberg 提出了**不確定性原則(uncertainty principle)**。我們無法同時準確的測量粒子的位置分量與對應的動量分量。即：

$$
\Delta p_{x}\Delta x\geq \hbar
$$

其中 $\Delta$ 代表測量的不確定度。

> [!note]
> 不確定性與測量儀器好壞無關，就算是理想儀器測量時也必定引入不確定性。
> 不確定性原則不代表無法準確測量位置或動量，只是說無法**同時**準確測量。

這種不確定性在宏觀物體上很難展現。例如：我們想預測月球繞地球的運動。已知月球質量為 $m=6\times 10^{22}\text{ kg}$，平均軌道速度 $v=10^{3}\text{ m/s}$。若我們可以測量月球位置不確定度為 $\Delta x=10^{-6}\text{ m}$，則根據不確定性原則 $\Delta p_{x}\geq \frac{\hbar}{\Delta x}\approx10^{-28}\text{kg m/s}\implies\Delta v_{x}\approx 10^{-50}\text{ m/s}$ 幾乎可不計。

但若縮小到微觀尺度上，考慮電子繞氫原子。假設我們放棄對電子位置的精確了解 $\Delta x\approx 10^{-10}\text{ m}$，即電子可能出現在原子任意區域。則動量不確定度為 $\Delta p_{x}\geq 10^{-24}\text{ kg m/s}$。我們知道電子動量 $E_{k}=13.6\text{ eV}\approx 2.18\times 10^{-18}\text{ J}$，則 $p=\sqrt{ 2mE_{k} }\approx2\times 10^{-24}\text{ kg m/s}$。那麼，$\frac{\Delta p_{x}}{p}=0.5$，有 $50\%$ 不確定性。

因此，我們必須由位置機率與動量機率來描述粒子行為。

# Physical Origin of The Uncertainty Principle

這裡我們嘗試用古典物理解釋不確定性原則，主要思想是測量過程本身就會引入不確定性。

考慮使用顯微鏡觀察電子，為了看見電子，我們必須讓光照射在電子上，並觀察電子反射回的光子。

![[Pasted image 20260314135118.png]]

我們希望光子以 $-\phi\leq \theta\leq \phi$ 進入物鏡。所以，光子的 $x$ 動量分量介於 $-p \sin \phi\leq p_{x}\leq p \sin \phi$。因此光子的不確定度為：

$$
\Delta p_{x}(\text{photon})=2p_{\text{photon}}\sin \phi
$$

為了讓光子獲得動量，電子會得到方向相反大小相同的動量，所以電子的不確定度為：

$$
\Delta p_{x}(\text{electron})=2p_{\text{electron}}\sin \phi=\frac{2h}{\lambda}\sin \phi
$$

所以，在定位電子的過程中，自然地引入了不確定性。

我們有兩種方法可以減少動量不確定性：
- 用波長更長的光子
- 減小 $\phi$ 

可這兩種方法都會增加位置的不確定性。

# Matter Wave And The Uncertainty Principle

這邊我們使用物質波的概念推倒不確定性原則。

我們使用一種常見的波開始推導：

$$
\psi(x,t)=A\sin(kx-\omega t)
$$

此波有以下性質：
- 振幅 $A$ 在所有 $x$ 與 $t$ 都相同
- 有明確的波長 $\lambda=\frac{2\pi}{k}$ 
- 有明確的頻率 $\nu=\frac{\omega}{2\pi}$ 
- 波向 $+x$ 方向傳播，速度為 $\lambda \nu=\frac{\omega}{k}$ 

只要一個波有確定的動量與能量，就滿足德布羅意條件。即具有明確的 $\lambda$ 與 $\nu$。

由於波的振幅在所有 $x$ 都相同，所以我們無法確定粒子會出現在哪。這就是：

$$
\Delta x=\infty
$$

這其實符合不確定性原則，因為具有確定的 $\lambda$ 即具有確定的 $p$。根據 $\Delta p_{x}\Delta x\geq \hbar$，當 $\Delta p_{x}=0$ 時必有 $\Delta x=\infty$。

因此，這種波雖然可以描述確定動量與能量的粒子，但粒子卻完全無法定位。

讓我們嘗試計算此波的波速：

$$
\begin{align}
v & =\lambda\nu \\
 & =\frac{h}{p} \frac{E}{h} \\
 & =\frac{E}{p} \\
 & = \frac{\frac{1}{2}mv^{2}}{mv} \\
 & =\frac{1}{2}v_{\text{particle}}
\end{align}
$$

因此，波的速度是粒子速度的一半。在此例中，由於波在整個空間都有振幅，所以波追不上粒子不會對物理意義造成影響。但若粒子是局部性的，此情況就不能接受。

要描述局域粒子，我們需要一種波，其振幅只在空間中某區域不為零，即**波包(wave packet)**。粒子會出現在波包振幅不為零處，粒子定位越精準，波包就必須越窄。

數學上，波包由無限多個正弦波疊加而成。每個波的權重由振幅 $A$ 控制，因此振幅變為一個函數：

$$
A(\lambda,\nu)
$$

因為疊加了無限個波，所以我們用積分表示：

$$
\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}A(k,\omega)\sin(kx-\omega t) \ dk \ d\omega
$$

對於每個 $k$ 與 $\omega$，$A(k,\omega)$ 可能都有不同的值。所以 $A(k,\omega)$ 實際決定了每種波長混合了多少比例。

![[Pasted image 20260314142702.png|389]]

圖左為 $A(k)$ 混合比例，圖右為生成的波包。可觀察出混合的 $k$ 範圍越大，形成的波包就越窄。

這從數學角度說明了不確定性原則：
- 當 $k$ 範圍較小時，波長、動量較為確定，但由於波包較寬，位置較不確定。
- 當 $k$ 範圍較大時，波長、動量較不確定，但由於波包較窄，位置較為確定。

# Velocity of The Wave Packet: Group Velocity

因為粒子會出現在波包範圍，理應波包移動時粒子跟隨移動。

我們利用簡化的波包研究此現象。疊加兩行進波：

$$
\begin{align}
 & \psi_{1}=A\sin(kx-\omega t) \\
 & \psi_{2}=A\sin[(k+\Delta k)x-(\omega+\Delta\omega)t]
\end{align}
$$

其中 $\Delta k\ll k$，$\Delta \omega\ll\omega$。

利用三角恆等式，我們有：

$$
\psi(x,t)=\psi_{1}+\psi_{2}=2A\cos\left(  \frac{\Delta kx-\Delta\omega t}{2} \right)\sin(kx-\omega t)
$$

可以看成兩項乘積：
- 原來的波 $\sin(kx-\omega t)$ 
- 振幅被調製的波 $\cos\left( \frac{\Delta kx-\Delta\omega t}2{} \right)$，其波長較長，頻率較低。

![[Pasted image 20260314150919.png]]

上圖可以觀察出是一系列的波包，可用來描述粒子束，每個波包表示一個粒子。

波型中有兩種速度：
- 內部波的速度
- 波包的速度

首先研究波行進的速度，勢必要固定一個波峰來觀察。我們只要保持：

$$
kx-\omega t=\text{constant}
$$

就可以不停追蹤同一個波峰。

對時間微分：

$$
\begin{align}
 & \frac{d}{dt}(kx-\omega t)=0 \\
 & \implies k \frac{dx}{dt}=\omega \\
 & \implies \frac{dx}{dt}=\frac{\omega}{k}
\end{align}
$$

於是內部波的波速就是：

$$
v=\frac{\omega}{k}
$$

而波包的速度，即**群速度(group velocity)** 為：

$$
v_{\text{group}}= \frac{\frac{\Delta\omega}{2}}{\frac{\Delta k}{2}}=\frac{\Delta\omega}{\Delta k}\approx \frac{d\omega}{dk}
$$

我們可以簡單驗證群速度就是粒子速度。

由德布羅意關係 $\lambda=\frac{h}{p}$ 與 $\lambda=\frac{2\pi}{k}$，有 $k=\frac{p}{\hbar}\implies dk=\frac{dp}{\hbar}$。

由德布羅意關係 $\nu=\frac{E}{h}$ 與 $\nu=\frac{\omega}{2\pi}$ 有 $\omega=\frac{E}{\hbar}\implies d\omega=\frac{dE}{\hbar}$。

帶入群速度公式：$v_{\text{group}}= \frac{d\omega}{dk}=\frac{dE}{dp}=\frac{d}{dp}\left( \frac{p^{2}}{2m} \right)=\frac{p}{m}=v_{\text{particle}}$。

# The Principle of Complementarity

一個物質的雙重特性 (粒子性與波動性) 被稱為**波爾互補原理(Bohr's principle of complementarity)**。

某些實驗可能測得物質的波動特性，某些又可能測得粒子特性。但是，沒有一種實驗可以使物質同時表現波動與粒子性。

# 威儀指定習題

![[Pasted image 20260315142721.png]]

Sol:
$E_{k}=6000\text{ eV}\approx 9.6\times 10^{-15}\text{ J}=\frac{p^{2}}{2m}\implies p \approx1.3\times 10^{-22}$  
$\lambda=\frac{h}{p}\implies \lambda \approx \frac{6.63\times 10^{-34}}{1.3\times 10^{-22}}\approx 5\times 10^{-12}\text{ m}$ 

![[Pasted image 20260315142936.png]]

Sol:
這題純屬忘記前面的觀念。
每個電子都受電場的力，$F_{E}=eE$ 向**下** (電子帶負電)。
還受到磁場的力 $F_{B}=||-(ev)\times B||=evB$ 向**上** (帶負電，粒子移動方向取反)。
想要順利通過，必須有：$F_{E}=F_{B}\implies eE=evB\implies v=\frac{E}{B}$。
又 $\lambda=\frac{h}{p}=\frac{h}{mv}= \frac{hB}{mE}$。

![[Pasted image 20260315144555.png]]

Sol:
$E_{k}=20\text{ eV}\approx 3.2\times 10^{-18}\text{ J}$ 
又 $\alpha$ 粒子由兩個質子兩個中子組成，所以 $m=4\times 1.6\times 10^{-27}\text{ kg}$。
$p=\sqrt{ 2mE_{k} }\approx2.07\times 10^{-22}\text{ kg m/s}$ 
$\lambda=\frac{h}{p}\approx3.2\times 10^{-12}\text{ m}$ 
$n\lambda=2d\sin \theta\implies \sin \theta= \frac{n\lambda}{2d}$ 
因為我們要求 $n$ 的最大值，令 $\sin \theta=1\implies n\approx175.9$ 
$\lfloor n \rfloor=175$ 

![[Pasted image 20260315145935.png]]

Sol:
這題寫不出來就純純是英文沒看懂。allowed orbits are those that contain an integral number of de Broglie wavelengths 意思是：允許的軌道長度是德布羅意波長的整數倍。
也就是：$2\pi r=n\lambda$ 其中 $\lambda=\frac{h}{p}$。
帶入：$2\pi r=n \frac{h}{p}\implies rp=n\hbar\implies mvr=n\hbar$。

![[Pasted image 20260315151631.png]]

Sol:
(a)
$m=10^{-6}\text{ g}=10^{-9}\text{ kg}$ 
$\Delta p=mv=10^{-15}$ 
$\Delta p\Delta x\geq \hbar\implies\Delta x\approx 1.05\times 10^{-19}\text{ m}$ 
(b)
$\Delta p\approx 9.1\times 10^{-37}$ 
$\Delta p\Delta x\geq \hbar\implies\Delta x\approx 115\text{ m}$ 

![[Pasted image 20260315152310.png]]

Sol:
第一版中給的答案貌似是錯誤的 (？
我們有 $\Delta x=10^{-7}\text{ m}$，則 $\Delta p\Delta x\geq \hbar\implies\Delta p\geq 1.05\times 10^{-27}$ 
$\implies\Delta v\geq \frac{1.05\times 10^{-27}}{9.1\times 10^{-31}}=1150$ 
$\Delta vt=1150\times 10^{-6}=1.15\times 10^{-3}$ 
$\Delta x'=\Delta x+\Delta vt\approx1.15\times 10^{-3}\text{ m}$ 