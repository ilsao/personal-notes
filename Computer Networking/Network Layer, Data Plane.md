
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
- Switching via an interconnection network：為了克服單一總線的帶寬限制，我們使用多條總線。例如，縱橫式交換機使用 2N 條總線組成互聯網絡，連接 N 個輸入端口與 N 個輸出端口。**交換結構控制器(switching fabric controller)** 可以控制交叉點的開關。比如想從 A 轉發封包到 Y，控制器可以閉合繼續到 Z 的分支使得封包到達 Y。這也表示這種機制是**非阻塞的(non-blocking)**，只要沒有多個封包同時轉發到一個輸出端口，就可以並行傳送。需要注意，多個封包無法同時轉發到一個輸出端口，因為同一時刻一個總線只能發送一個分組。

## Output Port Processing

![[Pasted image 20251119224625.png]]

如上圖所示，輸出端口選擇並取出隊列中的分組並進行傳輸。

## Where Does Queuing Occur ?

在以下討論中，假設我們有 $N$ 個輸入端口與 $N$ 個輸出端口，且輸入線路速率與輸出線路速率一致，為 $R_{\text{line}}\text{ pkts/sec}$。我們還假設任何鏈路發送分組的速率與接收分組的速率相同。定義 $R_{\text{switch}}$ 為交換結構將分組從輸入端口傳送到輸出端口的速率。

若 $R_{\text{switch}}$ 是 $R_{\text{line}}$ 的 $N$ 倍，在**輸入端口的排隊幾乎可以忽略**(這邊可沒說輸出端口的排隊可忽略啊，別自己腦補)。因為就算在最糟的情況下，即所有分組都要被轉發到同一個輸出端口，也能在下一批分組到來前被成功轉發。

1. 輸入排隊

以下討論基於縱橫式交換結構，並有如下假設：
- 所有鏈路速度相同。
- 從輸入端口轉發給輸出端口所需的時間與輸入端口接收分組的時間相同。
- 分組 FCFS。

當 $R_{\text{switch}}$ 的速度不夠快，就會發生輸入排隊。

![[Pasted image 20251119230325.png]]

上圖的例子表示了**隊列首部(Head-Of-the-Line, HOL)** 阻塞。因為左下的深色分組與左上的深色分組競爭右上的輸出端口(若最後決定轉發左上分組)，即使左下的淺色分組沒有與其他分組競爭，也必須等待。

2. 輸出排隊

再次考慮 $R_{\text{switch}}$ 為 $R_{\text{line}}$ 的 $N$ 倍的情況，此時輸出端口每一秒會接收到 $N^{2}$ 個分組，而輸出端口的轉發速率才 $N\text{ pkts/sec}$，勢必會發生排隊。

當隊列緩衝區不夠時，就會發生丟包。有兩種策略：
- **棄尾(drop-tail)**：丟棄最後到來的分組。
- 選擇性的刪除或標記早已在隊列中的分組。

某些策略下，在緩存滿之前就丟棄封包是有利的。利用**明確擁塞通告比特(Explicit Congestion Notification bit)** 可以對分組標記，並將雍塞信號告訴發送方。

這種分組丟棄與標記策略統稱**主動隊列管理(Active Queue Management, AQM)**。

3. 多大的緩從才足夠？ 

過去，經驗方法跟我們說，緩存大小 ($B$) 應該等於 RTT 乘以鏈路容量 ($C$)。

例如：一條 $\text{RTT}=250\text{ ms}$ 的 $10\text{ Gbps}$ 鏈路，需要 $B=0.25 \times 10=2.5\text{ Gb}$ 的緩存。

但是，現在的理論說如果有大量的 TCP 流 ($N$ 條)，則 $B=\text{RTT}\cdot \frac{C}{\sqrt{ N }}$。

注意，緩存大小不是越大越好！過大的緩存雖然可以防止丟包，但是可能**造成端到端延遲巨大**。

**緩存膨脹(Bufferbloat)**：緩存過大，導致排隊延遲過大。

## Packet Scheduling

1. FIFO

2. 優先權排隊(Priority Queuing)

3. 循環和加權公平排隊 (Round Robin and Weighted Fair Queuing, WFQ)