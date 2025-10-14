
# 網絡應用體系結構

## 客戶-服務器體系結構(client-server architecture)

在客戶-服務器體系結構中，客戶端不會直接互相通信，而是通過服務器通信。

缺點：一台單獨的服務器主機無法跟上客戶請求，需要託管大量主機的數據中心。

## P2P 體系結構(P2P architecture)

在 P2P 體系結構中，端到端之間直接通信，擁有良好的可拓展性。

缺點：不安全。

# HTTP

HTTP 是一個**無狀態協議(stateless protocol)**，也就是 HTTP 不會保存任何關於客戶的信息。

## 非持續連接與持續連接

### 往返時間

**往返時間(Round-Trip Time, RTT)**：一個分組(極小，可能 1 byte)從客戶端傳輸到服務端再傳回客戶端所需要的時間。

因為分組過小，所以 RTT 不用計算傳輸(transmission)時間，只需要計算：傳播(propagation)延遲 + 處理延遲 + 排隊延遲。

1. 非持續連接

   對於請求的所有對象，都需要單獨建立一個連接。
   
   例如，首先請求一個 `index.html`，html 中包含了 10 個圖像。
   (1) 客戶端在 80 端口發起 TCP 連接，等待連接建立。
   (2) 客戶端發送請求。
   (3) 服務器接收請求，返回文件。
   (4) 等客戶端收到文件，關閉連接。
   (5) 客戶端解析文件，發現文件內包含 10 個圖像。
   (6) 對 10 個圖像都重複以上操作。所以總共會有 11 (1 + 10) 個請求。

   創建一個連接所需要的時間：三次握手(客戶端傳報文，服務段回，客戶端確認)，在第三次握手時，會將請求和第三次的確認一同發送。所以需要兩個 RTT。
   
   而傳輸一個文件的時間為：2 * RTT + 服務器傳輸文件到客戶端的時間。

![[Pasted image 20250917002606.png]]

   這代表每次多創建一次連接就會浪費一個 RTT 時間。這時就出現了新技術，持續連接。

2. 持續連接

   HTTP/1.1 支持持續連接，使得服務器響應後仍可保持 TCP 連接，直到超時還未使用。

## HTTP 報文格式

以下提供一個典型的 HTTP 請求報文：

``` 
GET /somedir/page.html HTTP/1.1
Host: www.someschool.edu
Connection: close
User-agent: Mozilla/5.0
Accept-language: fr
```

HTTP 請求報文的第一行為**請求行(request line)**，後續稱為**首部行(header line)**。

其中，`Connection: close` 表示**不要**使用持續連接，一旦發送完請求的對象就斷開連接。

HEAD 方法類似於 GET ，但是服務器響應 HTTP 報文後不會返回請求對象。HEAD 的常見用法是調試。

PUT 方法用來上傳對象到服務器，而 DELETE 方法用來刪除服務器中的對象。

![[Pasted image 20250917004115.png]]

上圖為一個請求報文的通用格式，其中**實體體(entity body)** 在 GET 方法時為空，只有使用 POST 方法時才會使用。實體體通常包含用戶輸入的字符，使得服務器依據其內容響應或更新內容。

以下提供了一條典型的 HTTP 響應報文：

```
HTTP/1.1 200 OK
Connection: close
Date: Tue, 18, Aug 2015 15:44:04 GMT
Server: Apache/2.2.3 (CentOS)
Last-Modified: Tue, 18 Aug 2015 15:11:03 GMT
Content-Length: 6821
Content-Type: text/html

(data ...)
```

![[Pasted image 20250917005952.png]]

上圖為響應報文的通用格式。

響應報文第一行為**狀態行(status line)**，接著六個首部行，再接著實體體。

`Data` 中的數據是服務器從文件系統中檢索到請求對象的時間。

`Last-Modified` 表示對象創建或最後修改的時間，對於 HTTP 緩存的實現至關重要。

以下列出常見狀態碼(引用：[這篇文章][https://xiaolincoding.com/network/2_http/http_interview.html#http-%E5%B8%B8%E8%A7%81%E7%9A%84%E7%8A%B6%E6%80%81%E7%A0%81%E6%9C%89%E5%93%AA%E4%BA%9B])：

1xx 類狀態碼屬於提示信息，是協議處理中的一種中間狀態，實際用到的比較少。

2xx 類狀態碼表示服務器成功處理了客戶端的請求，也是我們最願意看到的狀態。

「200 OK」是最常見的成功狀態碼，表示一切正常。如果是非 HEAD 請求，服務器返回的響應頭都會有 body 數據。

「204 No Content」也是常見的成功狀態碼，與 200 OK 基本相同，但響應頭沒有 body 數據。

「206 Partial Content」是應用於 HTTP 分塊下載或斷點續傳，表示響應返回的 body 數據並不是資源的全部，而是其中的一部分，也是服務器處理成功的狀態。

3xx 類狀態碼表示客戶端請求的資源發生了變動，需要客戶端用新的 URL 重新發送請求獲取資源，也就是重定向。

「301 Moved Permanently」表示永久重定向，說明請求的資源已經不存在了，需改用新的 URL 再次訪問。

「302 Found」表示臨時重定向，說明請求的資源還在，但暫時需要用另一個 URL 來訪問。

301 和 302 都會在響應頭裡使用字段 `Location`，指明後續要跳轉的 URL，瀏覽器會自動重定向新的 URL。

「304 Not Modified」不具有跳轉的含義，表示資源未修改，重定向已存在的緩沖文件，也稱緩存重定向，也就是告訴客戶端可以繼續使用緩存資源，用於緩存控制。

4xx 類狀態碼表示客戶端發送的報文有誤，服務器無法處理，也就是錯誤碼的含義。

「400 Bad Request」表示客戶端請求的報文有錯誤，但只是個籠統的錯誤。

「403 Forbidden」表示服務器禁止訪問資源，並不是客戶端的請求出錯。

「404 Not Found」表示請求的資源在服務器上不存在或未找到，所以無法提供給客戶端。

5xx 類狀態碼表示客戶端請求報文正確，但是服務器處理時內部發生了錯誤，屬於服務器端的錯誤碼。

「500 Internal Server Error」與 400 類型，是個籠統通用的錯誤碼，服務器發生了什麼錯誤，我們並不知道。

「501 Not Implemented」表示客戶端請求的功能還不支持，類似「即將開業，敬請期待」的意思。

「502 Bad Gateway」通常是服務器作為網關或代理時返回的錯誤碼，表示服務器自身工作正常，訪問後端服務器發生了錯誤。

「503 Service Unavailable」表示服務器當前很忙，暫時無法響應客戶端，類似「網絡服務正忙，請稍後重試」的意思。

「505 HTTP Version Not Supported」 表示服務器不支持請求報文使用的 HTTP 版本。

## 用戶與服務器的交互：cookie

因為 HTTP 服務器是無狀態的，所以需要通過 cookie 來識別用戶。

cookie 有 4 個組件：
1. HTTP 響應報文中的 cookie 首部行。
2. HTTP 請求報文中的 cookie 首部行。
3. 用戶端保存的 cookie 文件，由瀏覽器留存。
4. Web 站點的後端數據庫。

## Web 緩存

**Web 緩存器(Web cache)** 也稱**代理服務器(proxy server)**，能夠代理初始 Web 服務器來滿足 HTTP 請求。

通常來說，一個配置正確的瀏覽器的所有請求都先被重定向到 Web 緩存器中。一次瀏覽器請求對象的流程如下：
1. 瀏覽器創建一個到 Web 緩存器的 TCP 連接，並向 Web 緩存器發送 HTTP 請求。
2. Web 緩存器檢查本地是否有該對象緩存。若有，Web 緩存器就用 HTTP 響應報文返回該對象。
3. 若無，Web 緩存器就創建到初始 Web 服務器的 TCP 連接，並向初始 Web 服務器請求該對象。
4. Web 緩存器接收對象並緩存，然後返回該對象給瀏覽器。

### 條件 GET 方法

HTTP 使用**條件 GET(conditional GET)** 來保證緩存器中的對象總是最新的。

當代理服務器向初始服務器發送請求報文後，得到的響應報文會包含一個 `Last-Modified` 手部行，表明最後修改時間。

當瀏覽器向代理服務器發送請求，且該請求的文件距離 `Last-Modified` 已經過了一段時間，代理服務器就會向初始服務器發送條件 GET 來檢查對象是否更新。

緩存器發送一個條件 GET 報文：

```
GET /somedir/kiwi.gif HTTP/1.1
Host: www.somewebsite.com
If-modified-since: Wed, 9 Sep 2015 09:23:24
```

初始服務器會檢查文件是否更新，若發生更新則返回該對象。否則返回一個不包含實體體的響應報文：

```
HTTP/1.1 304 Not Modified
Date: Sat, 10 Oct 2015 15:39:29
Server: Apache/1.3.0 (Unix)

(empty entity body)
```

# 電子郵件

電子郵件系統由三個主要部分組成：
- **用戶代理(user agent)**：用來將郵件傳送到郵件服務器或接收報文。
- **郵件服務器(mail server)**：每個接收方在郵件服務器上都有一個郵箱，管理維護著發送給他的報文。
- **簡單郵件傳輸協議(Simple Mail Transfer Protocol, SMTP)**

一個典型的郵件發送過程是：發送方的用戶代理傳送到發送方的郵件服務器，然後郵件被分發給收件方的郵件服務器，最後被發送到收件方的郵箱中。

如果發送方的服務器不能將郵件交付給接收方的郵件服務器，發送方的郵件服務器會將該郵件存儲在**報文隊列(message queue)** 中，並在一段時間後再次嘗試。若幾天後仍不成功，服務器就會刪除該報文並以郵件方式通知發送方。

每台服務器都運行著 SMTP 的客戶端與服務端，當發送時則視為客戶端，接收時視為服務端。

## SMTP

SMTP 用於從發送方的郵件服務器發送報文到接收方的郵件服務器。而且報文內容僅接受七字節的 ASCII 碼，所以附件等多媒體文件必須先轉換為 ASCII 碼才能進行傳輸。

比較特殊的是，SMTP 不會使用中轉服務器，不論兩個互相通訊的服務器距離多遠。SMTP 將兩台服務器建立直接的 TCP 連接。

一旦 TCP 連接建立完成，就會開始通訊。以下給出一個例子：

``` 
S: 220 hamburger.edu
C: HELO crepes.fr
S: 250 Hello crepes.fr, pleased to meet you
C: MAIL FROM: <alice@crepes.fr>
S: 250 alice@crepes.fr ... Sender ok
C: RCPT TO: <bob@hamburger.edu>
S: 250 bob@hamburger.edu ... Recipient ok
C: DATA
S: 354 Enter mail, end with "." on a line by itself
C: Do you like ketchup?
C: How about pickles?
C: .
S: 250 Message accepted for delivery
C: QUIT
S: 221 hamburger.edu closing connection
```

SMTP 使用持續連接，如果有好幾個報文發往同一個郵箱，只需要使用一個新的 `MAIL FROM: crepes.fr` 就可以開始發送一個新的郵件。

## 郵件報文格式

前述的那些指令屬於 SMTP 握手協議的一部份，真正的郵件首部行位於報文前 DATA 命令後。

一個經典的報文首部如下：

```
From: ilsao@outlook.com
To: asciibase64@outlook.com
Subject: Test
```

# 郵件訪問協議

假設 Alice 要將郵件發給 Bob。

Alice 會用 SMTP 或 HTTP 協議將郵件發給自己的郵件服務器，然後 Alice 的郵件服務器會將郵件轉發給 Bob 的郵件服務器。

需要注意的是，當 Bob 的郵件代理想要拉取服務器的郵件時，無法使用 SMTP 協議。因為 SMTP 協議是一個推送協議。通常郵件代理會使用 HTTP(Gmail) 或 IMAP(outlook) 拉取郵件。

# DNS

常見的那些網址稱為**主機名(hostname)**。而通常，路由器使用 IP 地址來尋址。

IP 地址提供一種層次化的結構，使得從左往右掃會令資訊更佳精確。

## DNS 提供的服務

DNS(Domain Name System) 的主要服務是，將主機名轉換為 IP 地址。

DNS 是：
- 一個由層次化 DNS 服務所實現的分布式數據庫。
- 提供主機查詢分布式數據庫的應用層協議。

除此之外，DNS 還提供以下服務：
- **主機別名(host aliasing)**：一個較複雜的主機名可能有多個更好記得主機別名。例如 `relay1.east-coast.enterprise.com` 可能有這樣的主機別名： `enterprise.com` 或 `www.enterprise.com`。我們將原本較複雜的主機名**正規名稱(canonical hostname)**。DNS 提供主機別名到正規名稱的轉換(alias hostname -> canonical hostname)。
- **郵件服務器別名(mail server aliasing)**：同上，提供主機別名到正規名稱的轉換，只是此時別名的主機是郵件服務器。
- **負載分配(load distribution)**：對於一個繁忙的網站，通常會被複製到多個服務器上。所以，一個主機別名可以對應到很多 IP 地址。當用戶查詢這個名稱時，每次回覆會**輪換(rotation)** 這些地址(第一次返回第一個，第二次返回第二個......)。DNS 輪換可以將流量分散到不同的複製服務器。DNS 輪換也用在電子郵件系統中，使得多個郵件服務器可以共用一個別名。

## DNS 運行流程概覽

假設一個用戶應用需要查詢 IP。在該機器上的 DNS 客戶端會確認需要查詢的主機名，然後使用 UDP 將搜尋請求報文發送到 53 端口。一段延遲之後客戶端就會收到主機名到 IP 的映射。

僅運行單一一個 DNS 服務器是不可行也不可拓展的，因為：
- 如果該服務器崩潰，整個網絡的 DNS 都會崩潰。
- 流量過大，單一服務器無法完成服務。
- 該服務器無法靠近所有需要服務的節點。
- 數據量大，不好維護。

所以，DNS 被設計為一個**層次化分布式數據庫**系統。

通常來說，DNS 被分為三個層次：
1. **根 DNS 服務器(root DNS servers)**：提供主機名到 TLD 服務器的 IP 地址的轉換。
2. **頂級域名(Top-Level Domain) DNS 服務器** ：所有頂級域都由這種服務器提供映射。例如：`com, cn, fr, edu, org, net, gov` 等。提供主機名到權威服務器 IP 地址的轉換。
3. **權威 DNS 服務器(authoritative DNS server)** ：儲存主機名到真實地址的映射，提供主機名到主機 IP 地址的轉換。

有一種特殊的 DNS 服務器，稱**本地域名服務器(local DNS sever，也稱 default name server)**。雖然它不屬於任何層次，但是還是非常重要。每個 ISP 都會有一個本地域名服務器，用戶想要查詢某主機名的地址時，會由本地域名服務器代為查詢。如果本地域名服務器內有該地址的緩存，也可以直接返回緩存的地址給用戶。

還有額外的一種 DNS 服務器，稱**中繼域名服務器(intermediate DNS server)**。之前我們總是假設每個層次的服務器知道下一層次的服務器地址，但很可能這種假設不成立。當無法直接映射到目標地址時，會將請求發送到可能知道目標地址映射的中繼域名服務器，最後才得到權威域名服務器的地址。

**遞歸查詢(recursive queries)**：

![[Pasted image 20250930150055.png]]

**迭代查詢(iterative queries)**：

![[Pasted image 20250930150114.png]]

DNS 緩存：

在查詢鏈中，當 DNS 服務器收到一個 DNS 回覆，就可以將該映射緩存在本地內存中。

若緩存已經存在，則就算此服務器不是權威域名服務器也可以通過此服務器取得主機名到 IP 地址的映射。

## DNS 紀錄與訊息

DNS 服務器會紀錄**資源紀錄(Resource Records, RRs)**。一個資源紀錄表示如下：`(Name, Value, Type, TTL)`。

以下來詳細敘述各項參數：
- `Type = A`：代表此項為一個主機名(Name)與地址(Value)的映射。Ex: `(relay1.bar.foo.com, 145.37.93.126, A)` 
- `Type = NS`：代表此項為一個域名(Name)與其權威服務器名(Value)的映射。Ex: `(foo.com, dns.foo.com, NS)` 
- `Type = CNAME`：代表此項為一個主機別名(Name)與主機名(Value)的映射。Ex: `(foo.com, relay1.bar.foo.com, CNAME)` 
- `Type = MX`：代表此項為一個郵箱服務器的主機別名(Name)與主機名(Value)的映射。Ex: `(foo.com, mail.bar.foo.com, MX)` 

TTL(Time to Live) 代表緩存應該在多少時間後被刷新，單位是秒。

權威服務器一定會包含類型為 `A` 的紀錄，存放期望主機名與地址的映射。但不一定只有權威服務器有這條紀錄，其他服務器可能因為緩存所以暫時存放了這條紀錄。

一個非權威服務器應該包含一個類型為 `NS` 的紀錄，存放域名到權威服務器的映射。並且，還會存放一個類型為 `A` 的紀錄，存放權威服務器名與權威服務器地址的映射。

## DNS 報文

以下展示了一個 DNS 報文的結構，對於請求與回應該報文的結構都應該一樣。

![[Pasted image 20251002093811.png]]

首 12 字節為首部信息。`Identification` 用來將查詢與回應配對起來(因為同時會有很多查詢跟回應)。而 `flag` 項包含幾個位元標誌：
- 標示請求/回應
- 標示此服務器使否為權威服務器
- 標示此請求期望使用遞歸查詢
- 標示此服務器是否支持遞歸查詢

在 `Question` 區，包含了：
1. `Name`：包含了想要查詢的 `Name` 值。
2. `Type`：包含了想要查詢的 `Type` 值。

在 `Answer` 區，包含了一條或多條(一個主機名可能對應個地址，例如複製過的 Web 服務器)請求資源紀錄的直接回覆。

`Authority` 區包含了其他權威服務器的紀錄。如果此服務器無法直接回答，會通過此區域說明哪個服務器是權威服務器，通常為 `NS` 紀錄。

`Addtional` 區提供了與 `Authority` 區相關的資料。比如：`Authority` 提供了對應權威服務器的域名，則 `Addtional` 區可能會直接提供該域名的 IP 地址，方便用戶少走一步。

## 插入數據到 DNS 數據庫

我們通過 `Network Utopia` 為例，說明數據插入的過程。

我們需要在 registrar 註冊一個域名 `networkutopia.com` 。registrar 會幫我們查詢域名是否重複，並將我們的域名註冊到 DNS 數據庫中。

當我們在 registrar 處註冊域名時，我們需要提供主要與次要權威 DNS 服務器的名稱與 IP 地址。比如：`dns1.networkutopia.com`, `dns2.networkutopia.com`, `212.2.212.1`, `212.212.212.2`。

提供完這些數據後，registrar 會將類型為 NS 與 A 的紀錄插入到 TLD com 服務器中。例如：`(networkutopia.com, dns1.networkutopia.com, NS)`, `(dns1.networkutopia.com, 212.2.212.1, A)`。

我們還必須確保該權威域名服務器擁有類型為 A ，且包含 `networkutopia.com` 地址的紀錄，與類型為 MX 且包含 `mail.networkutopia.com` 的紀錄。

以上，大家就可以訪問這個網址啦！

# P2P 

老師說這個東西太老了大家都不用，所以跳過不講。但是我還是覺得它很重要，所以在這裡留下了它的一級標題。但是現在我要把它跳過啦，因為我感覺現在不太需要用它。等到真的需要的時候再回來學或去網上查資料吧～

# 影片串流與內容分發網絡 (Content Distribution Networks, CDN)

## HTTP 串流與 DASH

在 HTTP 串流中，影片被放在一個 HTTP 服務器上。客戶端使用 `GET` 請求來獲取服伺器上的影片文件。同時，將下載的數據放在一個緩衝區中，一旦緩衝區中的大小達到預先要求的大小，客戶端就會將緩衝區中的數據解壓解碼並開始播放。所以，串流使得可以邊下載邊播放影片。

但 HTTP 串流有很多缺點：
- 無法跳轉
- 無法根據網速自動切換解析度
- ...

所以我們需要另一種基於 HTTP 方法來解決這些缺陷，我們稱爲**基於 HTTP 的自適應串流協議(Dynamic Adaptive Streaming over HTTP)**。

在 DASH 中，影片會被編碼為不同解析度的多個小片段。客戶端會根據當前網絡環境自動調整使用 `GET` 下載的解析度。

在 DASH 的實現中，影片仍被存放在 HTTP 服務器中。該服務器會包含一個 **MPD(Media Presentation Description)** 文件，標示某個影片不同解析度的片段的存放位置等資訊。客戶端每次想播放影片前，必須先下載這種 `.mpd` 文件，才知道應該選擇哪種解析度的影片來下載。

## 內容分發網絡

傳統的 server - client 模型在影片串流中有以下三個主要缺點：
- 服務器(物理上的)無法靠近所有用戶，導致某些地區的用戶延遲較高(可能由於瓶頸鏈路導致)。
- 一個熱門的影片可能會需要多次重複傳輸。
- 如果這個提供影片的服務器炸了，那麼所有人都沒視頻好刷了。

所以，很多影片提供者使用內容分發網絡。CDN 服務會將內容分發在許多物理上分佈式的服務器上，希望用戶傾向於選擇距離較近 CDN ，以提供最佳的用戶體驗。

CDN 通常使用以下兩種部署策略之一：
- Enter Deep：深入到各 ISP 網絡中，在各 ISP 的網絡中建立服務器**叢集(cluster)**。使得服務器更靠近用戶，減少通過的路由器與鏈路量，從而減少延遲提升吞吐量。缺點是維護這一堆服務器很貴。
- Bring Home：不深入各 ISP 網絡，幾十個大型的節點中建立較少量的大型服務器叢集(通常設置在 IXP，各 ISP 會在 IXP 對等，剛好 CDN 部署在這裡可以連通不同 ISP)。維護開銷較低，架構也更集中更容易管理。

一旦 CDN 部署完畢，就會開始將內容複製到這些叢集中。但是不可能將所有東西都複製上去，萬一有一個幾十年前的陳年老片沒人看，不就白複製了嗎？所以在此，使用與 Web 緩存類似的方法。記得驅逐方式為 LRU 喔！

## CDN 的運作方式

當一個主機想要取得特定影片，CDN 需要先攔截該請求，並做下列操作：
1. 選擇最適合的 CDN 服務器叢集。
2. 重定向客戶端請求道該叢集的服務器中。

CDN 透過與 DNS 合作來達成攔截與重定向。

我們透過一個例子來了解，假設一個內容提供商 NetCinema 利用第三方 CDN KingCDN 來分發影片給客戶端。如果在 URL 中包含特定字符 video 則表示請求的是影片資源。

1. 客戶點擊包含 video 的鏈接，並發送 DNS 請求。
2. 用戶的本地 DNS 服務器 (LDNS) 發送請求到權威 DNS 服務器。權威 DNS 服務器發現 video 字符串，所以不會返回 IP 地址，而是返回一個到 KingCDN 域中的主機名，例如 a1105.kingcdn.com
3. 此時，DNS 請求進入到 KingCDN 的域中。LDNS 發送請求到 KingCDN 的 DNS 系統中，然後得到一個內容服務器的地址。
4. LDNS 轉發該地址給客戶端。
5. 客戶端建立 TCP 鏈接，並使用 HTTP GET 取得資源。

![[Pasted image 20251014131706.png]]

## 叢集選擇策略

一種簡單的方法是，**地理上最近(geographically closest)**。使用商用地理定位系統，可以很簡單的找到他們的物理地址。然後選擇地理上最靠近的叢集。

缺點：地理上最近不一定保證二者經過的路由器跳轉數少。實際上，LDNS也可能與客戶端非常遠。而且，這種方法還忽略的網絡狀況。如果延遲較高，也不會調整。

還有一種方法，稱**即時測量機制(real-time measurements)**。這種方法會定期評估 CDN 與客戶端的延遲與丟包率，動態選擇 CDN 叢集。例如，可以定期的發送探測訊號給 LDNS(例如 ping 封包或 DNS 查詢)

缺點：很多 LDNS 不會回應這種探測訊號。

# Socket Programming

老師不教，但是我很想學。所以我打算先把該補的內容補掉之後再來更新這部分內容。