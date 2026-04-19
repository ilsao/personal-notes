# Analysis Procedure

1. 將門電路以輸入變量表示並用任意符號 (symbol) 標記
2. 將後續門電路用上述符號標記
3. 重複操作並展開

![[Pasted image 20260416182841.png|573]]

![[Pasted image 20260416182900.png|467]]

# Design Procedure

1. state the problem
2. 決定輸入與輸出的數量，並標記符號
3. 寫出真值表
4. 計算輸入到輸出的最簡布爾表達
5. 畫出電路圖並評估對錯

需要考慮的限制：
- 門電路數量
- 門電路的輸入端口數
- propagation delay
- 連接數 (wire 的數量)
- 門電路的驅動能力

考慮實現一個從 BCD 轉 Excess-3 (BCD + 0011) 的電路實現：

![[Pasted image 20260416184912.png|505]]

化簡真值表：

![[Pasted image 20260416185003.png|577]]

![[Pasted image 20260416185049.png|438]]

解釋下為何 efficient implementation 電路實現上更優：
- $y$：通過一個 NOR 代替 AND + 2NOT
- $x$：提出兩個 $(C+D)$，使得可以共用結果。
- $w$：再次提出 $(C+D)$，與 $x$ 共用結果。

![[Pasted image 20260416185438.png|596]]

# 1-Bit Half Adder

不包含 Carry-in。只包含兩個 $1$ 位輸入 $x,y$，並輸出 Carry (C) 與 Sum (S)。

![[Pasted image 20260416192737.png|600]]

觀察易得：
- $C=xy=(x'+y')'$  
- $S=x\oplus y$ 又 $S'=xy+x'y$ 所以 $S=(C+x'y)'$ 

![[Pasted image 20260416193200.png|731]]

# 1-Bit Full Adder

包含 Cary-in，下面記做 $z$。

![[Pasted image 20260416193305.png|464]]

用 K-map 化減 (左：S，右：C)：

![[Pasted image 20260416193558.png|780]]

![[Pasted image 20260416193616.png|674]]

亦可繼續化減：

![[Pasted image 20260416193840.png|399]]

![[Pasted image 20260416193916.png|709]]

可以用 4 個 1-bit FA 組成一個 4-bit ripple adder：

![[Pasted image 20260416194202.png|639]]

# Carry Lookahead Adder

Ripple Adder 需要等前一位 Carry 計算出來後，才能得出當前位的 Carry。

我們使用 Carry Lookahead Adder 提前計算 Carry。

對於第 $i$ 個 FA，當 $A_{i}=B_{i}=1$ 時，必然會造成進位。稱其為 carry generated，記做 $G_{i}$。當 $A_{i}$ 或 $B_{i}$ 某一個為 $1$ (稱其為 carry propagated，記做 $P_{i}$。)，且 Carry in $C_{i}$ 為 $1$ 時，必然造成進位。

![[Pasted image 20260416194910.png|321]]

$G_{i}=A_{i}B_{i}$，$P_{i}=A_{i}\oplus B_{i}$，$S_{i}=P_{i}\oplus C_{i}$， $C_{i+1}=G_{i}+P_{i}C_{i}$ 

對 ripple adder 來說，$G_{i}$、$P_{i}$、$S_{i}$ 與 $C_{i}$ 都是 local functions。

對 carry lookahead adder 來說，我們想將 $C_{i}$ 改為一個較 global 的 function。

$C_{i+1}$ 可從各**位元單元(cell)** 中抽離：

$C_{1}=G_{0}+P_{0}C_{0}$ 

$C_{2}=G_{1}+P_{1}C_{1}=G_{1}+P_{1}(G_{0}+P_{0}C_{0})$ 
$=G_{1}+P_{1}G_{0}+P_{1}P_{0}C_{0}$ 

$C_{3}=G_{2}+P_{2}C_{2}=G_{2}+P_{2}(G_{1}+P_{1}G_{0}+P_{1}P_{0}C_{0})$ 
$=G_{2}+P_{2}G_{1}+P_{2}P_{1}G_{0}+P_{2}P_{1}P_{0}C_{0}$ 

$C_{4}=G_{3}+P_{3}C_{3}=G_{3}+P_{3}(G_{2}+P_{2}G_{1}+P_{2}P_{1}G_{0}+P_{2}P_{1}P_{0}C_{0})$ 
$=G_{3}+P_{3}G_{2}+P_{3}P_{2}G_{1}+P_{3}P_{2}P_{1}G_{0}+P_{3}P_{2}P_{1}P_{0}C_{0}$ 

![[Pasted image 20260416200951.png|635]]

於是 4-bit 的 FA 如下：

![[Pasted image 20260416201420.png|523]]

對比 ripple adder 與 carry lookahead adder 的結構區別：

![[Pasted image 20260416201827.png|837]]

理論上可以這樣重複下去，搭成一個支持更多位的 carry lookahead adder。但由於門電路的輸入端口數限制，我們不會這麼做。

我們通過連接多個 4-bit carry lookahead generator 來組成更多位的 carry lookahead generator。

我們記：

$G_{0-3}=G_{3}+P_{3}G_{2}+P_{3}P_{2}G_{1}+P_{3}P_{2}P_{1}G_{0}$ 

$P_{0-3}=P_{3}P_{2}P_{1}P_{0}$ 

$C_{4}=G_{0-3}+P_{0-3}C_{0}$ 

例如：用**五**個 (不是四個喔) 4-bit carry lookahead adder 搭建 16-bit carry lookahead adder。

![[Pasted image 20260416202436.png]]

# 4-Bit Adder / Subtracter

注意到我們使用補碼 ($x'+1$) 加法代替減法，只需加入一個控制位 (加法 / 減法) 即可。

![[Pasted image 20260416203902.png|805]]

其中，$V$ 用來檢測溢出。

當兩個正數相加得到負數，又或兩負數相加得到正數，即溢出。($A_{n-1}$ 與 $B_{n-1}$ 為輸入數的符號位，$S_{n-1}$ 為輸出數的符號位)

| $A_{n-1}$ | $B_{n-1}$ | $C_{n-1}$ |     | $C_n$ | $S_{n-1}$ | overflow? |
| --------- | --------- | --------- | --- | ----- | --------- | --------- |
| 0         | 0         | 0         |     | 0     | 0         | X         |
| 0         | 1         | 0         |     | 0     | 1         | X         |
| 1         | 0         | 0         |     | 0     | 1         | X         |
| 1         | 1         | 0         |     | 1     | 0         | O         |
| 0         | 0         | 1         |     | 0     | 1         | O         |
| 0         | 1         | 1         |     | 1     | 0         | X         |
| 1         | 0         | 1         |     | 1     | 0         | X         |
| 1         | 1         | 1         |     | 1     | 1         | X         |

我們透過符號位的真值表得出：$V=C_{n-1}\oplus C_{n}$。

# BCD Adder

BCD Adder 會有：
- 9 位輸入：兩個 4 位 BCD + 一個 carry-in
- 5 位輸出：一個 4 位 BCD + 一個 carry-out

因為輸入不會大於 9，所以輸出最多為：$9 + 9 + 1 = 19$ 其中 $1$ 代表 carry-in。

當輸出大於 $9$ 時，令 $C=1$，且輸出 $+6$。

![[Pasted image 20260416213007.png|606]]

觀察出：$C=K+Z_{8}Z_{4}+Z_{8}Z_{2}$，其中 $K$ 為 Binary Sum 的 carry-out。

![[Pasted image 20260416213210.png|551]]

注意到，上方的加法器用來實際執行兩數相加，而下方的加法器用來執行可能的 $+6$ 操作。

# Binary Multiplier

![[Pasted image 20260416213438.png|305]]![[Pasted image 20260416213452.png|389]]

## 4-Bit By 3-Bit Binary Multiplier

![[Pasted image 20260416213714.png|514]]

# Magnitude Comparator

想得到：$A>B$ $A=B$ $A<B$ 的輸出。

若用真值表列，因為 $A$ 與 $B$ 個 $n$ 位輸入，所以有 $2^{n+n}=2^{2n}$ 個項。對較大的 $n$，比較麻煩。

我們採取一個個比較的方法：

若：$A=A_{3}A_{2}A_{1}A_{0}$、$B=B_{3}B_{2}B_{1}B_{0}$，則：

$(A=B)=A\text{ XNOR }B=(AB'+A'B)'=x_{3}x_{2}x_{1}x_{0}$ 

$(A>B)=A_{3}B_{3}'+x_{3}A_{2}B_{2}'+x_{3}x_{2}A_{1}B_{1}'+x_{3}x_{2}x_{1}A_{0}B_{0}'$ 

$(A<B)=A_{3}'B_{3}+x_{3}A_{2}'B_{2}+x_{3}x_{2}A_{1}'B_{1}+x_{3}x_{2}x_{1}A_{0}'B_{0}$ 

![[Pasted image 20260416214539.png|561]]

# Decoder

此指 one-hot decoder：

![[Pasted image 20260416214927.png|637]]

用 AND 硬搭：

![[Pasted image 20260416215004.png|448]]

## Decode with Enable / Demultiplexer

這邊可想成，當 $E=1$ 時，所有皆 $1$。否則，由 decoder 決定哪位為 $0$。

![[Pasted image 20260416215443.png|345]]

![[Pasted image 20260416215508.png|523]]

![[Pasted image 20260416215932.png|805]]

這邊 Demultiplexer 會用 $A,B$ 控制哪個位要被置 $E$，其他置 $0$。

## $4\times 16$ Decoder

用兩個 $3\times 8$ 解碼器搭：

![[Pasted image 20260416220153.png|658]]

## Combinational Logic Implementation

因為解碼器的每個輸出都可視為一個 minterm，我們可以用它來實現真值表。

例如實現 FA。

![[Pasted image 20260416193305.png|338]]

$S(x,y,z)=\sum(1,2,4,7)$ 

$C(x,y,z)=\sum(3,5,6,7)$ 

![[Pasted image 20260416220453.png|616]]

# Encoder

![[Pasted image 20260416220534.png|639]]

用 OR 硬搭：

![[Pasted image 20260416220630.png|596]]

但如果輸入的不是合法的 one-hot，可能導致輸出錯誤。

## Priority Encoder

只編碼最高位，避免了不合法的 one-hot。

![[Pasted image 20260416220813.png|558]]

其中 valid bit 代表輸出的有效性。

注意到，這邊輸出的 don't care 才是寫在 k-map 裡面的 x。而輸入的 don't care 會被想成該位不影響 minterm。

![[Pasted image 20260416221426.png|653]]

![[Pasted image 20260416221514.png|616]]

# Multiplexer

$2\times 1$ MUX：

![[Pasted image 20260416221620.png|467]]![[Pasted image 20260416221631.png|357]]

$4\times 1$ MUX：

![[Pasted image 20260416221757.png|739]]

## Boolean Function Implementation Using MUX

MUX 可視為一個 Decoder 與 OR 的組合。

$2^{n-1}\times 1$ MUX 可實現任何 $n$ 輸入的布爾函數。

Procedure：
1. 將最後一個變量 (現令 $D$) 當作輸入，其他變量當作選擇
2. 將所有 minterm 兩兩一組看，因為這樣他們只會差在最後一位
3. 決定輸出是 $D,D',0,1$ 中的哪個
4. 用 $D,D',0,1$ 當作輸入

例如，實現 $F(x,y,z)=\sum(1,2,6,7)$。

![[Pasted image 20260417133703.png|298]]![[Pasted image 20260417133810.png|355]]

又或者 $F(A,B,C,D)=\sum(1,3,4,11,12,13,14,15)$ 

![[Pasted image 20260417134031.png|756]]

# Three-State Gate

![[Pasted image 20260417134246.png]]

其中，**高抗阻(high-impedance)** 會表現得像這條線沒接上。

用來實現 MUX：

![[Pasted image 20260417134353.png|657]]

# 練習題

![[Pasted image 20260418121512.png]]

Sol:
![[Pasted image 20260418121533.png|91]]
$\text{Gray}=\text{Binary}\oplus (\text{Binary}\gg1)$ 
$w=A,x=A\oplus B,y=A\oplus B\oplus C,z=A\oplus B\oplus C\oplus D$ 
![[Pasted image 20260418122703.png|437]]

![[Pasted image 20260418123952.png]]

Sol:
![[Pasted image 20260418131255.png|290]]
注意到我們若使用公式計算 $V$，容易混淆。
我們直接用，計算後的值能否被 $4$ 位**補碼**表達即可。