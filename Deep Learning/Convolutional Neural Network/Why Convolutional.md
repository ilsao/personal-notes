# 不變性

1. **平移不變性(translation invariance)**：不管需要監測對象出現在圖像哪裡，都不應該影響網絡的判斷 (神經網絡的前幾層應該對相同的圖像區域具有類似的反映)。
2. **局部性(locality)**：神經網絡的前幾層應該僅檢測圖像的局部特徵，而非圖像的整體關係。

# 多層感知機的限制

為了讓 MLP 保留二維空間結構，我們使 MLP 接受二維圖像輸入 $\mathbf{X}$，並且其每層的隱藏表示 $\mathbf{H}$ 與 $\mathbf{X}$ 擁有同樣形狀。

為了輸出二維結果，我們必須使用四階權重張量 $\mathbf{W}$。回憶權重的定義，我們要把每個輸入全部都用不同的權重加權一次。其中 $ij$ 控制輸入對應的參數，而 $kl$ 用來遍歷所有權重。

假設 $\mathbf{U}$ 包含偏置參數，我們如下表示全連接層：

$$
\begin{align}
 [\mathbf{H}]_{ij} & =[\mathbf{U}]_{ij}+\sum_{k}\sum_{l}[\mathbf{W}]_{i,j,k,l}[\mathbf{X}]_{kl} \\
  & =[\mathbf{U}]_{ij}+\sum_{a}\sum_{b}[\mathbf{V}]_{i,j,a,b}[\mathbf{X}]_{i+a,j+b}
\end{align}
$$

其中 $\mathbf{W}$ 到 $\mathbf{V}$ 具有一對一的關係，即 $k=i+a$，$l=j+b$。

## 平移不變性

現在我們回憶上述的第一個原則：平移不變性。這意味著檢測對象在 $\mathbf{X}$ 上的平移，僅導致 $\mathbf{H}$ 的平移。

即，$\mathbf{V}$ 與 $\mathbf{U}$ 實際不受 $ij$ 的影響。也就是說 $[\mathbf{V}]_{i,j,a,b}=[\mathbf{V}]_{ab}$，$\mathbf{U}$ 為一個常數 $u$。

$$
[\mathbf{H}]_{ij}=u+\sum_{a}\sum_{b}[\mathbf{V}]_{a,b}[\mathbf{X}]_{i+a,j+b}
$$

注意到，這就是**捲積(convolution)**。其中 $[\mathbf{V}]_{ab}$ 的係數比 $[\mathbf{V}]_{i,j,a,b}$ 少得多，因為前者不再依賴於圖像中的位置。

## 局部性

為了滿足局部性，我們應該保證 $|a|\leq\Delta$ 與 $|b|\leq\Delta$。即：

$$
[\mathbf{H}]_{ij}=u+\sum_{a}^{\Delta}\sum_{b}^{\Delta}[\mathbf{V}]_{a,b}[\mathbf{X}]_{i+a,j+b}
$$

上式是一個**捲積層(convolutional layer)**，$\mathbf{V}$ 稱為**捲積核(convolution kernel)** 或**濾波器(filter)**。

# 捲積

兩個函數的捲積被定義為：

$$
(f*g)(\mathbf{x})=\int f(\mathbf{z})g(\mathbf{x}-\mathbf{z}) \ d\mathbf{x}
$$

也即，將 $g$ 對 $y$ 軸翻轉並平移 $\mathbf{x}$ 後，測量 $f$ 與 $g$ 之間的重疊關係。

當函數為離散對象，積分就變成求和：

$$
(f*g)(i)=\sum_{a}f(a)g(i-a)
$$

對於二維張量：

$$
(f*g)(i,j)=\sum_{a}\sum_{b}f(a,b)g(i-a,j-b)
$$

注意到此處定義為 $(i-a,i-b)$，但轉換為加法並不困難。

# 通道

上述討論中，我們忽略了圖像包含三個通道 (rgb)。

所以，捲積應當調整為 $[\mathbf{V}]_{a,b,c}$ 且 $[\mathbf{X}]_{i,j,k}$。而且，因為輸入是三維的，隱藏表示也必須是三維的。

我們把隱藏表示想成一系列二維張量組成的**通道(channel)**，這些通道也稱**特徵映射(feature maps)**，因為這些通道在實際應用中用來向後續層提供空間化的學習特徵。例如，某些通道用來識別邊緣，一些用來識別紋理。

所以，為了支持這項功能，我們為 $\mathbf{V}$ 添加另一個維度 $[\mathbf{V}]_{a,b,c,d}$，其中 $c$ 表示每個顏色對當前輸出通道 $d$ 的貢獻。

$$
[\mathbf{H}]_{i,j,k}=\sum_{a}^{\Delta}\sum_{b }^{\Delta}\sum_{c}[\mathbf{V}]_{a,b,c,d}[\mathbf{X}]_{i+a,j+b,c}
$$

上式定義了具有 $d$ 個通道的捲積層。