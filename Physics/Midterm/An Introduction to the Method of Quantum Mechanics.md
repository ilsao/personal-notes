
目前為止，我們引入了量子化概念，這些理論構成了**舊量子理論(Old Quantum Theory, OQT)**。

OQT 有幾個缺陷：
1. 該理論只能應用於週期性系統。
2. 波爾理論解釋氫原子光譜的觀測波長，但無法解釋為何某些波長的強度較高。即，沒有解釋不同能階之間的躍遷速率。
3. 波爾理論無法解釋多電子原子的情況。
4. 該理論假設微觀電子有確定的軌道，但根據不確定性原則，此假設不成立。

# The Schrodinger Theorem of Quantum Mechanics

## The Time-dependent Schrodinger Equation

德布羅意假設無法計算受力作用時，粒子應該關聯到怎樣的波。因為受力，它的動量與能量不固定，討論 $\lambda$ 與 $\nu$ 沒有意義。

薛丁格假設了這樣的方程，使得我們可以通過給定位能，計算出對應的波函數：

$$
\boxed{-\frac{\hbar^{2}}{2m} \frac{\partial^{2}\psi}{\partial x^{2}}+E_{p}=i\hbar \frac{\partial \psi}{\partial t}}
$$

薛丁格方程是這麼猜出來的，我們由 $E=\frac{1}{2}mv^{2}+E_{p}$ 出發。兩邊同乘 $\psi$：

$$
E\psi=\frac{p^{2}}{2m}\psi+E_{p}\psi
$$

因為 $i\hbar \frac{\partial}{\partial t}$ 是能量 $E$ 的提取運算子，$-i\hbar \frac{\partial}{\partial x}$ 是動量 $p$ 的提取運算子，所以我們有：

$$
i\hbar \frac{\partial \psi}{\partial t}= \frac{1}{2m}\left( -i\hbar \frac{\partial}{\partial x} \right)\left( -i\hbar \frac{\partial}{\partial x} \right)\psi + E_{p}\implies-\frac{\hbar^{2}}{2m} \frac{\partial^{2}\psi}{\partial x^{2}}+E_{p}=i\hbar \frac{\partial \psi}{\partial t}
$$

上式被稱為**一維時間相依薛丁格方程(one-dimensional time-dependent Schrodinger equation)**

## The Schrodinger Equation for a Free Particle

考慮一個沿著 $x$ 軸移動的粒子，其動量為 $p=mv$，能量為 $E=\frac{1}{2}mv^{2}$。假設沒有外力作用於粒子，則位能 $E_{p}=\text{constant}$，我們選擇 $E_{p}=0$。

此情況下，薛丁格方程可以寫為：

$$
- \frac{\hbar^{2}}{2m}\frac{\partial^{2}\psi}{\partial x^{2}}=i\hbar \frac{\partial \psi}{\partial t}
$$

我們不會解這個微分方程，莫得關係，直接給你答案：

$$
\psi=A[\cos(kx-\omega t)+i\sin(kx-\omega t)]=Ae^{i(kx-\omega t)}
$$

通過將上式帶入薛丁格方程來檢測正確性：

$$
\begin{align}
 & -\frac{\hbar^{2}}{2m} \frac{\partial^{2}\psi}{\partial x^{2}}=\frac{\hbar^{2}}{2m}(k^{2}Ae^{i(kx-\omega t)}) \\
 & i\hbar \frac{\partial \psi}{\partial t}=i\hbar(-i\omega Ae^{i(kx-\omega t)}) \\
 & \implies \frac{\hbar^{2}k^{2}}{2m}Ae^{i(kx-\omega t)}=\hbar\omega Ae^{i(kx-\omega t)} \\
 & \implies \frac{\hbar^{2}k^{2}}{2m}=\hbar\omega
\end{align}
$$

只要滿足 $\frac{\hbar^{2}k^{2}}{2m}=\hbar\omega$，就說明這是一個解。

因為我們根據德布羅意假設：

$$
\boxed{\begin{align}
 & E=h\nu=h \frac{\omega}{2\pi}=\hbar\omega \\
 & p=\frac{h}{\lambda}=\frac{h}{\frac{2\pi}{k}}=\hbar k \\
\end{align}}
$$

又有：

$$
\boxed{E=\frac{p^{2}}{2m}\implies \hbar\omega=\frac{\hbar^{2}k^{2}}{2m}}
$$

> [!warning] 注意
> 自由粒子符合 $E= \frac{\hbar^{2}k^{2}}{2m}$，因為 $E=E_{k}$。
> 但對非自由粒子而言，$E=E_{k}+E_{p}$，不能這樣簡化。
> 並且注意到非自由粒子的動量會變化，$p=\hbar k$。因為 $\hbar$ 是常數，所以 $k$ 必須是隨位置變化的函數。

與我們帶入薛丁格方程得到的結果相同，所以對一個確定動量與能量的自由粒子，其波函數為：

$$
\boxed{\psi=Ae^{i(kx-\omega t)}}
$$

> [!note]
> 波函數可以是虛函數，因為其本身沒意義，我們需要的是 $|\psi|^{2}$。
> 
當 $\psi$ 是虛函數時，我們按數學定義寫：

$$
|\psi|^{2}=\psi^{*}\psi=A^{*}e^{i(kx-\omega t)}Ae^{i(kx-\omega t)}=A^{*}A
$$

此結果應該為實數且為正值，因為數學上不存在虛數機率

> [!note]
> $\psi^{*}$ 是 $\psi$ 的共軛，即：實部與 $\psi$ 實部相同，虛部與 $\psi$ 虛部相反。

## Expectation Values

由於不確定性原則，我們無法同時準確測量位置與動量，但我們可以對它們討論期望值。

若粒子在位置 $x_{i}$ 出現的機率為 $P_{i}$，則期望值定義為：

$$
\bar{x}=x_{1}P_{1}+x_{2}P_{2}+\dots+x_{n}P_{n}=\sum x_{i}P_{i}
$$

當粒子的位置可以連續變化時，求和就會變成積分：

$$
\bar{x}=\int_{-\infty}^{\infty}xP(x)\ dx
$$

並有：

$$
\int_{-\infty}^{\infty}P(x) \ dx = 1
$$

在波函數中考慮時，則為：

$$
\boxed{\bar{x}=\int_{-\infty}^{\infty}\psi^{*}x\psi \ dx}
$$

且：

$$
\int_{-\infty}^{\infty}\psi^{*}\psi \ dx = 1
$$

我們使用 $E_{p}(x)$ 帶入，也可求得位能的期望值：

$$
\boxed{\overline{ E_{p} }=\int_{-\infty}^{\infty}\psi^{*}E_{p}(x)\psi \ dx}
$$

我們將提出動量 $p$ 的操作子記做：

$$
p\longleftrightarrow -i\hbar \frac{\partial}{\partial x}
$$

將提出能量 $E$ 的操作子記做：

$$
E\longleftrightarrow i\hbar \frac{\partial}{\partial t}
$$

如果要計算動量的期望值：

$$
\boxed{\bar{p}=\int_{-\infty}^{\infty}\psi^{*}\left( -i\hbar \frac{\partial}{\partial x} \right)\psi \ dx}
$$

若要計算能量的期望值：

$$
\boxed{\bar{E}=\int_{-\infty}^{\infty}\psi^{*}\left( i\hbar \frac{\partial}{\partial t} \right)\psi \ dx}
$$

我們使用自由粒子的波函數展示一下計算能量期望值的正確性：

$$
\begin{align}
\bar{E} & =\int_{-\infty}^{\infty}\psi^{*}\left( -i\hbar \frac{\partial}{\partial t} \right)Ae^{i(kx-\omega t)} \ dx \\
 & =\int_{-\infty}^{\infty}\psi^{*}(-i\hbar)(-i\omega)Ae^{i(kx-\omega t)}\ dx \\
 & =\hbar\omega \int_{-\infty}^{\infty}\psi^{*}\psi \ dx \\
 & =\hbar\omega
\end{align}
$$

與德布羅意關係相符，因為對確定能量 $E=\hbar\omega$ 來說，期望值就是該值本身。

## The Time-independent Schrodinger Equation

求解偏微分方程的一個技巧是：**變數分離法(separation of variables)**。

即，將 $\psi(x,t)$ 表達為兩個分別關於 $x$ 與 $t$ 的兩個函數乘積：

$$
\psi(x,t)=\chi(x)\Gamma(t)
$$

我們將這種變化帶入薛丁格方程中：

$$
-\frac{\hbar^{2}}{2m} \Gamma(t) \frac{\partial^{2}\chi(x)}{\partial x^{2}}+E_{p}\chi(x)\Gamma(t)=i\hbar \chi(x) \frac{\partial\Gamma(t)}{\partial t}\implies-\frac{\hbar^{2}}{2m} \frac{1}{\chi(x)} \frac{\partial^{2}\chi(x)}{\partial x^{2}}+E_{p}=i\hbar \frac{1}{\Gamma(t)} \frac{\partial\Gamma(t)}{\partial t}
$$

方程左側僅依賴 $x$，右側僅依賴 $t$。由於 $x$ 與 $t$ 為兩個互相獨立的變數，所以等號兩側必等於同一常數 $G$，稱為**分離常數(separation constant)**。

即：

$$
\begin{align}
 -\frac{\hbar^{2}}{2m} \frac{1}{\chi(x)} \frac{\partial^{2}\chi(x)}{\partial x^{2}} +E_{p}& =G \\
 i\hbar \frac{1}{\Gamma(t)} \frac{\partial\Gamma(t)}{\partial t} & =G
\end{align}
$$

有關 $\Gamma$ 的微分方程較好解，解得：

$$
\Gamma(t)=Ke^{-iGt/h}
$$

由於 $K$ 可以是任意常數，我們取 $K=1$。

現在嘗試解 $G$，對波函數套用套用能量算符：

$$
\begin{align}
 i\hbar \frac{\partial}{\partial t}\psi(x,t) & =i\hbar \frac{\partial}{\partial t}\chi(x)\Gamma(t) \\
 & = i\hbar \frac{\partial}{\partial t}\chi(x)e^{-iGt/h} \\
 & = G\chi(x)\Gamma(t)=G\psi(x,t)
\end{align}
$$

顯然，我們有：

$$
G=E\text{ and }\boxed{\Gamma(t)=e^{-iEt/h}}\quad\forall \psi
$$

現在，想要求解 $\psi$，我們只需要求解一個偏微分即可方程：

$$
\boxed{-\frac{\hbar^{2}}{2m} \frac{d^{2}\chi(x)}{dx^{2}}+E_{p}(x)\chi
(x)=E\chi(x)}
$$

> [!note]
> 因為上述微分對單變量為分，所以變回 $\frac{d}{dx}$。

上述方程稱為**定態薛丁格方程(time-independent Schrodinger equation)**。

我們將解出的 $\chi$ 稱為**本徵函數(eigenfunction)** 或**本徵態(eigenstates)**，而 $E$ 稱為**本徵值(eigenvalues)**。

## Required Properties of the Eigenfunction $\chi(x)$ and its Derivation

本徵函數 $\chi(x)$ 必須 well-behaved，即：
1. 在任何地方都有限 (finite)
2. 在任何地方都僅有一個值
3. 在任何地方都連續

下圖分別展示了不 well-behaved 的幾種函數圖形：

![[Pasted image 20260314221328.png]]

注意到若 $\chi$ 或 $\frac{d\chi}{dx}$ 不是有限的，則動量的期望值 $\bar{p}$ 會是無限大。這意味著能量無限大，物理上不可能。

同樣地，若 $\chi$ 在某點不僅有一個值，代表 $\bar{p}$ 也有多個值。雖然我們無法準確測量 $p$ 的值，但我們理應可以 $p$ 的平均值。

最後，若 $\chi$ 在某點不連續，則 $\frac{d\chi}{dx}$ 在該點無限大。若 $\frac{d\chi}{dx}$ 不連續，則 $\frac{d^{2}\chi}{dx^{2}}$ 不連續，物理上不可能。(回憶：因為 $-\frac{\hbar}{2m} \frac{d^{2}\chi}{dx^{2}}+E_{p}\chi=E\chi$ 必須有限)

在**束縛系統(bound systems)** 中，這些限制可能導致能量或其他物理量的量子化。

> [!note]
> 這邊用 $p$ 討論，是因為 $\chi$ 是關於 $x$ 的函數。
> 而 $p$ 的運算子也是對 $x$ 微分 $-i\hbar \frac{\partial}{\partial x}$。

# Application of the Schrodinger Theory

## Particle Inside an Infinite Potential Well

考慮一個粒子被放入一個長度為 $a$ 的無限位能井：

$$
E_{p}(x)=\begin{cases}
\infty & \text{for }x< 0\text{ or }x>a \\
0 & \text{for } 0\leq x\leq a
\end{cases}
$$

![[Pasted image 20260314231240.png]]

因為這是一個無限位能井，所以粒子想離開需要無限大的能量，所以井外 $|\chi|^{2}=0$。

為了求井內的 $\chi$，我們在 $E_{p}=0$ 的情況下求解：

$$
\begin{align}
 & -\frac{\hbar^{2}}{2m} \frac{d^{2}\chi}{dx^{2}}=E\chi \\
\implies & \frac{d^{2}\chi}{dx}+ \frac{2mE}{\hbar^{2}}\chi =0 \\
\implies & \boxed{\frac{d^{2}\chi}{dx}+k^{2}\chi=0}\quad k^{2}=\frac{2mE}{\hbar^{2}}
\end{align}
$$

這邊我們來證明 $k^{2} = \frac{2mE}{\hbar^{2}}$：

$$
\begin{align}
p & =\frac{h}{\lambda}=\frac{h}{\frac{2\pi}{k}}=k\hbar \\
\implies E & =\frac{p^{2}}{2m}=\frac{k^{2}\hbar^{2}}{2m} \\
\implies k^{2} & =\frac{2mE}{\hbar^{2}}
\end{align}
$$

計算後解得：

$$
\chi(x)=ae^{ikx}+be^{-ikx}=(a+b)\cos kx+i(a-b)\sin kx=\boxed{A\cos kx+B\sin kx}
$$

其中 $a$ 與 $b$ 為任意常數。

目前為止，$k$ 與 $E$ 還沒有受到限制。有限性與單值性在上式中已經滿足，我們現在要讓 $\chi$ 連續。這意味著 $\chi(0)$ 與 $\chi(a)$ 都為 $0$。

帶回解得：

$$
\boxed{\chi=B\sin kx\quad k=\frac{n\pi}{a}\quad n=1,2,3,\dots}
$$

> [!note]
> $n=0$ 不可取，這樣會導致 $k=0$，從而導致 $\chi=0\ \forall x$。

從而：

$$
E= \frac{k^{2}\hbar^{2}}{2m}=\frac{n^{2}\pi^{2}}{a^{2}} \frac{\hbar^{2}}{2m}=\boxed{n^{2}E_{0}}\quad \boxed{E_{0}= \frac{\pi^{2}\hbar^{2}}{2ma^{2}}}
$$

![[Pasted image 20260314231510.png]]

注意到，在此情況下本徵函數一階導數在 $x=0$ 或 $x=a$ 時不連續。使得此時 $E_{p}=\infty$，但由於我們是無限位能井，顯然這是可行的特例。

> [!note]
> 古典物理在解釋被限制在具有剛性壁容器的粒子系統時，內能與絕對溫度相關聯，當處於絕對零度時內能為零。
> 但量子力學指出，粒子具有最小能量 $E_{0}$，所以能量為零是不允許出現的狀況。
> 若 $E=0$，則 $p=\Delta p=0$，使得 $\Delta x=\infty$。因為粒子被限制在井中，所以 $\Delta x$ 不可能無限大，最大的 $\Delta x=a$。

物理系統趨向於低能量狀態，即基態。此時，本徵函數為：

$$
\chi(x)=B\sin \frac{\pi}{a}x
$$

注意到，本徵函數乘以 $\Gamma(t)$ 後，$\psi(x,t)$ 會形成駐波。如圖所示：

![[Pasted image 20260314232132.png|245]]

# Quantum Tunneling

![[Pasted image 20260314232451.png|589]]

在井外時，雖然能量 $E<E_{p}$ 但是薛丁格方程仍存在解。為了使波函數連續，所以波函數延伸至井外。

所以按理來說，有那麼一丁點可能粒子隧穿到壁壘外側。

經過一番推導，可得知在壁壘中的波函數：

$$
\psi \propto e^{-\sqrt{ 2m(U_{0}-E)x/\hbar }}\quad U_{0}\text{: barrier height}
$$

實際上，Scanning Probe Microscope 就是利用隧穿效應，偵測電子從原子逃逸出來的電流大小來顯示原子表面：

![[Pasted image 20260314232827.png|903]]

# 威儀指定習題

![[Pasted image 20260315160017.png|668]]![[Pasted image 20260315160037.png|666]]

Sol:
(a) 在 $x=0$ 時不連續
(b) 在 $x\to 0$ 時 $\chi(x)\to \infty$ 
(c) 在 $x\to0$ 時 $\chi(x)\to-\infty$ 

![[Pasted image 20260315160633.png|768]]

Sol:
代入 time-independent Schrodinger equation $\frac{d^{2}\chi}{dx^{2}}+k^{2}\chi=0$ 解。
$\frac{d}{dx}\left( \frac{d}{dx} \right)(ae^{ikx}+be^{-ikx})=\frac{d}{dx}(ikae^{ikx}-ikbe^{-ikx})=-k^{2}ae^{ikx}+k^{2}be^{-ikx}=-k^{2}\chi$ 
$\implies \frac{d^{2}\chi}{dx^{2}}+k^{2}\chi=-k^{2}\chi+k^{2}\chi=0$ 
符合 time-independent Schrodinger equation，所以 $ae^{ikx}+be^{-ikx}$ 也是一個解。

![[Pasted image 20260315164336.png|671]]![[Pasted image 20260315164354.png|669]]

Sol:
(a)
$E_{0}= \frac{\pi ^2\hbar^{2}}{2ma^{2}}\approx \frac{3.14^{2}\times(1.05\times 10^{-34})^{2}}{2\times 9.1\times 10^{-31}\times 10^{-20}}\approx 5.98\times 10^{-18}\text{ J}\approx37.4\text{ eV}$  
(b)
兩者具有相同量級。
(c)
$E_{0}= \frac{\pi^{2}\hbar^{2}}{2m(10^{-14})^{2}}\approx5.98\times 10^{-10}\text{ J}\approx 3.7\times 10^{9}\text{ eV}$ 
(d)
幾乎不可能在原子核中找到電子，因為 (c) 的答案顯示，幾乎是原子核束縛能的 $10^{3}$ 倍。

![[Pasted image 20260315193507.png|811]]

Sol:
(a)
$E_{0}=\frac{\pi^{2}\hbar^{2}}{2ma^{2}}\approx 5.44\times 10^{-70}\text{ J}$ 
(b)
$E=n^{2}E_{0}\implies n=\sqrt{ \frac{E}{E_{0}} }$ 
$E=E_{k}=\frac{1}{2}mv^{2}=5\times 10^{-7}$ 
$n=\sqrt{ \frac{5\times 10^{-7}}{5.44\times 10^{-70}} }\approx 3\times 10^{31}$ 

![[Pasted image 20260315194720.png]]

Sol:
就愛這種送分題，嘻嘻。
$\lim_{ n \to \infty } \frac{(n+1)^{2}E_{0}-n^{2}E_{0}}{n^{2}E_{0}}=\lim_{ n \to \infty } \frac{(n+1)^{2}-n^{2}}{n^{2}}=\lim_{ n \to \infty } \frac{2n+1}{n^{2}}=0$ 

![[Pasted image 20260315194830.png|676]]

Sol:
其實沒你想的那麼難，不用算什麼機率之類的東西。
我們利用能量算出速度，然後使用速度除以長度即可。
$E_{k}=E=\frac{1}{2}mv^{2}=6\times 10^{6}\times 1.6\times 10^{-19}\implies v\approx 1.69\times 10^{7}\text{ m/s}$ 
$\text{collisions/s}=\frac{\text{velocity}}{\text{width}}= \frac{1.69\times 10^{7}}{10^{-14}}=1.69\times 10^{21}$ 

# 威儀考古

1. 在 Schrodinger equation 的 eigenfunction 中，$\psi$ 與 $\frac{\partial \psi}{\partial x}$ 需要滿足什麼條件？

Sol:
連續、有限、單值

2. 量子力學認為能量？$T=0\text{ K}$ 時能量？

Sol:
量子化
能量 $E=E_{0}\neq 0$ 

3. 請問 $\chi(x)=A\ln(kx)$ 是否可能為薛丁格方程式？為啥？

Sol:
不能，因為當 $x\to 0$ 時，$\ln(kx)\to - \infty$，非有限值。

4. Time-independent Schrodinger equation 為：$-\frac{\hbar^{2}}{2m} \frac{d^{2}}{dx^{2}}\chi+E_{p}\chi=E\chi$ 為何 $E$ 被量子化？

Sol:
$\chi$ 需要滿足物理條件與系統邊界條件，僅在特定 $E$ 值時薛丁格方程才有可接受解。