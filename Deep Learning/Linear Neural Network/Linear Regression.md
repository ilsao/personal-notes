# 線性回歸的基本元素

首先，我們得了解些機器學習的術語。我們將數據集中的每行數據稱為**樣本(sample，或數據點, data point，或數據樣本, data instance)**。而預測所依據的自變量稱為**特徵(feature，或協變量, covariate)**，預測目標稱為**標籤(label)** 或**目標(target)**。

通常，我們使用 $n$ 表示數據集中的樣本數。對索引為 $i$ 的樣本，其輸入表示為 $\mathbf{x}^{(i)}=[x_{1}^{(i)}, x_{2}^{(i)}]^{T}$，對應的標籤為 ${y}^{(i)}$。

## 線性模型

給定一個數據集，我們想要找到一個權重 $\mathbf{w}$ 與偏移 $b$ 使得預測結果 $\hat{y}$ 滿足：

$$
\hat{y}=\mathbf{w}^{T}\mathbf{x}+b
$$

但由於 $\mathbf{x}$ 僅表示一組數據，我們使用其組成的矩陣 $\mathbf{X}$ 表示：

$$
\mathbf{\hat{y}}=\mathbf{X}\mathbf{w}+b
$$

由於真實的數據不可能真的完全滿足這個關係，所以我們需要引入噪聲項來容忍誤差。

在開始尋找 $\mathbf{w}$ 與 $b$ 前，我們需要：
1. 評估模型質量的方法。
2. 提高模型質量的方法。

## 損失函數

**損失函數(loss function)** 可以評估預測值與實際值的差距，通常我們選取非負數作為損失。回歸問題最常用的損失函數是**平方誤差函數**。

當樣本 $i$ 的預測值為 $\hat{y}^{(i)}$ 且實際值為 $y^{(i)}$ 時，平方誤差定義如下：

$$
l^{(i)}(\mathbf{w},b)=\frac{1}{2}(\hat{y}^{(i)} - y^{(i)})^{2}
$$

其中，係數 $\frac{1}{2}$ 不會帶來啥較大的差別，但是可以使得我們微分後係數為 $1$。

為了度量模型在整個數據集上的表現狀況，我們需要取平均：

$$
L(\mathbf{w},b)=\frac{1}{n}\sum_{i=1}^{n}l^{i}(\mathbf{w},b)=\frac{1}{n}\sum_{i=1}^{n} \frac{1}{2}(\mathbf{w}^{T}\mathbf{x}^{(i)}+b-y^{(i)})^2
$$

訓練模型的過程，就是尋找 $(\mathbf{w},b)$ 使得損失函數值最小。

## 解析解

剛好，回歸模型可以找到一個解析解。

我們需要先將偏移 $b$ 合併入 $\mathbf{w}$。具體做法是對每列數據都添加一項恆為 $1$ 的偽特徵 $x_{0}$，並且在 $\mathbf{w}$ 中添加一項參數 $w_{0}=b$。

那麼在點乘 $\mathbf{w}$ 與 $\mathbf{x}$ 時，自然就會引入偏移量 $b$。

現在，我們的目標是最小化 $||\mathbf{y}-\mathbf{X}\mathbf{w}||^{2}$。由於損失函數的圖形是一個僅有一個臨界點的曲面，我們只需要將損失關於 $\mathbf{w}$ 的導數設為零，就可以解出：

$$
\mathbf{w}^{*}=(\mathbf{X}^{T}\mathbf{X})^{-1}\mathbf{X}^{T}\mathbf{y}
$$

但是，其他模型很難找到解析解，不好應用到深度學習中。

這邊我們說明一下：損失平面。就是損失函數關於權重的函數圖形，兩項權重對應的圖形就是三維空間中的碗型曲面。

## 隨機梯度下降

梯度下降最簡單的用法是，計算所有樣本當前的損失均值關於模型參數的梯度。但是，這樣會造成每次更新參數前我們都要遍歷整個數據集。

我們可以使用一個變體，稱為**小批量隨機梯度下降(minibatch stochastic gradient descent)**。

每次迭代我們選取固定數量 (通常是 $2$ 的冪) 的隨機樣本 $B$ (稱為**批量大小(batch size)**)，與一個預先確定的正數 $\eta$ (稱為**學習率(learning rate)**)，並作如下計算：

$$
\mathbf{w}\leftarrow \mathbf{w}- \frac{\eta}{|B|}\sum_{i\in B}\partial_{\mathbf{w}}l^{(i)}(\mathbf{w},b)
$$
$$
b\leftarrow b- \frac{\eta}{|B|}\sum_{i\in B}\partial_{b}l^{(i)}(\mathbf{w},b)
$$

注意到，梯度代表損失增加**最快**的方向，所以我們需要減掉梯度而非加上。

批量大小與學習率是預先確定好的，在訓練過程中不會更改，稱為**超參數(hyperparamater)**。修改這些超參數就稱為**調參(hyperparameter tuning)**。

找到一組參數，使得模型在未見過的數據上取得較低損失的行為，稱為**泛化(generalization)**。

# 正態分布與平方損失

這裡，我們通過假設噪聲 (實際值與預測值的偏差) 分布來解讀平方損失函數。

我們得先知道**正態分布(normal distribution)**：若隨機變量 $x$ 有均值 $\mu$ 與方差 $\sigma^{2}$ (標準差 $\sigma$)，則**正態分布概率密度函數**如下：

$$
p(x)=\frac{1}{\sqrt{ 2\pi\sigma^{2} }}\text{exp}\left( -\frac{1}{2\sigma^{2}}(x-\mu)^{2} \right)
$$

![[Deep Learning/pic/Linear Neural Network/Linear Regression/1.png]]

根據圖形可知：
- 均值影響圖形的水平偏移。
- 標準差影響圖形的峰值。

均方誤差損失可以用在線性回歸的原因是，我們假設噪聲符合正態分布。也就是說：

$$
y=\mathbf{w}^{T}\mathbf{x}+b+\epsilon\quad\epsilon\in N(0, \sigma^{2})
$$

也就是說，給定輸入 $\mathbf{x}$，輸出 $y$ 符合均值為 $\mathbf{w}^{T}\mathbf{x}+b$ 且方差為 $\epsilon$ 的正態分布。

那麼，給定 $\mathbf{x}$，觀測到特定的輸出 $y$ 的條件概率密度 (**似然(likelihood)**) 如下：

$$
P(y \ | \ \mathbf{x})=\frac{1}{\sqrt{ 2\pi\sigma^{2} }}\text{exp}\left( -\frac{1}{2\sigma^{2}}(y-\mathbf{w}^{T}\mathbf{x}-b)^{2} \right)
$$

因為數據集中各樣本互相獨立並且同分布 (所有數據都由同一個機制生成)，所以整個數據集出現的機率為：

$$
P(\mathbf{y} \ | \ \mathbf{x})=\prod_{i=1}^{n}p(y^{(i)} \ | \ \mathbf{x}^{(i)})
$$

而我們訓練模型，就想要找到參數 $\mathbf{w}$ 與 $b$ 使得此機率最大。

由於歷史原因，通常我們的優化過程是最小化而非最大化。而且，想計算乘積並不容易，我們取 $-\log$。

$$
-\log P(\mathbf{y} \ | \ \mathbf{x})=\sum_{i=1}^{n} \frac{1}{2}\log(2\pi\sigma^{2})+ \frac{1}{2\sigma^{2}}(y^{(i)}-\mathbf{w}^{T}\mathbf{x}^{(i)}-b)^{2}
$$

因為第一項不依賴 $\mathbf{w}$ 與 $b$ ，我們只需要假設 $\sigma$ 為某常數就可以忽略之。第二項除了 $\frac{1}{2}\sigma^{2}$ 就與均方誤差相同，這也是為啥最小化均方誤差就等於對線性模型的極大似然估計。

# 從線性回歸到深度網絡

![[Deep Learning/pic/Linear Neural Network/Linear Regression/2.png]]

線性回歸可以描述為上圖的神經網絡。

其中，輸入層的輸入數(或稱**特徵維度(feature dimensionality)**) 為 $d$。

因為模型重點在發生計算的地方，通常我們計算層數時會忽略輸入層。也就是說，上圖的層數為 $1$。

對於線性回歸，每個輸入都與每個輸出相連，我們稱為**全連接層(fully-connected layer)** 或**稠密層(dense layer)**。