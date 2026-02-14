# RTL 仿真 (Simulation) - 功能驗證

## RTL 仿真的基本原理

本質上是利用軟件模擬硬件電路。

例如如下流水燈 Verilog 代碼：

``` verilog
module light(
  input clk,
  input rst,
  output reg [15:0] led
);
  reg [31:0] count;
  always @(posedge clk) begin
    if (rst) begin led <= 1; count <= 0; end
    else begin
      if (count == 0) led <= {led[14:0], led[15]};
      count <= (count >= 5000000 ? 32'b0 : count + 1);
    end
  end
endmodule
```

可以通過以下 C 代碼進行仿真：

```c
#include <stdio.h>
#include <stdint.h>

#define _CONCAT(x, y) x ## y
#define CONCAT(x, y)  _CONCAT(x, y)
#define BITMASK(bits) ((1ull << (bits)) - 1)
// similar to x[hi:lo] in verilog
#define BITS(x, hi, lo) (((x) >> (lo)) & BITMASK((hi) - (lo) + 1))
// only use in struct
#define DEF_WIRE(name, w) uint64_t name : w
#define DEF_REG(name, w)  uint64_t name : w; \
                          uint64_t CONCAT(name, _next) : w; \
                          uint64_t CONCAT(name, _update) : 1
#define EVAL(c, name, val) do { \
                             c->CONCAT(name, _next) = (val); \
                             c->CONCAT(name, _update) = 1; \
                           } while (0)
#define UPDATE(c, name)    do { \
                             if (c->CONCAT(name, _update)) { \
                               c->name = c->CONCAT(name, _next); \
                             } \
                           } while (0)

typedef struct {
  DEF_WIRE(clk, 1);
  DEF_WIRE(rst, 1);
  DEF_REG (led, 16);
  DEF_REG (count, 32);
} Circuit;
static Circuit circuit;

static void cycle(Circuit *c) {
  c->led_update = 0;
  c->count_update = 0;
  if (c->rst) {
    EVAL(c, led, 1);
    EVAL(c, count, 0);
  } else {
    if (c->count == 0) {
      EVAL(c, led, (BITS(c->led, 14, 0) << 1) | BITS(c->led, 15, 15));
    }
    EVAL(c, count, c->count >= 5000000 ? 0 : c->count + 1);
  }
  UPDATE(c, led);
  UPDATE(c, count);
}

static void reset(Circuit *c) {
  c->rst = 1;
  cycle(c);
  c->rst = 0;
}

static void display(Circuit *c) {
  static uint16_t last_led = 0;
  if (last_led != c->led) { // only update display when c->led changes
    for (int i = 0; i < 16; i ++) {
      putchar(BITS(c->led, i, i) ? 'o' : '.');
    }
    putchar('\r');
    fflush(stdout);
    last_led = c->led;
  }
}

int main() {
  reset(&circuit);
  while (1) {
    cycle(&circuit);
    display(&circuit);
  }
  return 0;
}
```

## Verilator

測試以下代碼：

``` verilog
module our;
     initial begin $display("Hello World"); $finish; end
endmodule
```

使用：

```sh
verilator --binary -j 0 -Wall filename.v
```

可以將 Verilog 編譯成可執行檔案。

- `--binary`：創建一個可執行檔。
- `-j 0`：使用與機器擁有 CPU 數相匹的線程數。

如果想將上述代碼轉換成 C++，我們首先需要創建一個 C++ wrapper file：

```cpp
#include "Vour.h"
#include "verilated.h"
int main(int argc, char** argv) {
	VerilatedContext* contextp = new VerilatedContext;
	contextp->commandArgs(argc, argv);
	Vour* top = new Vour{contextp};
	while (!contextp->gotFinish()) { top->eval(); }
	delete top;
	delete contextp;
	return 0;
}
```

並使用以下指令：

```sh
verilator --cc --exe --build -j 0 -Wall sim_main.cpp our.v
```

- `--cc`：取得 C++ 代碼。
- `--exe`：取得可執行檔而不是一個庫。
- `--build`：幫你省去手動打 `make`。

## 示例：雙控開關

```verilog
module top(
  input a,
  input b,
  output f
);
  assign f = a ^ b;
endmodule
```

因為此模塊具有輸出與輸入端口，所以我們需要對 wrapper file 中的 while 循環進行修改。

類似：

```c++
// pseducode
#include <stdio.h>
#include <stdlib.h>
#include <assert.h>

while (???) {
  int a = rand() & 1;
  int b = rand() & 1;
  top->a = a;
  top->b = b;
  top->eval();
  printf("a = %d, b = %d, f = %d\n", a, b, top->f);
  assert(top->f == (a ^ b));
}
```

## 打印並查看波型

首先，在 wrapper file 中創建一個 `VerilatedFstC` 對象，並在 `eval()` 後調用 `traceobj->dump(contextp->time())`。最後，調用 `traceobj->close()`。

```cpp
#include "verilated_fst_c.h"
...
int main(int argc, char** argv) {
    const std::unique_ptr<VerilatedContext> contextp{new VerilatedContext};
    ...    
    Verilated::traceEverOn(true);    
    VerilatedFstC* tfp = new VerilatedFstC;    
    topp->trace(tfp, 99);  // Trace 99 levels of hierarchy (or see below)    
    // tfp->dumpvars(1, "t");  // trace 1 level under "t"
    tfp->open("obj_dir/t_trace_ena_cc/simx.fst");
    ...
    while (contextp->time() < sim_time && !contextp->gotFinish()) {        
	    contextp->timeInc(1);
        topp->eval();
        tfp->dump(contextp->time());
    }
    tfp->close();
}
```

並在編譯時使用選項 `--trace-fst`。

## 接入 NVBoard

因為咱沒有 FPGA，就用 NVBoard 模擬。

具體接入詳見：[NVBoard README](https://github.com/NJU-ProjectN/nvboard) 與項目示例：`nvboard/example/Makefile`。

## 靜態代碼檢查

使用 `--lint-only` 參數使得 verilator 檢查代碼，而不生成 C++ 文件。

如果確定某些代碼風格的警告不會對邏輯產生影響，可以通過 `-Wno-xxx` 關閉 `xxx` 警告。

# Verilog 的仿真行為與編碼風格

## 仿真行為

具體來說，參考 [IEEE Standard for Verilog](http://staff.ustc.edu.cn/~songch/download/IEEE.1364-2005.pdf) 或者 [一生一芯講義](https://ysyx.oscc.cc/docs/2407/e/5.html#verilog%E7%9A%84%E4%BB%BF%E7%9C%9F%E8%A1%8C%E4%B8%BA%E5%92%8C%E7%BC%96%E7%A0%81%E9%A3%8E%E6%A0%BC)。

簡單來說，事件隊列分為以下五種：
1. **激活事件(active event)**：在當前仿真時刻應該立即被處理的事件。當此隊列為空時，下級隊列的事件可能會被提升到此隊列中，從而執行該事件。
2. **非激活事件(inactive event)**：在當前仿真時刻不應被立即處理，應該等激活事件對列清空才可處理。
3. **非阻塞賦值更新事件(nonblocking assign update event)**：在當前仿真時刻已完成求值，但在當前仿真時刻結束時才可進行賦值的事件。
4. **監控事件(monitoir event)** 
5. **未來事件(future event)**：存放在未來仿真時刻才會被處裡的事件。

## 良好的 Verilog 編碼風格

盡量遵守以下建議：
1. 時序電路建模中，使用非阻塞賦值。
2. 鎖存器電路建模中，用非阻塞賦值。
3. 用 `always` 塊建立組合邏輯電路模型時，用阻塞賦值。
4. 在同一個 `always` 塊中建立組合邏輯與時序電路模型時，用非阻塞賦值。
5. 在同一個 `always` 塊中不要同時用非阻塞賦值與阻塞賦值。
6. 不要在多個 `always` 塊中對同一個變量賦值。
7. 用 `$strobe` 顯示非阻塞賦值的變量值。
8. 不要用 `#0` 延遲。

# 邏輯綜合 (Logic Synthesis) - 從 RTL 代碼到網表

RTL 代碼只是電路的描述，晶圓廠實際需要 GDSII(Graphic Design System II) 格式的版圖文件，描述具體的電路格局。

通常晶圓廠提供工藝設計套件(Process Design Kit, PDK)。PDK 中的**標準單元庫(standard cell library)** 包含該工藝支持的邏輯單元，稱作**標準單元(standard cell)**。

邏輯綜合就是從 RTL 代碼實際轉換為標準單元的過程。

我們需要經過：
- **解析文件(Parsing)** 
- **細化(Elaboration)**：模塊的實例化與參數計算。
- **粗粒度綜合(Coarse-grain synthesis)**：用**字級單元(word-level cell)** 描述設計。
- **細粒度綜合(Fine-grain synthesis)**：用**門級單元(gate-level cell)** 描述設計。
- **工藝映射(Technology mapping)**：將工藝無關的電路映射到具體工藝實現，也就是映射到目標工藝的標準單元。 

# 評估電路

評估電路通常是三個維度，性能、功耗、面積。統稱 PPA (Performance, Power, Area)。

## 面積評估

最簡單，`.lib` 已經給出了標準單元的面積，綜合器只需要統計每個標準單元實例化的次數即可。

## 性能評估

電路的性能常通過頻率衡量，即每秒電路可工作多少次。這又是由每次工作最少需要花多少時間得出。

我們定義一次工作為時序邏輯元件在時鐘信號的驅動下更新狀態。所以分析它們的過程稱為**時序分析(timing analysis)**。

電路的工作頻率受限於延遲最長的組合邏輯路徑，我們稱為**關鍵路徑(critical path)**。

為了計算該路徑，EDA 工具從標準單元庫中讀取延遲信息。由於此過程不涉及電路實際工作，所以稱為**靜態時序分析(Static Timing Analysis, STA)**。

但是，上述方法得到的時序報告無法完全反映芯片流片時的頻率，因為網表並未包含標準單元間的物理位置信息。可以想像，若物理位置距離過遠，會造成較大的延遲。此延遲稱為**線延遲(net delay)**。而上述講述方法只能反映出信號經過標準單元本身的延遲，稱為**邏輯延遲(logic delay)**。

## 功耗評估

通過計算每個標準單元的功耗，計算出電路的總功耗。

- **內部功耗(Internal Power)**：在晶體管翻轉時, 由於nMOS和pMOS並非瞬間就完成狀態切換, 因此在一段很短的時間內, nMOS和pMOS會同時處於導通狀態, 導致形成了從電源端到地端的短路電流, 這部分電流所產生的功耗就是內部功耗, 也稱短路功耗。內部功耗屬於動態功耗(dynamic power)的一部分。
- **翻轉功耗(Switch Power)**：CMOS電路翻轉時, 為了完成從0到1或從1到0的變化, 需要對相應的等效電容進行充電或放電, 這個過程產生的功耗就是翻轉功耗, 也稱開關功耗。翻轉功耗也屬於動態功耗的一部分, 也即, 動態功耗由內部功耗和翻轉功耗兩部分組成。
- **漏電功耗(Leakage Power)**：在理想情況下, 晶體管處於截止狀態時, 源極和漏極之間沒有任何電流通過。但實際上並非如此, 真正的晶體管會因為多種原因, 導致在源極和漏極之間存在一定的微小電流, 稱為漏電電流(leakage current)。由漏電電流形成的功耗就是漏電功耗. 由於漏電功耗在晶體管不翻轉時也會存在, 因此也稱為靜態功耗。

# 若干代碼風格和規範

## 若你沒有深入了解行為建模，不要使用

如果開發者內心沒有實際電路圖，而期望使用行為建模的方式生成一個可以工作的電路圖，就已經偏離描述電路的本質了。最終綜合器可能會生成 PPA 不佳的電路。

### 真正的描述電路 = 實例化 + 連線

就這麼說吧，咱不推薦初學者使用 `always` 語句。

為了方便使用觸發器與選擇器，我們提供以下模板：

```verilog
// 觸發器模板
module Reg #(WIDTH = 1, RESET_VAL = 0) (
  input clk,
  input rst,
  input [WIDTH-1:0] din,
  output reg [WIDTH-1:0] dout,
  input wen
);
  always @(posedge clk) begin
    if (rst) dout <= RESET_VAL;
    else if (wen) dout <= din;
  end
endmodule

// 使用觸發器模板的示例
module example(
  input clk,
  input rst,
  input [3:0] in,
  output [3:0] out
);
  // 位寬為 1 比特, 復位值為 1'b1, 寫使能一直有效
  Reg #(1, 1'b1) i0 (clk, rst, in[0], out[0], 1'b1);
  // 位寬為 3 比特, 復位值為 3'b0, 寫使能為 out[0]
  Reg #(3, 3'b0) i1 (clk, rst, in[3:1], out[3:1], out[0]);
endmodule
```

```verilog
// 選擇器模板內部實現
module MuxKeyInternal #(NR_KEY = 2, KEY_LEN = 1, DATA_LEN = 1, HAS_DEFAULT = 0) (
 output reg [DATA_LEN-1:0] out,
 input [KEY_LEN-1:0] key,
 input [DATA_LEN-1:0] default_out,
 input [NR_KEY*(KEY_LEN + DATA_LEN)-1:0] lut
);

 localparam PAIR_LEN = KEY_LEN + DATA_LEN;
 wire [PAIR_LEN-1:0] pair_list [NR_KEY-1:0];
 wire [KEY_LEN-1:0] key_list [NR_KEY-1:0];
 wire [DATA_LEN-1:0] data_list [NR_KEY-1:0];

 genvar n;
 generate
 for (n = 0; n &lt; NR_KEY; n = n + 1) begin
 assign pair_list[n] = lut[PAIR_LEN*(n+1)-1 : PAIR_LEN*n];
 assign data_list[n] = pair_list[n][DATA_LEN-1:0];
 assign key_list[n] = pair_list[n][PAIR_LEN-1:DATA_LEN];
 end
 endgenerate

 reg [DATA_LEN-1 : 0] lut_out;
 reg hit;
 integer i;
 always @(*) begin
 lut_out = 0;
 hit = 0;
 for (i = 0; i &lt; NR_KEY; i = i + 1) begin
 lut_out = lut_out | ({DATA_LEN{key == key_list[i]}} &amp; data_list[i]);
 hit = hit | (key == key_list[i]);
 end
 if (!HAS_DEFAULT) out = lut_out;
 else out = (hit ? lut_out : default_out);
 end
endmodule

// 不帶默認值的選擇器模板
module MuxKey #(NR_KEY = 2, KEY_LEN = 1, DATA_LEN = 1) (
 output [DATA_LEN-1:0] out,
 input [KEY_LEN-1:0] key,
 input [NR_KEY*(KEY_LEN + DATA_LEN)-1:0] lut
);
 MuxKeyInternal #(NR_KEY, KEY_LEN, DATA_LEN, 0) i0 (out, key, {DATA_LEN{1'b0}}, lut);
endmodule

// 帶默認值的選擇器模板
module MuxKeyWithDefault #(NR_KEY = 2, KEY_LEN = 1, DATA_LEN = 1) (
 output [DATA_LEN-1:0] out,
 input [KEY_LEN-1:0] key,
 input [DATA_LEN-1:0] default_out,
 input [NR_KEY*(KEY_LEN + DATA_LEN)-1:0] lut
);
 MuxKeyInternal #(NR_KEY, KEY_LEN, DATA_LEN, 1) i0 (out, key, default_out, lut);
endmodule
```

我們需要提供以下參數：
- `NR_KEY`：鍵值對數量。
- `KEY_LEN`：鍵值位寬。
- `DATA_LEN`：數據位寬。

``` verilog
module mux21(a,b,s,y);
 input a,b,s;
 output y;

 // 通過 MuxKey 實現如下 always 代碼
 // always @(*) begin
 // case (s)
 // 1'b0: y = a;
 // 1'b1: y = b;
 // endcase
 // end
 MuxKey #(2, 1, 1) i0 (y, s, {
 1'b0, a,
 1'b1, b
 });
endmodule

module mux41(a,s,y);
 input [3:0] a;
 input [1:0] s;
 output y;

 // 通過 MuxKeyWithDefault 實現如下 always 代碼
 // always @(*) begin
 // case (s)
 // 2'b00: y = a[0];
 // 2'b01: y = a[1];
 // 2'b10: y = a[2];
 // 2'b11: y = a[3];
 // default: y = 1'b0;
 // endcase
 // end
 MuxKeyWithDefault #(4, 2, 1) i0 (y, s, 1'b0, {
 2'b00, a[0],
 2'b01, a[1],
 2'b10, a[2],
 2'b11, a[3]
 });
endmodule
```

## 在模塊名與宏定義前添加學號前綴

例如 `module IFU` 需要修改為 `module ysyx_xxxx_IFU`，`define SIZE 5` 修改為 `define ysyx_xxxx_SIZE 5`。