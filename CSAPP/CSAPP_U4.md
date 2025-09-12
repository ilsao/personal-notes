
# Y86-64指令集體系結構

## Y86-64

這部分為書中作者定義的ISA，不做過多筆記，去翻書吧。

### 練習題

4.1

``` Y86-64
30 F3 0F 00 00 00 00 00 00 00
20 31
40 13 FD FF FF FF FF FF FF FF
60 31
70 0C 01 00 00 00 00 00 00
```

4.2

略好不好，都是查表浪費時間的題目。

4.3 ~ 4.6

略

4.7

表示執行`pushq %rsp`時執行的行為是壓入`%rsp`的原始值。

4.8

表示彈出`%rsp`的原始值。

# 邏輯設計和硬件控制語言HCL

## 邏輯門

邏輯門是數字電路的基本計算單元。`AND`用`&&`表示，`OR`用`||`表示，而`NOT`用`!`表示，不使用`&`、`|`和`~`表示則是因為邏輯門只對單個位的數進行操作，而不是整個字。

![[Pasted image 20250531232349.png]]

## 組合電路和HCL布爾表達式

**組合電路**：多個邏輯門組成一個網而構建成的計算塊 (computational block)

構建網的幾個限制：
* 邏輯門的輸入必須由下述輸出提供：
	1. 系統輸入 (主輸入)
	2. 存儲器單元輸出
	3. 邏輯門輸出
* 兩個或多個邏輯門的輸出不能連接在一起，否則它們可能會使線上的信號矛盾，導致不合法的電壓或電路故障。
* 網必須是無環的，否則會導致該網絡計算的函數有歧異。

![[Pasted image 20250531233352.png]]

上圖為一個組合電路的例子。接收兩個輸入`a`與`b`，若`a`與`b`都為`1`或`a`與`b`都為`0`則`eq`輸出`1`。 用HCL寫這個網的函數就是：

``` C
bool eq = (a && b) || (!a && !b);
```

需要注意我們不把上述代碼看成執行計算後將結果放入內存中某個位置，相反他只是給表達式一個名字。

![[Pasted image 20250531233959.png]]

上圖為**多路復用器 (multiplexor，MUX)** 。在這個單個位的多路復用器中，數據信號為`a`與`b`，控制信號是輸入位`s`。當`s`為`1`則輸出`a`，若`s`為`0`則輸出`b`。HCL表達式為：

``` C
bool out = (s && a) || (!s &&b);
```

HCL與C表達式的區別：
* 組合電路的輸出會持續響應輸出的變化。即輸入改變後，經過一定延遲輸出也會相應改變。相比之下C只會在程序執行過程中遇到時才會求值。
* C的邏輯表達式允許任意整數，`0`表示`FALSE`，其他值表示`TRUE`。而邏輯門只對`0`進行操作`1`。
* C的邏輯表達式可能只被部分求值，如果一個`AND`或`OR`操作的結果只用第一個參數求值就可以確定，那麼就不會對第二個參數求值了。而組合邏輯沒有這種規則。

### 練習題

4.9

``` C
bool xor = (a && !b) || (!a && b);
```

通常`xor`與`eq`是互補的，一個為`1`另一個就為`0`。

## 字級的組合電路和HCL整數表達式

![[Pasted image 20250531235531.png]]

上圖 (a) 執行字級計算的組合電路根據輸入字的各個位用邏輯門計算，測試`A`與`B`是否相等。這個電路由64個上文提到的Bit equal電路實現。

在HCL中，我們將所有字級的信號都聲明為`int`，不指定字的大小。這樣做是為了方便，但在全功能的硬建描述語言中，每個字都可以聲明為特定的位數。HCL允許比較字是否相等：

``` C
bool Eq = (A == B); // 此處A與B是int類型
```

![[Pasted image 20250601000751.png]]

上圖是字級的多路復用器電路，與上文介紹的類似，但是不是簡單的複製黏貼。它只對`s`執行一次`NOT`操作，然後在每個位處複用它以減少反相器或非門 (inverters) 的數量。

在HCL中，MUX用**情況表達式 (case expression)** 描述。 情況表達式的通用格是如下：

``` C
[
	select1 : expr1;
	select2 : expr2;
	.
	.
	.
	selectk : exprk;
]
```

每種情況$i$都有一個布爾表達式$select_{i}$和一個整數表達式$expr_{i}$。前者表明甚麼時候選擇這種情況，後者指明得到的值。

與C的`switch`不同，我們不要求不同的選擇表達式之間互斥。這種選擇表達式是順序求值的，且第一個為`1`者會被選中。字級多路復用器的HCL描述就是：

``` C
word Out = [
		s : A;
		1 : B;
];
```

因為上述代碼的第二個選擇表達式為`1`，所以前面沒有情況被選中就會選擇這種情況。這是HCL中一種指定默認情況的方法，幾乎所有情況表達式都以此結尾。

允許不互斥的選擇表達式使HCL變得更可讀，但實際的多路復用器信號必須互斥，因為它們要控制哪個輸入字應為輸出。要

![[Pasted image 20250601002456.png]]

上圖是一個四路復用器，使用`s1`與`s0`從`A、B、C、D`中選擇。我們把`s1`與`s2`當作一個兩位的二進制數。使用HCL表示這個電路：

``` C
word Out4 = [
		!s1 && !s0 : A;  # 00
		!s1 : B;         # 01
		!s0 : C;         # 10
		1 : D;           # 11
];
```

![[Pasted image 20250601003057.png]]

上圖實現尋找`A`、`B`與`C`最小值的功能。HCL如下：

``` C
word Min3 = [
		A <= B && A <= C : A;
		B <= A && B <= C : B;
		1: C;
];
```

![[Pasted image 20250601004639.png]]

上圖為**算數/邏輯單元 (ALU)**。有三個輸入，根據控制輸入的值，電路會對數據輸入進行不同的運算或邏輯操作。注意減法順序，是`B`減去`A`，這是為了與`subq`的參數順序一致。

### 練習題

4.10

所有Bit equal換成xor，最後的`AND`換成`OR`連接`NOT`。

4.11

``` C
word Min3 = [
		A <= B && A <= C : A;
		B <= C : B;
		1 : C;
];
```

4.12

``` C
word Mid3 = [
		A <= B && A >= C : A;
		A >= B && A <= C : A;
		B <= A && B >= C : B;
		B >= A && B <= C : B;
		1 : C;
];
```

## 集合關係

![[Pasted image 20250601193819.png]]

上圖的電路中利用信號`code`來控制輸出。根據`code`值，可以用相等測試來產生`s1`與`s0`。

``` C
bool s1 = code == 2 || code == 3;
bool s0 = code == 1 || code == 3;
```

另一種簡潔的表達方式為：

``` C
bool s1 = code in {2, 3};
bool s0 = code in {1, 3};
```

判斷集合關係的通用格式是：

$$iexpr \text{ in } \{ iexpr_{1} iexpr_{2}, \dots, iexpr_{k} \}$$
這裡被測試的值$iex pr$和待匹配的值$iex pr_{1} \sim iex pr_{k}$都是整數表達式。

## 存儲器和時鐘

時鐘：週期性記號，決定甚麼時候把新值加載到設備中。

**時鐘寄存器(簡稱寄存器)**：儲存單個位或字，由時鐘信號控制加載輸入值。

**隨機訪問存儲器(簡稱內存)**：
1. 虛擬內存
2. 寄存器文件：`%rax ~ %r15`

硬件寄存器：在硬件中，寄存器直接將他的輸入和輸出線連接到電路的其他部分。

![[Pasted image 20250608224431.png]]

上圖展示了一次寄存器操作。只要信號保持在低電位，寄存器的值就不會改變。當時鐘變成高電位時，輸入信號就會加載到寄存器中，直到下一次時鐘上升沿。

軟件寄存器：在機器級編程中，寄存器代表的是CPU中可循址的字，這裡的地址是寄存器的ID。

![[Pasted image 20250608224638.png]]

上圖為一個典型的寄存器文件架構。

寄存器文件中包含A、B兩個**讀端口**，和一個W**寫端口**。這樣一個**多端口**隨機訪問存儲器允許同時進行多個讀和寫操作。

當`srcA`被寫入一個寄存器地址，經過一段時間後，該寄存器中的值就會被保存到`valA`中。

向寄存器文件寫入值是由時鐘信號控制的，每次時鐘上升時，`valW`的值就會被寫入到`dstW`指向的寄存器中。

處理器有一個隨機訪問存儲器來存儲程序數據，如下圖所示。

![[Pasted image 20250608225306.png]]

藉由`write`的零與一控制讀、寫。藉由`error`的零與一控制是否發生錯誤。

# Y86-64的順序實現

此部分我們描述一個稱為SEQ(sequential)的處理器，在每個時鐘週期上，SEQ執行處裡一條完整指令所需的所有步驟。

## 將處理組織成階段

* 取指(fetch)
	從內存中讀取指令字節。從指令中抽取出兩個部分，分別是`icode`(指令代碼)和`ifun`(指令功能)。還可能取出一個或兩個寄存器操作數指示符`rA`和`rB`。他還可能取出一個8字節常數`valC`。最後按順序方式計算當前指令的下一條指令的地址`valP`，即`valP`等於`PC + 已取出指令的長度`。
* 譯碼(decode)
	從寄存器文件中讀出兩個操作數，得到值`valA`或/和`valB`。
* 執行(excute)
	ALU執行指令指明的操作(根據`ifun`)，得到一個值`valE`。此時也可能設置條件碼。對條件傳送指令來說，此階段會檢驗條件碼和傳送條件，若成立則更新目標寄存器。同樣，對跳轉指令來說，此時會決定是否跳轉。
* 訪存(memory)
	將數據寫入內存或從內存中讀取值，讀取的值為`valM`。
* 寫回(write back)
	此階段最多可寫兩個結果到寄存器文件中，即E端口和M端口。分別用來儲存ALU的計算結果`valE`和從內存中讀取的值`valM`。
* 更新PC(PC update)

``` C
 1 0x000: 30f20900000000000000 |     irmovq $9, %rdx 
 2 0x00a: 30f31500000000000000 |     irmovq $21, %rbx 
 3 0x014: 6123                 |     subq %rdx, %rbx        # subtract 
 4 0x016: 30f48000000000000000 |     irmovq $128,%rsp       # Problem 4.13 
 5 0x020: 40436400000000000000 |     rmmovq %rsp, 100(%rbx) # store 
 6 0x02a: a02f                 |     pushq %rdx             # push 
 7 0x02c: b00f                 |     popq %rax              # Problem 4.14 
 8 0x02e: 734000000000000000   |     je done                # Not taken 
 9 0x037: 804100000000000000   |     call proc              # Problem 4.18 
10 0x040:                      | done: 
11 0x040: 00                   |     halt 
12 0x041:                      | proc: 
13 0x041: 90                   |     ret                    # Return
```

上述代碼為Y86-64指令序列示例，我們會跟蹤這些指令通過各個階段的處理。

| 階段   | `OPq rA, rB`                                                                                            | `rrmovq rA, rB`                                                                                         | `irmovq V, rB`                                                                                                                        |
| ---- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| 取指   | $icode: ifun$ $\leftarrow$ $M_{1}[PC]$<br>$rA: rB \leftarrow M_{1}[PC+1]$<br><br>$valP \leftarrow PC+2$ | $icode: ifun$ $\leftarrow$ $M_{1}[PC]$<br>$rA: rB \leftarrow M_{1}[PC+1]$<br><br>$valP \leftarrow PC+2$ | $icode: ifun$ $\leftarrow$ $M_{1}[PC]$<br>$rA: rB \leftarrow M_{1}[PC+1]$<br>$valC \leftarrow M_{8}[PC+2]$<br>$valP \leftarrow PC+10$ |
| 譯碼   | $valA \leftarrow R[rA]$<br>$valB \leftarrow R[rB]$                                                      | $valA \leftarrow R[rA]$                                                                                 |                                                                                                                                       |
| 執行   | $valE \leftarrow valB \ OP \ valA$<br>$Set \ CC$                                                        | $valE \leftarrow 0 + valA$                                                                              | $valE \leftarrow 0 + valC$                                                                                                            |
| 訪存   |                                                                                                         |                                                                                                         |                                                                                                                                       |
| 寫回   | $R[rB] \leftarrow valE$                                                                                 | $R[rB] \leftarrow valE$                                                                                 | $R[rB] \leftarrow valE$                                                                                                               |
| 更新PC | $PC \leftarrow valP$                                                                                    | $PC \leftarrow valP$                                                                                    | $PC \leftarrow valP$                                                                                                                  |

上表給出對`OPq`、`rrmovq`、`irmovq`類型指令所需要的處理。符號$M_{1}[x]$表示讀取`x`處1字節，$M_{8}[x]$表示讀取`x`處8字節。

注意：表達式`valB OP valA`的順序與Y86-64和x86-64的習慣是一樣的。

| 階段   | `OPq rA, rB`                                                                                            | `subq %rdx, %rbx`                                                                                                        |
| ---- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| 取指   | $icode: ifun$ $\leftarrow$ $M_{1}[PC]$<br>$rA: rB \leftarrow M_{1}[PC+1]$<br><br>$valP \leftarrow PC+2$ | $icode: ifun$ $\leftarrow$ $M_{1}[0x014] = 6:1$<br>$rA: rB \leftarrow M_{1}[0x015] = 2:3$<br><br>$valP \leftarrow 0x016$ |
| 譯碼   | $valA \leftarrow R[rA]$<br>$valB \leftarrow R[rB]$                                                      | $valA \leftarrow R[\%rdx]=9$<br>$valB \leftarrow R[\%rbx]=21$                                                            |
| 執行   | $valE \leftarrow valB \ OP \ valA$<br>$Set \ CC$                                                        | $valE \leftarrow 21-9=12$<br>$ZF \leftarrow 0，SF\leftarrow 0，OF\leftarrow 0$                                             |
| 訪存   |                                                                                                         |                                                                                                                          |
| 寫回   | $R[rB] \leftarrow valE$                                                                                 | $R[\%rbx] \leftarrow 12$                                                                                                 |
| 更新PC | $PC \leftarrow valP$                                                                                    | $PC \leftarrow 0x016$                                                                                                    |

上表跟蹤了`subq`的指令執行。

| 階段   | `pushq rA`                                                                                              | `popq rA`                                                                                               |
| ---- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| 取指   | $icode: ifun$ $\leftarrow$ $M_{1}[PC]$<br>$rA: rB \leftarrow M_{1}[PC+1]$<br><br>$valP \leftarrow PC+2$ | $icode: ifun$ $\leftarrow$ $M_{1}[PC]$<br>$rA: rB \leftarrow M_{1}[PC+1]$<br><br>$valP \leftarrow PC+2$ |
| 譯碼   | $valA \leftarrow R[rA]$<br>$valB \leftarrow R[\%rsp]$                                                   | $valA \leftarrow R[\%rsp]$<br>$valB \leftarrow R[\%rsp]$                                                |
| 執行   | $valE = valB - 8$                                                                                       | $valE = valB + 8$                                                                                       |
| 訪存   | $M_{8}[valE] \leftarrow valA$                                                                           | $valM = M_{8}[valA]$                                                                                    |
| 寫回   | $R[\%rsp] \leftarrow valE$                                                                              | $R[\%rsp] \leftarrow valE$<br>$R[rA] \leftarrow valM$                                                   |
| 更新PC | $PC \leftarrow valP$                                                                                    | $PC \leftarrow valP$                                                                                    |

上表給出`pushq`和`popq`指令的處理流程。

| 階段   | `jxx Dest`                                                                                            | `call Dest`                                                                                           | `ret`                                                                    |
| ---- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| 取指   | $icode: ifun$ $\leftarrow$ $M_{1}[PC]$<br><br>$valC \leftarrow M_{8}[PC+1]$<br>$valP \leftarrow PC+9$ | $icode: ifun$ $\leftarrow$ $M_{1}[PC]$<br><br>$valC \leftarrow M_{8}[PC+1]$<br>$valP \leftarrow PC+9$ | $icode: ifun$ $\leftarrow$ $M_{1}[PC]$<br><br><br>$valP \leftarrow PC+1$ |
| 譯碼   |                                                                                                       | <br>$valB \leftarrow M[\%rsp]$                                                                        | $valA \leftarrow M[\%rsp]$<br>$valB \leftarrow M[\%rsp]$                 |
| 執行   | <br>$Cnd \leftarrow Cond(CC, ifun)$                                                                   | $valE\leftarrow valB-8$                                                                               | $valE = valB + 8$                                                        |
| 訪存   |                                                                                                       | $M_{8}[valE]\leftarrow valP$                                                                          | $valM\leftarrow M_{8}[valA]$                                             |
| 寫回   |                                                                                                       | $R[\%rsp] \leftarrow valE$                                                                            | $M[\%rsp] \leftarrow valE$                                               |
| 更新PC | $PC\leftarrow Cnd ? valC : valP$                                                                      | $PC \leftarrow valC$                                                                                  | $PC \leftarrow valM$                                                     |

上表給出跳轉、`call`和`ret`的處理流程。

### 練習題

4.13

| 階段   | `irmovq V, rB`                                                                                                                        | `irmovq $128, %rsp`                                                                                                                                          |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 取指   | $icode: ifun$ $\leftarrow$ $M_{1}[PC]$<br>$rA: rB \leftarrow M_{1}[PC+1]$<br>$valC \leftarrow M_{8}[PC+2]$<br>$valP \leftarrow PC+10$ | $icode: ifun$ $\leftarrow$ $M_{1}[0x016] = 3:0$<br>$rA: rB \leftarrow M_{1}[0x017] = f:4$<br>$valC \leftarrow M_{8}[0x018] = 128$<br>$valP \leftarrow 0x020$ |
| 譯碼   |                                                                                                                                       |                                                                                                                                                              |
| 執行   | $valE \leftarrow 0 + valC$                                                                                                            | $valE \leftarrow 128$                                                                                                                                        |
| 訪存   |                                                                                                                                       |                                                                                                                                                              |
| 寫回   | $R[rB] \leftarrow valE$                                                                                                               | $R[\%rsp] = 128$                                                                                                                                             |
| 更新PC | $PC \leftarrow valP$                                                                                                                  | $PC \leftarrow 0x020$                                                                                                                                        |

4.14

略，查代碼就好，很簡單留給你們試試。

4.15

壓入原始`%rsp`值，與4.7中確認的一樣。

4.16

彈出原始`%rsp`值，與4.8中確認一樣。

4.17

| 階段   | `cmovXX rA, rB`                                                                                            |
| ---- | ---------------------------------------------------------------------------------------------------------- |
| 取指   | $icode: ifun$ $\leftarrow$ $M_{1}[PC]$<br>$rA: rB \leftarrow M_{1}[PC+1]$<br>$valC \leftarrow M_{8}[PC+2]$ |
| 譯碼   | $valA \leftarrow R[rA]$<br>$valB \leftarrow R[rB]$                                                         |
| 執行   | $valE \leftarrow 0+valA$<br>$Cnd \leftarrow Cond(C C, ifun)$                                               |
| 訪存   |                                                                                                            |
| 寫回   | <br>$R[rB] \leftarrow Cnd?valE:valB$                                                                       |
| 更新PC | $PC \leftarrow valP$                                                                                       |

4.18

略，查查看就知道了。

## SEQ硬件結構

![[Pasted image 20250611141326.png]]

上圖為SEQ的抽象視圖，下圖為完整的SEQ硬件結構。

![[Pasted image 20250611141344.png]]

* 白色方框表示時鐘寄存器。PC是SEQ中唯一的時鐘寄存器。
* 淺藍色方框表示硬件單元。
* 灰色圓角矩形表示控制邏輯塊，這些塊用來從一組信號源中進行選擇或者計算一些布爾函數。
* 白色圓圈標示路線名稱，非硬件單元。
* 最粗的線表示寬度為字長的數據，這種線每條代表一簇64根線，將一個字從硬件的一個部分傳遞到另一部份。
* 較細的線表示寬度為字節或更窄的數據，這種線每條表示一簇4根或8根線。
* 虛線表示單個位的連接，代表芯片上單元與塊之間傳遞的控制值。

## SEQ的時序

SEQ的實現包含組合邏輯和時鐘寄存器(程序計數器、條件碼寄存器)與隨機訪問存儲器(寄存器文件、數據內存)。

組合邏輯不須要任何時序控制，只要輸入變化了，值就通過邏輯門網絡傳播。

而剩下的存儲器設備我們需要對其時序進行明確的控制。

對於Y86-64，我們遵循以下原則：
	從不回讀。
	處理器從不需要為了執行一條指令而去讀由該指令更新了的狀態。

比如在我們的設計中，`pushq %rsp`會將`%rsp`的原值壓入棧頂。若我們壓入的是`%rsp+8`的話，代表為了執行該操作我們需要讀取寄存器文件中更新過的棧指針，這與我們的原則相悖。

我們使用以下代碼來跟蹤SEQ的運行週期。

``` C
0x000:     irmovq $0x100,%rbx     # %rbx <-- 0x100 
0x00a:     irmovq $0x200,%rdx     # %rdx <-- 0x200 
0x014:     addq %rdx,%rbx         # %rbx <-- 0x300 CC <-- 000 
0x016:     je dest                # Not taken 
0x01f:     rmmovq %rbx,0(%rdx)    # M[0x200] <-- 0x300 
0x029: dest: halt
```

![[Pasted image 20250611151546.png]]

1. 週期3開始時：狀態單元保持的是第二條`irmovq`指令更新過的狀態，該指令用淺灰色表示，而組合邏輯用白色表示，說明他還沒來的即對變化了的狀態做響應。時鐘週期開始時，`0x014`載入PC中，取出和處理`addq`指令。
2. 週期3結束時：值沿著邏輯電路流動。所有存儲器準備更新值。
3. 週期4開始時：更新PC。存儲器遇到時鐘上升沿，更新由周期3結束時提供的值。同時取出`je`並處理。
4. 週期4結束時：組合邏輯根據`je`指令更新，PC待更新的值也計算結束。但所有存儲器保持原值，等待下個時鐘上升沿(下個週期)後更新。

## SEQ階段的實現

下表事先列出我們常用的常數值。

| 名稱        | 值(hex) | 含意             |
| --------- | ------ | -------------- |
| `IHALT`   | 0      | `halt`指令的偽代碼   |
| `INOP`    | 1      | `nop`指令的偽代碼    |
| `IRRMOVQ` | 2      | `rrmovq`指令的偽代碼 |
| `IIRMOVQ` | 3      | `irmovq`指令的偽代碼 |
| `IRMMOVQ` | 4      | `rmmovq`指令的偽代碼 |
| `IMRMOVQ` | 5      | `mrmovq`指令的偽代碼 |
| `IOPQ`    | 6      | 整數運算指令的代碼      |
| `IJXX`    | 7      | 跳轉指令的代碼        |
| `ICALL`   | 8      | `call`指令的代碼    |
| `IRET`    | 9      | `ret`指令的代碼     |
| `IPUSHQ`  | A      | `pupshq`指令的代碼  |
| `IPOPQ`   | B      | `popq`指令的代碼    |
| `FNONE`   | 0      | 默認功能碼          |
| `RRSP`    | 4      | `%rsp`的寄存器ID   |
| `RNONE`   | F      | 表明沒有寄存器文件訪問    |
| `ALUADD`  | 0      | 加法運算的功能        |
| `SAOK`    | 1      | 正常操作狀態碼        |
| `SADR`    | 2      | 地址異常狀態碼        |
| `SINS`    | 3      | 非法指令異常狀態碼      |
| `SHLT`    | 4      | `halt`狀態碼      |

### 取指階段

![[Pasted image 20250624162315.png]]

此階段會從以PC(字節0)開始處讀取10個字節。第一個字節被解釋為指令字節，(標為`Split`的單元)分為兩個4位數。

我們可以計算三個一位的信號：
* `instr_valid`：該字節是否是合法的指令
* `need_regids`：該指令是否需要寄存器
* `need_valC`：該指令是否需要常數參數

由此我們可以設計`need_regids`的HCL描述：

``` C
bool need_regids = icode in {
	IRRMOVQ, IOPQ, IPUSHQ, IPOPQ, IIRMOVQ, IRMMOVQ, IMRMOVQ
};
```

`need_valC`的HCL描述：

``` C
bool need_valC = icode in {
	IIRMOVQ, IRMMOVQ, IMRMOVQ, IJXX, ICALL
};
```

標號為`Align`的單元會處理剩下的9個字節。當`need_regids`為1時，字節1被分開裝入`rA`與`rB`中。否則這兩個字段被設為`0xF`(`RNONE`)。根據信號`need_regids`與`need_valC`的值，要麼根據字節$1\sim 8$來產生`valC`，要麼根據字節$2\sim 9$來產生。

`PC_increment`單元根據當前PC與`need_regids`和`need_valC`產生`valP`。

$$
\text{valP = }pc + \text{need\_regids} + 8\times\text{need\_valC}
$$

### 譯碼和寫回階段

![[Pasted image 20250624165518.png]]

對於`valA`與`valB`的產生規則，我們需要參考前述表格的"譯碼"階段。

``` C
word srcA = [
	icode in { IRRMOVQ, IRMMOVQ, IOPQ, IPUSHQ } : rA;
	icode in { IPOPQ, IRET } : RRSP;
	1 : RNONE; // Don't need register
];
```

``` C
word srcB = [
	icode in { IRMMOVQ, IMRMOVQ, IOPQ } : rB; 
	// We don't need IRRMOVQ and IIRMOVQ here, because in these two command we only use rB as              destination instead of calculate valB
	icode in { IPUSHQ, IPOPQ, ICALL, IRET } : RRSP;
	1 : RNONE; 
];
```

`dstE`表明寫端口E的目的寄存器，計算出來的`valE`存放在此處。

下方處理`dstE`的代碼暫時忽略條件移動指令。我們查看執行階段時，會重新審視這個信號，正確實現條件傳送。

``` C
// Warning: Conditional move not implemented correctly here
word dstE = [
	icode in { IRRMOVQ } : rB;
	icode in { IIRMOVQ, IOPQ } : rB;
	icode in { IPUSHQ, IPOPQ, ICALL, IRET } : RRSP;
	1 : RNONE;
];
```

`dstM`表明寫端口M的目的寄存器，從內存中讀出的`valM`會放在此處。

``` C
word dstM = [
	icode in { IMRMOVQ, IPOPQ } : rA;
	1 : RNONE;
];
```

#### 練習題

4.22

`M`優先度更高 (輸出原始值)

### 執行階段

![[Pasted image 20250624185833.png]]

ALU單元根據`alufun`信號設置，對輸入`aluA`和`aluB`執行運算。

在計算中`aluB`在前，`aluA`在後。這樣可以保證`subq`指令是`valB`減去`valA`。

``` C
word aluA = [
	icode in { IRRMOVQ, IOPQ } : valA;
	icode in { IIRMOVQ, IRMMOVQ, IMRMOVQ } : valC;
	icode in { ICALL, IPUSHQ } : -8;
	icode in { IRET, IPOPQ } : 8;
];
```

``` C
word aluB = [
	icode in { IOPQ } : valB;
	icode in { IRMMOVQ, IMRMOVQ } : valB;
	icode in { ICALL, IPUSHQ } : valB;
	icode in { IRET, IPOPQ } : valB;
	icode in { IRRMOVQ, IIRMOVQ } : 0;
];
```

通常ALU在執行階段做加法器使用，不過，對於`OPq`指令，我們希望他使用指令`ifun`字段中編碼的操作。

``` C
word alufun = [
	icode == IOPQ : ifun;
	1 : ALUADD;
];
```

執行階段還包含條件碼寄存器，在執行`OPq`時設置條件碼。

``` C
bool set_cc = icode in { IOPQ };
```

標號為`cond`的硬件單元會根據條件碼和功能碼來確定是否進行條件分支或者條件數據傳輸。他產生信號`Cnd`，用於設置`dstE`或下一個PC。

``` C
word dstE = [
	icode in { IRRMOVQ } && Cnd : rB;
	icode in { IIRMOVQ, IOPQ } : rB;
	icode in { IPUSHQ, IPOPQ, ICALL, IRET } : RRSP;
	1 : RNONE;
];
```

### 訪存階段

![[Pasted image 20250624220702.png]]

此階段讀或寫程序數據到內存中。兩個控制塊產生內存地址和內存輸入數據(為寫操作)，另外兩個塊產生控制該執行讀還是寫操作的控制信號。當執行讀操作時，數據內存產生值`valM`。

`mem_addr`為(讀寫)操作的目標地址，`mem_data`為(讀寫)操作的數據。

``` C
word mem_addr = [
	icode in { IRMMOVQ, IPUSHQ, ICALL, IMRMOVQ } : valE;
	icode in { IPOPQ, IRET } : valA;
];
```

``` C
word mem_data = [
	icode in { IRMMOVQ, IPUSHQ } : valA;
	icode == ICALL : valP
];
```

``` C
bool mem_read = icode in { IMRMOVQ, IPOPQ, IRET };
```

``` C
bool mem_write = icode in { IRMMOVQ, IPUSHQ, ICALL };
```

``` C
word stat = [
	imem_error || dmem_error : SADR;
	!instr_valid : SINS;
	icode == IHALT : SHLT;
	1 : SAOK;
];
```

### 更新PC階段

![[Pasted image 20250624230446.png]]

``` C
word new_pc = [
	icode == ICALL : valC;
	icode = IJXX && Cnd : valC;
	icode == IRET : valM;
	1 : valP;
];
```

### SEQ小節

以上就是Y86-64處理器的一個完整設計。SEQ唯一的問題就是速度慢，時鐘必須非常慢才能讓信號在一個周期內傳播所有階段。此方法不能充分利用硬件單元，因為每個單元只在整個時鐘周期的一部份時間內才被使用。

# 流水線的通用原理

流水線化的系統中，待執行的任務被劃分成了若干個獨立的階段，允許多個階段同時運行。

流水線化的重要特性就是提高系統的**吞吐量(throughput)**，但也會輕微的增加**延遲(latency)**，就是一次完整流程所需的時間。

## 計算流水線

![[Pasted image 20250625160548.png]]

上圖為一個非流水線畫的硬件系統。圖b稱**流水線圖(pipeline diagram)**。在現代邏輯設計中，電路延遲以**微微秒**或**皮秒(picosecond, ps)**，也就是$10^{-12}$秒為單位計算。從頭到尾執行一條指令所需的時間稱**延遲(latency)**。

若組合邏輯需要300ps，加載寄存器需要20ps，則可以計算此系統的最大吞吐量：

$$
\text{throughput} = \frac{1s}{320ps}=3.125\times 10^{-9}s=3.125 \ GIPS
$$

![[Pasted image 20250625161122.png]]

上圖是一個三階段流水線化的計算硬件，個階段間的寄存器稱**流水線寄存器(pipeline register)**。

更改後的系統吞吐量大約為$8.33 \ GIPS$，代價是增加了一些硬件，以及延遲少量增加。

延遲變大由增加的流水線寄存器的時間開銷。

## 流水線操作的詳細說明

![[Pasted image 20250625162525.png]]

## 流水線的侷限性

1. 不一致的劃分
	在前面展示的系統中，每階段的延遲(100ps)一致。不過實際設計中，可能會出現每階段延遲不同的情況，而運行時鐘的速率是由最慢階段的延遲控制的，導致各階段出現長度不一的空閒。
![[Pasted image 20250625163034.png]]

2. 流水線過深，收益下降
	流水線的深度即階段個數，過深的流水線深度會增加通過流水線寄存器的延遲和。
	為提高時鐘平率，現代處理器採用很深的(15或更多階段)流水線。

### 練習題

4.28

A

CD間

B

BC間、DE間

C

AB間、CD間、DE間

D

五個階段

4.29

略

## 帶反饋的流水線系統

**數據相關(data dependency)**：之後的數據依賴於先前的數據。

**控制相關(control dependency)**：跳轉或`ret`指令導致下條指令的PC不確定。

# Y86-64的流水線實現

## SEQ+：重新安排計算階段

SEQ+就是將更新PC階段放在時鐘開始時執行的，更符合流水線設計的SEQ架構。

![[Pasted image 20250625174145.png]]

(a): SEQ，PC計算發生在時鐘周期結束的時候。根據當前時鐘周期內計算出的信號計算PC值。

(b): SEQ+，PC計算發生在時鐘周期開始時。我們需要創建狀態寄存器來保存**上一條**指令計算出的信號。當新的時鐘周期開始時，這些信號通過與SEQ同樣的邏輯計算PC。

![[Pasted image 20250625174535.png]]

上圖給出SEQ+硬件更為詳細的說明。PC邏輯從時鐘週期結束處移到時鐘週期開始處。

SEQ到SEQ+中對狀態單元的改進稱**電路重定時(circuit retiming)**。重定時改變了一個系統的狀態表示，但是不改變他的邏輯行為。通常用他來平衡一個流水線系統中各個階段間的延遲。

## 插入流水線寄存器

我們需要在SEQ+的各個階段間插入流水線寄存器，並對信號重新排列，得到新的PIPE$-$處理器。

![[Pasted image 20250626124749.png]]

上圖是PIPE$-$的抽象結構。流水線寄存器在圖中以黑色方框表示，每個寄存器包括不同字段，以白色方框表示。

流水寄存器如下標示：
	F:  Fetch
	D: Decode
	E:  Execute
	M: Memory
	W: Write back

## 對信號進行重新排列和標號

流水線化設計中，我們需要保存不同指令的同名信號。例如在PIPE$-$中我們需要保存4個Stat信號。

我們為信號的命名規則如下: 
	大寫流水線寄存器做前綴：流水線寄存器
	小寫流水線寄存器做前綴：在某階段剛被計算出來的信號
	M_stat: 流水線寄存器M的狀態碼字段
	m_stat: 訪存階段中由控制邏輯塊產生的狀態信號

我們注意到PIPE$-$中標號為Select A的塊，他會從流水線寄存器D的`valP`或寄存器文件A端口選擇一個。

這麼做是為了減少傳送給E和M的狀態數量。

因為只有`call`在訪存階段需要`valP`的值，只有跳轉在執行階段需要`valP`的值。而剛好這兩種指令不需要在寄存器文件中讀取值，所以我們可以合併此二信號。

## 預測下一個PC

流水線化設計希望每個周期都有一條新指令進入執行階段並完成，可惜的是，如果取出的指令是條件分支，需要等指令通過執行階段才能確定是否選擇分支。同樣，如果取出`ret`指令，則要等指令通過訪存階段才能確定返回地址。

對`call`和`jmp`來說，下一條指令的地址即常數字段`valC`。

通過預測PC的下一個值，多數情況下我們可以做到每個時鐘週期發射一條新指令。

猜測分支方向並取指的技術稱為**分支預測**。在此我們的策略是**總是選擇(always taken)**。其他還有**從不選擇(never taken, NT)**、**反向選擇，正向不選擇(backward taken, forward not-taken, BTFNT)**。

我們不預測`ret`的值，因為返回值幾乎是無限的。我們只是簡單的暫停處理新指令，直到`ret`通過寫回階段。

Select PC塊從三個值中選擇一個作為指令內存的地址：
1. 預測的PC。
2. 到達流水寄存器M且不選擇分支的指令->`valP`的值(儲存在`M_valA`中)。
3. `ret`到達流水寄存器W時`W_valM`的值。

## 流水線冒險

相鄰指令間會出現以下問題：
1. 數據相關
2. 控制相關

這些相關可能會導致一些問題，我們稱**冒險(hazard)**：
1. 數據冒險(data hazard)
2. 控制冒險(control hazard)

### 用暫停避免數據冒險

**暫停(stalling)** 是避免冒險的常用技術，暫停時，處理器會停止流水線中一條或多條指令，直到冒險條件不再被滿足。

讓一條指令停頓在譯碼階段，直到產生源操作數的指令通過寫回階段，這樣處理器就避免了一次冒險。

![[Pasted image 20250626173422.png]]

將`addq`阻塞在譯碼階段時，我們還需要將`halt`阻塞在取碼階段。

通過將PC保持不變就能做到，此時，會不斷對`halt`進行取指，直到暫停結束。

暫停技術可讓一組指令阻塞在所處的階段，但是允許其他指令繼續通過流水線。

在該指令本該執行的階段，我們插入**氣泡(bubble)**。氣泡就像`nop`，不會改變寄存器、內存、條件碼或程序狀態。

雖然這種機制容易實現，但是會導致流水線暫停三個周期，而且這種狀況十分常見，會嚴重降低吞吐量。

### 用轉發避免數據冒險

![[Pasted image 20250626224839.png]]

這裡我們關注週期6。此時，`0x016`處代碼需要將`%rax`的值作為`valB`，而`0x00a`處代碼正要將3寫回`%rax`。正常我們需要再等待一個週期(即下個時鐘上升沿使得寄存器被寫入)才能進行`0x016`處的譯碼階段。

這裡我們使用一個稱為**數據轉發(data forwarding, 或簡稱轉發，有時稱為旁路(bypassing))** 的技術，直接將`W_valE`傳送到`srcB`中，就能避免暫停。

![[Pasted image 20250626225554.png]]

同樣，我們還可以直接轉發執行階段中ALU剛計算出的值(`e_valE`)，如上圖所示。

綜上所述，我們其實有五個轉發源(`e_valE, m_valM, M_valE, W_valM, W_valE`)和兩個轉發目的(`valA, valB`)。

![[Pasted image 20250626230400.png]]

上圖是PIPE結構，為PIPE$-$的拓展。

`Sel+Fwd A`是`Select A`塊與轉發邏輯的結合，允許`E_valA`的值為`valP`、寄存器文件A讀出的值，或某個轉發過來的值。

`Fwd B`實現`valB`的轉發邏輯。

### 加載/使用數據冒險

![[Pasted image 20250627145233.png]]

如上圖所示，位於`0x028`與`0x032`發生的**加載/使用冒險(load/use hazard)** 無法單純的使用轉發來解決。

關注週期7與8，`0x028`的訪存發生在`0x032`譯碼階段後，無法使用轉發來解決問題(除非可以回到過去)。

![[Pasted image 20250627153423.png]]

如上圖所示，我們使用暫停與轉發結合，就避免了加載/使用冒險。

這種用暫停來處理加載/使用冒險的方法稱為**加載互鎖(load interlock)**。加載互鎖和轉發技術結合起來幾乎可以處理所有可能類型的數據冒險。

### 避免控制冒險

當處理器無法根據取指確定下條指令的地址時，就會出現控制冒險。在我們的流水線化處理器中，控制冒險只會發生在`ret`和跳轉指令中。而且，後一種狀態只有在條件跳轉方向預測錯誤時才會造成麻煩。

對於`ret`指令，考慮以下代碼：

``` C
0x000:     irmovq stack,%rsp   # Initialize stack pointer 
0x00a:     call proc           # Procedure call 
0x013:     irmovq $10,%rdx     # Return point 
0x01d:     halt 
0x020: .pos 0x20 
0x020: proc:                   # proc: 
0x020:     ret                 # Return immediately 
0x021:     rrmovq %rdx,%rbx    # Not executed 
0x030: .pos 0x30 
0x030: stack:                  # stack: Stack pointer
```

![[Pasted image 20250627161917.png]]

上圖給出我們希望流水線如何處理`ret`指令。我們要等待`ret`到達寫回階段才能知道下個PC，所以在流水線中插入三個氣泡。

要處理預測錯誤的分支，考慮以下代碼：

``` C
0x000:     xorq %rax,%rax 
0x002:     jne target         # Not taken 
0x00b:     irmovq $1, %rax    # Fall through 
0x015:     halt 
0x016: target: 
0x016:     irmovq $2, %rdx    # Target 
0x020:     irmovq $3, %rbx    # Target+1 
0x02a:     halt
```

![[Pasted image 20250627162551.png]]

如上圖所示，遇到條件跳轉我們都會選擇跳轉。當條件跳轉指令執行到執行階段時，我們就可以確定預測的結果是否正確。

在`prog7`狀況下，我們預測錯誤。幸好這時預測錯誤的兩條指令還沒有導致程序員可見狀態發生改變(只有運行到執行階段才會發生這種狀況)。

此時我們只需要在兩條指令後面插入氣泡，就能**取消(有時稱為指令排除(instruction squashing))** 預測錯誤的指令。唯一的缺點是浪費了兩個時鐘週期。

## 異常處理

我們的指令集體系結構包括三種異常：
1. `halt`指令
2. 非法指令或非法功能碼組合
3. 取指或數據讀寫試圖訪問一個非法地址

我們將導致異常的指令稱作**異常指令(excepting instruction)**。其中，在非法指令的情況中，沒有實際的異常指令。

異常處理包括以下三個細節：
1. 同時有多條指令引發異常
	由流水線中最深指令引發的異常優先級最高
2. 條件分支時預測的下一個PC處指令觸發異常，但分支預測錯誤
	取消該指令
3. 某指令觸發異常，其後的指令在異常指令完成前改變部分程序員可見狀態
	處於訪存或寫回階段的指令產生異常時，流水線控制邏輯需禁止更新條件碼寄存器或數據內存。

## PIPE各階段的實現

### PC選擇和取指階段

![[Pasted image 20250627211817.png]]

PC選擇邏輯從三個源中選擇：
1. 對分支預測錯誤的指令進入訪存階段時，從`M_valA`讀出該指令的`valP`。
2. 當`ret`指令進入寫回階段時，從`W_valM`讀出返回地址。
3. 使用`F_predPC`。

``` C
word f_pc = [
	M_icode == IJXX && !M_Cnd : M_valA;
	W_icode == IRET : W_valM;
	1 : F_predPC;
];
```

若為函數調用或跳轉，選擇`valC`，否則選擇`valP`。

``` C
word f_predPC = [
	f_icode in { ICALL, IJXX} : f_valC;
	1 : f_valP;
];
```

與SEQ不同，我們需要將指令狀態的計算分為兩個部分。

取指階段檢測：指令地址越界引起的內存錯誤、非法指令、`halt`指令。

訪存階段檢測：非法數據地址。

``` C
word f_stat = [
	imem_error : SADR;
	!instr_valid : SINS;
	f_icode == IHALT : SHLT;
	1 : SAOK;
];
```

### 譯碼階段和寫回階段

![[Pasted image 20250628110359.png]]

上圖示PIPE譯碼和寫回階段的詳細說明。

注意，傳給寫端口的寄存器ID來自於寫回階段(`W_dstE`和`W_dstM`)，而不是來自譯碼階段。

``` C
word d_dstE = [
	D_icode in { IRRMOVQ } : D_rB;
	D_icode in { IIRMOVQ, IOPQ } : D_rB;
	D_icode in { IPUSHQ, IPOPQ, ICALL, IRET } : RRSP;
	1 : RNONE;
];
```

| 數據字      | 寄存器ID    | 源描述           |
| -------- | -------- | ------------- |
| `e_valE` | `e_dstE` | ALU輸出         |
| `m_valM` | `M_dstM` | 內存輸出          |
| `M_valE` | `M_dstE` | 訪存階段對端口E未進行的寫 |
| `W_valM` | `W_dstM` | 寫回階段對端口M未進行的寫 |
| `W_valE` | `W_dstE` | 寫回階段對端口E未進行的寫 |

``` C
word d_valA = [
	D_icode in { ICALL, IJXX } : D_valP;
	d_srcA == e_dstE : e_valE;
	d_srcA == m_dstM : M_valM;
	d_srcA == M_dstE : M_valE;
	d_srcA == W_dstM : W_valM;
	d_srcA == W_dstE : W_valE;
	1 : d_rvalA;
];
```

處理轉發邏輯的優先級是十分重要的。

我們應給予處於較早流水線階段中的轉發源更高的優先級，因為其等同於設置該寄存器的最近的指令。

![[Pasted image 20250628120746.png]]
上圖說明了這種例子，如果使用處於較晚流水線階段的轉發，會造成程序執行結果錯誤。

``` C
word d_valB = [
	d_srcB == e_dstE : e_valE;
	d_srcB == M_dstM : m_valM;
	d_srcB == M_dstE : M_valE;
	d_srcB == W_dstM : W_valM;
	d_srcB == W_dstE : W_valE;
	1 : d_rvalB;
];
```

流水線寄存器W保存著最近完成指令的狀態，所以使用該值計算整個處理器的狀態。

注意，當寫回階段有氣泡應視為正常操作。

``` C
word Stat = [
	W_stat == SBUB : SAOK;
	1 : W_stat;
];
```

#### 練習題

4.32

注意，遇到`popq`需要暫停一個週期。此時，會讀取增加後的`%rsp`，與慣例不同。

4.33

``` C
irmovq $5, %rdx
irmovq $0x100, %rsp
rmmovq %rdx, 0(%rsp)
popq %rsp
nop
nop
rrmovq %rsp, %rax
```

連續兩個`nop`導致`rrmovq`在譯碼階段時，`pop`處於寫回階段。若給予錯誤的轉發優先級，會導致讀取增加後的`%rsp`。

![[Pasted image 20250630153826.png]]

### 執行階段

![[Pasted image 20250630160958.png]]

上圖是PIPE執行階段的邏輯，這些硬件單元與SEQ中的相同，使用的信號做些微的重命名。

我們注意`e_valE`與`e_dstE`轉發到譯碼階段。

且`SetCC`接收兩個信號`W_Stat`與`m_Stat`以更新條件碼。

#### 練習題

4.35

若使用`E_dstE`代替`d_valA`中的`e_dstE`會導致無法判斷條件數據傳送的失敗，導致轉發了不應該被轉發的值。

### 訪存階段

![[Pasted image 20250630163322.png]]

相比於SEQ，PIPE缺少了`Mem.data`塊。在SEQ中，此塊用來對`valP`和`valA`做選擇的。但在PIPE中被`Sel+Fwd A`取代。

#### 練習題

4.36

``` C
word m_stat = [
	dmem_error : SADR;
	1 : M_stat;
];
```

## 流水線控制邏輯

在此我們要創建流水線控制邏輯，處理數據轉發和分支預測不能處理的4種情況。

1. 加載/使用冒險：從內存讀出值後，下一條指令需要立即使用該值 -> 暫停一周期
2. `ret`指令
3. 分支預測錯誤
4. 異常

### 特殊情況的處理

當遇到加載/使用冒險，即`mrmovq`或`popq`指令，並處於執行階段時，且需要該目的寄存器的指令正處於譯碼階段，我們需要將第二條指令阻塞在譯碼階段，並在下一個週期往執行階段插入一個氣泡。之後，轉發邏輯會解決這個數據冒險。

對於`ret`，我們需要暫停三個時鐘週期(第四個周期恢復)。直到`ret`經過訪存階段，讀出返回地址。

當分支預測錯誤時，即跳轉指令到達執行階段檢測到預測錯誤，在下一個時鐘週期往執行和譯碼階段插入氣泡，取消兩個錯誤的指令。

對於異常指令，我們需要滿足ISA規定的行為，即前面所有指令結束前，後面的指令不能影響程序狀態。

這些因素會導致滿足行為較麻煩：
1. 異常在兩個不同階段(取指、訪存)被發現
2. 狀態在三個不同階段(執行、訪存和寫回)被更新

當異常指令到達訪存階段時，我們採取以下措施防止後續指令更改程序員可見狀態：
1. 禁止執行階段的指令設置條件碼
2. 向訪存階段插入氣泡，以禁止向內存中寫入
3. 當寫回階段有異常指令時，暫停寫回階段，因而暫停了流水線

### 發現特殊控制條件

| 條件      | 觸發條件                                                                              |
| ------- | --------------------------------------------------------------------------------- |
| `ret`指令 | $IRET \in \{ D\_icode, E\_icode, M\_{icode} \}$                                   |
| 加載/使用冒險 | $E\_icode \in \{ IMRMOVL, IPOPL \} \ \&\& \ E\_dstM \in \{ d\_srcA, d\_{srcB} \}$ |
| 分支預測錯誤  | $E\_icode ==IJXX \ \&\& \ !e\_Cnd$                                                |
| 異常      | $m\_stat \in \{ SARD, SINS, SHLT \} \ \| \ W\_stat \in \{ SADR, SINS, SHLT \}$    |

### 流水線控制機制

假設每個流水線寄存器有兩個控制輸入：暫停(stall)和氣泡(bubble)，兩個信號同時為1視為錯誤。

當暫停信號設置為1時，禁止更新狀態，寄存器保持原值。使得將某個指令阻塞在某個階段。

當氣泡信號設置為1時，寄存器狀態設置成固定的**復位配置(reset configuration)**，得到等效為`nop`的狀態。

復位配置的0、1模式由流水線寄存器的字段集合決定。例如，往流水線寄存器D插入氣泡，我們需要將`icode`設為`INOP`。想要往流水線寄存器E插入氣泡，則需要將`icode`設為`INOP`，並將`dstE, dstM, srcA, srcB`設為常數`RNONE`。

![[Pasted image 20250630180331.png]]

| 條件(流水寄存器) | F   | D             | E               | M                | W   |
| --------- | --- | ------------- | --------------- | ---------------- | --- |
| `ret`     | 暫停  | 氣泡(此時檢測到預測錯誤) | 正常(`ret`處於譯碼階段) | 正常(運行到此時已插入三個氣泡) | 正常  |
| 加載/使用冒險   | 暫停  | 暫停            | 氣泡(此時檢測到預測錯誤)   | 正常(指令處於執行階段)     | 正常  |
| 分支預測錯誤    | 正常  | 氣泡            | 氣泡(此時檢測到預測錯誤)   | 正常(指令處於訪存階段)     | 正常  |

### 控制條件的組合

目前為止，我們假設一個時鐘周期內最多只出現一個特殊情況。現在來考慮同時處裡多個特殊情況。

![[Pasted image 20250630182235.png]]

上圖為特殊控制條件的流水線狀態，圖中的一對`Combination`可能同時出現。

當出現`Combination A`時，如下處理。

![[Pasted image 20250630183649.png]]

| 條件(流水寄存器) | F   | D             | E               | M                | W   |
| --------- | --- | ------------- | --------------- | ---------------- | --- |
| `ret`     | 暫停  | 氣泡(此時檢測到預測錯誤) | 正常(`ret`處於譯碼階段) | 正常(運行到此時已插入三個氣泡) | 正常  |
| 分支預測錯誤    | 正常  | 氣泡            | 氣泡(此時檢測到預測錯誤)   | 正常(指令處於訪存階段)     | 正常  |
| 組合        | 暫停  | 氣泡            | 氣泡              | 正常               | 正常  |

當出現`Combination B`時，如下處理。

![[Pasted image 20250630183955.png]]

| 條件(流水寄存器) | F   | D             | E               | M                | W   |
| --------- | --- | ------------- | --------------- | ---------------- | --- |
| `ret`     | 暫停  | 氣泡(此時檢測到預測錯誤) | 正常(`ret`處於譯碼階段) | 正常(運行到此時已插入三個氣泡) | 正常  |
| 加載/使用冒險   | 暫停  | 暫停            | 氣泡(此時檢測到預測錯誤)   | 正常(指令處於執行階段)     | 正常  |
| 組合        | 暫停  | 暫停+氣泡         | 氣泡              | 正常               | 正常  |
| 期望        | 暫停  | 暫停            | 氣泡              | 正常               | 正常  |

### 控制邏輯實現

![[Pasted image 20250701194414.png]]

上圖是流水線控制邏輯的整題結構。

結合此部分各表格，我們可以寫出各個流水線控制信號的HCL描述。

``` C
bool F_stall = 
	E_icode in { IMRMOVQ, IPOPQ } && E_dstM in { d_srcA, d_srcB } ||
	IRET in { D_icode, E_icode, M_icode };
```

``` C
bool D_stall = 
	E_icode in { IMRMOVQ, IPOPQ } && E_dstM in { d_srcA, d_srcB };
```

``` C
bool D_bubble = 
	(E_icode == IJXX && !e_Cnd) ||
	!(E_icode in { IMRMOVQ, IPOPQ } && E_dstM in { d_srcA, d_srcB }) && 
	IRET in { D_icode, E_icode, M_icode };
```

``` C
bool E_bubble = 
	E_icode in { IMRMOVQ, IPOPQ } && E_dstM in { d_srcA, d_srcB } ||
	(E_icode == IJXX && !e_Cnd);
```

``` C
bool set_cc = 
	(E_icode == IOPQ) &&
	!m_stat in { SADR, SINS, SHLT } && !W_stat in { SADR, SINS, SHLT };
```

``` C
bool M_bubble = 
	m_stat in { SADR, SINS, SHLT } || W_stat in { SADR, SINS, SHLT };
```

`W_stall`只要檢查`W_stat`因為如果`m_stat`為真，該指令會在訪存階段暫停，而無法進入寫回階段。

``` C
bool W_stall = 
	W_stat in { SADR, SINS, SHLT };
```

## 性能分析

我們使用**CPI(Cycle Per Instruction，每指令周期數)** 來評估整體性能。時間單位是時間週期，而不是微微秒。

若某階段共處理了$C_{i}$條指令和$C_{b}$個氣泡，則處理器大約需要$C_{i}+C_{b}$個時鐘週期來執行$C_{i}$條指令。

我們如下定義CPI：

$$
CPI = \frac{C_{i}+C_{b}}{C_{i}}=1.0+\frac{C_{b}}{C_{i}}
$$

即，$1.0$加上處罰項$\frac{C_{b}}{C_{i}}$，該項表明一條指令平均要插入多少個氣泡。

若令加載/使用冒險插入的氣泡平均數為$lp(load \ penalty，加載處罰)$，預測分支錯誤插入的氣泡平均數為$mp(\text{mispredicted branch penalty}，預測錯誤分支處罰)$，`ret`指令插入的氣泡平均數為$rp(\text{return penlaty}，返回處罰)$。

則CPI可表示為：

$$
CPI = 1.0 + lp+mp+rp
$$

### 練習題

4.43-4.44

略