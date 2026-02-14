# 隱藏層

對於線性模型來說，線性意味著單調假設，可能導致錯誤的判斷。

我們通過在模型中加入一或多個隱藏層，來克服線性模型的限制。最簡單的辦法是將多個全連接層堆疊，每層都輸出到後面的層，直到生成輸出。

我們把 $L-1$ 層看作表示，最後一層看做線性預測器。這種架構就稱為多層感知機。

![[Deep Learning/pic/Multilayer Perceptrons/Multilayer Perceptron/1.png]]

如之前所述，輸入層不參與任何計算，輸出只需要計算隱藏層與輸出層。所以，此模型的層數為 $2$。

注意到，因為是全連接層，所以每個輸入都會引響隱藏層的每個神經元，而每個隱藏層的神經元都會影響輸出層的每個神經元。

假設我們一個小批量有 $n$ 個樣本，每個樣本有 $d$ (通常是 $2$ 的冪)個輸入特徵。那麼 $\mathbf{X}\in \mathbb{R}^{n\times d}$。

對於有 $h$ 個隱藏單元的單隱藏層 MLP，則 $\mathbf{H}\in \mathbb{R}^{n\times h}$ 表示隱藏層的輸出 (稱為**隱藏表示(hidden representation)**)。

因為隱藏層與輸出層是全連接的，所以隱藏層權重 $\mathbf{W}^{(1)}\in \mathbb{R}^{d\times h}$，隱藏層偏置 $\mathbf{b}^{(1)}\in \mathbb{R}^{1\times h}$。以及輸出層權重 $\mathbf{W}^{(2)}\in \mathbb{R}^{h\times q}$，輸出層偏置 $\mathbf{b}^{(2)}\in \mathbb{R}^{1\times q}$。並且我們如下計算 MLP 輸出 $\mathbf{O}\in \mathbb{R}^{n\times q}$ 如下計算：

$$
\begin{align}
 & \mathbf{H}=\mathbf{XW}^{(1)}+\mathbf{b}^{(1)} \\
 & \mathbf{O}=\mathbf{HW}^{(2)}+\mathbf{b}^{(2)}
\end{align}
$$

但是，我們會發現上述隱藏單元只是由輸入仿射變換而來，而輸出由隱藏單元仿射變換得到。注意到，仿射函數的仿射函數還是仿射函數，所以上述模型其實完全可以通過之前的線性模型表示。

為了發揮多層架構的潛力，在仿射變換後對每個隱藏單元應用**非線性**的**激活函數(activation function)** $\sigma$。激活函數的輸出值稱為**活性值(activations)**。

一般來說，添加激活函數後，就不可能再將 MLP 退化成線性模型。

## 從線性到非線性

$$
\begin{align}
 & \mathbf{H}=\sigma(\mathbf{XW}^{(1)}+\mathbf{b}^{(1)}) \\
 & \mathbf{O}=\mathbf{HW}^{(2)}+\mathbf{b}^{(2)}
\end{align}
$$

因為 $\mathbf{X}$ 的每一行對應小批量中的一個樣本，出於記號習慣，非線性函數 $\sigma$ 也按照行的方式作用輸入。也就是，一次計算一個樣本。

之前說過的 softmax 也是表示按行操作，但此處的激活函數不僅按行操作，也按元素操作 (softmax 不按元素操作，因為其對行求和)。

$\sigma$ 對元素操作，其意義表示對每個隱藏單元做一次非線性轉換 (從而得出活性值)，而不依賴其他隱藏單元的輸出結果。

為了構建更通用的多層感知機，我們可以不斷堆疊隱藏層，例如：$\mathbf{H}^{(1)}=\sigma_{1}(\mathbf{XW}^{(1)}+\mathbf{b}^{(1)})$ 與 $\mathbf{H}^{(2)}=\sigma_{2}(\mathbf{H}^{(1)}\mathbf{W}^{(2)}+\mathbf{b}^{(2)})$。

## 通用近似定理

雖然按理來說，單層隱藏層就足以擬合任意函數，但是通常我們傾向於使用更深的網絡而非更廣的網絡。

# 激活函數

**激活函數(activation function)** 通過計算加權和並加上偏置來確定神經元是否被激活，它們會將輸入信號轉換成可微運算輸出。多數激活函數都是非線性的。

## ReLU

最受歡迎的激活函數，**修正線性單元(Rectified linear unit, ReLU)**。實現非常簡單：

$$
\text{ReLU}(x)=\text{max}(0, x)
$$

此函數作用是保留正元素並丟棄負元素。

![[Deep Learning/pic/Multilayer Perceptrons/Multilayer Perceptron/2.png]]

當輸入為負時，ReLU 函數導數為 $0$。當輸入為正時，ReLU 導數為 $1$。而當輸入值正好為 $0$ 時，ReLU 函數不可導。此時我們默認使用左側導數 $0$。

![[Deep Learning/pic/Multilayer Perceptrons/Multilayer Perceptron/3.png]]

ReLU 的導數表現極佳，要麼讓參數消失，要麼讓參數通過。這可以很好的解決梯度消失問題。

ReLU 有一個變體，參數化 ReLU (Parameterized ReLU, pReLU)。為 ReLU 添加一個線性項，使得即使參數是負的，也有部分信息可以通過：

$$
\text{pReLU}(x)=\text{max}(0, x)+\alpha\text{min}(0,x)
$$

## sigmoid

對一個定義域在整個 $\mathbb{R}$ 中的輸入，sigmoid 將輸入變換到 $(0, 1)$ 上的輸出。

所以，sigmoid 也稱作**擠壓函數(squashing function)**：

$$
\text{sigmoid}(x)= \frac{1}{1+\text{exp}(-x)}
$$

![[Deep Learning/pic/Multilayer Perceptrons/Multilayer Perceptron/4.png]]

sigmoid 的導數為以下公式：

$$
\frac{d}{dx}\text{sigmoid}(x)= \frac{\text{exp}(-x)}{(1+\text{exp}(-x))^{2}}=\text{sigmoid}(x)(1-\text{sigmoid}(x))
$$
注意到，當輸入為 $0$ 時，sigmoid 函數的導數達到最大值 $0.25$，而越遠離 $0$ 導數越接近 $0$。

![[Deep Learning/pic/Multilayer Perceptrons/Multilayer Perceptron/5.png]]

## tanh

與 sigmoid 類似，tanh 把任意輸入轉換到 $(-1, 1)$ 之間：

$$
\text{tanh}(x)= \frac{1-\text{exp}(-2x)}{1+\text{exp}(-2x)}
$$

![[Deep Learning/pic/Multilayer Perceptrons/Multilayer Perceptron/6.png]]

tanh 的導數是：

$$
\frac{d}{dx}\text{tanh}(x)=1-\text{tanh}^{2}(x)
$$

當 $x=0$ 時，導數有最大值 $1$，$x$ 越遠離 $0$ 則導數越接近 $0$。

![[Deep Learning/pic/Multilayer Perceptrons/Multilayer Perceptron/7.png]]

