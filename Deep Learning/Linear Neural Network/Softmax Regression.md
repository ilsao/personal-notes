# 網絡架構

softmax 回歸通常用來解決分類問題。

因為要分類，所以我們會有多個輸出。而，我們需要有與輸出數量相同的仿射變換。

如果我們有 $4$ 個輸入與 $3$ 個輸出，我們會需要 $12$ 個標量表示權重，$3$ 個標量表示偏移。

$$
\begin{align}
 & o_{1}=x_{1}w_{11}+x_{2}w_{12}+x_{3}w_{13}+x_{4}w_{14}+b_{1} \\
 & o_{2}=x_{1}w_{21}+x_{2}w_{22}+x_{3}w_{23}+x_{4}w_{24}+b_{2} \\
 & o_{3}=x_{1}w_{31}+x_{2}w_{32}+x_{3}w_{33}+x_{4}w_{34}+b_{3}
\end{align}
$$

或寫成：

$$
\mathbf{o}=\mathbf{W}\mathbf{x}+\mathbf{b}
$$

其中，$\mathbf{W}$ 是一個 $3\times4$ 的矩陣。

![[Deep Learning/pic/Linear Neural Network/Softmax Regression/1.png]]

注意到，softmax 的輸出層也是全連接層。

# Softmax 運算

我們應該設置一個閾值，當某類別的預測結果超過該值，我們就認定輸入屬於該類別。

我們不能直接將輸出視為概率，因為輸出不保證非負，也不保證總和為 $1$。

而且，我們還需要對模型**校準(calibration)**，保證輸出的機率符合實際分布：
- 完美校準：預測與實際出現機率相同。
- 欠校準：預測比實際出現機率大，模型過為自信。
- 過校準：預測比實際出現機率小，模型過為不自信。

我們使用 Softmax 函數將輸出轉化為機率：

$$
\mathbf{\hat{y}}=\text{softmax}(\mathbf{o})\quad \hat{y}_{j}= \frac{\text{exp}(o_{j})}{\sum_{k}\text{exp}(o_{k})}
$$

Softmax 通過取 $e$ 的冪保證非負，又通過當前值 / 總值保證總和為 $1$。

因為 Softmax 不會改變輸出的次序，所以以下關係仍保持：

$$
\text{argmax}_{j}\hat{y}_{j}=\text{argmax}_{j}o_{j}
$$

就算 Softmax 不是一個線性函數，但是 Softmax 回歸仍由輸入的仿射變換決定輸出，所以依舊屬於線性模型的範疇。

# 小批量樣本的矢量化

為了充分利用 GPU，我們對小批量樣本數據進行矢量計算。

假設我們讀取一個批量的樣本 $\mathbf{X}$，特徵維度 (輸入數量) 為 $d$，批量大小為 $n$，並且輸出為 $q$ 個類別。那麼小批量的特徵 $\mathbf{X}\in\mathbb{R}^{n\times d}$，權重 $\mathbf{W}\in\mathbb{R}^{d\times q}$，偏移 $\mathbf{b}\in\mathbb{R}^{1\times q}$。

Softmax 回歸的矢量表達式為：

$$
\mathbf{O}=\mathbf{X}\mathbf{W}+\mathbf{b}
$$
$$
\mathbf{\hat{Y}}=\text{softmax}(\mathbf{O})
$$

其中，小批量的未規範化預測 $\mathbf{O}$ 與輸出概率 $\mathbf{\hat{Y}}$ 大小都是 $n\times q$。

# 損失函數

## 對數似然

Softmax 函數給出一個向量 $\mathbf{\hat{y}}$，我們將其視為對給定任意輸入 $\mathbf{x}$ 的每個類別的條件機率。

假設整個數據集 $\{\mathbf{X},\mathbf{Y}\}$ 有 $n$ 個樣本，索引 $i$ 的樣本由特徵向量 $\mathbf{x}^{(i)}$ 與獨熱標籤 $\mathbf{\hat{y}}^{(i)}$ 組成：

$$
P(\mathbf{Y} \ | \ \mathbf{X})=\prod_{i=1}^{n}P(\mathbf{\hat{y}}^{(i)} \ | \ \mathbf{x}^{(i)})
$$

根據最大似然估計，最大化 $P(\mathbf{Y} \ | \ \mathbf{X})$ 就等於最小化負對數似然：

$$
-\log P(\mathbf{Y} \ | \ \mathbf{X})=\sum_{i=1}^{n}-\log P(\mathbf{\hat{y}}^{(i)} \ | \ \mathbf{x}^{(i)})=\sum_{i=1}^{n}l(\mathbf{y}^{(i)}, \mathbf{\hat{y}})
$$

其中，我們對實際值 $\mathbf{y}$ 與預測值 $\mathbf{\hat{y}}$ 定義損失函數：

$$
l(\mathbf{y},\mathbf{\hat{y}})=-\sum_{j=1}^{q}y_{j}\log \hat{y}_{j}
$$

因為實際值 $\mathbf{y}$ 是一個獨熱標籤，其中只有一項有值 $1$，其他項皆為零。所以，真實真實的損失函數其實是 $-\log \hat{y}_{p}$，其中 $p$ 是對應 $\mathbf{y}$ 為 $1$ 的索引。

這種損失函數稱為**交叉熵損失(cross-entropy loss)**。

## Softmax 及其導數

我們將 softmax 函數帶入損失函數中：

$$
\begin{align}
l(\mathbf{y},\mathbf{\hat{y}}) & =-\sum_{j=1}^{q}y_{j}\log \frac{\text{exp}(o_{j})}{\sum_{k=1}^{q}\text{exp}(o_{k})} \\
 & =\sum_{j=1}^{q}y_{j}\log \sum_{k=1}^{q}\text{exp}(o_{k})-\sum_{j=1}^{q}y_{j}o_{j} \\
 & =\log \sum_{k=1}^{q}\text{exp}(o_{k})-\sum_{j=1}^{q}y_{j}o_{j}
\end{align}
$$

考慮其對未規範化的輸出 $o_{j}$ 的導數，我們有：

$$
\begin{align}
\partial_{o_{j}}l(\mathbf{y},\mathbf{\hat{y}}) & = \frac{\text{exp}(o_{j})}{\sum_{k=1}^{q}\text{exp}(o_{k})}-y_{j}= \text{softmax}(o_{j})-y_{j}
\end{align}
$$

我們可以觀察到，導數是 softmax 函數分配的概率與實際發生情況之間的差值。也就是說，梯度就是預測值 $\hat{y}$ 與實際值 $y$ 的差異。

# 信息論基礎

## 熵

信息論的思想是量化數據中的信息，**熵(entropy)** 可以用來表示一個概率分布 $P$ 包含的平均信息量與不確定性。

熵的公式如下：

$$
H[P]=\sum_{j}-P(j)\log P(j)
$$

其中，$P(j)$ 表示事件 $j$ 發生的機率。而 $H[P]$ 的單位為**納特(nat)**，此時 $\log$ 的底數為 $e$。

如果 $\log$ 的底數為 $2$，則 $H[P]$ 的單位為比特。

## 信息量

如果我們可以非常容易預測到某事件的發生，那麼它發生時我們不會感到驚訝。

相反，如果某事件發生的機率非常小，它發生時我們則會感到非常驚訝。

信息量就是使用 $-\log P(j)$ 量化這種驚訝程度，在觀察事件 $j$ 時，我們會給定一個 (主觀) 機率 $P(j)$。當某事件發生機率越小，則信息量越大。

而我們上述所定義的熵，就是當分配的機率與實際發生的機率相同時，對信息量的期望值 (加權並求合) 。

## 重新審視交叉熵

我們把 $H[P]$ 當作：實際知道真實機率的人所經歷的驚訝程度。那麼，交叉熵從 $P$ 到 $Q$ 記為 $H[P,Q]$。此時交叉熵的含意是：主觀機率為 $Q$ 的觀察者，在經歷真實機率 $P$ 生成的數據時的驚訝程度。

交叉熵定義如下：

$$
H[P,Q]=\sum_{j}-P(j)\log Q(j)
$$

當 $Q=P$ 時，交叉熵達到最低，此時 $H[P,P]=H[P]$。

我們可以如下考慮交叉熵分類目標：
1. 最大化觀測數據的似然。
2. 最小化傳達標所需的驚訝程度。

# 模型預測和評估

在訓練 softmax 回歸後，我們通常使用預測概率最高者當作輸出類別。

我們使用**精度(accuracy)** 評估模型的性能，經度等於正確預測數 / 總預測數。