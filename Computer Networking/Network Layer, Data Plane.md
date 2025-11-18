
# Overview of Network Layer

## Forwarding and Routing: The Data and Control Planes

網絡層需要做到以下兩件事：
1. 封包轉發：**數據平面**根據轉發表將封包轉發到對應端口。(通常由硬件實現)
2. 路由計算：**控制平面**根據路由算法決定轉發表如何填寫。(通常由軟件實現)

## Network Service Model

**網絡服務模型(Network Service Model)**：說明了從發送端到接收端，一個封包在網絡傳輸中的性質與保證。

一個理想的網絡層可能實現了以下功能： 
- 保證送達
- 保證延遲上限：不只保證送達，還保證在指定時間內送達。
- 按序送達
- 最低頻寬保證
- 安全性（加密）

但事實是，網絡層只提供了盡力而為服務(Best-Effort Service)，不保證任何結果。

# What is Inside a Router?

一個普通的路由器架構如下所示：

![[Pasted image 20251118134059.png]]

可以觀察到有以下結構：
- Input port：負責**查表(lookup)**，並決定封包應被送往哪個端口。對於**控制封包**來說，會被直接送到**路由處理器(Routing processor)**。
- Switch fabric：負責把輸入端口與輸出端口連起來。
- Output port：負責緩存封包並把封包傳到 output link。
- Routing Processor：負責控制平面的功能。

## Input Port Processing and Destination-Based Forwarding

![[Pasted image 20251118144045.png]]

上圖為輸入處理的一個詳細圖示。

line termination 和 processing，會將傳入的光訊號轉換成 bit，並將鏈路層的幀解封包成 IP 封包。

而 Lookup 部分則是此部分的核心，通過查表會將封包經由 switch fabric 傳送到對應 output port。

轉發表由 routing processor 或 SDN 維護。這樣的設計使得封包的轉發可以由 input port 決定，而不是聚集在 routing processor 決定從而使得處理資源不足造成瓶頸。

在匹配轉發表時，路由器使用**最長前綴匹配(longest prefix matching rule)**。

查表後，封包就會被傳入 switching fabric。在某些設計中，如果其他輸入端口正在使用 switching fabric，封包就會在隊列中排隊。

## Switching

當封包通過 switching fabric 後，就算真正被轉發到 output port了。switching 有不同的方法，如下圖所示：

![[Pasted image 20251118150459.png]]

- Switching via memory：這是種古老且簡單的技術。輸入端口與輸出端口在此都被視為 I/O 設備，當一個封包到達，會傳一個中斷信號給 routing processor。此時封包會被複製到內存，然後由 routing processor 查表(先提取首部資料)並決定輸出端口，最後將封包複製到輸出端口的緩衝區中。注意，**在這種架構中查表由 routing processor 完成而不是輸入端口**。在這種架構下，如果內存帶寬最多可以寫 $B\text{ pkts/sec}$，那麼最大吞吐量也不會超過 $B/2$。因為一次只能同時進行一個內存讀寫操作，所以 switching fabric 不可以同時轉發兩個封包。
- Switching via a bus：這種方法可以直接將封包從輸入端直接通過總線(bus)傳輸到輸出端，而不需經過 routing processor。輸入端口會先給封包加上**交換器內部標籤(switch-internal label)**，標示此封包要被送到哪個輸出端口。然後，輸入端口會將該封包送入總線，所有輸出端口都會接收到此封包，但是只有標籤符合的輸出端口才會將封包留下，接著標籤就會被移除。(類似廣播的概念)。需要注意的是，同一時間只能有一個封包經過總線。所以，交換速度會被總線速度限制。
- Switching via an interconnection network