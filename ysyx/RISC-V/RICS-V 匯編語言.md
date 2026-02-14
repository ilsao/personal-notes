
# 函數調用約定 (Calling Convention)

函數調用過程通常分為六個階段：
1. 將參數存儲到函數能訪問到的地方。
2. 跳轉到函數的開始。
3. 獲取函數需要的局部資源，按需求保存會被修改的寄存器。
4. 執行函數中的指令。
5. 將返回值存儲到調用者能訪問到的地方，恢復寄存器並釋放局部資源。
6. 返回函數調用處。

為了提升性能，我們想盡量少將數據存在內存中。

RISC-V 擁有足夠的寄存器可以達到這種要求。關鍵在於，在函數調用過程中某些寄存器的值不會被保留，這些寄存器稱為**臨時寄存器**。

我們稱不會再調用其他函數的函數為**葉函數**，葉函數通常具有較少的參數與局部變量。

下圖展示了寄存器在函數調用中是否會被保留。

![[ysyx/RISC-V/pic/U3/1.png]]

以下展示了一個函數的開頭：

```asm
entry_label:
	addi sp, sp, -framesize
	sw ra, framesize-4(sp)
	# save registers if needed
	# body of the function
```

其中，`sp` 指向棧頂，而返回地址 `ra` 被保存在棧底。

如果函數的參數或局部變量過多，則會在函數開頭為這些東西分配函數棧，並在函數結尾釋放棧幀。

```asm
	# restore registers from stack if needed
	lw ra, framesize-4(sp)
	addi sp, sp, framesize
	ret
```

# 匯編器

下圖展示了一些 RISC-V 偽指令：

![[ysyx/RISC-V/pic/U3/2.png]]

![[ysyx/RISC-V/pic/U3/3.png]]

匯編程序的開頭是**匯編指示符(assemble directives)**，用來告訴匯編器數據的位置或者定義常量。

下圖展示了匯編指示符：

![[ysyx/RISC-V/pic/U3/4.png]]

下面 `Hello World` 程序用到的匯編指示符解釋如下：
- `.text`：進入代碼段。
- `.align 2`：後續代碼按照 $2^{2}$ 對齊。
- `global main`：聲明全局符號 `main`。
- `.section .rodata`：進入只讀數據段。
- `.balign 4`：後續代碼按照 $4$ 對齊。
- `.string "Hello, %s \n"`：創建空字符結尾的字符串。
- `.string "World"`：創建空字符結尾的字符串。

``` asm
.text
.align 2
.global main
main:
	addi sp, sp, -16
	lw ra, 12(sp)
	lui a0, %hi(string1)
	addi a0, a0, %lo(string1)
	lui a1, %hi(string1)
	addi a1, a1, %lo(string1)
	call printf
	lw ra, 12(sp)
	addi sp, sp, 16
	li a0, 0            # load return value
	ret
	.section .rodata
	.balign 4
string1:
	.string "Hello, %s \n"
string2:
	.string "World"
```

注意到以下代碼：

``` asm
	lui a0, %hi(string1)
	addi a0, a0, %lo(string1)
	lui a1, %hi(string1)
	addi a1, a1, %lo(string1)
```

我們將字符串的加載分割成了兩步，這是因為字符串存放的地址是 32 位的，但是 `addi` 的立即數只能存取 12 位。

所以我們通過**匯編器重定位表達式(assembler relocation)** `%hi(symbol)` 與 `%lo(symbol)` 加載高 20 位與低 12 位。

下面是生成的 `hello.o` 文件：

![[ysyx/RISC-V/pic/U3/5.png]]

注意到所有涉及地址的地方地址都被寫為 `0x0`，其真實地址由鏈接器決定。

**鏈接器鬆弛(linker relaxation)**：跳轉並鏈接指令有 20 位的相對地址域，大多時候一條指令就可以跳到目的地址。但是編譯器實際上會為每個跳轉都生成兩條指令。鏈接器會掃描代碼，然後替換所有可以合併的跳轉指令。

# 靜態鏈接與動態鏈接



# 加載器