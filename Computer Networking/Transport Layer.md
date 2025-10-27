
# Introduction and Transport-Layer Services

傳輸層協議提供進程與進程間的通信，不像網絡層提供的是端系統到端系統間的通信。

## Relation Between Transport and Network Layers

傳輸層協議只存在於主機中，傳輸層只將信息傳遞到網絡邊緣(即，網絡層)，或者從網絡邊緣接收信息給程序。不關心封包如何在網絡核心如何中移動。

傳輸層協議是受限於網絡層的，如果網絡層協議沒有保證頻寬或延遲，則傳輸層協議也無法保證。

但是，傳輸層可以提供以下兩件服務：
- 可靠性傳輸
- 數據加密

## Overview of the Transport Layer in the Internet

傳輸層包含兩種協議：
- **TCP(Transmission Control Protocol)**
- **UDP(User Datagram Protocol)** 

在具體講解傳輸層前，必須先了解一點點的網絡層知識。

網絡層的協議稱作 IP(Internet Protocol)，提供的服務模型是**盡力而為的傳輸服務(best-effort delivery service)**。也就是說，傳輸很不可靠的意思啦。IP 提供的服務是端系統到端系統的傳輸。

TCP 與 UDP 就是要將主機到主機的傳輸拓展成進程到進程的傳輸。所以需要用到一種技術，稱為**多路復用(multiplexing)** 與**多路解復用(demultiplexing)**。並且兩種協議在協議頭部引入了繳驗和，確認文件的完整性。

除了上述提到的服務，TCP 比 UDP 還多提供了以下的服務：
- 可靠的數據傳輸
- 壅塞控制

# Multiplexing and Demultiplexing

![[Pasted image 20251014151039.png]]

傳輸層通過給封包在 source port number field 加上來源端口號與在 destination port number field 加上目標端口號，就可以實現多路復用與解復用。

也就是說，每個 socket 會被指定一個端口號。而每個段到達該主機時，傳輸層會查看目標端口號，並傳送給相對應的 socket。

端口號是一個 16 位的數字，範圍 $0\sim 65535$。而 $0\sim1023$ 是**常用端口(well-known port number)**，不能由一般的開發者使用。

# 無連接運輸：UDP

作為一個運輸層協議，UDP 必須至少對下層提供某些服務：
- 多路復用/解復用。
- 差錯檢測。

因為在 UDP 的連接中，源與目的主機不需要進行握手，所以 UDP 稱為無連接運輸。

DNS 通常就使用 UDP 進行查詢。

以下情況更適合使用 UDP 而非 TCP：
- 需精細控制何時發送數據。
- 無需建立連接(減少握手延遲，DNS 很大可能就是因為考慮這個而選擇 UDP)。
- 無連接狀態，減少參數跟蹤，使得服務器可以支持更多活躍用戶。
- 首部開銷小。TCP 需要 20 Bytes 的首部開銷，UDP 僅需 8 字節。

## UDP 報文段結構

![[Pasted image 20251023153711.png]]

上圖為 UDP 報文段結構。其中長度字段表示了 UDP 報文段中的總字節數(首部 + 數據)，繳驗和部分用來實現差錯檢測。

## UDP 繳驗和

UDP 繳驗和使用 one's complement 表示。也就是說，如果最高位溢位，需要回卷(加 1 到最低位)。

整體計算流程如下：
1. 將整個報文段分為 16 位(2 字節)一組。
2. 將每組相加(記得回卷)。
3. 對最終結果取反。

想要繳驗報文段是否出現差錯，在繳驗端需要執行繳驗和計算的第一與二步，然後將結果與繳驗和相加。

如果相加的結果不是 `1111111111111111` 則代表繳驗失敗，報文段出現差錯(丟棄報文，但不會給應用程序發送任何警報)。否則，通過繳驗。

你可能會問，不是有些鏈路層協議提供繳驗了嗎，為何 UDP 還需要提供差錯檢測？

因為，報文經過的鏈路不一定全部都提供繳驗服務，所以 UDP 必須在端到端基礎上在運輸層提供差錯檢測。

這正是一個符合**端到端原則(end-to-end principle)** 的例子。

端到端原則：網絡的功能應儘量在端點實現，網絡核心應盡可能的保持簡單。

# 可靠數據傳輸 (Reliable Data Transfer) 原理

我們要保證數據通過 `rdt_send()` 後，經由 `udt_send()` 傳輸到接收者時仍能保持完整。

在此，我們只說明**單向數據傳輸(unidirectional data transfer)** 的情況。可靠的**雙向數據傳輸(bidirectional data transfer)** 只需要基於此情況在雙向實現即可。

## 構造可靠數據傳輸協議

當接收者檢測到分組出現差錯時，接收者會回覆**否定確認(negative acknowledgment)**。反之，回覆**肯定確認(positive acknowledgment)**。發送者收到否定確認時，就會重新發送一次分組。基於這種重傳機制的協議稱為**自動重傳請求(Automatic Repeat reQuest, ARQ)** 協議。

具體來說，ARQ 使用以下三種功能處理差錯：
- 差錯檢測
- 接收方反饋：使用 ACK 與 NAK 反饋是否發生差錯。(後續說明將優化此功能)
- 重傳

**停等(stop-and-wait)** 協議：發送方發送完分組後，等待接收 ACK 或 NAK 的過程中拒絕執行 `rdt_send()` 事件。

但是，ACK 在從接收方發回發送方時，也可能出錯。

我們使用這種策略：當發送方收到無法辨認的 ACK 時，重傳當前分組。(注意，此時還沒引入計時器機制，且假設通信中沒有丟包)

但是，這樣會導致**冗餘分組(duplicate packet)**。接收方無法判斷當前接收到的分組是新分組還是重複的冗餘分組。

所以，我們可以在封包中加入一個**序列號(sequence)**，表明當前傳送的是第幾個分組。

還有，我們其實完全可以捨棄 NAK 的設計。我們將 ACK 的定義也加上一個序號，表明當前分組成功接收，並指示下一個欲接收的分組序號。例如 ACK 6 表示序號為 5 的分組成功接收，欲接收序號為 6 的分組。

如果發送方收到兩個冗餘 ACK (duplicate ACK)，就知道接收方沒有正確的接收到該序號的分組。

我們還需考慮丟包的情況，我們不可能為一個分組無限等待。

這裡，我們引入計時器的機制。

1. 發送方在發送分組後，啟動計時器。
2. 若發送的分組或接收方回傳的 ACK 發生丟包，發送方不會收到任何 ACK。此時，若計時器時間到，則發送方響應計時器中斷。
3. 停止定時器並重新發送分組。

需要注意，如果傳輸期間沒有丟包，但計時器提早到時，會導致**冗餘數據分組(duplicate data packet)**。但是，接收方可以使用上述的序號機制分別冗餘數據分組的情況。

因為現在這種可靠數據傳輸協議不支持流水線設計，所以其實可以僅使用兩個序號交替表示分組。

以下為 rdt 的有限狀態機圖示。(注意此圖中 ACK 的含義與上述不同，此處 ACK 1 代表正確收到分組 1，而不是欲收到分組 1)

![[Pasted image 20251023173531.png]]

因為原書沒有提供接收方的狀態機，我用 chatGPT 生成了一個：

```
狀態: 等待序號 = 0（Wait for 0）
 ├── 收到 seq=0 且 checksum 正確：
 │     → 交付資料給上層
 │     → 發送 ACK(0)
 │     → 狀態切換到「等待 1」
 ├── 收到 seq=1 或 損壞封包：
 │     → 丟棄資料
 │     → 重傳 ACK(1)（上一次的 ack）
 │     → 狀態不變
 ↓
狀態: 等待序號 = 1（Wait for 1）
 ├── 收到 seq=1 且 checksum 正確：
 │     → 交付資料給上層
 │     → 發送 ACK(1)
 │     → 狀態切換到「等待 0」
 ├── 收到 seq=0 或 損壞封包：
 │     → 丟棄資料
 │     → 重傳 ACK(0)
 │     → 狀態不變
```

因為目前這種協議設計的分組序號在 0 與 1 之間交替，所以這種協議也被稱為**比特交替協議(alternating-bit protocol)**。

在看到發送方狀態機的時候我有疑惑：若在等待 ACK 0 時收到 ACK 1 ，為何不是馬上選擇重傳而選擇不做動作？這是因為，不只有接收方收到損壞的分組 0 時才會發送 ACK 1。如果計時器時間設置過短，導致發送了兩次分組 1 也會導致發送方在等待 ACK 0 時收到 ACK 1。如下圖 (d) 所示。

下圖我們討論了此協議可能發生的幾種情況：

![[Pasted image 20251023174604.png]]

我們可以注意到 (d)，發送方狀態機保證連續兩個 ACK 1 只做一次回應。

## 流水線可靠數據傳輸協議

我們先定義發送方**利用率(utilization)** 為發送方實際用於發送比特到信道與發送時間的比：

$$
U_{\text{sender}}= \frac{L/R}{RTT+L/R}
$$

通常來說，$RTT\gg \frac{L}{R}$。所以，如果不使用流水線化協議，利用率會非常低。

將可靠數據傳輸拓展到支持流水線，需要增加以下功能：
- 增加序號範圍，因為每個正在流水線中的分組都需有一個獨立的序號。
- 發送方與接收方(可能)需要緩存多個分組。
- 流水線化的處理延遲，丟失，損壞。通常使用：Go-Back-N, Selective Repeat。

## 回退 N 步 (Go Back N, GBN)

![[Pasted image 20251024154607.png]]

如上圖所示，GBN 需要發送方維護三個變量：
- `base`：基序號，指向最早的未確認分組。
- `nextseqnum`：指向最小的未使用分組(即將發送的分組)。
- Windows size：限制已發送卻未得到確認的分組的許可序號範圍。

當收到一個 ACK 確認，`base` 就會向前移動，同時窗口向前滑動。所以 GBN 有時也被稱作**滑動窗口協議(sliding-window protocol)**。

對於序號的決定，如果分組序號的字段有 $k$ 位，我們將範圍設定在 $[0,2^{k}-1]$。因為序號有限，所以對序號的運算必須先使用模運算。

需要注意的是，TCP 的序號使用字節流中的字節進行計數，而不使用分組計數。

以下提供了一個基於 ACK，無 NAK 的 GBN 協議發送方與接收方的拓展 FSM。之所以稱拓展 FSM，是因為引入變量與條件操作的觀念。

![[Pasted image 20251024161116.png]]
(發送方拓展 FSM)

發送方需響應三種事件：
- 上層調用：被調用時，確認窗口是否已滿。如果已滿(發送但未確認的分組數等於窗口大小)則拒絕服務。否則，產生一個分組並發送，然後更新相應變量。
- 收到 ACK：在 GBN 中，使用**累積確認(cumulative acknowledgment)**。ACK n 表示接收方已經正確收到序號 $n$ 及之前所有分組。所以 `base` 直接更新到 $n+1$。如果 `base == nextseqnum`，代表窗口內所有分組都正確收到確認。否則，表示窗口內還有分組沒收到確認，重啟計時器。
- 超時：重新發送所有已發送但未確認的分組。這也是協議名 Go-Back-N 的由來。

   ![[Pasted image 20251024161152.png]]
(接收方拓展 FSM)

接收方操作比較簡單。若分組 $n$ 被正確接收且是順序到來(上一個到來的分組是 $n-1$)，則發送 ACK n 給發送方。否則，接收方丟棄分組並發送最近按序接收的分組序號的 ACK。

以下是窗口長度為 $4$ 的 GBN 運行狀況：

![[Pasted image 20251024163017.png]]

## 選擇重傳 (Selective Repeat)

選擇重傳允許接收者亂序接收分組，且僅讓發送者重傳出錯的分組。這需要我們在發送方與接收方各維護一個滑動窗口。

![[Pasted image 20251024164050.png]]

發送方應該如下響應事件：
- 上層調用：被調用時，確認窗口是否已滿。如果已滿(發送但未確認的分組數等於窗口大小)則拒絕服務。否則，產生一個分組並發送，然後更新相應變量。
- 收到 ACK：若序號在窗口內，將該分組標示為已接收。如果序號等於 `send_base` 則 `send_base` 向前移動到具有最小序號的未確認分組處。
- 超時：每個分組有單獨的計時器，一次計時器超時只會造成一個分組重發。

接收方應該如下響應事件：
- 序號在 `[rcv_base, rcv_base + N - 1]` 內的分組被正確接收：分組落在接收窗口內，發送該序號的 ACK 給發送方。如果該分組還未緩存，緩存該分組。如果接收到的分組序號等於 `rcv_base`，將從 `rcv_base` 起的連續已緩存分組交付給上層。
- 序號在 `[rcv_base - N, rcv_base - 1]` 內的分組被正確接收：分組落在接收窗口外，但仍需產生一個 ACK，即便接收方已確認過該分組。
- 其他情況：忽略該分組。

注意，接收方的重複發送已確認分組 ACK 是必須的。

例如，如果接收方發出的 ACK 丟包，發送方無法正確更新 `send_base`。此時，發送方因為超時會導致重發。如果接收方沒有再次給出 ACK，會導致發送方窗口永遠無法更新。

下圖模擬了一次 SR 運行過程：

![[Pasted image 20251024165612.png]]

需要注意，因為發送方與接收放互相不知道對方窗口位置，所以會導致以下狀況：

![[Pasted image 20251025163559.png]]

如上圖所示，因為接收雙方互相不知曉對方的窗口狀態，所以無法識別是情況 a 還是情況 b。也就是說，接收方無法知曉當前接收的分組是舊的分組還是新的分組，這是非常致命的。

## 窗口長度

假設窗口長度為 $N$，最大序號為 $W$，則：

對 GBN 來說，窗口最大長度為：$N<W$。

對 SR 來說，窗口最大長度為：$N< \frac{W}{2}$。

# 面向連接運輸：TCP

## TCP 連接

TCP 稱為**面向連接的(connection oriented)**，因為程序在開始發送數據前必須互相握手。這種連接是邏輯上存在的，而非實際存在的。連接狀態只保留在程序中，而不會保留在中間更底層的網絡設備中。

TCP 是**全雙工(full-duplex)** 的，也就是連接雙方都可以發送與接收數據。

通信雙方建立連接後，TCP 會將即將發送的數據放進緩存，然後在適合的時間從緩存發送這些數據。

TCP 一次從緩存中取出的數據大小取決於 **MSS(Maximum Segment Size)** 。一 MSS 代表報文段中有效載荷的最大長度(不包含首部)。

MSS 的大小取決於**最大傳輸單元(Maximum Transmission Unit, MTU)** 的大小。MTU 是鏈路層上一個最大鏈路層幀的大小，通常 MTU 為 1500 Bytes，所以 MSS 通常設置為 1460。(TCP 首部 20 Bytes + IP 首部 20 Bytes)

而接收方收到數據後，也會先存在接收緩存中，直到進程從緩存讀取數據。

## TCP 報文段結構

![[Pasted image 20251025172819.png]]

上圖為 TCP 報文段結構。

包含以下字段：
- 32 bits 序號字段 (sequence number field)：等會兒說。
- 32 bits 確認號字段 (acknowledgement number field)：等會兒說。
- 16 bits 接收窗口字段 (receive window field)：接收方願意接受的字節數。用於流量控制。
- 4 bits 首部長度字段 (header length field)：因為 TCP 首部長度可變，用來標示首部長度。
- 可選與變長的選項字段 (options fields)：現在不會沒關係。
- 6 bits 標記字段 (flag field)：ACK bit 說明該報文段包含一個對成功接收的報文段的確認。RST SYN FIN bit 用於連接建立與拆除。

TCP 報文段中的序號與確認好非常重要喔～

TCP 會隨機的選擇一個初始序號當作要發送的第一個報文段的序號(指向有效載荷的第一個字節)。對於第二個發送的報文段序號，則是初始序號 + 第一個報文段的長度(字節)。第三個報文段的序號則是初始序號 + 第一個報文段 + 第二個報文段的長度... 以此類推。

而確認號則表示當前主機期望收到的報文段序號。例如，主機 A 與主機 B 在通訊。A 收到了 B 的 0~535 字節，那麼確認號應為 536。又例如，A 收到了 B 的 0~535 字節，又亂序收到了 900~1000 字節，確認號仍為 536。因為 TCP 只確認連續到來的字節 + 1。

因為 TCP 是全雙工的(full-duplex)，所以使用**捎帶(piggybacked)** 技術。

也就是說，正在通訊的雙方會將數據與給對方的回應 ACK 綁在同一個報文段中傳輸。

以下給出一個使用 telnet 通訊的例子：

![[Pasted image 20251025175354.png]]

## 往返時間的估計與超時

因為 RTT 在通訊過程中是變動的，所以我們需要一些技術來幫助我們設置超時計時器長度。

### 估計往返時間

我們使用 EstimatedRTT 估計我們對將來往返時間的期待。EstimatedRTT 的初始值被設置為第一個未重傳且收到 ACK 的報文段的往返時間。

TCP 對所有未重傳且收到 ACK 的報文段測量樣本 RTT(SampleRTT)，然後使用加權平均來計算 EstimatedRTT：

$$
\text{EstimatedRTT}=(1-\alpha)\text{EstimatedRTT}+\alpha\text{SampleRTT}
$$

其中，$\alpha$ 的推薦值為 $\alpha=0.125$。

而 EstimatedRTT 的指數表達形式為：

$$
\text{EstimatedRTT}_{n}=\alpha \sum_{k=1}^{n}(1-\alpha)^{n-k}\text{SampleRTT}_{k}
$$

也就是說，距離當前預估 RTT 較近的 SampleRTT 佔有較大的比重。這種平均方式稱為**指數加權移動平均(Exponential Weighted Moving Average, EWMA)**。

除了計算 EstimatedRTT，我們還需估算 SampleRTT 偏離 EstimatedRTT 的程度：

$$
\text{DevRTT}=(1-\beta)\text{DevRTT}+\beta|\text{SampleRTT}-\text{EstimatedRTT}|
$$

其中，$\beta$ 的推薦值為 $\beta=0.25$。

### 設置與管理重傳超時間隔

超時間隔設置公式如下：

$$
\text{TimeoutInterval}=\text{EstimatedRTT}+4\text{DevRTT}
$$

推薦的初始 TimeoutInterval 值為 1 秒。

當超時出現，TimeoutInterval 將會短暫的被設置為兩倍，避免超時重傳的報文段再次超時。

但是，只要收到新的 ACK 並更新了 EstimatedRTT，TimeoutInterval 就會被使用上述公式重新設置。

## 可靠數據傳輸

為每個報文段都設置一個計時器的代價過於高昂，所以本文講述的 TCP 都使用單一計時器的設計。

雖然單一計時器會導致某些報文段的丟失可能經過較久才被檢測，但是節省了內存與處理器開銷。

讓我們先給出一個高度簡化的 TCP 發送方偽代碼：

``` plaintext
NextSeqNum = InitialSeqNumber
SendBase = InitialSeqNumber

loop (forever) {
	switch (event)
	
		event: data received from application above
			create TCP segment with sequence number NextSeqNum
			if (timer currently is not running)
				start timer
			pass segment to IP
			NextSeqNum += length(data)
			break;
		
		event: timer timeout
			retransmit not-yet-acknowledged segment with smallest sequence number
			start timer
			break;
		
		evnet: ACK received, with ACK field value of y
			if (y > SendBase) {
				SendBase = y
				if (there are currently not-yet-acknowledged segments)
					start timer
			}
			break;
}
```

需要注意的是，TCP 採用累積確認，也就是說 ACK y 說明字節編號在 y 之前的所有字節都已確認收到。

但不要以為使用累積確認 TCP 就會丟棄失序的報文段，相反，**TCP 會將失序的報文段緩存起來**。

所以，TCP 實際上是 GBN 與 SR 的混合體。

因為 TCP 只維護一個 SendBase 與 NextSeqNum，所以看起來不像 SR。又因為超時重傳只會重傳具有最小未確認序號的報文段，所以看起來不像 GBN。

注意，如果一個 ACK n 丟失，但是在超時前收到一個 ACK (n+1)，TCP 也不會重傳 n。因為採用累積確認，這保證了收到 (n+1) 就一定收到了 n。

接下來，讓我們討論更多 TCP 實現的功能。

### 超時間隔加倍

當超時事件發生，TCP 會將超時間隔設置為原本的兩倍。

但是，只要當收到上層應用的數據或收到 ACK 導致計時器被啟動，超時間隔就會被重新設置為 TimeoutInterval。

### 快速重傳

**冗餘 ACK(duplicate ACK)**：對某個報文段超過一次的確認。

為了理解冗餘 ACK 出現的情況，我們統整了下表：

| 事件                                 | TCP 接收方操作                                 |
| ---------------------------------- | ----------------------------------------- |
| 具有所期望序號的報文段按序到達。所有在期望序號以前的數據都已被確認。 | 延遲的 ACK。等待 500ms，若時間內沒有按序的報文段到達，單獨發送 ACK。 |
| 具有所期望序號的報文段按序到達。另一個按序報文段等待 ACK 傳輸。 | 立即發送累積 ACK，以同時確認兩個按序報文段。                  |
| 比期望序號大的報文段失序到達。檢測出間隔。              | 立即發送冗餘 ACK，指示下一個期待字節序號。(指向間隔低端的序號)        |
| 能部分或完全填充接收數據間隔的報文段到達。              | 若該報文段位於間隔低端，立即發送 ACK。                     |

當發生冗餘 ACK 時，代表一個序號比預期大的報文段失序到來。那麼，如果連續收到多個冗餘 ACK 就表示具有預期序號的報文段很有可能丟失了。

所以，一旦收到 3 個冗餘 ACK (也就是對同一個序號的 4 次 ACK，一次正常 ACK 三次冗餘 ACK)
，就會觸發**快速重傳(fast retransmit)**，將具有該序號的報文段重傳。

使用以下偽代碼代替上述簡易版 TCP 偽代碼：

``` plaintext
event: ACK received, with ACK field value of y
if (y > SendBase) {
	SendBase = y
	if (there are currently not-yet-acknowledged segments) 
		start timer
	else {
		increament number of duplicate ACKs recieved for y
		if (number of duplicate ACKs recieved for y == 3)
			resend segment with sequence number y
	}
	break;
}
```

## 流量控制 (flow control)

之前說過，接收方有一個接收緩衝區。收到的數據會先存在其中，等進程需要才會讀取。

但是，進程可能剛好在忙著幹別的事，沒空讀緩存。如果這時發送方一直不斷地發送數據，就會導致緩衝區溢出。

所以，TCP 需要做流量控制。通過在發送方維護一個**接收窗口(receive window, rwnd)** 實現。因為 TCP 是全雙工通信，所以在連接雙方都各維護一個接收窗口。

為了簡化描述，在此我們假設 TCP 接收方丟棄所有失序的報文段。

假設主機 A 透過 TCP 傳給主機 B 一個文件。B 為該連接分配了一個接收緩存，我們使用 `RcvBuffer` 表示其大小。我們定義以下變量：
- `LastByteRead`：B 的進程從緩存讀取出數據流的最後一個字節的編號。
- `LastByteRcvd`：B 接收到緩存中的數據流的最後一個字節編號。

為了避免溢出，下式必須成立：

$$
\text{LastByteRcvd}-\text{LastByteRead}\leq \text{RcvBuffer}
$$

而接收窗口的大小由緩存空間可用大小動態計算：

$$
\text{rwnd}=\text{RcvBuffer}-[\text{LastByteRcvd-LastByteRead}]
$$

B 在初始時設定 `rwnd = RcvBuffer`，之後動態計算 `rwnd` 的大小。

B 通過將 `rwnd` 的值存在 ACK 中的 receive window 字段，通知 A 當前緩存可用大小。

A 必須保證發送到連接中但未被確認的數據量小於等於 `rwnd`，才能保證 B 的緩存不會溢出。所以，A 還需要維護兩個變量：`LastByteSent` 與 `LastByteAcked`，使得：

$$
\text{LasyByteSent}-\text{LastByteAcked}\leq \text{rwnd}
$$

我們需要考慮 `rwnd = 0` 時的狀況。如果此時 B 的緩存清出空間了，但是 A 沒有發送數據，B 也沒有發送數據給 A，則 A 會以為 B 的緩存還是滿的！

所以此時 A 會每經過一段時間發送 Zero-Window Probe，通常是一個一字節的報文段，直到 B 的緩存清出空間給 A 用。

## TCP 連接管理

一次 TCP 三次握手如下建立：
1. 客戶端向服務器發送一種特殊的報文段 **SYN 報文段(SYN segment)**。該報文段不包含應用層數據，且將標誌為中的 SYN bit 置 1 。客戶端會隨機選擇 `client_isn` 當作初始序號，並將該值放於序號字段中。
2. 服務器接收到 SYN 報文段，為該連接配置緩存與變量。然後，服務器向客戶端發送 **SYNACK 報文段(SYNACK segment)**，該報文段也不包含應用層數據，並且 SYN bit 置 1。服務器會隨機選擇 `server_isn` 當作初始序號，並存放於序號字段中。最後，在確認字段放入 `client_isn + 1`。
3. 客戶端收到 SYNACK 報文段，為該連接分配緩存與變量。然後發送一個報文段給服務器，因為連接已建立，所以不需要將 SYN bit 置 1。最後，在報文段的確認字段填入 `server_sin + 1` 並附上應用層想傳送給服務器的數據。

![[Pasted image 20251026223025.png]]

TCP 的四次揮手如下：
1. 客戶端向服務器發送一個 FIN bit 置 1 的報文段，表明想結束連接。
2. 服務器發送一個 ACK。然後發送最後的資料。
3. 服務器發送完最後的資料，也發送一個 FIN 報文段。
4. 客戶端回覆 ACK，並等待兩個最長報文壽命，然後關閉連接。

以下是一個 TCP 客戶端經歷的典型狀態序列：

![[Pasted image 20251026223849.png]]

以下是一個 TCP 服務端經歷的典型狀態序列：

![[Pasted image 20251026224105.png]]

# 雍塞控制原理

## 雍塞原因與代價

1. 兩個發送方與一個有無限大緩衝區的路由器

假設 A 與 B 都以 $\lambda_{\text{in}}\text{ Bytes/s}$ 的速度發送數據到連接中。忽略重傳，流量控制，雍塞控制。

假設該路由器通過一段容量為 $R\text{ bps}$ 的共享式輸出鏈路來發送數據。

下圖 (a) 展示了**每連接的吞吐量(per-connection throughput)**，(b) 展示了隨著 $\lambda_{\text{in}}$ 越接近 $R/2$，延遲的增加狀況。

![[Pasted image 20251027121834.png]]

當發送速率在 $0\sim R/2$ 之間，接收方的吞吐量等於發送方的發送數據，大於 $R/2$ 時，則會被限制在 $R/2$。這是因為兩個主機共享一條鏈路造成的，無論將傳送速率設置的多快，吞吐量都不會超過 $R/2$。

這樣看來，將 $\lambda_{\text{in}}$ 設置為 $R/2$ 貌似是一個非常好的選項？太天真了，看看右圖。當發送速率接近於 $R/2$ 時，延遲接近於無限。

這就是雍塞網絡的一個代價，**當到達速率接近鏈路容量時，排隊延遲巨大。**

2. 兩個發送方與一個有限緩衝區的路由器

這種情況下，分組到達一個已滿的緩衝區時會被丟棄，並且會被發送方重傳。

除了 $\lambda_{\text{in}}$ 表示初始數據的傳輸速率，我們引入 $\lambda'_{\text{in}}$ 表示初始數據加上重傳數據的傳輸速率。有時 $\lambda'_{\text{in}}$ 被稱為**供給載荷(offered load)**。

在這種假設下，我們考慮三種情況。

第一種情況：主機 A 可以確定路由器緩存是否空閒，僅當緩衝區空閒時才會發送分組。在此情況下，不會產生丟包。 $\lambda_{\text{in}}=\lambda'_{\text{in}}$，所以連接吞吐量等於 $\lambda_{\text{in}}$。注意，平均主機發送速率不能超過 $R/2$，因為假定不會發生丟包。此情況吞吐量如下圖 (a)。

第二種情況：發送方只在確定某個分組丟失才重傳。我們假設有 $\frac{1}{3}$ 的分組丟失，所以當 $\lambda'_{\text{in}}=R/2$ 時，只有 $\frac{R}{2 }\times \frac{2}{3}=R/3$ 的數據是真正被接收到的數據。在此，我們又可以看到一個網絡雍塞造成的問題，**發送方必須執行重傳以補償因為緩衝區溢出而發生的丟包。** 此情況的吞吐量如下圖 (b) 所示。

第三種情況：發送方可能因為提前超時而重傳還在路由器隊列中排隊但未丟失分組。此時，接收方會收到兩份一樣的分組，重傳分組會被丟棄。假設每個分組都被重傳過一次，那麼 $\lambda'_{\text{in}}=R/2$ 時，真正接收到的數據吞吐量只有 $\frac{R}{2} \times \frac{1}{2}=R/4$。所以，我們又看到了網絡雍塞造成的一個問題，**發送方遇到大延遲時，會進行不必要的重傳而造成路由器佔用鏈路帶寬來發送不必要的重傳分組**。此情況如下圖 (c) 所示。

![[Pasted image 20251027125507.png]]

3. 4 個發送方和具有有限緩衝區的多台路由器與多跳路徑

![[Pasted image 20251027132834.png]]

考慮從 A 到 C 的連接，該連接需要經過 R1 與 R2。連接與 D-B 共享 R1，與 B-D 共享 R2。

若 $\lambda_{\text{in}}$ 增加較小時，因為路由器緩衝區未滿，所以 $\lambda_{\text{out}}$ 也會增加。

但是，若 $\lambda_{\text{in}}$ 很大時(此時 $\lambda'_{\text{in}}$ 也很大)，考慮 B-D 連接與 A-C 連接。在 R2 上此二連接必須為有限的緩衝區競爭，所以當 B-D 供給載荷較大時， A-C 通過 R2 的流量較少。當 B-D 供給載荷接近無窮大時，A-C 在 R2 上的吞吐量接近於 0。如下圖所示。

![[Pasted image 20251027134958.png]]

這時，因為所有通過 R2 的 A-C 連接分組都被丟棄，相當於 R1 為 A-C 連接提供的流量都浪費了。

所以，我們又看到了另一個因為雍塞造成的代價。**當一個分組被丟棄，其上游路由器提供的傳輸容量因為該分組被丟棄而浪費**。

## 雍塞控制方法

- 端到端雍塞控制

  網絡層沒有對運輸層提供顯式的支持。即使網絡中存在雍塞，端系統也必須透過分組行為的觀察(超時或者三次冗餘確認)來推測網絡是否雍塞。在 TCP 中，報文段丟失被認為是網絡雍塞的一個跡象，TCP 會相應減少其窗口長度。

- 網絡輔助的雍塞控制

  在網絡輔助的雍塞控制中，路由器向發送方提供關於網絡中雍塞狀態的顯式信息。這種反饋簡單的用 1 bit 來指示網絡中的雍塞情況。

# TCP 雍塞控制

## 經典的 TCP 雍塞控制

首先，我們來介紹 TCP 如何限制發送流量。

發送方 TCP 中維護著一個變量，**雍塞窗口(congestion window, cwnd)**。此窗口對發送流量進行了限制，一個發送方中已發送但未被確認的數據量不會超過 `cwnd` 與 `rwnd` 的最小值。

$$
\text{LastByteSent}-\text{LastByteAcked} \leq \text{min}\{\text{cwnd, rwnd}\}
$$

為何限制 `cwnd` 就可以限制傳輸速度？因為在 RTT 開始時，發送方開始發送 `cwnd` 個字節的數據，然後在 RTT 結束時，發送方收到接收方傳回的 ACK。所以發送速率大約為 $\text{cwnd/RTT Bytes/s}$。

當 TCP 收到一個 ACK 時，會認為網絡狀況良好，從而增加 `cwnd`。ACK 到達速率快，窗口增長速率快，反之，慢。所以，TCP 被稱為**自計時(self-clocking)** 的。

1. **慢啟動(slow-start)**

初始時，`cwnd` 的值被設為一個 MSS 的較小值。

在慢啟動階段，**每個**報文段首次被確認窗口大小就會增加一個 MSS。(一個 RTT 可能增加多個 MSS，呈指數增長)

其中，我們維護一個變量 `ssthresh`，當 `cwnd` 的值等於 `ssthresh` 時，結束慢啟動並轉移到雍塞避免模式。

慢啟動何時結束：
- `cwnd == ssthresh`：從慢啟動轉換到雍塞避免。
- 超時：將 `ssthresh = cwnd / 2`，然後將 `cwnd = 1 MSS`，重新開始慢啟動。
- 收到三個冗餘 ACK：執行快速重傳，`ssthresh = cwnd / 2`，`cwnd = ssthresh + 3 * MSS`， 然後進入快速恢復階段。

2. **雍塞避免(congestion avoidance)**

進入雍塞避免狀態時，代表此時的 `cwnd` 大約為上次遇到雍塞時的一半(當 `cwnd == ssthresh` 時切換到雍塞避免狀態)，距離雍塞可能並不遠。

所以，TCP 採用較為保守的方式增加窗口。每個 RTT 只將 `cwnd` 增加一個 MSS，也就是說，每個 ACK 增加 `MSS/cwnd` 個字節。

雍塞避免何時結束：
- 超時：`ssthresh = cwnd / 2`，`cwnd = 1 MSS`，然後回歸慢啟動狀態。
- 冗余 ACK：`ssthresh = cwnd / 2`，`cwnd = ssthresh + 3 * Mss`，並進入快速恢復階段。

3. **快速恢復(Fast recovery)**

進入快速恢復階段後，每收到一個冗餘 ACK 都會 `cwnd += 1 MSS`。

快速恢復何時結束：
- 超時：`ssthresh = cwnd / 2`，`cwnd = 1 MSS` 並進入慢啟動階段。
- 收到一個對丟失報文段的 ACK：`cwnd = ssthresh` 然後進入雍塞避免階段。

![[Pasted image 20251027213728.png]]

TCP 有一種古老的模式 TCP Tahoe，沒有快速恢復階段，無條件將雍塞窗口設為 1 MSS。而較新版 TCP Reno 中，綜合了快速恢復。

下圖對比了 TCP Reno 與 TCP Tahoe 的運行(TCP Reno 省略從快速恢復轉到雍塞避免時將 `cwnd = ssthresh` 沒畫)：

![[Pasted image 20251027221949.png]]

4. 對 TCP 吞吐量的宏觀描述

讓我們分析一個長期存活的 TCP 連接的平均吞吐量。在此，我們省略由於超時而出現的慢啟動階段。該階段通常非常短，因為發送方會以指數增長離開該階段。

我們假設網絡最高可給予此連接的速率是 $W$，$W$ 與 RTT 在整個連接中幾乎保持不變。

因為每當速率增長到 $W$ 時：
1. 超時：掉到 `cwnd = 1`，然後開始慢啟動。但是因為慢啟動時間忽略，所以可以視為 `cwnd = W/2`。
2. 冗余 ACK：`ssthresh = cwnd / 2, cwnd = ssthresh`。

所以，在整個連接中數據傳輸的速率不斷在 $\text{W/RTT}$ 與 $\text{W/}2\times\text{RTT}$ 間變化。所以平均吞吐量為：

$$
\text{Avg Throughput}= \frac{0.75\times W}{\text{RTT}}
$$

## 公平性

考慮 $K$ 條 TCP 連接，每條都有不同端到端路徑，但是都經過一段傳輸速率為 $R\text{ bps}$ 的瓶頸鏈路。

一個公平的雍塞控制機制需要保證：每條連接的平均傳輸速率 $\approx R/K$。

讓我們假設一個忽略了慢啟動，並且整個連接都處於雍塞避免階段的兩個連接。

![[Pasted image 20251027232243.png]]

假設一開始連接 1 與 2 實現了 A 點的吞吐量。因為此時兩連接的共同吞吐量和 $<R$，所以雍塞避免階段會對兩個連接的雍塞窗口一直加 1 MSS，使得由 A 向 $45^{\circ}$ 線前進。

當處於 B 點時，因為吞吐量總和大於 $R$，發生丟包。然後雍塞窗口變為一半，來到 $C$ 點。持續此行為，最後會收斂到平等寬帶共享線的附近。