# Blackbody Radiation

所有具有溫度的物體都會放出電磁波。單個原子會放出離散的頻率，分子會放出**頻帶(band of frequencies)**，而固體會放出連續光譜。

固體發出的光譜由其溫度與(某種層面上來說)成分有關。在室溫下，所發出的光譜大多集中在**紅外線(infrared)** 區域。

發出的光譜具有普遍性者 (即不受組成成分影響) 稱為黑體。黑體會吸收所有照射到其上的電磁波，所以不會反光而造成黑色的外觀。

我們可以通過在金屬腔上開一個小洞來模擬黑體。因為，任何進入小洞的電磁波只有很小的機率從洞口逃出。多次反彈後，輻射最終會被腔體中的原子吸收。這些原子最終會重新發出電磁波，其中某部分可能會從洞口逃出。這些逸出的輻射理論上會與其他黑體所發射的輻射相同。

![[Pasted image 20260228124748.png]]

## Character of the Spectrum of a Blackbody

黑體發出的光譜有如下特徵：
1. 若將輻射繪製成頻率與強度的圖表，我們可以看到較寬且連續的圖形。注意到 $y$ 軸的單位是 $I(\nu)$，即每單位時間單位面積下，固定頻率所發出的能量。
2. 將 $I(\nu)$ 對 $\nu$ 積分，其結果不受頻率影響而與溫度四次方正比。此事實被稱為 Stefan-Boltzmann law。其中 $\sigma=5.67\times 10^{-8}\text{ W/m}^{2}\text{-K}^{4}$ 
$$
\boxed{I_{T}=\int_{0}^{\infty}I(\nu) \ d\nu=\sigma T^{4}}
$$
3. 當溫度漸增，光譜整體往高頻率 (短波長) 趨近 (能量較大)，且峰值變大。根據某人實驗，峰值 $I(\nu)$ 處的頻率 $\nu_{\text{max}}$ 與溫度成正比。
$$
\nu_{\text{max}}\propto T
$$

![[Pasted image 20260228130111.png]]

> [!warning] 注意
> 威儀影片中的圖表使用波長 $\lambda$ 當作 $x$ 軸，注意單位。

> [!note]
> 此公式用來計算某**溫度** (單位 $K$) 下放出的**黑體輻射功率**。

## Planck's Theory

為了解釋黑體輻射，普朗克假設系統中的粒子都在以頻率 $\nu$ 做簡諧運動。其放出的能量滿足下式：

$$
E=nh\nu
$$

其中 $n=1,2,3,\dots$，而 $\boxed{h=6.63\times 10^{-34}\text{ J-sec}}$ 為普朗克常數。

> [!note]
> 為了解釋黑體輻射，普朗克將**簡諧運動體的能量**量子化。

通過古典物理，我們知道簡諧運動體發出的頻率與其振幅平方成正比。普朗克大膽假設將能量量子化，所以簡諧運動體發出的電磁波能量也是 $h\nu$ 的倍數。$h\nu$ 被稱為 quanta (或單數 quantum)。

我們之所以認為振幅是逐漸減小而非突然跳著減小，是因為 $h$ 實在小到我們無法觀察到突然的跳轉。

讓我們假設一個 $10\text{ kg}$ 的物體吊掛在彈性係數 $k=10^{3}\text{ N/m}$ 的彈簧上，並使初始振幅為 $A=0.1\text{ m}$。

我們有：

$$E=\frac{1}{2}kA^{2}=5\text{ J}$$

與

$$
\nu=\frac{1}{2\pi}\sqrt{ \frac{k}{m} }=1.59\text{ Hz}
$$

由普朗克定律計算每次減少的能量：

$$
\Delta E=h\nu=6.63\times 10^{-34}\text{ J-sec}\cdot 1.59\text{ sec}^{-1}\approx10^{-33}\text{ J}
$$

可以看到每次跳減的能量非常小。

# The Photoelectric Effect

我們將光照射在金屬板上，致使金屬板表面發出電子的效應稱為**光電效應(photoelectirc effect)**。

## Experimental Facts

![[Pasted image 20260228131853.png]]

如上圖所示，裝置由一個**真空管(evacuated tube)** (防止光電子與管內氣體分子碰撞) 與兩片金屬板構成，$C$ 是**陰極(cathode)**，$A$ 是**陽極(anode)**。

**單色光(monochromatic light)** (單波長) 透過**石英(quartz)** 窗照射在 $C$ 上。因為陽極 $A$ 相對於 $C$ 具有負電位 $V$，被激發出的電子會遭遇**阻止電壓(retarding voltage)** $V$。為了使**光電子(photoelectron)** 到達陽極，它們必須以大於位能 $|e|V$ 的動能 $E_{k}$ 被發出。

通過調整阻止電壓的值，我們可以計算電子的能量。其他可以調整的參數為入射光的強度 $I$ 與頻率 $\nu$。

![[Pasted image 20260228141556.png]]

圖 (a) 我們觀察到：$E_{k}>|e|V$ 的電子數隨 $I$ 上升而增加。

圖 (b) 我們觀察到：在 $V_{0}$ 時沒有光電流產生，這代表了 $V_{0}$ 的阻止電壓將所有電子阻擋。也就是說，$V_{0}$ 是光電子逸出的最大動能。而 $I$ 與對大動能 $E_{k\text{,max}}$ 無關。

圖 $(c)$ 我們觀察到：最大動能與光的頻率 $\nu$ 成正比，即：
$$
V_{0}=\alpha \nu
$$
注意到斜率**不會**隨材質改變。但是，$v_{c}$ 則**會**隨材質而改變。

## Failure of Classical Physics to Explain the Result

古典物理說光是一種電磁波，讓我們回憶波的性質：
- 波的能量連續分布在經過的所有空間。
- 波的強度與振幅平方成正比。

現在，我們來考慮一個被束縛在金屬中的電子，假設金屬的束縛能是 $E_{b}$。若電子從電磁波中獲得的能量大於其束縛能，就會逸出金屬。

$$
E_{k}=E_{\text{absorb}}-E_{b}
$$

隨著光的振幅增加，光的強度增加。根據古典物理，電子取得的能量應該變多。這樣，圖 (a) 可以被解釋。

但是，圖 (b) 無法被解釋。隨著強度增加，所有電子獲得的能量都應該變多，從而導致最大動能增加才對。而 (b) 中顯示最大動能與光強度無關，這無法被解釋。

事實上，圖 (c) 也沒法被解釋。電磁波能量依賴於強度而非頻率。這無法解釋 $V_{0}$ 為何依賴於頻率，也無法解釋為何存在 $V_{c}$ 使無論光強度多大都無法產生光電流。

最後，更無法解釋為何光電流瞬間產生。

考慮面積為 $1\text{ m}^{2}$ 的金屬板，照射強度為 $10^{-10}\text{ W/m}^{2}$ 的光，假設某一原子上的所有能量都被某一電子吸收。而金屬原子間距為 $d\approx2\times10^{-10}\text{ m}$。

一行的原子數為：

$$
\frac{1\text{ m}}{d}=5\times 10^{9}
$$

若為立方結構，第一層原子數為：

$$
(5\times 10^{9})^{2}=2.5\times 10^{19}
$$

則每秒每個電子獲得的能量為：

$$
\frac{10^{-10}\text{ J/s}}{2.5\times 10^{19}}=4\times 10^{-30}\text{ J/s}
$$

若最小束縛能為 $1eV$：

$$
t= \frac{1eV\times1.6 \times 10^{-19} \text{ J/eV}}{4\times 10^{-30}\text{ J/s}}=4\times 10^{10}\text{ s}\approx10^{5}\text{ days}
$$

明顯與瞬間產生光電子的現象相悖。

## Einstein's Theory

愛因斯坦說，頻率為 $\nu$ 的電磁波能量不集中在播前，而是集中在稱為**光子(photon)** 的小能量束 (具有粒子性) 上。其中每個光子的能量為：

$$
\boxed{E_{\text{photon}}=h\nu}
$$

> [!note]
> 為了解釋光電效應，愛因斯坦將**光**量子化成光子。

> [!note]
> 給定波長 (nm $10^{-9}$)，利用 $E_{\text{photon}}=\frac{1240}{\lambda}(\text{eV})$ 計算光子能量。

這種情況下，電磁波攜帶能量的方式更像一束粒子，光強度對應粒子密度。增加強度而非頻率，會造成光子密度上升，但對單個光子攜帶的能量不會有變化。

光電效應可以被解釋為能量為 $h\nu$ 的光子與金屬電子碰撞，並將全部能量傳遞給電子。根據能量守恆，有：

$$
\boxed{h\nu=E_{k}+E_{b}}
$$

我們令 $\phi$ 為最小束縛能，稱為金屬的**功函數(work function)**。於是上式可改寫為：

$$
E_{k\text{,max}}=h\nu-\phi
$$

因為有 $E_{k\text{,max}}=eV_{0}$，所以上式可寫成：

$$
\boxed{V_{0}=\frac{h\nu}{e}-\frac{\phi}{e}}
$$

讓我們逐步解釋三張圖。

圖 (a)：隨著光強度增加，光子密度增加，導致光子與電子碰撞機率上升，光電流增強。

圖 (b)：最大動能 (因此阻止電壓 $V_{0}$) 不應隨光強度改變，因為光強度變化不會造成單個電子的能量變化。

圖 (c)：如上式，光子攜帶的能量 $h\nu$，隨頻率上升而增加。所以頻率變化造成電磁波能量變化，而束縛能 $V_{c}=\frac{\phi}{e}$。注意到 $V_{0}$ 隨 $\nu$ 線性增加，且斜率為：

$$
\frac{h\nu}{e}\approx4.1\times 10^{-15}\text{ J}
$$

若 $h\nu<\phi$，因為光子能量小於金屬功函數，無電子逸出。

最後，因為粒子碰撞瞬時發生，沒有所謂能量積累的過程，電子發射是瞬時的。只要有光子能量 $h\nu>\phi$ 與電子碰撞，該電子就會立刻被擊出。

> [!note]
> 光電效應之所以只要光子帶有比功函數大的能量就能將電子擊出，是因為光電效應並不是將電子激發，不需要帶有特定能量的光子才能激發。


# Further Evidence for the Photon Theorem

## X-ray Production

之前的光電效應使用光照射金屬。

之後，Wilhelm K. Roentgen 發現通過電子擊打固體靶時會產生輻射。此輻射被命名為 X 射線，該射線有很強的穿透性，可以穿透對可見光來說不透明的物體。並且它不會被磁場偏轉，說明它不是帶電粒子。

Max von Laue 發現 X 射線會產生繞射，證明其是一種電磁波。其波長遠小於可見光，典型值為 $\lambda \approx 1\times 10^{-10}\text{ m}$。

![[Pasted image 20260228154128.png]]

電子通過加熱燈絲發射，經過高電壓 $V$ (幾千伏特) 加速後撞擊靶材。電子動能為：

$$
E_{k}=eV
$$

撞擊後會產生 X 射線。

X 射線的光譜具有：
- 連續光譜
- 短波長側存在明確的截止波長 $\lambda_{\text{min}}$ ($\nu_{\text{max}}$)

![[Pasted image 20260228154615.png]]

![[Pasted image 20260228154629.png]]

實驗發現：

$$
\lambda_{\text{min}}\propto \frac{1}{V}\quad \nu_{\text{max}}\propto V
$$

除了連續光譜，還會出現幾個尖峰，我們稱其為特徵 X 射線。該特徵與電壓 $V$ 無關，僅與靶材原子結構有關。

> [!note]
> 後續介紹原子模型時，你會了解這是因為能階躍遷而放出的電磁波。其能量為 $h\nu=E_{i}-E_{f}$。

我們來探究連續光譜 (制動輻射，bremsstrahlung) 出現的原因。入射電子接近原子核時，受到庫倫吸引而減速。經典電磁學認為加速電荷會連續放出不同頻率的電磁波，但無法解釋為何有明確的截止頻率。

假設電子的能量以量子形式 $h\nu$ 發出，令電子初始能量 $E_{k}$ 與最終能量 $E_{k}'$。我們有：

$$
E_{k}-E_{k}'=h\nu_{1}+h\nu_{2}+h\nu_{3}+\dots
$$

![[Pasted image 20260228155526.png]]

若我們假設散發的能量轉成單一光子，且電子墜毀在原子核 $E_{k}'=0$，則：

$$
E_{k}=h\nu_{\text{max}}
$$

因為：

$$
E_{k}=eV
$$

所以：

$$
\boxed{\nu_{\text{max}}=\frac{eV}{h}}
$$

與前面觀察 $\nu_{\text{max}}\propto V$ 吻合。

不僅如此，此實驗還可測量出普朗克常數的值。

# Momentum of the Photon

根據愛因斯坦的狹義相對論，粒子總相對論能量為：

$$
E=E_{k}+E_{0}
$$

且：

$$
E=mc^{2}
$$

其中 $E_{0}$ 為靜止能量。但因為光子靜止時質量為零，所以靜止能量為零。說明光子不能靜止存在。

通過結合相對論與之前假設：

$$
E_{\text{photon}}=h\nu=mc^{2}
$$

我們想計算光子動量：

$$
p=mv=mc
$$

可以如下構建：

$$
\begin{align}
 & h\nu=mc^{2} \\
\implies & mc=\frac{h\nu}{c} \quad\left[ \nu=\frac{c}{\lambda} \right]\\
\implies & mc=\frac{h}{\lambda} \\
\implies & \boxed{p_{\text{photon}}=\frac{E}{c}=\frac{h}{\lambda}}
\end{align}
$$

# 威儀指定習題

![[Pasted image 20260301140118.png]]![[Pasted image 20260301140132.png]]

Sol:
利用 Stefan-Boltzmann law，計算某溫度下放出黑體輻射的**功率**。
首先將太陽**功率**轉換下單位得：$8.4\times 10^{4}\text{ W/m}^{2}$。
注意到地球用半球接收到太陽光，而用整個球表面積發出黑體輻射。
考慮 lambert's cosine law，半球會被視為面積 $\pi R^{2}$，是整個表面積的 $\frac{1}{4}$ 倍。
因此，平均到地球表面後吸收功率應該是：$\frac{8.4\times 10^{4}}{4}$。
根據黑體輻射公式：$\sigma T^{4}=2.1\times 10^{4}$ 其中 $\sigma=5.67\times 10^{-8}$。
$\implies T\approx 1100\text{ K}$。

![[Pasted image 20260301142220.png]]

Sol:
(a)
要計算截止電壓 $V_{0}$，回想到公式 $V_{0}=E_{k,\text{max}}=h\nu-\phi$。
因為題目給的是波長，利用公式 $E_{\text{photon}}=\frac{1240}{\lambda}=\frac{1240}{300\text{(nm)}}=4.13\text{ eV}$。
那麼 $V_{0}=4.13-1.5=2.63\text{ eV}$。
(b)
動能公式：$E_{k,\text{max}}=\frac{1}{2}mv^{2}$ 
$2.63\text{ eV}\times 1.6\times 10^{-19}\text{J/eV}=\frac{1}{2}\times(9.1\times10^{-31}\text{kg})\times v^{2}\implies v\approx 9.6\times 10^{5}\text{ m/s}$ 

![[Pasted image 20260301144741.png]]

Sol:
這題秒殺。
(a)
$E_{\text{photon}}=\frac{1240}{200}=6.2\text{ eV}$ 
(b)
$E=2.0+\phi\implies \phi=4.2\text{ eV}$ 
(c)
$E_{\text{photon}}=\frac{1240}{600}\approx 2.07\text{ eV}$ 
$E<\phi$，無法激發電子，$V_{0}=0$。

![[Pasted image 20260301145507.png]]

Sol:
因為 cut-off frequency 是 $\nu_{0}$，所以 $h\nu_{0}=\phi$ 使得剛好沒電子出現。
此時使用 $3\nu_{0}$，則 $3h\nu_{0}=E+\phi\implies E=2h\nu_{0}$。

![[Pasted image 20260301145729.png]]

Sol:
$\begin{cases}h\nu_{0} & =15\text{ eV}+\phi \\ \frac{1}{2}h\nu_{0}  & =3\text{ eV}+\phi\end{cases}\implies h\nu_{0}=24\text{ eV},\ \phi=9\text{ eV}$ 
$\phi=9\text{ eV}=h\nu\implies \nu= \frac{9\cdot 1.6\times 10^{-19}}{6.63\times10^{-34}}\approx 2.17\times10^{15}\text{ Hz}$ 

![[Pasted image 20260301150456.png]]![[Pasted image 20260301150512.png]]

Sol:
回憶 X 射線如何產生：電子受原子核吸引而減少能量，此能量以電磁波形式放出。
想求 X 射線的最大頻率，我們假設電子最終墜毀在原子核將所有能量放出，並且所有能量被集中到一個光子上。
電子能量為：$E_{k}=eV=5000\text{ eV}$。
所以：$5000\text{ eV}=h\nu\implies \nu=\frac{5000\times 1.6\times 10^{-19}}{6.63\times 10^{-34}}\approx 1.2\times 10^{18}\text{ Hz}$ 
$\lambda \nu=c\implies \lambda=\frac{c}{\nu}= \frac{3\times 10^{8}}{1.2\times 10^{18}}=2.5\times 10^{-10}\text{ m}$ 