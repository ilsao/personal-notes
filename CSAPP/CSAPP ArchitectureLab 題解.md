
# 前言

此實驗Part C極難，Part A 與 Part B全都是為Part C所準備而較為簡單。最終我的Part C得分為：39.3/60.0，所以我的解析也僅供參考，而非最佳解。期間我也參考過其他大佬的文章，但所有代碼相關改動都是由我一個個嘗試出來的。如果各位大佬有更好的優化方法歡迎指正！
# Part A

跟隨實驗手冊，此部分我們需要在`sim/misc`目錄下完成。

此部分我們需要編寫三個`Y86-64`程序，模擬`example.c`中三個函數的行為。

## `sum.ys`：迭代求鏈表各項和

`example.c`對鏈表的實現：

``` C
typedef struct ELE {
    long val;
    struct ELE *next;
} *list_ptr;
```

`example.c`對這個函數的實現：

``` C
/* sum_list - Sum the elements of a linked list */
long sum_list(list_ptr ls)
{
    long val = 0;
    while (ls) {
		val += ls->val;
		ls = ls->next;
    }
    return val;
}
```

同時，手冊提供了`Y86-64`格式的測試資料(鏈表)：

``` C
# Sample linked list 
.align 8 
ele1: 
	.quad 0x00a 
	.quad ele2 
ele2: 
	.quad 0x0b0 
	.quad ele3 
ele3: 
	.quad 0xc00 
	.quad 0
```

利用我們在CSAPP第三章所學的匯編與第四章的`Y86-64`知識，我們可以簡單的翻譯出下列代碼：

``` C
# sum_list - Sum the elements of a linked list
# author: asciibase64

.pos 0
    irmovq stack, %rsp
    call main
    halt

# Sample linked list
.align 8
ele1:
    .quad 0x00a
    .quad ele2
ele2:
    .quad 0x0b0
    .quad ele3
ele3:
    .quad 0xc00
    .quad 0

main:
    irmovq ele1, %rdi
    call sum_list
    halt

# long sum_list(list_ptr ls)
sum_list:
    xorq %rax, %rax
    jmp check

    loop: 
        mrmovq (%rdi), %rsi
        addq %rsi, %rax
        mrmovq 8(%rdi), %rdi

    check: 
        andq %rdi, %rdi
        jne loop
    ret

.pos 0x200
stack: 

```

注意，在`stack: `後，應留一行空行，否則無法正確運行。

我們可以通過以下兩條指令運行我們的代碼：

``` bash
./yas sum.ys
./yis sum.yo
```

![[Pasted image 20250702123902.png]]

注意`%rax`的值，`0xcba`為正確值。說明我們編寫的代碼正確無誤。

## `rsum.ys`：遞歸求鏈表各項和

`example.c`對這個函數的實現：

``` C
/* rsum_list - Recursive version of sum_list */
long rsum_list(list_ptr ls)
{
    if (!ls)
		return 0;
    else {
		long val = ls->val;
		long rest = rsum_list(ls->next);
		return val + rest;
    }
}
```

此階段使用與上個階段相同的測資。

我們可以寫出如下代碼：

``` C
# rsum_list - Recursive version of sum_list
# author: asciibase64

.pos 0
    irmovq stack, %rsp
    call main
    halt

# Sample linked list
.align 8
ele1:
    .quad 0x00a
    .quad ele2
ele2:
    .quad 0x0b0
    .quad ele3
ele3:
    .quad 0xc00
    .quad 0

main:
    irmovq ele1, %rdi
    call rsum_list
    halt

# long rsum_list(list_ptr ls)
rsum_list:
    xorq %rax, %rax
    
    check: 
        andq %rdi, %rdi
        je stop

    loop: 
        mrmovq (%rdi), %rsi
        addq %rsi, %rax
        mrmovq 8(%rdi), %rdi
        pushq %rax
        call rsum_list
        popq %rsi
        addq %rsi, %rax
    stop: 
        ret

.pos 0x200
stack: 

```

測試：

![[Pasted image 20250702124023.png]]

## `copy.ys`：將源數值塊複製到目的數值塊

`example.c`對此函數的實現如下：

``` C
/* copy_block - Copy src to dest and return xor checksum of src */
long copy_block(long *src, long *dest, long len)
{
    long result = 0;
    while (len > 0) {
		long val = *src++;
		*dest++ = val;
		result ^= val;
		len--;
    }
    return result;
}
```

特別注意`long val = *src++`的操作符優先級判定，該操作應被拆解成：

``` C
long val = *src;
src++; // 其中，src指針+1相等於內存中加上8字節
```

我們可以寫出如下代碼：

``` C
# copy_block - Copy src to dest and return xor checksum of src 
# author: asciibase64

.pos 0
    irmovq stack, %rsp
    call main
    halt

.align 8
# Source block
src:
    .quad 0x00a
    .quad 0x0b0
    .quad 0xc00
# Destination block
dest:
    .quad 0x111
    .quad 0x222
    .quad 0x333

main:
    irmovq src, %rdi
    irmovq dest, %rsi
    irmovq $3, %rdx
    call copy
    halt

# long copy_block(long *src, long *dest, long len)
copy:
    xorq %rax, %rax

    loop: 
        mrmovq (%rdi), %rcx
        irmovq $8, %r8
        addq %r8, %rdi
        rmmovq %rcx, (%rsi)
        addq %r8, %rsi
        xorq %rcx, %rax
        irmovq $1, %r8
        subq %rdx, %r8

    check: 
        andq %rdx, %rdx
        jg loop
    ret


.pos 0x200
stack: 

```

測試：

![[Pasted image 20250702124051.png]]

# Part B

此部分需要在`sim/seq`目錄中完成。

此部分任務目標為實現Homework 4.51和4.25中描述的指令`iaddq`，讓SEQ處理器實現立即數與寄存器相加的功能。

為了添加該功能，我們需要修改`seq-full.hcl`。該文件完整實現了書中描述的SEQ處理器，同時還包含一些解決任務需要的常數。

讓我們確定`iaddq`在各個階段需要完成甚麼事情：

| 階段   | `iaddq V, rB`                                                                                                                 |
| ---- | ----------------------------------------------------------------------------------------------------------------------------- |
| 取指   | $icode:ifun\leftarrow M_{1}[PC]$<br>$rA:rB \leftarrow M_{1}[PC+1]$<br>$valC \leftarrow M_{8}[PC+2]$<br>$valP\leftarrow PC+10$ |
| 譯碼   | $valB \leftarrow R[rB]$                                                                                                       |
| 執行   | $valE \leftarrow valB + valC$<br>$Set \ CC$                                                                                   |
| 訪存   |                                                                                                                               |
| 寫回   | $R[rB] \leftarrow valE$                                                                                                       |
| 更新PC | $PC \leftarrow valP$                                                                                                          |

確定這些資訊後，想要修改SEQ的HCL代碼以增加`iaddq`功能就變得非常簡單，只要在對應階段的硬件中加入`iaddq`指令。

## 取指階段

將`iaddq`加入有效指令中：

``` C
bool instr_valid = icode in 
	{ INOP, IHALT, IRRMOVQ, IIRMOVQ, IRMMOVQ, IMRMOVQ,
	       IOPQ, IIADDQ, IJXX, ICALL, IRET, IPUSHQ, IPOPQ };
```

`iaddq`需要`rB`寄存器：

``` C
bool need_regids =
	icode in { IRRMOVQ, IOPQ, IIADDQ, IPUSHQ, IPOPQ, 
		     IIRMOVQ, IRMMOVQ, IMRMOVQ };
```

`iaddq`需要值`valC`：

``` C
bool need_valC =
	icode in { IIADDQ, IIRMOVQ, IRMMOVQ, IMRMOVQ, IJXX, ICALL };
```

## 譯碼階段

`iaddq`需要`rB`作為`srcB`的值：

``` C
word srcB = [
	icode in { IOPQ, IIADDQ, IRMMOVQ, IMRMOVQ  } : rB;
	icode in { IPUSHQ, IPOPQ, ICALL, IRET } : RRSP;
	1 : RNONE;  # Don't need register
];
```

`iaddq`需要將`valE`寫回寄存器文件`rB`，所以需要設置`dstE`：

``` C
word dstE = [
	icode in { IRRMOVQ } && Cnd : rB;
	icode in { IIRMOVQ, IOPQ, IIADDQ} : rB;
	icode in { IPUSHQ, IPOPQ, ICALL, IRET } : RRSP;
	1 : RNONE;  # Don't write any register
];
```

## 執行階段

`iaddq`需要將`valC`當作aluA的值，`valB`當作aluB的值：

``` C
word aluA = [
	icode in { IRRMOVQ, IOPQ } : valA;
	icode in { IIRMOVQ, IRMMOVQ, IMRMOVQ, IIADDQ } : valC;
	icode in { ICALL, IPUSHQ } : -8;
	icode in { IRET, IPOPQ } : 8;
	# Other instructions don't need ALU
];

word aluB = [
	icode in { IRMMOVQ, IMRMOVQ, IOPQ, IIADDQ, ICALL, 
		      IPUSHQ, IRET, IPOPQ } : valB;
	icode in { IRRMOVQ, IIRMOVQ } : 0;
	# Other instructions don't need ALU
];
```

`iaddq`需要`set_cc`功能：

``` C
bool set_cc = icode in { IOPQ, IIADDQ };
```

## 剩餘階段

實現`iaddq`不需要對訪存、更新PC階段做任何更改，保持默認即可。

## 測試

編譯ssim會遇到許多問題，但是先不要著急，讓我們參考一篇知乎文章就可以解決這個問題：[CSAPP Lab4-Architecture Lab 深入解析](https://zhuanlan.zhihu.com/p/480380496)，這篇文章的測試SEQ階段詳細講解了如何解決這種問題。

使用`asumi.yo`測試我們新寫的SEQ處理器：

``` Bash
ilsao@ubuntu:~/Desktop/CSAPP/architecture lab/sim/seq$ ./ssim -t ../y86-code/asumi.yo
Y86-64 Processor: seq-full.hcl
137 bytes of code read
IF: Fetched irmovq at 0x0.  ra=----, rb=%rsp, valC = 0x100
IF: Fetched call at 0xa.  ra=----, rb=----, valC = 0x38
Wrote 0x13 to address 0xf8
IF: Fetched irmovq at 0x38.  ra=----, rb=%rdi, valC = 0x18
IF: Fetched irmovq at 0x42.  ra=----, rb=%rsi, valC = 0x4
IF: Fetched call at 0x4c.  ra=----, rb=----, valC = 0x56
Wrote 0x55 to address 0xf0
IF: Fetched xorq at 0x56.  ra=%rax, rb=%rax, valC = 0x0
IF: Fetched andq at 0x58.  ra=%rsi, rb=%rsi, valC = 0x0
IF: Fetched jmp at 0x5a.  ra=----, rb=----, valC = 0x83
IF: Fetched jne at 0x83.  ra=----, rb=----, valC = 0x63
IF: Fetched mrmovq at 0x63.  ra=%r10, rb=%rdi, valC = 0x0
IF: Fetched addq at 0x6d.  ra=%r10, rb=%rax, valC = 0x0
IF: Fetched iaddq at 0x6f.  ra=----, rb=%rdi, valC = 0x8
IF: Fetched iaddq at 0x79.  ra=----, rb=%rsi, valC = 0xffffffffffffffff
IF: Fetched jne at 0x83.  ra=----, rb=----, valC = 0x63
IF: Fetched mrmovq at 0x63.  ra=%r10, rb=%rdi, valC = 0x0
IF: Fetched addq at 0x6d.  ra=%r10, rb=%rax, valC = 0x0
IF: Fetched iaddq at 0x6f.  ra=----, rb=%rdi, valC = 0x8
IF: Fetched iaddq at 0x79.  ra=----, rb=%rsi, valC = 0xffffffffffffffff
IF: Fetched jne at 0x83.  ra=----, rb=----, valC = 0x63
IF: Fetched mrmovq at 0x63.  ra=%r10, rb=%rdi, valC = 0x0
IF: Fetched addq at 0x6d.  ra=%r10, rb=%rax, valC = 0x0
IF: Fetched iaddq at 0x6f.  ra=----, rb=%rdi, valC = 0x8
IF: Fetched iaddq at 0x79.  ra=----, rb=%rsi, valC = 0xffffffffffffffff
IF: Fetched jne at 0x83.  ra=----, rb=----, valC = 0x63
IF: Fetched mrmovq at 0x63.  ra=%r10, rb=%rdi, valC = 0x0
IF: Fetched addq at 0x6d.  ra=%r10, rb=%rax, valC = 0x0
IF: Fetched iaddq at 0x6f.  ra=----, rb=%rdi, valC = 0x8
IF: Fetched iaddq at 0x79.  ra=----, rb=%rsi, valC = 0xffffffffffffffff
IF: Fetched jne at 0x83.  ra=----, rb=----, valC = 0x63
IF: Fetched ret at 0x8c.  ra=----, rb=----, valC = 0x0
IF: Fetched ret at 0x55.  ra=----, rb=----, valC = 0x0
IF: Fetched halt at 0x13.  ra=----, rb=----, valC = 0x0
32 instructions executed
Status = HLT
Condition Codes: Z=1 S=0 O=0
Changed Register State:
%rax:	0x0000000000000000	0x0000abcdabcdabcd
%rsp:	0x0000000000000000	0x0000000000000100
%rdi:	0x0000000000000000	0x0000000000000038
%r10:	0x0000000000000000	0x0000a000a000a000
Changed Memory State:
0x00f0:	0x0000000000000000	0x0000000000000055
0x00f8:	0x0000000000000000	0x0000000000000013
ISA Check Succeeds
```

可以看到程序測試成功。

我們再運行基準測試程序，測試舊有的ISA指令是否同樣被我們設計出的處理器支持：

``` Bash
ilsao@ubuntu:~/Desktop/CSAPP/architecture lab/sim/seq$ cd ../y86-code; make testssim
../seq/ssim -t asum.yo > asum.seq
../seq/ssim -t asumr.yo > asumr.seq
../seq/ssim -t cjr.yo > cjr.seq
../seq/ssim -t j-cc.yo > j-cc.seq
../seq/ssim -t poptest.yo > poptest.seq
../seq/ssim -t pushquestion.yo > pushquestion.seq
../seq/ssim -t pushtest.yo > pushtest.seq
../seq/ssim -t prog1.yo > prog1.seq
../seq/ssim -t prog2.yo > prog2.seq
../seq/ssim -t prog3.yo > prog3.seq
../seq/ssim -t prog4.yo > prog4.seq
../seq/ssim -t prog5.yo > prog5.seq
../seq/ssim -t prog6.yo > prog6.seq
../seq/ssim -t prog7.yo > prog7.seq
../seq/ssim -t prog8.yo > prog8.seq
../seq/ssim -t ret-hazard.yo > ret-hazard.seq
grep "ISA Check" *.seq
asum.seq:ISA Check Succeeds
asumr.seq:ISA Check Succeeds
cjr.seq:ISA Check Succeeds
j-cc.seq:ISA Check Succeeds
poptest.seq:ISA Check Succeeds
prog1.seq:ISA Check Succeeds
prog2.seq:ISA Check Succeeds
prog3.seq:ISA Check Succeeds
prog4.seq:ISA Check Succeeds
prog5.seq:ISA Check Succeeds
prog6.seq:ISA Check Succeeds
prog7.seq:ISA Check Succeeds
prog8.seq:ISA Check Succeeds
pushquestion.seq:ISA Check Succeeds
pushtest.seq:ISA Check Succeeds
ret-hazard.seq:ISA Check Succeeds
rm asum.seq asumr.seq cjr.seq j-cc.seq poptest.seq pushquestion.seq pushtest.seq prog1.seq prog2.seq prog3.seq prog4.seq prog5.seq prog6.seq prog7.seq prog8.seq ret-hazard.seq
```

可以發現所有檢測接成功。

通過基準測試程式後，我們需要測試專門為`iaddq`指令設計的額外集。

首先測試除了`iaddq`以外的所有指令：

``` Bash
ilsao@ubuntu:~/Desktop/CSAPP/architecture lab/sim/y86-code$ cd ../ptest; make SIM=../seq/ssim
./optest.pl -s ../seq/ssim 
Simulating with ../seq/ssim
  All 49 ISA Checks Succeed
./jtest.pl -s ../seq/ssim 
Simulating with ../seq/ssim
  All 64 ISA Checks Succeed
./ctest.pl -s ../seq/ssim 
Simulating with ../seq/ssim
  All 22 ISA Checks Succeed
./htest.pl -s ../seq/ssim 
Simulating with ../seq/ssim
  All 600 ISA Checks Succeed
```

測試`iaddq`指令:

``` Bash
ilsao@ubuntu:~/Desktop/CSAPP/architecture lab/sim/ptest$ cd ../ptest; make SIM=../seq/ssim -i
./optest.pl -s ../seq/ssim 
Simulating with ../seq/ssim
  All 49 ISA Checks Succeed
./jtest.pl -s ../seq/ssim 
Simulating with ../seq/ssim
  All 64 ISA Checks Succeed
./ctest.pl -s ../seq/ssim 
Simulating with ../seq/ssim
  All 22 ISA Checks Succeed
./htest.pl -s ../seq/ssim 
Simulating with ../seq/ssim
  All 600 ISA Checks Succeed

```

# Part C

此部分需要在`sim/pipe`目錄中完成。

以下是C語言與`Y86-64`版本的`ncopy`函數，我們的任務是修改`ncopy.ys`和`pipe-full.hcl`，使得`ncopy.ys`在模擬器中運行的越快越好。

``` C
/* 
* ncopy - copy src to dst, returning number of positive ints 
* contained in src array. 
*/ 
word_t ncopy(word_t *src, word_t *dst, word_t len) 
{ 
	word_t count = 0; 
	word_t val; 
 
	while (len > 0) { 
		val = *src++; 
		*dst++ = val; 
		if (val > 0) 
			count++; 
		len--; 
	} 
	return count; 
}
```

![[Pasted image 20250703162937.png]]

## 編碼限制

* `ncopy.ys`必須可以在任何大小的數組上工作
* `ncopy.ys`必須可以在YIS上正確運行
* `nocpy`文件的大小必須小於1000字節，我們可使用指令`./check-len.pl < ncopy.yo`確認程序的大小
* `pipe-full.hcl`實現必須通過`../y86-code`和`../ptest`中的測試

## 概念：循環展開

由於在官方文檔中提醒，閱讀CSAPP 5.8節會有所幫助，所以在此提供CSAPP 5.8節循環展開的部分概念以供參考。

循環展開通過增加每次迭代計算元素的數量，減少循環迭代的次數。

循環展開從兩方面增進程序的性能：
1. 減少不直接參與結果計算的操作數量，例如循環索引計算或條件分支。
2. 循環展開提供一些方法進一步變化代碼，減少計算中關鍵路徑上的操作數量。

若將一個循環按任意因子$k$展開，稱$k\times 1$循環展開。

我們令向量長度為$n$，則此循環的上限應為$n-k+1$，且循環內對元素$i$到$i+k-1$應合併運算。每次迭代索引$i$加$k$。

由於最大循環索引$i+k-1$會小於$n$，所以我們需要第二個循環，每次循環處理一個元素直到最後。此循環會執行$0\sim k-1$次。

## 添加`iaddq`功能

首先考慮給我們的流水線化處理器添加`iaddq`功能，並將`ncopy.ys`中可以使用`iaddq`指令替代的部分替代。

修改`pipe-full.hcl`使得處理器支持`iaddq`功能的步驟與Part B類似，在此不過多贅述。

以下提供使用`iaddq`指令修改過的`ncopy.ys`代碼。

``` C
#/* $begin ncopy-ys */
##################################################################
# ncopy.ys - Copy a src block of len words to dst.
# Return the number of positive words (>0) contained in src.
#
# author: asciibase64
#
# Describe how and why you modified the baseline code.
#
##################################################################
# Do not modify this portion
# Function prologue.
# %rdi = src, %rsi = dst, %rdx = len
ncopy:

##################################################################
# You can modify this portion
	# Loop header
	xorq %rax,%rax		# count = 0;
	andq %rdx,%rdx		# len <= 0?
	jle Done		    # if so, goto Done:

Loop:	
	mrmovq (%rdi), %r10	# read val from src...
	rmmovq %r10, (%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Npos		# if so, goto Npos:
	iaddq $1, %rax		# count++
Npos:	
	iaddq $-1, %rdx		# len--
	iaddq $8, %rdi		# src++
	iaddq $8, %rsi		# dst++
	andq %rdx,%rdx		# len > 0?
	jg Loop			    # if so, goto Loop:
##################################################################
# Do not modify the following section of code
# Function epilogue.
Done:
	ret
##################################################################
# Keep the following label at the end of your function
End:
#/* $end ncopy-ys */

```

### 測試

``` Bash
./correctness.pl
```

使用以上腳本確認正確性。

``` Bash
./benchmark.pl
```

使用以上腳本確認CPE。

![[Pasted image 20250703172419.png]]

可以看到CPE比原本的15.18好了不少。

## 循環展開

由於直接使用匯編代碼編寫循環展開的代碼不夠直觀，我們先使用C語言編寫$2\times 1$循環展開的代碼：

``` C
word_t ncopy2(word_t *src, word_t *dst, word_t len)
{
    word_t count = 0;
    word_t val;
    len--;
    while (len > 0) {
	    val = *src++;
	    *dst++ = val;
	    if (val > 0)
	        count++;

        val = *src++;
	    *dst++ = val;
	    if (val > 0)
	        count++;
	    len -= 2;
    }

    if (len == 0) {
        val = *src++;
	    *dst++ = val;
	    if (val > 0)
	        count++;
    }

    return count;
}
```

轉換成匯編代碼(僅擷取用戶編寫部分)：

``` C
	# Loop header
	xorq %rax,%rax		# count = 0;
	iaddq $-1, %rdx		# len--;
	jmp Check

Loop:	
	mrmovq (%rdi), %r10	# read val from src...
	rmmovq %r10, (%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Loop2			# if so, goto Loop2:
	iaddq $1, %rax		# count++
Loop2:
	mrmovq 8(%rdi), %r10	# read val from src...
	rmmovq %r10, 8(%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Npos			# if so, goto Npos:
	iaddq $1, %rax		# count++
Npos:	
	iaddq $-2, %rdx		# len -= 2;
	iaddq $16, %rdi		# src++
	iaddq $16, %rsi		# dst++
Check:
	andq %rdx,%rdx		# len > 0?
	jg Loop			    # if so, goto Loop:
LastCheck:
	andq %rdx, %rdx		# len != 0?
	jne Done			# if so, goto Done:
	mrmovq (%rdi), %r10	# read val from src...
	rmmovq %r10, (%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Npos			# if so, goto Npos:
	iaddq $1, %rax		# count++
```

測試後得到CPE：

``` Bash
Average CPE	10.64
```

推測可以繼續展開，繼續展開測試CPE會不會下降。

考慮到二次以上展開的後續處理較為麻煩，我重構了循環展開的代碼(以$3\times 1$為例)：

``` C
word_t ncopy3(word_t *src, word_t *dst, word_t len)
{
    word_t count = 0;
    word_t val;

    word_t min = 3;
    while (len >= min) {
        val = *src++;
	    *dst++ = val;
	    if (val > 0)
	        count++;
        val = *src++;
	    *dst++ = val;
	    if (val > 0)
	        count++;
        val = *src++;
	    *dst++ = val;
	    if (val > 0)
	        count++;
	    len -= min;
    }

    while (len > 0) {
        val = *src++;
	    *dst++ = val;
	    if (val > 0)
	        count++;
        len--;
    }

    return count;
}
```

``` C
	# Loop header
	xorq %rax,%rax		# count = 0;
	irmovq $3, %rcx		# min = 3;
	jmp Check

Loop:	
	mrmovq (%rdi), %r10	# read val from src...
	rmmovq %r10, (%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Loop2			# if so, goto Loop2:
	iaddq $1, %rax		# count++
Loop2:
	mrmovq 8(%rdi), %r10	# read val from src...
	rmmovq %r10, 8(%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Loop3			# if so, goto Loop3:
	iaddq $1, %rax		# count++
Loop3:
	mrmovq 16(%rdi), %r10	# read val from src...
	rmmovq %r10, 16(%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Npos			# if so, goto Npos:
	iaddq $1, %rax		# count++
Npos:	
	iaddq $24, %rdi		# src++
	iaddq $24, %rsi		# dst++
Check:
	subq %rcx,%rdx		# len > min (len -= min at the same time)?
	jg Loop			    # if so, goto Loop:

BeforeLastCheck:
	addq %rcx, %rdx	# Because our Check do len -= min at the same time, we have to add min back
	jmp LastCheck

LastLoop:
	mrmovq (%rdi), %r10	# read val from src...
	rmmovq %r10, (%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle LastNpos		# if so, goto LastNpos:
	iaddq $1, %rax		# count++
LastNpos:	
	iaddq $-1, %rdx		# len--
	iaddq $8, %rdi		# src++
	iaddq $8, %rsi		# dst++
LastCheck:
	andq %rdx,%rdx		# len > 0?
	jg LastLoop		# if so, goto LastLoop:
```

測試CPE：

``` Bash
./benchmark.pl
Average CPE	9.97
```

我們嘗試繼續進行循環展開，直到找到最優解。

``` Bash
2*1    Average CPE	10.64
3*1    Average CPE	9.97
4*1    Average CPE	9.79
5*1    Average CPE	9.73
6*1    Average CPE	9.73
7*1    Average CPE	9.76
```

參考上表，最終我選擇$5\times 1$循環展開。

``` C
# Loop header
	xorq %rax,%rax		# count = 0;
	irmovq $5, %rcx		# min = 5;
	jmp Check

Loop:	
	mrmovq (%rdi), %r10	# read val from src...
	rmmovq %r10, (%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Loop2			# if so, goto Loop2:
	iaddq $1, %rax		# count++
Loop2:
	mrmovq 8(%rdi), %r10	# read val from src...
	rmmovq %r10, 8(%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Loop3			# if so, goto Loop3:
	iaddq $1, %rax		# count++
Loop3:
	mrmovq 16(%rdi), %r10	# read val from src...
	rmmovq %r10, 16(%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Loop4			# if so, goto Loop4:
	iaddq $1, %rax		# count++
Loop4:
	mrmovq 24(%rdi), %r10	# read val from src...
	rmmovq %r10, 24(%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Loop5			# if so, goto Loop5:
	iaddq $1, %rax		# count++
Loop5:
	mrmovq 32(%rdi), %r10	# read val from src...
	rmmovq %r10, 32(%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Npos			# if so, goto Npos:
	iaddq $1, %rax		# count++
Npos:	
	iaddq $40, %rdi		# src++
	iaddq $40, %rsi		# dst++
Check:
	subq %rcx,%rdx		# len >= min (len -= min at the same time)?
	jge Loop			    # if so, goto Loop:

BeforeLastCheck:
	addq %rcx, %rdx	# Because our Check do len -= min at the same time, we have to add min back
	jmp LastCheck

LastLoop:
	mrmovq (%rdi), %r10	# read val from src...
	rmmovq %r10, (%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle LastNpos		# if so, goto LastNpos:
	iaddq $1, %rax		# count++
LastNpos:	
	iaddq $-1, %rdx		# len--
	iaddq $8, %rdi		# src++
	iaddq $8, %rsi		# dst++
LastCheck:
	andq %rdx,%rdx		# len > 0?
	jg LastLoop		# if so, goto LastLoop:
```

## 減少流水線冒險

### 加載/使用冒險

加載/使用冒險發生在遇到`mrmovq/popq`指令後，下一條指令需要立即使用從內存中的讀取值時。

要減少這種冒險，我們可以簡單的改變Loop之間的交互。

``` C
Loop:	
	mrmovq (%rdi), %r10	# read val from src...
	rmmovq %r10, (%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Loop2			# if so, goto Loop2:
	iaddq $1, %rax		# count++
Loop2:
	mrmovq 8(%rdi), %r10	# read val from src...
	rmmovq %r10, 8(%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Loop3			# if so, goto Loop3:
	iaddq $1, %rax		# count++
```

以上代碼是原本的順序，可以看見在運行`Loop`第一行與第二行時發生了加載/使用冒險。

我們對代碼做如下更改：

``` C
	# Loop header
	xorq %rax,%rax		# count = 0;
	irmovq $5, %rcx		# min = 5;
	jmp Check

Loop:	
	mrmovq (%rdi), %r10	# read val from src...
	mrmovq 8(%rdi), %r11 #read val from src for Loop2
	rmmovq %r10, (%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Loop2			# if so, goto Loop2:
	iaddq $1, %rax		# count++
Loop2:
	mrmovq 16(%rdi), %r10	# read val from src for Loop3
	rmmovq %r11, 8(%rsi)	# use the val from Loop and store it to dst
	andq %r11, %r11		# val <= 0?
	jle Loop3			# if so, goto Loop3:
	iaddq $1, %rax		# count++
Loop3:
	mrmovq 24(%rdi), %r11	# read val from src...
	rmmovq %r10, 16(%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Loop4			# if so, goto Loop4:
	iaddq $1, %rax		# count++
Loop4:
	mrmovq 32(%rdi), %r10	# read val from src...
	rmmovq %r11, 24(%rsi)	# ...and store it to dst
	andq %r11, %r11		# val <= 0?
	jle Loop5			# if so, goto Loop5:
	iaddq $1, %rax		# count++
Loop5:
	rmmovq %r10, 32(%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Npos			# if so, goto Npos:
	iaddq $1, %rax		# count++
Npos:	
	iaddq $40, %rdi		# src++
	iaddq $40, %rsi		# dst++
Check:
	subq %rcx,%rdx		# len >= min (len -= min at the same time)?
	jge Loop			    # if so, goto Loop:

BeforeLastCheck:
	addq %rcx, %rdx	# Because our Check do len -= min at the same time, we have to add min back
	jmp LastCheck

LastLoop:
	mrmovq (%rdi), %r10	# read val from src...
	rmmovq %r10, (%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle LastNpos		# if so, goto LastNpos:
	iaddq $1, %rax		# count++
LastNpos:	
	iaddq $-1, %rdx		# len--
	iaddq $8, %rdi		# src++
	iaddq $8, %rsi		# dst++
LastCheck:
	andq %rdx,%rdx		# len > 0?
	jg LastLoop		# if so, goto LastLoop:
```

運行之後得到CPE：

``` Bash
Average CPE 8.92
Score 31.6/60.0
```

## 針對小數據優化

### 循環展開

由最後一次運行的CPE可以觀察出來，當數據量較少時，CPE較大。嘗試對剩餘數據處理做循環展開。

``` Bash
ilsao@ubuntu:~/Desktop/CSAPP/architecture lab/sim/pipe$ ./benchmark.pl
	ncopy
0	23
1	33	33.00
2	46	23.00
3	56	18.67
4	69	17.25
5	79	15.80
6	66	11.00
7	76	10.86
8	89	11.12
9	99	11.00
10	112	11.20
11	96	8.73
12	109	9.08
13	119	9.15
14	132	9.43
15	142	9.47
16	129	8.06
17	139	8.18
18	152	8.44
19	162	8.53
20	175	8.75
21	159	7.57
22	172	7.82
23	182	7.91
24	195	8.12
25	205	8.20
26	192	7.38
27	202	7.48
28	215	7.68
29	225	7.76
30	238	7.93
31	222	7.16
32	235	7.34
33	245	7.42
34	258	7.59
35	268	7.66
36	255	7.08
37	265	7.16
38	278	7.32
39	288	7.38
40	301	7.53
41	285	6.95
42	298	7.10
43	308	7.16
44	321	7.30
45	331	7.36
46	318	6.91
47	328	6.98
48	341	7.10
49	351	7.16
50	364	7.28
51	348	6.82
52	361	6.94
53	371	7.00
54	384	7.11
55	394	7.16
56	381	6.80
57	391	6.86
58	404	6.97
59	414	7.02
60	427	7.12
61	411	6.74
62	424	6.84
63	434	6.89
64	447	6.98
Average CPE	8.92
Score	31.6/60.0
```

循環展開後的代碼如下：

``` C
	# Loop header
	xorq %rax,%rax		# count = 0;
	irmovq $5, %rcx		# min = 5;
	jmp Check

Loop:	
	mrmovq (%rdi), %r10	# read val from src...
	mrmovq 8(%rdi), %r11 #read val from src for Loop2
	rmmovq %r10, (%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Loop2			# if so, goto Loop2:
	iaddq $1, %rax		# count++
Loop2:
	mrmovq 16(%rdi), %r10	# read val from src for Loop3
	rmmovq %r11, 8(%rsi)	# use the val from Loop and store it to dst
	andq %r11, %r11		# val <= 0?
	jle Loop3			# if so, goto Loop3:
	iaddq $1, %rax		# count++
Loop3:
	mrmovq 24(%rdi), %r11	# read val from src...
	rmmovq %r10, 16(%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Loop4			# if so, goto Loop4:
	iaddq $1, %rax		# count++
Loop4:
	mrmovq 32(%rdi), %r10	# read val from src...
	rmmovq %r11, 24(%rsi)	# ...and store it to dst
	andq %r11, %r11		# val <= 0?
	jle Loop5			# if so, goto Loop5:
	iaddq $1, %rax		# count++
Loop5:
	rmmovq %r10, 32(%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle Npos			# if so, goto Npos:
	iaddq $1, %rax		# count++
Npos:	
	iaddq $40, %rdi		# src++
	iaddq $40, %rsi		# dst++
Check:
	subq %rcx,%rdx		# len > min (len -= min at the same time)?
	jge Loop			    # if so, goto Loop:

BeforeLastCheck:
	addq %rcx, %rdx	# Because our Check do len -= min at the same time, we have to add 5 back
	jmp FirstLastCheck

LastLoop:
	mrmovq (%rdi), %r10	# read val from src...
	iaddq $-1, %rdx		# len--
	rmmovq %r10, (%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle LastCheck		# if so, goto LastCheck:
	iaddq $1, %rax		# count++
LastCheck:
	iaddq $8, %rdi		# src++
	iaddq $8, %rsi		# dst++
	andq %rdx, %rdx
	jle Done
LastLoop2:
	mrmovq (%rdi), %r10	# read val from src...
	iaddq $-1, %rdx		# len--
	rmmovq %r10, (%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle LastCheck2		# if so, goto LastCheck2:
	iaddq $1, %rax		# count++
LastCheck2:
	iaddq $8, %rdi		# src++
	iaddq $8, %rsi		# dst++
	andq %rdx, %rdx
	jle Done
LastLoop3:
	mrmovq (%rdi), %r10	# read val from src...
	iaddq $-1, %rdx		# len--
	rmmovq %r10, (%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle LastCheck3		# if so, goto LastCheck3:
	iaddq $1, %rax		# count++
LastCheck3:
	iaddq $8, %rdi		# src++
	iaddq $8, %rsi		# dst++
	andq %rdx, %rdx
	jle Done
LastLoop4:
	mrmovq (%rdi), %r10	# read val from src...
	iaddq $-1, %rdx		# len--
	rmmovq %r10, (%rsi)	# ...and store it to dst
	andq %r10, %r10		# val <= 0?
	jle LastCheck4		# if so, goto LastCheck4:
	iaddq $1, %rax		# count++
LastCheck4:
	iaddq $8, %rdi		# src++
	iaddq $8, %rsi		# dst++
	jmp Done

FirstLastCheck:
	andq %rdx, %rdx
	jg LastLoop
```

最終得分：

``` Bash
ilsao@ubuntu:~/Desktop/CSAPP/architecture lab/sim/pipe$ ./benchmark.pl
	ncopy
0	23
1	30	30.00
2	44	22.00
3	55	18.33
4	68	17.00
5	53	10.60
6	63	10.50
7	74	10.57
8	88	11.00
9	98	10.89
10	86	8.60
11	93	8.45
12	107	8.92
13	118	9.08
14	131	9.36
15	116	7.73
16	126	7.88
17	137	8.06
18	151	8.39
19	161	8.47
20	149	7.45
21	156	7.43
22	170	7.73
23	181	7.87
24	194	8.08
25	179	7.16
26	189	7.27
27	200	7.41
28	214	7.64
29	224	7.72
30	212	7.07
31	219	7.06
32	233	7.28
33	244	7.39
34	257	7.56
35	242	6.91
36	252	7.00
37	263	7.11
38	277	7.29
39	287	7.36
40	275	6.88
41	282	6.88
42	296	7.05
43	307	7.14
44	320	7.27
45	305	6.78
46	315	6.85
47	326	6.94
48	340	7.08
49	350	7.14
50	338	6.76
51	345	6.76
52	359	6.90
53	370	6.98
54	383	7.09
55	368	6.69
56	378	6.75
57	389	6.82
58	403	6.95
59	413	7.00
60	401	6.68
61	408	6.69
62	422	6.81
63	433	6.87
64	446	6.97
Average CPE	8.54
Score	39.3/60.0
```

# 後記

CSAPP第四章是目前為止我認為最難的一章，因為之前沒有接觸過硬件設計相關知識，讀起來有種雲裡霧裡的感覺。

做這個Lab也能察覺到自身實力的缺漏，耗盡全身力氣也沒法優化到更高的分數。比較可惜的是無法為CPU設計更多支持的指令，只能為其添加`iaddq`指令，否則相信分數可以更高。