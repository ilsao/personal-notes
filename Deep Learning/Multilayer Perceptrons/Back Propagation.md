# 向前傳播

**向前傳播(forward propagation, forward pass)**：按順序從輸入層到輸出層，計算存儲在神經網絡中每層的結果。

我們一步步ㄧ研究單隱藏層神經網絡的機制，我們假設輸入樣本 $\mathbf{x}\in \mathbb{R}^{d}$，且隱藏層不包含偏置。此處中間變量為：

$$
\mathbf{z}=\mathbf{W}^{(1)}\mathbf{x}
$$

其中 $\mathbf{W}^{(1)}\in \mathbb{R}^{h\times d}$。我們將 $\mathbf{z}\in \mathbb{R}^{h}$ 傳入激活函數後，得到長度 $h$ 的隱藏激活向量：

$$
\mathbf{h}=\phi(\mathbf{z})
$$

繼續輸入到輸出層，其權重為 $\mathbf{W}^{(2)}\in \mathbb{R}^{q\times h}$ ，得到輸出層變量 $\mathbf{o}\in \mathbb{R}^{q}$：

$$
\mathbf{o}=\mathbf{W}^{(2)}\mathbf{h}
$$

設損失函數為 $l$：

$$
L=l(\mathbf{o},y)
$$

根據 $L_{2}$ 正則化，正則化項為：

$$
s=\frac{\lambda}{2}(||\mathbf{W}^{(1)}||^{2}_{F}+||\mathbf{W}^{(2)}||^{2}_{F})
$$

其中矩陣的 Frobenius 范數會將矩陣展平為向量，並套用 $L_{2}$ 范數。

最終，正則化損失為：

$$
J=L+s
$$

我們將 $J$ 稱為**目標函數(objective function)**。

# 向前傳播計算圖

圖中正方形表示變量，圓圈表示操作符：

![[Deep Learning/pic/Multilayer Perceptrons/Back Propagation/1.png]]

# 反向傳播

**反向傳播(back propagation, backpropagation)**：計算神經網絡參數梯度的方法。此方法利用鏈式法則，按相反順序從輸出層到輸入層遍歷網絡。