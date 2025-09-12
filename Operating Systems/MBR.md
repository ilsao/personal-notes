
按下電腦電源鍵後，執行的第一個程序是 BIOS(Base Input Output System)。

閱讀本文後，應該可以回答以下問題：
1. 它由誰加載？
2. 加載到哪裡？
3. 它的 `cs:ip` 由誰更改？

# 實模式下的 1MB 內存布局

Intel 8086 有 20 條地址線，可以訪問 $0\sim2^{20}$ 的地址空間，也就是 1MB 大小。即， `0x00000` ~ `0xFFFFF`。

以下為實模式下的內存布局：

| 起始      | 結束      | 大小         | 用途                                        |
| ------- | ------- | ---------- | ----------------------------------------- |
| `FFFF0` | `FFFFF` | 16B        | BIOS 入口地址，特意單獨拿出來討論                       |
| `F0000` | `FFFEF` | 64KB - 16B | 系統 BIOS 範圍                                |
| `C8000` | `EFFFF` | 160KB      | 映射硬件適配器的 ROM 或內存映射式 I/O                   |
| `C0000` | `C7FFF` | 32KB       | 顯示適配器 BIOS                                |
| `B8000` | `BFFFF` | 32KB       | 用於文本模式顯示適配器                               |
| `B0000` | `B7FFF` | 32KB       | 用於黑白顯示適配器                                 |
| `A0000` | `AFFFF` | 64KB       | 用於彩色顯示適配器                                 |
| `9FC00` | `9FFFF` | 1KB        | EBDA(Extended BIOS Data Area) 拓展 BIOS 數據區 |
| `7E00`  | `9FBFF` | 608KB      | 可用區域                                      |
| `7C00`  | `7DFF`  | 512B       | MBR 被 BIOS 加載到此處                          |
| `500`   | `7BFF`  | 30KB       | 可用區域                                      |
| `400`   | `4FF`   | 256B       | BIOS Data Area (BIOS 數據區)                 |
| `000`   | `3FF`   | 1KB        | Interrupt Vector Table (中斷向量表)            |

BIOS 存放在只讀存儲器上(Read-Only Memory, ROM)，由 ROM 加載。

CPU 中的 cs:ip 由 `0xF000 : 0xFFF0` 得到 `0xFFFF0`。段寄存器左移 4 位(1 字節)，加上段偏移。

得到的 `0xFFFF0` 是 BIOS 的入口地址，只有 16B，其中存放的是跳轉到真正 BIOS 代碼運行處的彙編代碼。

BIOS 會繳驗氣動盤中位於 0 盤 0 道 1 扇區的內容，此扇區的末尾必須為 `0x55` 和 `0xaa`，使得 BIOS 確認此處存放著 MBR(Master Boot Record，主引導紀錄)，並跳轉到 `0x7c00` 執行。