# The Map Method

我們使用 K-map 的方法是這樣的：
1. 將表達式轉為 sum of minterms
2. 將對應 minterms 寫上 1
3. 圈出以 2 為冪的接鄰 1 方塊，使方塊越大越好，且每個 1 都必須被圈到。
4. 看出答案

## Two-Variable Map

![[Pasted image 20260406214931.png]]

## Three-Variable Map

需要特別注意，使用的是 Gray Code 的順序：

![[Pasted image 20260406215841.png]]

而且，我們可以跨越左右邊界圈喔！

![[Pasted image 20260406215151.png]]

## Four-Variable Map

![[Pasted image 20260406215554.png]]

注意到，這圖上下左右的邊界都算接鄰！

![[Pasted image 20260406215726.png]]

# Systematic Simplification

**蘊含項(Implicant)**：任意可以覆蓋一或多個 1 的 product term。在 K-map 上只要圈出來的東西就是一個 implicant (包含單格 1)。

**主蘊含項(Prime Implicant)**：無法再擴大的 implicant，即圈到最大的 implicant。

**必要主蘊含項(Essential Prime Implicant)**：有某些 minterm 只被其覆蓋 (必選)。

![[Pasted image 20260406220619.png]]

![[Pasted image 20260406220721.png]]

![[Pasted image 20260406220743.png]]

## Prime Implicants Selection Rule

1. 找出所有 prime implicants
2. 選取所有 essential prime implicants
3. 剩下沒被選到的 1，用盡量少的 prime implicants 覆蓋它們 (圈最大)。

> [!note]
> 每個被選取的 prime implicant 都應該包含最少一個其他被選取的 prime implicants 沒有包含的 1。

![[Pasted image 20260406221251.png]]

## Five-Variable Map

用兩張圖：

![[Pasted image 20260406221359.png]]

![[Pasted image 20260406221428.png]]

![[Pasted image 20260406221534.png]]

注意到上圖 Number of Adjacent Squares，代表你圈了多少個小方塊兒。

## Product of Sums Simplification

法 1：complement from minterms
1. 用 sum of products 簡化 $F'$ 
2. 使用迪摩根定律 $F=(F')'$ 

法 2：duality from maxterms

![[Pasted image 20260406222932.png]]

## Don't-Care Conditions

Don't care conditions 可用來簡化邏輯，因為將其實現為 0 或 1 都是合法的。

![[Pasted image 20260406223654.png]]

## NAND Implementation

NAND 是萬用門，可以實現任意門電路。

![[Pasted image 20260414212026.png|566]]
![[Pasted image 20260414212044.png|725]]

![[Pasted image 20260414212142.png]]

使用以下步驟化減：
1. 將所有 AND 用 NAND 替代
2. 將所有 OR 用 Invert-OR 表示的 NAND 表示
3. 檢查所有的圈圈對，如果哪對沒配起來，則插入反相器。

![[Pasted image 20260414212523.png|653]]

## NOR Implementation

因為 NOR 是 NAND 的 dual，所以也是萬用門。

![[Pasted image 20260414212643.png|563]]
![[Pasted image 20260414212702.png|624]]

![[Pasted image 20260414212725.png|731]]

![[Pasted image 20260414212851.png|754]]

## Nondegenerate Forms

之前提過有 16 種 functions，其中 8 種是 degenerate forms，即 single operation。

剩餘八種為基本門電路的組合：AND, OR, NAND, NOR。

![[Pasted image 20260414214554.png|847]]

![[Pasted image 20260414214737.png]]

![[Pasted image 20260414214811.png]]

![[Pasted image 20260414215634.png|639]]

![[Pasted image 20260414215652.png|675]]

## Exclusive-OR Function

![[Pasted image 20260414215856.png|449]]

我們如下實現異或門：

$x\oplus y=xy'+x'y$ 先實際搭，然後轉 NAND。

![[Pasted image 20260414222014.png|480]]

## Odd and Even Functions

我們可用 $A\oplus B\oplus C$ 表示 odd function，用 $(A\oplus B\oplus C)$ 表示 even function。

因為若 $A$、$B$、$C$ 三個單位包含奇數個 $1$，$A\oplus B\oplus C$ 就會為真。 

![[Pasted image 20260414222337.png]]
![[Pasted image 20260414222602.png]]

## Four-Variable Exclusive-OR Function

$A\oplus B\oplus C\oplus D=(AB'+A'B)\oplus(CD'+C'D)$ 
$=(AB'+A'B)(CD+C'D')+(AB+A'B')(CD'+C'D)$ 

仍然，$A\oplus B\oplus C\oplus D$ 為 odd function。

## Parity Generation and Checking

令 parity bit 為：$p=x\oplus y\oplus z$。想驗證正確性：$c=x\oplus y\oplus z\oplus p$。

若：
- $c=0$：則當前計算的位做奇偶繳驗與繳驗位相同，可能沒錯誤發生，也可能發生**偶數**個位錯誤。
- $c=1$：發生**奇數**個位錯誤。

> [!note]
> 可能背反，小心。

## Verilog

![[Pasted image 20260414224032.png|849]]

![[Pasted image 20260414224106.png|759]]

![[Pasted image 20260414224135.png|881]]

![[Pasted image 20260414224231.png]]

![[Pasted image 20260414224249.png]]

# 練習題

1. Find the minterms of the following Boolean expressions by first plotting each function in a K-map: $w'x+xz+wyz$ 

Sol:
![[Pasted image 20260414232441.png|283]]
$F(w,x,y,z)=\sum(4,5,6,7,11,13,15)$ 

2. Find all the prime implicants for the following Boolean functions, and determine which are essential: (a) $F(A,B,C,D)=\sum(0,2,3,5,7,8,10,11,14,15)$ (b) $F(A,B,C,D)=\sum(2,3,4,5,6,7,9,11,12,13)$ 

Sol:
(a)
我忘記圈四角還有跨上下的右邊四個。
![[Pasted image 20260414235235.png|490]]
(b)
忘記圈跨上下黃色那個。
![[Pasted image 20260414235809.png|481]]

3. Simplify the following Boolean functions: $F=\prod(0,2,5,8,10,15)$ 

Sol:
![[Pasted image 20260415001106.png|538]]

![[Pasted image 20260415004020.png]]

Sol:
![[Pasted image 20260415004035.png|597]]
![[Pasted image 20260415004052.png|649]]

![[Pasted image 20260415004732.png]]

Sol:
沒想到可用多輸入。
記得提出 $F=D'(A+B'+C')$ 
![[Pasted image 20260415004747.png|685]]

![[Pasted image 20260415005531.png]]

Sol:
(I)
畫出 K-map 然後找 0 化減 (取反、用加的)
$F=(A+B)(A'+B')(C+D)(C'+D')=(AB'+A'B)(CD'+C'D)$ 
(II)
![[Pasted image 20260415005702.png|598]]

