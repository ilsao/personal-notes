# Digital Systems

下圖展示一個計算機的抽象結構：

![[Pasted image 20260227195523.png]]

其中，Control unit 否則產生控制信號，控制 Datapath 處理數據。

# Binary Numbers

信號可以被分爲三類：

| 名稱                   | 時間採樣 | 信號值 |
| -------------------- | ---- | --- |
| Analogy signal       | 連續   | 連續  |
| Discrete-time signal | 離散   | 連續  |
| Digital signal       | 離散   | 離散  |

通常我們如下表達十進制數字：

$$
\dots a_{2}a_{1}a_{0}.a_{-1}a_{-2}\dots=\dots +a_{2}10^{2}+a_{1}10^{1}+a_{0}10^{0}+a_{-1}10^{-1}+a_{-2}10^{-2}+\dots
$$

其中小數點稱為 Decimal point。

對十進制來說，我們稱其基底為 $10$。

對於 base-r 系統，我們如下表示：

$$
a_{n}r^{n}+\dots+a_{1}r+a_{0}+a_{-1}r^{-1}+\dots+a_{-m}r^{-m}
$$

> [!warning] 注意
> 注意 $a_{j}$ 的範圍是 $0\sim r-1$，因為逢 $r$ 進 $1$。

有些特殊的值可以記記：
- $2^{10}$: Kilo, K
- $2^{20}$: Mega, M
- $2^{30}$: Giga, G
- $2^{40}$: Tera, T
- $2^{50}$: Peta, P

![[Pasted image 20260227202203.png]]

上圖展示一些簡單的二進制運算。

> [!warning] 注意
> 對 base-r 執行減法時，若係數 $a$ 處需借位，應使用 $r-a$。

# Number-Base Conversion

對於想從 10 進制轉成 base-r 進制，我們通過：
1. 用 $r$ 除以目標數
2. 紀錄餘數
3. 用 $r$ 除以商
4. 直到商為 $0$
5. **將餘數倒著寫** 

例如想將 $(153)_{10}$ 轉到 base-5，我們計算：
$\frac{153}{5}=30\dots3$ 
$\frac{30}{5}=6\dots0$ 
$\frac{6}{5}=1\dots 1$ 
$\frac{1}{5}=0\dots 1$ 
$\implies(153)_{10}=(1103)_{5}$ 

若想將 10 進制小數轉成 base-r 進制，通過：
1. 小數 $\times r$ 
2. 取整數部分
3. 剩下小數繼續 $\times r$ 
4. 直到剩下小數為 $0$ 
5. 將整數部分正著寫

例如想將 $(0.6758)_{10}$ 轉到 base-2：
$0.6758\times 2=1.375$ 
$0.375\times2=0.75$ 
$0.75\times2=1.5$ 
$0.5\times2=1.0$ 
$\implies(0.6758)_{10}=(1.011)_{2}$

想將二進制轉到八進制，我們將二進制數**每三個**數分組轉換。若想轉換到十六進制，則**每四個**數分組轉換。

# Complements

**補碼(complement)** 有兩種，一種是 radix complement，一種是 diminished radix complement。

對於一個 base-r 的且有 $n$ 位數字的數 $N$，其 radix complement 稱為 r's complement。

定義為 $r^{n}-N$ for $N\neq 0$，對於 $N=0$，r's complement 為 $0$。

至於 diminished radix complement，我們定義為 $(r^{n}-1)-N$。

> [!note]
> 注意到 radix complement + 1 = diminished radix complement。
> 這也是為什麼對 2's complement 來說，$-N=\ \sim N+1$。

若我們想計算 $n$ 位 $r$ 進位的 $M-N$，通過：
1. 計算 $M$ 加上 $N$ 的 r'complement。即 $M+(r^{n}-N)=M-N+r^{n}$。
2. 若 $M\geq N$，會產生一個進位 $r^{n}$ 稱為 end carry。將 end carry 捨棄後就是正確結果。
3. 若 $M<N$，不會產生 end carry 且結果會變為 $r^{n}-(N-M)$。可以看出這是 $N-M$ 的 r's complement。想得到正確的答案，我們只需對結果再取一次補碼並添上負號即可。

> [!warning] 注意
> 對於 1's complement，一但有進位到溢出，我們需要補 $1$ 在末尾。

# Signed Binary Numbers



# Binary Codes

# Binary Storage and Registers

# Binary Logic