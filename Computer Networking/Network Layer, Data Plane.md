
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

最簡單的策略，不用多說了吧。

2. 優先權排隊(Priority Queuing)

在 priority queuing 中，到達輸出鏈路的分組會被分類放入不同優先級的隊列中。

當需要選擇一個分組傳輸時，會先從優先級較高的隊列中取出分組。(例如，實時電話的優先級可能比電子郵件的優先級高)

通常來說，同一個優先級隊列中的分組採取 FIFO。

3. 循環和加權公平排隊 (Round Robin and Weighted Fair Queuing, WFQ)

在**循環排隊規則(round robin queuing discipline)** 中，分組也會被分類，但是不像 priority queuing 那樣具有優先級。相反，會在不同隊列中循環輪替發送分組。

當然，如果輪到的隊列為空，會自動向下延續輪替。這種規則稱為**保持工作排隊(work-conserving queuing)**。

一種通用的循環排隊策略稱為**加權公平排隊(WFQ)**。

除了循環排隊規則外，WFQ 會給每個隊列一個權重 $w_{i}$。WFQ 會確保第 $i$ 類得到的吞吐量最少為 $R\cdot \frac{w_{i}}{\sum w}$。

# The Internet Protocol (IP): IPv4, Addressing, IPv6, and More

## IPv4 Datagram Format

![[Pasted image 20251120192704.png]]

IPv4 數據報中的關鍵字段如下：
- Version
- Header length
- Type of service：分別不同類型的 IP 數據報。比如將實時數據報與非實時流量分開。
- Datagram length
- Identifier, flags, fragmentation offset：這三個字段與 IP 分片有關。Identifier 用來標示分片後的數據報是否為同一個原數據報，而 fragmentation offset 用來標示該分片後的數據報在原數據報中的偏移量。
- Time-to-live：為了防止數據報在網絡中無限循環。每當數據報經過一個路由器時，TTL 的值就會減一。一但減為零該數據報就會被丟棄。
- Protocol：此字段通常只在到達目的後才有用，用來標示要將數據交給哪個運輸層協議。例如值 6 表示交給 TCP，值 17 說明交給 UDP。
- Header checksum：正常的繳驗和功能。需要注意的是，**每經過一台路由器繳驗和就要重新計算**，因為 TTL 的值不斷更新。為什麼要在運輸層與網絡層都進行差錯繳驗？因為 IP 層只對數據報繳驗，TCP/UDP 會對整個報文段繳驗。又因為 IP 的數據不一定都傳給 TCP/UDP，且 TCP 可以運行在不是 IP 協議的網絡中。
- Source and destination IP addresses
- Options
- Data (payload)

如果不包含可選項，一個 IP 報文首部有 20 字節。如果該數據報攜帶著 TCP 報文段，則包含 40 字節的首部與應用層報文。

## IPv4 Addressing

一台主機通常經由一條鏈路連接到網絡。主機與物理鏈路之間的邊界稱為**接口(Interface)**。

因為路由器需要從一條鏈路接收數據並從另一條鏈路轉發該數據，所以一個路由器會有多個接口。

IP 規定每個接口都有獨立的 IP 地址，所以**一個路由器會有多個 IP 地址**。

在因特網中，每個主機與路由器上的接口都必須有唯一的 IP 地址(NAT 後面的接口除外)。而地址與其所屬的子網關聯。

一個**子網(subnet)** 是由一段共同 IP 前綴構成的邏輯網，同子網內的接口可以直接通過鏈路層協議溝通而無需經過 routing。

一個子網可能有這樣的地址：`223.1.1.0/24`。其中 `/24`(稱為 slash-24)叫做**子網掩碼(network mask)**，說明 32 bits 中較高的 24 bits 定義了子網地址。

因特網的地址分配策略稱為**無類別域間路由選擇(Classless Inter-Domain Routing, CIDR)**，也就是使用前綴長度(由子網掩碼給出)表示子網大小。

在配置轉發表時，只需考慮子網的地址前綴即可，因為同一個子網中的接口共享相同的地址前綴。這種通過一條條目就可以發送到多個接口的能力稱為**地址聚合(address aggregation)** 或**路由聚合(route aggregation)** 或**路由摘要(route summarization)**。

我們來說說 IP 廣播地址 255.255.255.255。(只在子網內部廣播)

如果一台主機發送一個目的地址為 255.255.255.255 的數據報，那麼報文會被交付給所有**同子網**的主機。

- 如何取得一塊地址？

兩種辦法：
1. 通過 ISP 分配。一個 ISP 可能會從已分配給該 ISP 的地址中分配一些地址，如下圖展示。
2. 由**因特網名字和編號分配機構(Internet Corporation for Assigned Names and Numbers, ICANN)** 分配。

![[Pasted image 20251120221226.png]]

- 獲取主機地址：動態主機配置協議

某組織一但獲取了一塊地址，就可為組織內的主機與路由器分配 IP 地址。

通常，路由器地址由管理員手動配置。但是，主機地址通常由**動態主機配置協議(Dynamic Host Configuration Protocol, DHCP)** 分配。

因為 DHCP 可以自動將主機連接到網絡，所以也稱為**即插即用協議(plug-and-play protocol)** 或**零配置(zeroconf)** 協議。

DHCP 是一個客戶-服務器協議。客戶端為新到達的主機，想要獲取 IP 地址與其他網絡配置信息。

在簡化的場景下，每個子網有一個 DHCP 服務器。或者，一個 DHCP 中繼代理(通常為路由器)，這個代理知道服務該網絡的 DHCP 服務器的地址。

考慮下圖場景：DHCP 服務器連接到子網 `223.1.2/24`，而且有一台 DHCP 中繼代理路由器幫助 `223.1.1/24` 與 `223.1.3/24` 中的客戶端提供服務。

對於一個想通過 DHCP 獲取地址的主機來說，需要經過以下四個步驟：
1. DHCP server discovery：因為主機還沒分配地址，所以 `src:0.0.0.0`。主機通過 UDP 在 67 端口發送 **DHCP 發現報文(DHCP discovery message)**，因為不知道 DHCP 服務器位置，所以將目的地址設為廣播地址 `255.255.255.255`。因為一個局域網中可能同時有許多廣播信息，所以需要使用 transaction ID 表明哪些封包是當前通信使用的。
2. DHCP server offer(s)：服務器收到 DHCP 發現報文後，用 **DHCP 提供報文(DHCP offer message)** 對客戶端回應。因為客戶端還不知道自己被分配的地址，所以也通過廣播形式發送報文。(包含了一個 IP 地址租用期 address lease time)
3. DHCP request：因為可能一個局域網中有許多台 DHCP 服務器，客戶端必須從中選擇一個並用 **DHCP 請求報文(DHCP request message)** 回應，並回應配置的參數。
4. DHCP ACK：服務器使用 DHCP ACK message 回應 request，並驗證所要求的參數。

下圖展示了一次 DHCP 客戶-服務器交互(圖中 `yiaddr` 代表 your internet address)：

![[Pasted image 20251121145936.png]]

## Network Address Translation (NAT)

**NAT 使能路由器(NAT-enable router)**：經由此路由器可將私有 IP 地址轉換為公共 IP 地址。

考慮下圖場景，圖中央的路由器為 NAT 使能路由器。圖右側為家庭網絡，具有地址 `10.0.0.0/24`。

![[Pasted image 20251121152313.png]]

地址空間 `10.0.0.0/8` 用於私有網絡(或稱專用網絡, private network)，在公網沒有意義。

就上圖來說，所有離開 NAT 路由器的報文都只有一個 IP 地址 `138.76.29.7`，而進入家庭的報文都只有一個目的 IP 地址 `138.76.29.7`。(路由器的地址由 ISP 的 DHCP 服務器分發，而家庭內部主機的地址由 NAT 路由器上運行的 DHCP 服務器提供)

NAT 路由器使用 **NAT 轉換表(NAT translation table)** 轉發分組給內部主機。

假設主機 `10.0.0.1` 從端口 `3345` 發送 HTTP 請求給 `128.119.40.186`，經過 NAT 路由器後源地址會被修改為路由器的地址 `138.76.29.7`，並重新分配新的端口 `5001`。最後 NAT 路由器在 NAT 轉換表建立一個映射條目。

當收到回應後，透過 NAT 轉換表的映射，將封包交付給 `10.0.0.1, 3345`。

## IPv6

因為 32 bits 的地址快被用完啦，所以需要 IPv6。

下圖展示了 IPv6 的數據報格式：

![[Pasted image 20251121154244.png]]

IPv6 有以下新功能：
- 擴大的地址容量：32 bits -> 128 bits。還加入了**任播地址(anycast address)**，可以在一組主機中發送數據給任意一個主機。
- **流標籤(flow label)**：給屬於特殊流的分組的標籤，使得這些分組可以被區分出來。但是流本身也還沒有明確的定義。

各個字段含義咱就不討論了哈！

需要注意以下字段在 IPv6 已經不存在：
- 分片：IPv6 刪除了路由器中的分片功能，使得分片與組裝只能在源或目的地執行。
- 首部繳驗和
- 選項：雖然不在首部中，但是可以由 `Next hdr` 字段指出。這種更動使得 IPv6 首部變成定長的 40 字節。

談談如何從 IPv4 遷移到 IPv6。雖然 IPv6 可以像後兼容，但是 IPv4 不可處理 IPv6 數據報。

現今使用**隧道技術(tunneling)** 實現遷移。

假設現有兩 IPv6 節點使用 IPv6 數據報交互，但是中間需要經過 IPv4 節點。

我們將這些 IPv4 節點的集合稱為一個**隧道(tunnel)**。藉由隧道，IPv6 節點將數據報包含在一個 IPv4 數據報的載荷字段，使得 IPv4 節點得以轉發數據報。

![[Pasted image 20251121160508.png]]

# Generalized Forwarding and SDN

**泛化轉發(generalized forwarding)** 拓展了**基於目的地轉發(destination-based forwarding)** 的概念：
- 匹配：不僅尋找目的地址，而可以對多個首部字段匹配。
- 操作：不直接轉發，而可以有更多操作。

SDN 的引入使得每個路由器都有一個由遠程控制器計算的匹配與操作表，在 OpenFlow 中稱為**流表(flow table)**。實際上可能由多個流表實現一個流水線，但以下指考慮一個流表的實現。

至於你問啥是 OpenFlow 呀？就是一個讓遠程控制器操控分組交換機的協議。

好的我們繼續，流表包含：
- 首部字段值：進入分組交換機的分組首先與此條目匹配。匹配不到的被丟棄或者由遠程控制器做後續處理。
- 計數器：包括與該表相匹配的分組數量及自上次更新以來的時間。
- 操作：與表相相匹的分組應執行的操作，如轉發或丟棄之類。

## Match

![[Pasted image 20251122170818.png]]

上圖展示了 OpenFlow 1.0 中的一些字段。可以看出包含三層的信息，所以 OpenFlow 違反了分層原則。

其中，`Ingress Port` 代表分組交換機上接收分組的 Input port。

你需要知道，流表項可以使用 `*` 來代表通配符。而且，流表項具有優先級。

## Action

每個流表項都有零或多個操作列表，如有多個操作，則按照表中規定的順序執行。

其中重要的操作有：
- 轉發。
- 丟棄：沒有操作的流表項表明匹配的分組應該被丟棄。
- 修改字段：分組被轉發到輸出端口前，上面圖中除了 `IP Proto` 之外的字段都可以被修改。

## OpenFlow Examples of Match-plus-action in Action

考慮以下場景：

![[Pasted image 20251122172126.png]]

我們列舉一些常用的行為並實現需要的流表項。

1. 簡單轉發

考慮我們想要讓從 `h5, h6` 發出的分組不經由 `s3, s2` 之間的鏈路到達 `h3, h4`。

在 `s3` 中，我們需要以下流表項：

| Match                                  | Action       |
| -------------------------------------- | ------------ |
| `IP Src = 10.3.*.*; IP Dst = 10.2.*.*` | `Forward(3)` |
| `......`                               | `......`     |

在 `s1` 中，我們需要以下流表項：

| Match                                                    | Action       |
| -------------------------------------------------------- | ------------ |
| `Ingress Port = 1; IP Src = 10.3.*.*; IP Dst = 10.2.*.*` | `Forward(4)` |
| `......`                                                 | `......`     |

在 `s2` 中，我們需要以下流表項：

| Match                                 | Action       |
| ------------------------------------- | ------------ |
| `Ingress Port = 2; IP Dst = 10.2.0.3` | `Forward(3)` |
| `Ingress Port = 2; IP Dst = 10.2.0.4` | `Forward(4)` |
| `......`                              | `......`     |

2. 負載均衡 (Load Balancing)

考慮我們想讓從 `h3` 發送的數據報直接經由 `s2, s1` 之間的鏈路轉發，而 `h4` 發送的數據報由 `s2, s3` 然後 `s3, s1` 轉發。注意這種場景下無法直接由 Destination-Based Forwarding 得到此種行為。

在 `s2` 中，我們需要以下流表項：

| Match                                 | Action       |
| ------------------------------------- | ------------ |
| `Ingress Port = 3; IP Dst = 10.1.*.*` | `Forward(2)` |
| `Ingress Port = 4; IP Dst = 10.1.*.*` | `Forward(1)` |
| `......`                              | `......`     |

3. 防火牆

考率 `s2` 只希望接收來自與 `s3` 相連主機的流量。(不是任何通過 `s3` 轉發的流量)

在 `s2` 中，我們需要以下流表項：

| Match                                  | Action       |
| -------------------------------------- | ------------ |
| `IP Src = 10.3.*.*; IP Dst = 10.2.0.3` | `Forward(3)` |
| `IP Src = 10.3.*.*; IP Dst = 10.2.0.4` | `Forward(4)` |
| `......`                               | `......`     |

如果 `s2` 沒有其他表項，那麼只有來自 `10.3.*.*` 的流量會被轉發給 `s2` 相連的主機。 

# Middleboxes

**中間盒(middlebox)** 的定義如下：在源與目的主機之間數據路徑上，執行除 IP 路由器正常標準功能之外的其他功能的一種設備。

中間盒提供以下三種常見服務：
- NAT 轉換。
- 安全服務。
- 性能增強：壓縮、緩存、負載均衡等功能。

因為設備需要維護，要好多錢錢。所以現在正在嘗試**網絡功能虛擬化(Network Function Virtualization, NFV)**，將硬件設備執行的功能轉由軟件實現。