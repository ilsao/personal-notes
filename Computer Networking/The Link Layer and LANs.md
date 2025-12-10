
# Introduction to the Link Layer

在此，我們將任意運行鏈路層協議的設備皆稱為**節點(node)**，包括主機、路由器、交換機、WiFi 接入點。

我們將連接相鄰節點的通信信道稱為**鏈路(link)**。

## The Service Provided by the Link Layer

鏈路層協議可能提供的服務包括：
- **成幀(framing)**：一個網絡層數據報經由鏈路傳送前，需要將其用鏈路層幀封裝起來。不同的協議具有不同的幀格式。
- **鏈路接入(link access)**：**介質訪問控制(Medium Access Control, MAC)** 協議規定了幀在鏈路上傳輸的規則。當多個節點共享單個廣播時，具有多路訪問問題，MAC 協議在此用於調節多個節點間的幀傳輸。
- **可靠交付(reliable delivery)**：有些高出錯率的鏈路提供差錯檢測與糾正服務，使得無差錯的發送數據報。

## Where is the Link Layer Implemented

![[Pasted image 20251210141717.png]]

上圖展示了一個典型主機架構。

以太網功能要麼集成到主板芯片組，要麼使用專用以太網芯片。

大多情況下，鏈路層在稱為網絡適配器(Network Adapter，又稱網絡接口控制器, Network Interface Controller, NIC)的芯片上實現，大部分鏈路層控制器的功能都在硬件中實現。

至於鏈路層在軟件層面上的實現，通常實現在驅動上。提供了一些較高層的鏈路層功能，例如組裝鏈路層尋址信息、激活控制器硬件、處理差錯條件等。

在發送端，控制器取得由協議棧較高層生成並存在內存中的數據報，在鏈路層中填寫並封裝該數據報，然後依循鏈路接入協議將幀傳入通信鏈路中。

# Multiple Access Links and Protocols

我們知道有兩種網絡鏈路類型：**點對點鏈路(point-to-point link)** 和**廣播鏈路(broadcast link)**。

- 點對點鏈路：由鏈路一端的單個發送方與鏈路另一端的單個接收方組成。**點對點協議(point-to-point protocol)** 和**高級數據鏈路控制(high-level data link control, HDLC)** 就是專門為點對點鏈路設計的。
- 廣播鏈路：允許多個發送方與接收方連接到同一個廣播信道中，任意一個節點傳送一個幀時，所有節點都會收到一個副本。

我們使用**多路訪問協議(multiple access protocol)** 來規範共享廣播信道上的傳播。

如果多個節點同時傳輸幀，則傳輸的幀會在接收方處發生**碰撞(collide)**。此時幀的信號糾纏在一起，使得幀丟失。

我們可以將多路訪問協議劃分為以下三種：
- **信道劃分協議(channel partitioning protocol)** 
- **隨機接入協議(random access protocol)** 
- **輪流協議(taking-turns protocol)** 

理想情況下，對於一個速率 $R\text{ bps}$ 的廣播信道，多路訪問協議應該具有以下特性：
1. 只有一個節點發送數據時，應具有 $R$ 的吞吐量。
2. 當有 $M$ 個節點發送數據時，在適當時間間隔內應有 $\frac{R}{M}$ 的平均傳輸速率 (不要求順時傳輸速率)。
3. 協議去中心化，不會因為主節點故障使得系統崩潰。
4. 協議應簡單且好實現。

## Channel Partitioning Protocols

還記得在第一章提到的時分多路復用 (Time-Division Multiplexing, TDM) 與頻分多路復用 (Frequency-Division Multiplexing, FDM) 嗎？這就是兩種劃分信道帶寬的技術。

## Random Access Protocols

## Taking-Turns Protocols

## DOCSIS: The Link Layer Protocol for Cable Internet Access