
# Routing Algorithms

路由選擇算法分為：
- **集中式路由選擇算法(centralized routing algorithm)**：知道完整的網絡開銷與節點間的連通性後，通過計算這些結果而取得最低開銷路徑。這種算法通常被稱為**鏈路狀態(Link State, LS)** 算法。
- **分散式路由選擇算法(decentralized routing algorithm)**：路由器以迭代、分布式的方法計算出最低開銷路徑，沒有節點知道網絡的完整信息。這種算法通過相鄰路由器間的交換報文而交換資料，可能更適合路由器直接交互的控制平面。

路由選擇算法還分為：**靜態路由選擇算法(static routing algorithm)** 與**動態路由選擇算法(dynamic routing algorithm)**。

靜態路由選擇算法中的路由變化較為緩慢，通常是人工調整。

相反，動態路由選擇算法可以週期性的對網絡拓樸變化進行響應，但是更容易受到路由選擇循環或路由震盪之類問題的影響。

第三種路由選擇算法的分類方法還有：負載敏感、負載遲鈍。

**負載敏感算法(load-sensitive algorithm)** 中，鏈路開銷會跟隨擁塞水平上升而上升。相反，**負載遲鈍算法(load-insensitive algorithm)** 中則不會。

如今的路由選擇算法通常是負載遲鈍的。

## The Link-State (LS) Routing Algorithm

在 LS 中，每個路由器是如何知道網絡拓樸的狀態？答案是使用**鏈路狀態廣播(link state broadcast)** 算法。

ok 呀，本書略過很多細節後直接開講 Dijkstra。

我們定義以下符號：
- $D(v)$：到目前迭代為止，從源節點 $u$ 到目的節點 $v$ 的最低開銷路徑的開銷。
- $p(v)$：以源節點到 $v$ 的最低開銷路徑來看，到達 $v$ 的前一個節點。(經由此節點，下一跳就是 $v$)
- $N'$：節點組成的子集。若從源節點到 $v$ 的最低開銷路徑已經確定，則 $v$ 會被加入 $N'$ 中。

Dijkstra 分為 Initialization 與 Loop 兩個階段：

```
/* Initialization */
N' = {u}
for all nodes v
	if v is a neighbor of u
		D(v) = c(u, v)
	else
		D(v) = INT_MAX
		
/* Loop */
Loop
find w not in N' such that D(w) is a minimum
add w to N'
update D(v) for each neighbor v of w and not in N'
	D(v) = min(D(v), D(w) + c(w, v))
until N' = N
```

我們以下圖為例，尋找 $u$ 到其他所有節點的最短距離。

![[Pasted image 20251129145251.png]]

![[Pasted image 20251129145337.png]]

當 LS 算法結束後，我們可以得到從 $u$ 到目的節點沿路徑的前一個節點。所以，我們可以反向建立一條從 $u$ 到目的節點的最低開銷路徑。

而路由轉發表只需要存放從 $u$ 出發的第一個轉發節點即可。

![[Pasted image 20251129145731.png]]

但是捏，考慮一個情況會使得路由震盪。

![[Pasted image 20251129150323.png]]

如圖所示，初始狀況 (a) 有這些流量要發送。

第一次執行 LS，從 $y$ 當源節點。此時從順時針的路徑開銷較低，更新路由表使得變成圖 (b)。第二次運行 LS，逆時針開銷低，變 (c)...... 持續震盪。

要解決這種震盪，我們希望即使路由器以相同週期運行 LS，每個節點上算法執行的時機相異。我們的方法是使得發送鏈路通告的時間隨機話。

## The Distance-Vector (DV) Routing Algorithm