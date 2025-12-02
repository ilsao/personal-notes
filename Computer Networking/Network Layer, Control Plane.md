
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

**距離向量(Distance-Vector, DV)** 算法是一種迭代(持續與鄰居交換信息)、異步(不要求節點間同步計算)、分布式(每個節點都需要與鄰居交換信息)的算法。

我們得先知道著名的 Bellman-Ford 方程：

$$
d_{x}(y)=\text{min}_{v}\{c(x,v)+d_{v}(y)\}
$$

其中，$v$ 取自 $x$ 的鄰居節點集合。

以下，我們令 $N$ 為 $x$ 的鄰居節點集合。

在 DV 算法中，每個節點 $x$ 都會維護以下信息：
- 對每個鄰居 $v$ 的開銷 $c(x,v)$。
- 節點 $x$ 的距離向量，保存了到網絡中其他節點的距離列表。$\mathbf{D}_{x}=[D_{x}(y):y\in N]$ 
- $x$ 的每個鄰居 $v$ 的距離向量。$\mathbf{D}_{v}=[D_{v}(y):y\in N]$ 

在 DV 算法中，每個節點不定時的給他的鄰居發送自己距離向量副本。當 $x$ 收到他的鄰居 $w$ 發的新距離向量，他就保存 $w$ 的距離向量，然後如下使用 Bellman-Ford 方程更新自己的距離向量：

$$
D_{x}(y)=\text{min}_{v}\{c(x,v)+D_{v}(y)\}\quad \forall v\in N
$$

若 $x$ 有更新自己的距離向量，則 $x$ 應向他的每個鄰居節點發送更新後的距離向量。

所有節點不斷異步交換他們的距離向量，則估計開銷 $D_{x}(y)$ 會收斂到 $d_{x}(y)$，也就是實際的最低開銷路徑的開銷。

```
/* Initialization */
for all destinations y in N:
	D_x(y) = c(x, y) // if y is not a neighbor then c(x, y) = INT_MAX
for each neighbor w:
	D_w(y) = ? /* Have not recieved any neighbor cost table yet */
for each neighbor w:
	send distance vector D_x = [D_x(y) : y in N] to w

/* Loop */
loop
	wait (until a link cost change to some neighbor w 
	or recieve a distance vector from some neighbor w)
	
	for each y in N:
		D_x(y) = min_v{c(x, v) + D_v(y)}
		
if D_x(y) changed for any destination y:
	send distance vector D_x = [D_x(y) : y in N] to all neighbors
forever
```

在 DV 中，你只需要知道可以通過最短路徑的下一跳，也就是 $v^{*}(y)$ 。而 $v^{*}(y)$ 其實由 `D_x(y) = min_v{c(x, v) + D_v(y)}` 取到的 $v$ 決定，所以在處理這邊的同時，應該更新轉發表為 $v$。

![[Pasted image 20251202141344.png]]

上圖展示了對一個簡單網絡的 DV 運行情況。

### Distance Vector Algorithm: Link-Cost Changes and Link Failure

當 DV 算法檢測到節點與鄰居之間的鏈路開銷產生變化，就會更新自己的距離向量。如果最低開銷路徑的開銷發生變化，則向鄰居通知新的距離向量。

若鏈路錯誤的發送自己與目標的開銷，則會造成很大的問題。

![[Pasted image 20251202144425.png]]

考慮以下場景：同樣是 $x,y,z$ 三個路由器，本來 $c(x,y)=4$，但後來改成 $c(x,y)=60$。而 $c(y,z)=1$，$c(x,z)=50$ 沒有改變。因為 $y$ 檢測到開銷改變，所以會更新距離向量。因為 $z$ 還不知道 $c(x,y)$ 開銷的改變，所以 $D_{z}(x)=5$ 保持不變，$D_{y}(x)=c(y,z)+D_{z}(x)=1+5=6$，然後傳送自己的距離向量給鄰居，並設定下一跳為 $z$。

$z$ 收到 $D_{y}(x)=6$ 後，會被更新 $D_{z}(x)=6+1=7$，並設定下一跳為 $y$。導致封包在 $y,z$ 之間被傳來傳去，而且 $D_{y}(x)$ 與 $D_{z}(x)$ 的值不斷增加，直到開銷往復迭代後被正確更新。

這種問題稱為**路由選擇循環(routing loop)** (封包被傳來傳去)，會導致 **無窮計數(count-to-infinity)** (距離不斷自增) 問題。

### Distance Vector Algorithm: Adding Poisoned Reverse

剛才提到的那個簡單小場景可以通過使用**毒性逆轉(poisoned reverse)** 技術避免。

毒性逆轉的思想如下：若 $z$ 決定通過 $y$ 到達 $x$，就會告訴 $y$ $D_{z}(x)=\infty$。

當開銷更新時，雖然 $y$ 到 $x$ 的開銷為 $60$，因為 $D_{z}(x)=\infty$ 所以還是照走這條路送，然後將更新的距離向量傳給 $z$。此時 $z$ 會更新自己的距離向量 $D_{z}(x)=50$，然後傳給 $y$。$y$ 會更新距離向量 $D_{y}(x)=51$，然後傳給 $z$ 並決定轉發封包給 $z$，所以他會告訴 $z$ 自己的 $D_{y}(x)=\infty$。

需要注意的是，毒性逆轉並沒有解決一般的無窮計數問題，因為涉及到不只兩個直接相連的鄰居節點迴路無法直接通過毒性逆轉技術檢測到。