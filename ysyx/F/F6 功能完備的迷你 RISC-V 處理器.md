
# 迷你 RISC-V 指令集

RV32I 共有 42 條指令，但在此我們簡化成 8 條，用它們替代 RV32I 的功能。

我們可以從 https://github.com/riscv/riscv-isa-manual/releases/download/20240411/unpriv-isa-asciidoc.pdf 下在 RISC-V 的官方手冊。

六種基本指令格式如下：

![[ysyx/F/pic/F6/1.png]]

通過查找手冊，我們發現：
- PC 的位寬為 32 位，且低 2 位恆為零。(因為每條指令位寬固定 32 位 (4 字節)，所以內存始終與 4 字節對齊)
- GPR 共有 32 個，每個位寬 32 位。(其中 `x0` 恆硬編碼為零)
- `R[0]` 與 sISA 中的 `R[0]` 的區別在於 RISC-V 中的 `R[0]` 代表的 `x0` 寄存器恆硬編碼為零。
- 指令編碼的位寬為 32 位，有六種基本格式。
- 需要 5 位來表示一個 GPR，因為 5 位剛好可以覆蓋 `0 ~ 31` 的範圍。
- RV32E 是 RV32I 的精簡版本，縮減寄存器個數到 16 個 (`x0 ~ x15`)。

那麼，現在我們來說明 minirv 這個縮減版 ISA 的規範：
- `PC` 初始化為 0。
- GPR 數量為 16。 (與 RV32E 相同)
- 支持以下指令： `add`, `addi`, `lui`, `lw`, `lbu`, `sw`, `sb`, `jalr`。
- 其他 ISA 細節與 RV32I 相同。

## 只有兩條指令的 minirv 處理器

此部分先實現 `addi` 與 `jalr` 指令。

首先考慮 `addi` 指令。`addi` 指令格式如圖：

![[ysyx/F/pic/F6/2.png]]

![[ysyx/F/pic/F6/3.png]]

其次考慮 `jalr` 指令：

![[ysyx/F/pic/F6/4.png]]

![[ysyx/F/pic/F6/5.png]]

此指令會將立即數與指定寄存器 `rs1` 相加且最低位置零當作結果，該結果會被當成下一條指令的地址。而原本的下條指令地址 (`PC + 4`) 會被存入 `rd`。如果不須寫入，可以將 `rd` 填入 `x0`。

為了實現上的方便，我們直接使用 `Plexers/Multiplexer` 與 `Memory/Register` 組件而非自己實現。

值得注意的是，如果 `PC` 寄存器尋址的單位與 ROM 的寬度不一致，我們需要先轉換後再進行尋址。

並且，由於 minirv 指令較少，譯碼階段應避免使用譯碼器，而是使用比較器 (`Arithmetic/Comparator`)。

譯碼階段還需要注意立即數的處裡，注意判斷應該使用零擴展還是符號擴展。可以在 `Wiring/Bit Extender` 找到位擴展器並配置不同擴展方式。

對於 GPR，可以注意 `Plexers/Decoder` 中，譯碼器可以開啟 `Include Enable` 選項。我們應該思考如何使用此功能實現寫使能。

針對執行階段，我們可以使用 `Arithmetic/Adder` 實現加法功能。

目前階段我設計的 CPU 長這樣子：

![[ysyx/F/pic/F6/6.png]]

# 實現完整的 minirv 處理器

我們先來考慮 `add` 與 `lui` 指令的實現。

`add` 指令格式如圖：

![[ysyx/F/pic/F6/7.png]]

![[ysyx/F/pic/F6/8.png]]

`lui` 指令格式如圖：

![[ysyx/F/pic/F6/9.png]]

![[ysyx/F/pic/F6/10.png]]

# 為 minirv 添加圖形顯示功能

# 邁向現代化的處理器設計