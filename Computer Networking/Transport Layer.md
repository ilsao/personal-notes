
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