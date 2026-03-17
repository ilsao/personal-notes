# Rutherford Model

## The Scattering of $\alpha$ Particles

Rutherfor, Geiger 與 Marsden 通過 $\alpha$ 粒子散射實驗， 將 $\alpha$ 粒子 (He 原子核)打向金箔，發現：
- 大部分 $\alpha$ 粒子直線通過或小角度散射
- 少部分粒子大角度偏轉。

![[Pasted image 20260303124455.png]]

此結果與湯姆森提出的模型計算不符。

於是拉塞福提出行星原子模型。表示幾乎所有正電荷與質量都集中在 $10^{-14}\text{ m}$ 處的原子核。而電子在約 $10^{-10}\text{ m}$ 處繞原子核運動。

## Difficulties of the Nuclear Planetary Model

考慮電子繞核圓周運動，總能量為動能 + 位能 (負號表示二粒子電性相反)：

$$
E_{\text{total}}=\frac{1}{2}mv^{2}-\frac{1}{4\pi \epsilon_{0}} \frac{e^{2}}{r}
$$

由於向心力由電磁作用力提供：

$$
\frac{1}{4\pi\epsilon_{0}} \frac{e^{2}}{r^{2}}=\frac{mv^{2}}{r}
$$

將上式同乘 $\frac{r}{2}$：

$$
\frac{1}{2}\frac{1}{4\pi\epsilon_{0}} \frac{e^{2}}{r}=\frac{1}{2}mv^{2}
$$

帶回總能量：

$$
\boxed{E_{\text{total}}=-\frac{1}{2} \frac{1}{4\pi\epsilon_{0}} \frac{e^{2}}{r}}
$$

旋轉頻率為：

$$
\nu=\frac{\text{velocity}}{\text{distance}}=\frac{v}{2\pi r}
$$

通過向心力可知速度：

$$
v=\left( \frac{1}{4\pi\epsilon_{0}} \frac{e^{2}}{mr}\right)^{1/2}
$$

帶入頻率得：

$$
\nu=\left( \frac{e^{2}}{16\pi^{3}\epsilon_{0}m} \right)^{1/2} \frac{1}{r^{3/2}}
$$

若用古典物理解釋，會發現原子非常不穩定。

把圓周運動 (通過將速度分解而) 分解成兩個簡諧運動：

$$
\begin{align}
 & x=r\cos(2\pi \nu t) \\
 & y=r\sin(2\pi \nu t)
\end{align}
$$

古典電磁學認為加速電荷會輻射電磁波。因此當電子繞核旋轉時，會發出電磁波而造成能量減少，從而越發接近甚至墜入原子核。

又因為頻率與 $r$ 有關，隨著半徑的連續變化，發射頻率應該也連續變化，使得光譜應為連續光譜。但實際上，氫原子光譜是離散的。

# The Spectrum of Hydrogen

下圖展示了研究元素發射光譜的設備：

![[Pasted image 20260228204458.png]]

如圖，將少量氣態元素 (模擬理想氣體) 放入玻璃管。管中有兩個金屬電極，並在其上施加高電壓，使得電子釋出並擊打在氣體分子上。氣體發出的電磁輻射通過**準直器(collimator)** 與**繞射光柵(diffraction grating)**，最終在屏幕顯示干涉條紋。

> [!note]
> 回憶到，理想氣體忽略了分子間作用力。使得光譜盡可能與單個分子發出的光譜相同。

我們會發現，氫原子光譜離散，且每條線都滿足 Rydberg-Ritz 公式：

$$
\frac{1}{\lambda}=R\left( \frac{1}{n_{k}^{2}}-\frac{1}{n_{j}^{2}} \right)
$$

其中：

$$
R=0.96775\times 10^{7}\text{ m}^{-1}
$$

且 $n_{k}$ 與 $n_{j}$ 為整數。

通過固定 $n_{k}$ (較小)，並令 $n_{j}=n_{k}+1,n_{k}+2,n_{k}+3,\dots$，會形成不同系列。

Lyman 系列：
- $n_{k}=1$，散發紫外光。

Balmer 系列：
- $n_{k}=2$，散發可見光。

Paschen 系列：
- $n_{k}=3$，散發紅外線。

Brackett 系列：
- $n_{k}=4$。

# The Bohr Atom

為了解決拉塞福模型遇到的兩個問題 (不穩定性與連續光譜)，Neils Bohr 提出了一個氫原子模型。

## Bohr's Postulates

1. 古典力學認為電子有無限多條不同半徑的軌道，但 Bohr 假設電子只能在某些特定軌道上。電子角動量 $L$ 必須滿足：

$$
L=mvr=n\hbar\quad n=1,2,3,\dots\quad \hbar= \frac{h}{2\pi}\approx 1.05\times 10^{-34}
$$

> [!note]
> 為了構建原子模型，Bohr 假設**軌道角動量**量子化。 回顧上述電子圓周運動的能量，發現與 $-\frac{1}{n^{2}}$ 成正比。所以此假設也會使得能量量子化。

2. 與古典電磁學相反，允許那些處在特定軌道上的電子不會輻射電磁波。

> [!note]
> 避免古典預測的原子不穩定問題。

3. 若電子最初在能量為 $E_{i}$ 的軌道上，躍遷到較低能量 $E_{f}$ 的軌道，則會發射電磁波。其頻率為 (損失能量 = 光子能量)：

$$
\nu=\frac{E_{i}-E_{f}}{h}
$$

## Energy Spectrum of Bohr Atom

根據第一個假設，有：

$$
\boxed{v=\frac{n\hbar}{mr}}
$$

帶入向心力公式：

$$
\frac{1}{4\pi\epsilon_{0}} \frac{e^{2}}{r^{2}}=\frac{m}{r} \frac{n^{2}\hbar^{2}}{m^{2}r^{2}}
$$

則：

$$
\boxed{r_{n}=n^{2} \frac{4\pi \hbar^{2}\epsilon_{0}}{e^{2}m}=n^{2}r_{0}}
$$

所以，半徑也被量子化。只有 $r_{0},4r_{0},9r_{0},\dots$ 的軌道被允許存在。

這邊認為系統默認趨向最低能量狀態，即電子趨向存在於最小軌道半徑 $r_{0}$。

其中：

$$
\boxed{r_{0}\approx{0}.53\times 10^{-10}\text{ m}}
$$

由能量公式：

$$
E=-\frac{1}{2} \frac{1}{4\pi\epsilon_{0}} \frac{e^{2}}{r}
$$

帶入 $r_{n}$ 可得：

$$
\boxed{E_{n}=-\frac{e^{4}m}{8\epsilon_{0}^{2}h^{2}} \frac{1}{n^{2}}=-\frac{E_{0}}{n^{2}}\quad n=1,2,3,\dots}
$$

計算基態能量，得：$\boxed{E_{0}=13.56\text{ eV}}$。因此 $E_{n=1}=-13.56\text{ eV}$。

> [!note]
> 此處為負號是因為此能量為束縛能。

> [!warning] 注意
> 想將電子從基態激發到 $n$ 階，需要吸收二階束縛能絕對值之差。而不是 $n$ 階束縛能的絕對值。

> [!warning] 注意
> 現在更準確的數值 $\boxed{E_{0}=13.6\text{ eV}}$。

## Spectral Lines Predicted by Bohr Model

若電子由 $E_{i}$ 躍遷到 $E_{f}$，則：

$$
\nu=\frac{E_{i}-E_{f}}{h}=\frac{E_{0}}{h}\left( \frac{1}{n_{f}^{2}}-\frac{1}{n_{i}^{2}} \right)
$$

帶入 $\lambda \nu=c$：

$$
\boxed{\frac{1}{\lambda}=\frac{E_{0}}{hc}\left( \frac{1}{n_{f}^{2}}-\frac{1}{n_{i}^{2}} \right)}
$$

其中定義：

$$
R_{\text{Bohr}}=\frac{E_{0}}{hc}\approx 1.09740\times 10^{7}\text{ m}^{-1}
$$

與 Rydberg-Ritz 公式幾乎相同。

![[Pasted image 20260301012714.png]]

> [!note]
> 電子從 $n$ 階返回基態，會放出 $C^{n}_{2}$ 條光譜線。

# The Frank-Hertz Experiment

![[Pasted image 20260301012941.png]]

上圖顯示了 Frank-Hertz 的實驗裝置：
- 玻璃管：充滿待研究粒子蒸氣。
- **燈絲(Filament)**：加熱後提供電子。
- **極板(Plate)** 
- **柵極(Grid)**：帶電金屬網，可以吸引或排斥電子。因為大部分為空隙，多數電子可以穿過。

燈絲與柵極之間具有一個可調加速電壓 $V_{0}$。此電位差使電子擁有動能：

$$
E_{k}=eV_{0}
$$

在極板與柵極間施加一個阻擋電壓 $V_{r}$ (約 $1V$)，若 $V_{r}>V_{0}$ 則電子無法到達極板，無法對電流 $i$ 產生貢獻。即使 $V_{r}<V_{0}$，若電子在中途與蒸氣原子碰撞而損失動能，也可能無法到達極板。

> [!note]
> 若以**光子**擊打原子，則光子必須帶有**剛好**為軌道差距的能量才能使電子躍遷。
> 若以**電子**擊打原子，則電子只需帶有**大於等於**軌道差距的能量即可使電子躍遷。

![[Pasted image 20260301013831.png]]

上圖虛線表示玻璃管內不含蒸氣，保持真空。因為真空管是**非歐姆元件(nonohmic device)**，所以電流與電壓不成線性關係。

上圖紅線表示管內存在某種元素蒸氣，可以觀察出一系列突然的電流下降。

當電子與重原子碰撞，可能發生兩種類型的碰撞。

- 彈性碰撞：電子速度相反，但動能幾乎沒有損失。向後移動後又會被持續存在的電場向前加速，抵達極板時仍可克服阻擋電壓，不會造成電壓下降。

- 非彈性碰撞：

電子外部動能轉為原子內部能量 (原子被激發)。

注意到汞的第一激發態能量比基態高 $4.9\text{ eV}$，所以每當電子取得動能 $4.9\text{ eV}$ 或更高，能量就會被原子吸收用來躍遷。

> [!warning] 注意
> 汞的第二激發態與基態能量差值為 $6.7\text{ eV}$，但圖中很難觀察到電流下降。
> 因為電子一旦達到 $4.9\text{ eV}$ 就很可能發生非彈性碰撞而失去能量，能累積能量到 $6.7\text{ eV}$ 的電子比例很小。

> [!note]
> 此實驗證明了：
>- 原子能階離散。
>- 原子只吸收特定能量。
>- Bohr 的量子假設正確。

# Light Amplification by Stimulated Emission of Radiation

我們需要先知道兩種電子從高階掉到低階的原因：
- spontaneous emission：電子經過一段時間後，自發從高階掉往低階。
- stimulated emission：電子收到剛好等於兩能階差的能量，而從高階掉往低階。

![[Pasted image 20260301134825.png]]

stimulated emission 有三個特性：
- 一個光子進入激發，會造成第二個光子被發射，即所謂的 amplification。
- 發射的兩個光子與入射光子同方向。
- 發射的兩個光子與入射光子同相 (coherent)。

產生雷射除了需要 stimulated emission，還需要以下兩個條件：
- population inversion：![[Pasted image 20260301135210.png]]
- metastable state (亞穩態)：電子被激發到高能階後，正常只需 $10^{-8}\text{ s}$ 就會躍遷回低能階。處于亞穩態者需要 $10^{-3}\text{ s}$ 才會躍遷回低能階。使得 population inversion 變得容易。

雷射擁有以下性質：
- 單向
- 高強度
- 單頻
- 同向

下圖展示了雷射的產生過程：

![[Pasted image 20260301135552.png]]

裝置左側是完美反射的鏡子，右側是可以部分被穿透的鏡子。

首先外加一個能量，一段時間後各個粒子就會發出不同方向的電磁波。發出電磁波後，因為 stimulated emission，可能會產生一些 coherent 的電磁波。對於那些與鏡面不垂直者，會反彈或直接射出裝置，只有那些垂直者會在裝置內繼續反彈。多次反彈與 stimulated emission 後，產生大量 coherent 的電磁波，從 partial mirror 散發出去時就是雷射。

# 威儀指定習題


![[Pasted image 20260301160613.png]]

Sol:
(a)
$h\nu=E_{i}-E_{f}=-\frac{E_{0}}{n_{i}^{2}}-\left( -\frac{E_{0}}{n_{f}^{2}} \right)\approx 12.053\text{ eV}$ 
(b)
$h\nu=mc^{2}\implies p_{\text{photon}}=\frac{h\nu}{c}\approx 6.42\times 10^{-27}\text{ kg-m/sec}$ 
(c)
$\frac{hc}{\lambda}=12.053\text{ eV}\implies \lambda=\frac{6.63\times 10^{-34}\times 3\times 10^{8}}{12.053\times 1.6\times 10^{-19}}\approx 1.03\times 10^{-7}\text{ m}$ 

![[Pasted image 20260301162122.png]]![[Pasted image 20260301162137.png]]

Sol:
(b)
這邊注意啥是 recoil speed，顧名思義是發出去一個光子，氫原子自己應該反方向飛的速度。
這邊光子動能完全由電子躍遷提供：$E_{k}=E_{i}-E_{f}=-\frac{E_{0}}{16}+E_{0}\approx 12.7\text{ eV}$。
計算光子動量：$\frac{E}{c}\approx 6.77\times 10^{-27}\text{ kg-m/s}$。
一個氫原子重量為：$1.67\times 10^{-27}\text{ kg}$。
所以氫原子的 recoil speed 為：$\frac{6.77\times 10^{-27}}{1.67\times 10^{-27}}\approx 4.05\text{ m/s}$。

![[Pasted image 20260301163432.png]]

Sol:
首先計算光子動量：$p_{\text{p}}=\frac{100\text{ eV}}{c}\approx5.34\times 10^{-26}\text{ kg-m/s}$ 
而電子取得的能量為：$100\text{ eV}=E_{k}+\phi\implies E_{k}=100-13.56= 86.44\text{ eV}$ 
計算電子的動量：$\sqrt{ 2mE_{k} }\approx 5.0\times 10^{-24}\text{ kg-m/s}$ 
$p_{\text{p}}=p+p_{\text{e}}\implies p\approx -5.0\times 10^{-24}\text{ kg-m/s}$ 
$v=\frac{p}{m} = -\frac{5.0\times 10^{-24}}{1.67\times 10^{-27}}=3\times 10^{3}\text{ m/s}$ 

![[Pasted image 20260301170425.png]]

Sol:
注意審題，此題要求**入射光**的最低頻率。
因為發出了 $6$ 條光譜線，所以 $C^{n}_{2}=6\implies n=4$。
$n=4$ 時，具有束縛能 $E=-\frac{E_{0}}{16}=-\frac{13.56}{16}=-0.8475\text{ eV}$。
我們需要吸收 $13.56-0.8457=12.7143\text{ eV}$ 才能使電子被激發到 $n=4$。
$\implies \nu=\frac{12.7143\times 1.6\times 10^{-19}}{6.63\times 10^{-34}}\approx 3.07\times 10^{15}\text{ Hz}$  

![[Pasted image 20260301172032.png]]

Sol:
對於氫原子我們有：$r_{n}=n^{2}r_{0}\implies r_{2}=4\times (0.53\times 10^{-10})=2.12\times 10^{-10}\text{ m}$ 
回憶 Bohr 假設，$mvr=n\hbar\implies v=\frac{n\hbar}{mr}\approx 1.1\times 10^{6}\text{ m/s}$ 
圈數：$\frac{vt}{\text{distance}}=\frac{1.1\times 10^{6}\times 10^{-8}}{2\times \pi \times2.12\times 10^{-10}}\approx 8.3\times 10^{6}\text{ rev}$ 

![[Pasted image 20260301173942.png]]

Sol:
注意，out of its ground 代表要激發到 $n=2$。
所需能量為：$13.56-\frac{13.56}{4}=10.17\text{ eV}$ 
所需電位差為 $10.17\text{ V}$。

# 考古

1. 解釋 stimulated emission

Sol:
電子在激發態時受到一個剛好帶有躍遷能階差的光子誘發，從高階躍遷到低階而放出第二個頻率、方向、相位皆相同的光子。

2. 寫出兩個 stimulated emission 的特性

Sol:
1. 放出的兩個光子同相 (coherent)
2. 放出的光子方向相同
3. 放出的光子頻率相同
4. 放大作用