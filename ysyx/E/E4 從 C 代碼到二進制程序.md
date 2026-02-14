# 編譯

## 詞法分析

識別與紀錄源代碼文件中的 token。包括標示符、字符串、運算符、大括號等。

使用以下命令查看詞法分析的結果：

``` bash
clang -fsyntax-only -Xclang -dump-tokens a.c
```

## 語法分析

按照 C 語言語法，將識別出的 token 組織成樹狀結構 (抽象語法樹，Abstract Syntax Tree, AST)。

使用以下命令查看語法分析的結果：

``` bash
clang -fsyntax-only -Xclang -ast-dump a.c
```

## 語意分析

根據 C 語言的語意定義，確定 AST 中每個表達式的類型。

有時，表達式符合 C 語法，但不符合語意。例如 `struct mytype a; int b = a + 1;`。

對於 clang 來說，在輸出 AST 時就已經給出了表達式的類型。也就是說，大多數編譯器並沒有嚴格區分語法分析與語意分析。

語意分析的一個應用是靜態程序分析，可以在不運行程序的情況下對源碼進行分析。這種程序通常稱為 lint。

可以通過以下指令分析：

```bash
clang a.c --analyze -Xanalyzer -analyzer-output=text
```

## 中間代碼生成

編譯器前端會先將 C 代碼翻譯成中間代碼，然後由後端將中間代碼翻譯成匯編。

這樣有幾個好處：
- 優化：若編譯器支持多種目標語言，但沒有中間代碼，則需要為每種目標語言特別優化。相反，直接優化中間代碼就行。
- 多語言支持：若有 $m$ 種源語言與 $n$ 種目標語言，想直接翻譯則需要支持 $mn$ 種翻譯模塊。相反，支持中間代碼就只需要 $m+n$ 種。

## 目標代碼生成

將中間代碼翻譯成目標代碼的過程。其中，生成與本地環境不同的 ISA 代碼的過程，稱為**交叉編譯(cross-compilation)**。

使用：

``` bash
clang -S a.c
clang -S a.c --target=riscv64-linux-gnu
```

或：

```sh
gcc -S a.c
riscv64-linux-gnu-gcc -S a.c
```

# 二進制文件的生成與執行

## 編譯

本質上就是查閱 ISA 手冊，將匯編代碼逐條翻譯成二進制編碼。

使用：

```sh
clang -c a.c
```

並使用以下指令查看反匯編結果：

```sh
objdump -d a.o
```

或者交叉編譯：

```sh
clang -c a.c --target=riscv64-linux-gnu
riscv64-linux-gnu-objdump -d a.o
```

用 gcc 也行：

```sh
gcc -c a.c
riscv64-linux-gnu-gcc -c a.c
```

用 llvm 工具鏈反匯編，可以自動識別對應的 ISA 框架：

```sh
llvm-objdump -d a.o  # x86/RISC-V 均支持
```

## 鏈接

將多個目標文件合併成可執行文件：

``` sh
clang a.c 
```

加上 `--verbose` 可以觀察命令執行時的日志。

交叉編譯：

```sh
clang a.c --target=riscv64-linux-gnu
riscv64-linux-gnu-gcc a.c
```

## 執行

由加載器將程序加載到內存中。同時，運行時環境在程序真正開始執行前完成一系列設定。

# 實現完整的 minirvEMU

基本的代碼沒啥問題，現在考慮自動判定程序運行結束。

考慮支持一個新指令 `ebreak`：

![[ysyx/E/pic/E4/1.png]]![[ysyx/E/pic/E4/2.png]]