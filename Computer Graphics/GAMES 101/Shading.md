# A Simple Shading Model

在此，我們介紹一個基礎的著色算法：Blinn-Phong Reflectance Model。

Blinn-Phong 模型主要有三個計算項：
- Specular highlight：物體的高光。
- Diffuse reflection：物體因朝向不同引起的明暗變化。
- Ambient lighting：物體受非直射光線 (環境反射光) 照射產生的顏色。

我們必須意識到，著色是局部化的。所以我們可以對每個**著色點(shading point)** 計算顏色。

對於此模型，我們需要以下幾點輸入 (向量皆為單位向量)：
- 觀察方向 $\mathbf{v}$。
- 法線 $\mathbf{n}$。
- 光源方向 $\mathbf{l}$。
- 表面參數，如顏色，反射度等。

![[Computer Graphics/pic/GAMES 101/Shading/1.png]]

## Diffuse Reflection

因為一個表面反射的光會向四面八方散去，所以表面的顏色不會隨著視角的改變而不同。

又隨著表面與光源的夾角不同，表面所反射的光的多寡也不同。(Lambert's cosine law)

![[Computer Graphics/pic/GAMES 101/Shading/2.png]]

又因為我們考慮光線朝四面八方傳播 (如同一個在變大的球體)，假設在距離光源一單位處的光強度為 $I$，則在距離光源 $r$ 處某點的光強度為 (總功率 / 表面積) $\frac{I\times 4\pi}{4\pi r^{2}}=\frac{I}{r^{2}}$。

綜合上述，我們有：

$$
L_{d}=k_{d}\left( \frac{I}{r^{2}} \right)\text{max}(0, \mathbf{n}\cdot \mathbf{l})
$$

其中，$k_{d}$ 為 diffuse color 係數 (顏色)。

## Specular Term

顯然地，specular 依賴於觀察者的位置。因為只有當觀察角度與光線的反射角相差不大時，我們才可以觀察到高光。

如下圖所示 ($R$ 代表反射光)：

![[Computer Graphics/pic/GAMES 101/Shading/3.png]]

但是，想求反射角相對來說不是那麼容易。所以，我們引入半程向量 $\mathbf{h}$，並利用半程向量與法向量 $\mathbf{n}$ 計算。


![[Computer Graphics/pic/GAMES 101/Shading/4.png]]

其中，半程向量 (bisector) 如下計算：

$$
\mathbf{h}=\text{bisector}(\mathbf{l},\mathbf{v})= \frac{\mathbf{l}+\mathbf{v}}{||\mathbf{l}+\mathbf{v}||}
$$

那麼，specular reflected light 如下表示：

$$
L_{s}=k_{s}\left( \frac{I}{r^{2}} \right)\text{max}(0, \mathbf{n}\cdot \mathbf{h})^{p}
$$

注意到，$p$ 控制了 specular 亮度隨著與反射光角度差異遞減的速度。$p$ 越大，則衰減速率越快。

## Ambient Term

此項用於沒被光線直射時，物體的預設顏色。用來模擬其他物體造成的間接光照。

表示如下：

$$
L_{a}=k_{a}I_{a}
$$

## Blinn-Phong Reflection Model

最終，將三項相加就可以得到 Blinn-Phong 的結果：

$$
L=L_{a}+L_{d}+L_{s}=k_{a}I+k_{d}\left( \frac{I}{r^{2}} \right)\text{max}(0,\mathbf{n}\cdot \mathbf{l})+k_{s}\left( \frac{I}{r^{2}} \right)\text{max}(0,\mathbf{n}\cdot \mathbf{h})^{p}
$$

![[Computer Graphics/pic/GAMES 101/Shading/5.png]]

# Shading Frequencies

觀察下圖，下圖展示了三個不同的著色頻率：

![[Computer Graphics/pic/GAMES 101/Shading/6.png]]

對於左側的球體，採用的是 flat shading。對物體的每個**面**計算著色。

對於中間的球體，採用的是 gouraud shading。對物體的每個**頂點**計算著色。

對於右側的球體，採用的是 phong shading。對物體的每個**像素**計算著色。(注意這東西跟 blinn-phong 反射模型不同)

問題是，我們應該如何計算每個頂點或每個像素的法線向量？

## Defining Per-Vertex Normal Vectors

想計算每個頂點的法線向量，我們首先得計算每個面的法線向量，這很容易。如果你不會，那恐怕得回去找高中數學老師找回一下遺忘的知識了。

我們利用某點四周的面的平均，來計算某點的法線向量。

具體來說：

$$
N_{v}= \frac{\sum_{i}N_{i}}{||\sum_{i}N_{i}||}
$$

![[Computer Graphics/pic/GAMES 101/Shading/7.png]]

## Defining Per-Pixel Normal Vectors

至於計算像素的法向量，我們使用 Barycentric interpolation (重心插值)。

(之後講哈)

# Graphic Pipeline

