# 分布偏移的類型

## 協變量偏移

**協變量偏移(covariate shift)**：輸入的分布改變，但標籤函數 $P(y \ | \ \mathbf{x})$ 沒有改變。

例如：本來訓練集是寫實風的貓狗判斷，但測試集改用動畫風的貓狗要求預測。

## 標籤偏移

**標籤偏移(label shift)**：假設標籤發生概率 $P(y)$ 可以改變，但是類別條件分布 $P(\mathbf{x} \ | \ y)$ 沒有改變。這種情況多發生在 $y$ 導致 $\mathbf{x}$ 發生時。

例如：症狀 ($\mathbf{x}$) 對應疾病 ($y$)。當訓練集中發病的樣本只有 $30\%$，而測試集中發病的樣本有 $70\%$ 時，雖然疾病對應的症狀沒有改變，但是模型更傾向於將有病者判斷為無病。

## 概念偏移

**概念偏移(concept shift)**：當標籤的定義發生變化時，就發生概念偏移。

# 分布偏移糾正

## 經驗風險與實際風險

回憶訓練模型的過程，我們使用損失函數來度量預測值與實際標籤的差距。我們將此稱為**經驗風險(empirical risk)**。

而**實際風險(true risk)** 則是實際分布 $p(\mathbf{x},y)$ 中所有數據的總體損失期望值：

$$
E_{p}[l(f(\mathbf{x}),y)]=\int \int l(f(\mathbf{x}),y)p(\mathbf{x},y) \ d\mathbf{x} \ \ dy
$$

因為我們無法獲得總數據，所以訓練模型中我們最小化經驗風險，希望可以近似實際風險。

## 協變量偏移糾正

假設我們要評估 $P(y \ | \ \mathbf{x})$，但是觀測值 $\mathbf{x}_{i}$ 是從某些源分布 $q(\mathbf{x})$ 中得出，而非目標分布 $p(\mathbf{x})$。

但是，因為依賴性假設，條件機率保持不變：$p(y \ | \ \mathbf{x})=q(y\ | \ \mathbf{x})$。

如果 $q(\mathbf{x})$ 是有偏移的，我們可以使用以下恆等式進行修正：

$$
\int \int l(f(\mathbf{x}),y)p(y \ | \ \mathbf{x})p(\mathbf{x}) \ d\mathbf{x} \ dy=\int \int l(f(\mathbf{x}), y)q(y \ | \ \mathbf{x})q(\mathbf{x}) \frac{p(\mathbf{x})}{q(\mathbf{x})} \ d\mathbf{x} \ dy
$$

也就是說我們使用：數據來自正確分布與來自錯誤分布的機率之比，來重新衡量每個數據的權重：

$$
\beta_{i}\equiv \frac{p(\mathbf{x}_{i})}{q(\mathbf{x}_{i})}
$$

將此權重帶回數據樣本，我們使用**加權風險經驗最小化**來訓練模型：

$$
\text{minimize} \frac{1}{n}\sum_{i=1}^{n}\beta_{i}l(f(\mathbf{x}_{i}),y_{i})
$$

因為我們不知道該比率，所以必須估計它。

注意到，我們需要訪問真實數據的特徵 $\mathbf{x}$，但不須訪問其標籤 $y$。這有效防止了模型因為洩漏測試集而過擬合的狀況。

此情況下，訓練一個對數機率回歸 (logistic regression) (softmax 的二元分類特例) 來預測樣本是來自哪個分布，可以有效幫助預估此權重。

假設我們用 $z$ 標籤表示：從 $p$ 中抽取的數據 $z=1$，$q$ 的話 $z=-1$。

如果我們使用對數機率回歸，其中 $P(z=1 \ | \ \mathbf{x})=\frac{1}{1+\text{exp}(-h(\mathbf{x}))}$ (二元分類套用 sigmoid 輸出 0 ~ 1 的機率)，則自然地有：

$$
\beta_{i}= \frac{\frac{1}{1+\text{exp}(-h(\mathbf{x}_i))}}{\frac{\text{exp}(-h(\mathbf{x}_{i}))}{1+\text{exp}(-h(\mathbf{x}_{i}))}}=\text{exp}(h(\mathbf{x}_{i}))
$$

現在我們回顧一次協變量糾正算法。假設我們有訓練集 $\{(\mathbf{x}_{1},y_{1}),\dots,(\mathbf{x}_{n},y_{n})\}$ 和一個未標記測試集 $\{\mathbf{u}_{1},\dots,\mathbf{u}_{m}\}$，其中 $\mathbf{x}_{i}$ 來自某源分布，$\mathbf{u}_{i}$ 來自目標分布。
1. 生成一個二元訓練集：$\{(\mathbf{x}_{1},-1),\dots,(\mathbf{x}_{n},-1),(\mathbf{u}_{1},1),\dots,(\mathbf{u}_{m},1)\}$。
2. 用對數機率回歸訓練二元分類器得到函數 $h$。
3. 使用 $\beta_{i}=\text{exp}(h(\mathbf{x}_{i}))$ 或更好的 $\text{min}(\text{exp}(h(\mathbf{x}_{i}),c))$ ($c$ 為常數，可避免權重過高) 對訓練數據加權。
4. 使用權重進行加權經驗風險最小化對 $\{(\mathbf{x}_{1},y_{1}),\dots,(\mathbf{x}_{n},y_{n})\}$ 進行訓練。

注意，上述算法需要目標分布中的**每個**數據樣本在訓練時出現的機率非零。如果有 $p(\mathbf{x})>0$ 但是 $q(\mathbf{x})=0$ 的情況出現，則對應的重要性權重會是無窮大。

## 標籤偏移糾正

假設我們處理的是 $k$ 個類別的分類任務，標籤分布 $q(\mathbf{y})\neq p(\mathbf{y})$，但 $q(\mathbf{x} \ | \ y)=p(\mathbf{x} \ | \ y)$。

我們根據以下恆等式，有：

$$
\int \int l(f(\mathbf{x}),y)p(\mathbf{x} \ | \ y)p(y) \ d\mathbf{x} \ dy=\int \int l(f(\mathbf{x}),y)q(\mathbf{x} \ | \ y)q(y) \frac{p(y)}{q(y)} \ d\mathbf{x} \ dy
$$

並定義重要性權重對應標籤似然比：

$$
\beta_{i}\equiv \frac{p(y)}{q(y)}
$$

為了估計目標標籤分布 $p(y)$，我們先基於訓練集訓練一個分類器，並使用驗證集計算混淆矩陣。

混淆矩陣 $C$ 是一個 $k\times k$ 矩陣，每列對應真實標籤，每行對應預測標籤。那麼 $c_{ij}$ 代表驗證集中，真實標籤為 $j$ 但我們錯誤預測為 $i$ 的樣本數量比例。

並且，我們通過計算模型預測輸出的平均值，得到 $\mu(\mathbf{\hat{y}})\in \mathbb{R}^{k}$，其中 $\mu(\hat{y}_{i})$ 是預測 $i$ 的總預測比例。

因為我們無法得知 $p(y)$，若我們的分類器十分準確，可以通過求解以下方程得到：

$$
Cp(\mathbf{y})=\mu(\mathbf{\hat{y}})
$$

只要分類器足夠準確，則 $C$ 必定可逆。

回憶 $C$ 中每行代表的是一個預測分類標籤，若分類器足夠準確則必須是行滿秩的。

直接通過 $p(\mathbf{y})=C^{-1}\mu(\mathbf{\hat{y}})$，並帶入已知的 $q(y)$，就可求得 $\beta_{i}$，然後使用先前提過的加權經驗風險最小化訓練模型即可。