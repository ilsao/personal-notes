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

