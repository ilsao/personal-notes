
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
\Delta \theta \approx \frac{\lambda}{d}
$$

想提高解析度(將低 $\Delta \theta$ )：
- 加大口徑(提高 $d$ )
- 縮小 $\lambda$ 

# X-Ray Diffraction By Crystals: Bragg Scattering

因為晶體繞射在波長約等於原子大小時發生，所以選擇使用 X 射線。(可見光波長太短)

![[Pasted image 20251117111515.png]]

若晶面距為 $d$，則因為光進去再反射出來，所以程差為：$2d\sin \theta$。

注意此處 $\theta$ 為**亮紋**角度。

# Standing Waves

駐波：兩個反向傳播、同頻率、同振幅的波疊加。

假設弦被固定，波在弦上來回反射。

我們有入射波：$y_{1}=A\sin(\omega t-kx)$ 與反射波 $y_{2}=A\sin(\omega t+kx)$。

可得駐波方程：$2A\sin kx\cos\omega t$。

節點(Nodes)：當 $\sin kx=0\implies x=\frac{n\pi}{k}$ 時，稱為節點。該點位移永遠為零。

腹點(Antinodes)：當 $|\sin kx|=\pm1\implies x= \frac{\frac{1}{2}\pi+n\pi}{k}$ 時，稱為腹點。該點振幅最大。

若令弦左端($x=0$) 與右端($x=l$) 固定，則左端與右端必為節點。

因為這個條件，我們有：$\lambda=\frac{2l}{n}$。

弦上的駐波只有可能有滿足這個條件的波長，這種條件也稱作量子化條件。