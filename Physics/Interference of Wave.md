
# The Superposition Principle

疊加原理：兩個波相遇時，某點的位移等於二波位移的和。

$$
y_{\text{total}}(x,t)=y_{1}(x,t)+y_{2}(x,t)+\dots
$$

# Interference of Two Source

假設兩個波 $y_{1}=\sin(\omega t-kx)$，$y_{2}=\sin(\omega t-kx+\phi)$。

建設性干涉：若 $\phi=2n\pi$ (完全同相)，振幅變 $2A\implies$ 建設性干涉。

毀滅性干涉：若 $\phi=2n\pi+\pi$ (完全反相)，振幅變零 $\implies$ 毀滅性干涉。

程差(Path Difference)：某點 $P$ 到兩個波源的距離之差。

假設兩波源同相，二者的相位差來自於程差的不同。

經過一番艱辛的推導，可以得到：
- 建設性干涉：$\delta=n\lambda$ ($\delta$ 為程差)
- 毀滅性干涉：$\delta=\left( n+\frac{1}{2} \right)\lambda$ 

# Double Slit Interference of Light

惠更斯(Huygens)原理：每個波前上的點都可以視為一個新的次波源，之後的波前是這些次波源面的胞絡線。

我們利用惠更斯原理使得光的雙狹縫干涉具有同相的光：單色光先透過一個狹縫 $\implies$ 變成相干的平面波 $\implies$ 再打到兩個狹縫去干涉。

對於光的雙狹縫干涉實驗來說，我們必須假設狹縫非常非常小。

考慮下圖場景：兩狹縫間距 $d$。由於螢幕與狹縫距離遠，可將從狹縫出來的光視為平行。令螢幕上某點 $P$ 與狹縫連線，則此線與水平線夾角 $\theta$。

![[Pasted image 20251117104205.png]]

如上圖所示，我們可以得到光線到 $P$ 的程差為 $d\sin \theta$。

根據程差的值，我們有以下結論：
- **亮紋**：$d\sin \theta=n\lambda$ 
- 暗紋：$d\sin \theta=\left( n+\frac{1}{2} \right)\lambda$ 

討論 $d, \lambda$ 對紋路的影響：
- $d$ 變大 $\implies$ 間隔較小的 $\theta$ 就會有新的亮紋 $\implies$ 紋路變密。
- $\lambda$ 變大 $\implies$ 間隔較大的 $\theta$ 才會有新的亮紋 $\implies$ 紋路變鬆。

# Single Slit Diffraction

對於單狹縫繞射，我們必須使該狹縫的寬度與入射波的波長相同或略大。

![[Pasted image 20251117105242.png]]

如上圖所示，假設狹縫的寬度為 $d$。

通過一系列複雜的推導，我們得到**暗紋**角度公式：$d\sin \theta=n\lambda$。(注意，如果此公式放在雙狹縫干涉中，其角度為**亮紋**角度)

# Resolving Power

分辨兩個繞射過的光點是否重合的標準是什麼？(考慮繞射影響)

Rayleigh criterion：一個光點的中央主極剛好落在另一個光點的暗紋處。

再次經過冗長的推導，我們有極限角分辨率：

$$
\boxed{\Delta \theta \approx \frac{\lambda}{d}}
$$

想提高解析度(將低 $\Delta \theta$ )：
- 加大口徑(提高 $d$ )
- 縮小 $\lambda$ 

# X-Ray Diffraction By Crystals: Bragg Scattering

因為晶體繞射在波長約等於原子大小時發生，所以選擇使用 X 射線。(可見光波長太短)

![[Pasted image 20251117111515.png]]

若晶面距為 $d$，則因為光進去再反射出來，所以程差為：

$$
\boxed{2d\sin \theta}
$$

注意此處 $\theta$ 為**亮紋**角度。

# Standing Waves

駐波：兩個反向傳播、同頻率、同振幅的波疊加。

假設弦被固定，波在弦上來回反射。

我們有入射波：$y_{1}=A\sin(\omega t-kx)$ 與反射波 $y_{2}=A\sin(\omega t+kx)$。

可得駐波方程：

$$
\boxed{y=2A\sin kx\cos\omega t}
$$

節點(Nodes)：當 $\sin kx=0\implies x=\frac{n\pi}{k}$ 時，稱為節點。該點位移永遠為零。

腹點(Antinodes)：當 $|\sin kx|=\pm1\implies x= \frac{\frac{1}{2}\pi+n\pi}{k}$ 時，稱為腹點。該點振幅最大。

若令弦左端($x=0$) 與右端($x=l$) 固定，則左端與右端必為節點。

因為這個條件，我們有：

$$
\boxed{\lambda=\frac{2l}{n}}
$$

弦上的駐波只有可能有滿足這個條件的波長，這種條件也稱作量子化條件。

# 威儀指定習題

1. Two sources emit waves of the same frequency, wavelength, and amplitude. What is the amplitude of the resulting wave at a point $P$ at a distance $x_{1}$ from source $S_{1}$ and a distance $x_{2}$ from source $S_{2}$ if $x_{1}-x_{2}$ is (a) one wavelength? (b) one-half wavelength?

Sol:
(a)
建設性干涉：2A
(b)
破壞性干涉：0

2. Two slits separated by a distance $d= 4\times10^{-5}\text{ m}$, are $1.5\text{ }$ away from a screen (see the picture below). What is the separation $y_{2}-y_{1}$ between the first and the second interference maxima if light of wavelength $A$ = $5000 \mathring{A}$ is sent through the slits? 

![[Pasted image 20251117151126.png]]

Sol:
$y_{2}-y_{1}=l(\sin \theta_{2}-\sin \theta_{1})=1.5(\tan \theta_{2}-\tan \theta_{1})$ 
$d\sin \theta_{1}=5000\times10^{-10}\implies \theta_{1}\approx0.716^{\circ}$ 
$d\sin \theta_{2}=2\times5000\times10^{-1}\implies \theta_{2}\approx1.433^{\circ}$ 
$\implies 1.5(\tan \theta_{2}-\tan\theta_{1})\approx0.0188\text{ m}=1.88\text{ cm}$ 

3. Sodium chloride (NaCl) has a crystal structure similar to that of silver bromide (AgBr) shown in Fig. 12-18. The atomic weight of NaCl is $58.44\text{ g/mole}$ and its density is $2.16\text{ g/cm}^{3}$. (a) Calculate the spacing between the atoms in a NaCl crystal. (b) If X rays of wavelength $1.5 \ \mathring{A}$ are incident on a NaCl crystal, at what angle $\theta$ will the first order diffraction maximum be observed?

Sol:
(a)
設 spacing between the atoms in a NaCl crystal 為 $d$，則一立方公分內有 $\frac{1}{d^{3}}$ 個原子。
$\frac{1}{d^{3}}= \frac{2.16}{58.44}\times2\times 6\times 10^{23}=4.45\times 10^{22}\implies d\approx 2.82 \ \mathring{A}$ 
(b)
$2d\sin \theta=\lambda\implies \theta \approx15.4^{\circ}$ 

4. The wave velocity in a string $1\text{ m}$ long is $6\text{ m/sec}$. What are the frequencies of the standing waves in the string?

Sol:
已知：$\lambda=\frac{2l}{n}$，又$\lambda \nu=v$ 
$\implies \nu=\frac{6}{\frac{2}{n}}=3n\text{(Hz)}$，其中 $n$ 為正整數。

5. Monochromatic (single wavelength) light is directed on a double slit. A light meter is placed to the right of the slits in the position show below. When slit $S_{2}$ is closed, the light intensity at the location of the meter is $I_{1}$. When slit $S_{1}$ is closed the light intensity is $I_{2}$. (a) What is the light intensity $I_{T}$ when both slits are open if $x_{1}-x_{2}=\lambda$? (b) What is $I_{T}$ if $x_{1}-x_{2}=\frac{1}{2}\lambda$? $I_{1}$ and $I_{2}$ are not necessarily equal. Assume that the size of the slits is smaller than the wavelength so that the slits can be considered to be the light source. 

![[Pasted image 20251117233034.png]]

Sol:
(a)
已知 $I \propto\text{Amplitude}^{2}$，且此時為建設性干涉。
又知道 $I_{1}:I_{2}=A_{1}^{2}:A_{2}^{2}$，那麼 $I_{T}\propto (A_{1}+A_{2})^{2}=A_{1}^{2}+A_{2}^{2}+2A_{1}A_{2}\implies I_{T}=I_{1}+I_{2}+2(I_{1}I_{2})^{1/2}$ 
(b)
此時為破壞性干涉：$I_{T}\propto(A_{1}-A_{2})^{2}=A_{1}^{2}-2A_{1}A_{2}+A_{2}^{2}\implies I_{T}=I_{1}^{2}+I_{2}^{2}-2(I_{1}I_{2})^{1/2}$ 

# 威儀考古

1. 人耳最敏感、接收最清楚的聲波頻率為 3000Hz,由此請試著推算出人耳道的大約長度,假設聲速為每秒 340 公尺。

Sol:
人耳可視為一開一閉的管子 $\implies$ $l=\frac{\lambda}{4}$ (背)
$340=3000 \times \lambda\implies \lambda=\frac{17}{150}$ 
$\implies l=\frac{17}{600}\approx0.028\text{ m}=2.8\text{ cm}$ 

2. 西元1801年,楊氏(Thomas Young)如何證明光具有波動性?他的實驗中最困難的部分是甚麼?

Sol:
(a)
將**單頻光**透過雙狹縫而觀察到光的干涉，以證明光的波動性。
(b)
雙狹縫的間距必須極小(以 $\mu$ 為單位的小)。

3. 請解釋何謂波的線性相加原理

Sol:
$y_{\text{total}}(x,t)=y_{1}(x,t)+y_{2}(x,t)+\dots+y_{n}(x,t)$ 
兩波相遇 $\implies$ 產生干涉
兩波離開 $\implies$ 保持原有波型