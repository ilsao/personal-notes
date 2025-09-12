# 前言

閱讀本文需要擁有《深入理解計算機系統》第三章前置知識。本文不會對基礎指令做過多說明，但會說明部分較難知識。筆者學識稍淺，若有疏漏或錯誤處，歡迎各位大佬指正。

# 安裝Lab

切換到想安裝Lab的目錄後，使用wget下載Lab。

``` bash
wget csapp.cs.cmu.edu/3e/bomb.tar
```

解壓Lab。

``` bash
tar xvf bomb.tar
```

# 前置GDB知識

## 運行

`gdb <filename>`使用gdb調試文件

`r`運行程序，遇到斷點則停止

`c`繼續運行，直到遇到下一個斷點或程序結束

`si`單步步入(遇到函數則進入)

`ni`單步步過(遇到函數則直接執行完函數，不進入)

`until`運行到循環結束

`until <line>`運行到行號處

## 斷點

`b <line>`在第n行設置斷點

`b <function name>`在某個函數入口設置斷點

`b *(<address>)`在地址處設置斷點

`info b`顯示當前設置的斷點

`delete <breakpoint n>`刪除第n個斷點

`delete breakpoints`刪除所有斷點

`disable <breakpoint n>`暫停第n個斷點

`enable <breakpoint n>`開啟第n個斷點

## 窗口

`layout regs`顯示寄存器與反彙編窗口

`layout asm`顯示反彙編窗口

## 顯示內容

`x/<count><format> <address/registers>`打印內存值。從所給地址處開始，以format格式顯示count個值。
	`d`: 十進制
	`x`: 十六進制
	`t`: 二進制
	`f`: 浮點數
	`i`: 指令
	`c`: 字符
	`s`: 字符串

example: 
``` bash
x/s $rax
x/100c 0x401000
```

`Ctrl + L`清屏

# Phase_1

首先使用objdump將反彙編代碼儲存，以方便覽閱。

```bash
objdump -d bomb > bomb.asm
```

然後使用gdb打開程序，並給Phase_1打上斷點。

``` bash
gdb bomb
b phase_1
```

運行程序`r`，隨機輸入一些字符串後發現程序運行到斷點處。

![[Pasted image 20250505162004.png]]

顯示寄存器與反彙編窗口。

```Bash
layout regs
```

觀察顯示的反彙編代碼。

![[Pasted image 20250505162321.png]]

發現在地址`0x400ee9`處調用了函數`strings_not_equal`，然後在`0x400eee`處測試返回值(`%eax`)使否等於0，如果等於0則跳轉到`0x400ef7`(`je`指令，即jump equal)，否則調用`0x400ef2`處的`explode_bomb`。

複習CSAPP第三章內容，得知函數調用時數據傳輸的順序(第1個參數~第6個參數使用寄存器，如參數大於6個則使用棧傳遞)。

| 操作數大小(位) | 1    | 2    | 3    | 4    | 5    | 6    |
| -------- | ---- | ---- | ---- | ---- | ---- | ---- |
| 64       | %rdi | %rsi | %rdx | %rcx | %r8  | %r9  |
| 32       | %edi | %esi | %edx | %ecx | %r8d | %r9d |
| 16       | %di  | %si  | %dx  | %cx  | %r8w | %r9w |
| 8        | %dil | %sil | %dl  | %cl  | %r8b | %r9b |

由以上推斷我們可以猜測`string_not_equal`的兩個參數就是我們的輸入與標準答案。運行到`0x400ee9`後，我們查看`%rdi`與`%rsi`的值觀察看看。

``` Bash
x/s $rdi
x/s $rsi
```

![[Pasted image 20250505163357.png]]

得到答案

``` plaintext
Border relations with Canada have never been better.
```

# Phase_2

在`phase_2`處打斷點，隨機輸入幾個數字(我選擇1 2 4 8 16 32)，觀察其代碼。

![[Pasted image 20250505184426.png]]

發現有名為`read_six_numbers`的函數，跟進查看代碼。

![[Pasted image 20250505183138.png]]

發現有一個函數`sscanf`，查詢後發現`sscanf`函數是用來從指定字符串中按格式提取數據。

其原型為：

``` C++
int sscanf(const char *str, const char *format, ...);
```

參數解釋：
- str：待解析的字符串
- format：格式化字符串
- ...：可變參數列表，用來接收解析後的數據 (須為變量地址)

我們可以猜測`sscanf`就是用來提取用戶輸入。通過phase_1中展示的數據傳輸順序，查看`%rdi`與`%rsi`。

![[Pasted image 20250505183539.png]]

可以發現我們的猜測是正確的，故調用`sscanf`的參數應該是：

``` C++
sscanf("<user input>", "%d %d %d %d %d %d", &rdx, &rcx, &r8, &r9, &rsp, &(rsp+8))
```

通過閱讀`read_six_numbers`函數的代碼可以發現各參數存放的地址：

![[Pasted image 20250505183903.png]]

步過這個函數，繼續觀察`phase_2`的代碼。

![[Pasted image 20250505184249.png]]

首先`0x400f0a`檢查`(%rsp)`是否為`0x1`，如果不等則直接爆炸。由`0x400f02`處的代碼可知`%rsp = %rsi`，且在函數`read_six_numbers`中`%rsi = %rdx`，所以`(%rsp)`中的值就是用戶輸入的第一個數字(即檢查用戶輸入的第一個數字是否等於1)。

如果通過該檢查，則跳轉到`0x400f30`處，初始化`%rbx`與`%rbp`。通過觀察，可以發現`0x400f17`~`0x400f2c`是一個for循環。

![[Pasted image 20250505185240.png]]

仔細觀察循環，發現`%eax`讀取`-0x4(%rbx)`中的值。因為`int`類型占4字節，所以若`%rbx`指向用戶輸入的第`i`個數，`M[%rbx - 0x4]`會讀取用戶輸入的第`i - 1`個數。同時，因為執行`add`指令比執行`mul`指令速度快，所以程序使用`add`指令優化`%eax *= 2`。

最後兩條指令比對`%eax`與`(%rbx)`的值，若是不相等則爆炸。由此我們可以構造出一個長度為6的數組，首項為1，其後每一項都是前一項的兩倍。

得到答案：1 2 4 8 16 32。

# Phase_3

在phase_3處打斷點，輸入`1 2`，觀察該處代碼。

![[Pasted image 20250506100937.png]]

發現了熟悉的`sscanf`函數，如我們做phase_2時一樣，查看`sscanf`的幾個參數。

![[Pasted image 20250506101452.png]]

透過觀察`0x400f47`與`0x400f4c`處的`lea`指令發現將用戶輸入讀入`%rsp+0x8`與`%rsp+0xc`處。為更好理解，我們假設`%rsp+0x8`與`%rsp+0xc`為一個數組`userinput[2]`，`%rsp+0x8`為`userinput[0]`，`%rsp+0xc`為`userinput[1]`。

![[Pasted image 20250506101829.png]]

`0x400f60`~`0x400f65`處的代碼檢查輸入長度，通過查看`sscanf`函數參數我們知道輸入應該為兩位。`0x400f6a`處的代碼檢查`userinput[0]`，若大於7則爆炸。然後`0x400f71`處的指令將`%eax`賦值`userinput[0]`。

![[Pasted image 20250506102902.png]]

特別注意`0x400f75`處的代碼，發現其為`switch`指令的跳轉表，跳轉的公式即：`<基地址> + <寄存器值> * <表項類型大小>`。查看`0x402470`中的值，即跳轉表的基地址。由`0x400f6a`處的判斷可以推測該跳轉表大小應為7項，因為跳轉表儲存的值佔8字節，所以跳轉表所佔的字節大小為$7 \times 8 = 56$字節。

![[Pasted image 20250506105245.png]]

因為該機器為小端序，所以地址是倒序的，恢復後地址如下。

![[Pasted image 20250506105402.png]]

觀察phase_3剩餘代碼，在跳轉表跳轉到的地址處，我標註了跳轉過來對應的`userinput[0]`值。我們可以看到在每個跳轉後代碼都會給`%eax`賦予一個特定的值。

![[Pasted image 20250506105503.png]]

觀察`0x400fbe`處的代碼，是一個判斷語句。若賦予`%eax`的特定值等於`userinput[1]`則成功，所以此題不僅一個解。其中一個解為`1 311(0x137)`。

# Phase_4

依照慣例，在phase_4處打斷點，隨便輸入幾個數字，開始閱讀反彙編代碼。

![[Pasted image 20250506142658.png]]

注意觀察`0x40103a`~`0x401048`處的代碼，調用了`func4`函數。我們可以看到`0x40104d`要求`func4`的返回值要等於0才可正確解彈，我們還可以發現`0x401051`處要求用戶輸入的第二個數字等於0才可正確解彈。

查看`func4`的反彙編代碼。

![[Pasted image 20250506143117.png]]

直接閱讀彙編碼並不好理解這段代碼的運行規則，我們人肉把這段代碼轉換成C++代碼，試試這樣可讀性會不會提高。

``` C++
// func4(userinput[0], 0, 14);
int func4(int input, int a, int b) {
    int tmp1, tmp2;
    tmp1 = b - a;
    tmp2 = tmp1 >> 31;  // Get sign
    tmp1 += tmp2;       // Add sign
    tmp1 /= 2;
    tmp2 = tmp1 + a;
    if (tmp2 < input) {
        func4(input, tmp2 + 1, b);
        return 1;
    }
    else if (tmp2 == input) {
        return 0;
    }
    else {
        func4(input, a, tmp2 - 1);
        return tmp1 * 2;
    }
}
```

這樣閱讀起來方便多了。還記得我們的目標是使`func4`返回0，最簡單的方式是使`tmp2 == input`。通過初始傳入的參數計算`tmp2`的值，我們可以得到`tmp2`等於7。

得到答案：`7 0`(不僅一組解)。

# Phase_5

對phase_5打斷點，隨便輸入幾個數字，開始我們的分析。

![[Pasted image 20250506223427.png]]

讀者可能會疑惑`0x40106a`處的`mov %fs:0x28, %rax`是甚麼？複習一下CSAPP第三章可以發現，這個位置存放著程序的金絲雀值(canary)，用來檢測棧溢出。

![[Pasted image 20250506231858.png]]

在代碼的末尾我們可以看到程序再次取出棧中之前儲存的金絲雀值，通過`xor`比對是否與真正的金絲雀值相等，如果不相等則代表發生棧溢出。

`0x40107a`~`0x40107f`與`0x4010d2`~`0x4010d7`處代碼檢測輸入長度是否為6，並置零`%rax`的值。

接下來是重中之重，分析代碼中的循環，即`0x40108b`~`0x4010a8`處的代碼。

![[Pasted image 20250506224604.png]]

通過彙編代碼很難看懂代碼邏輯，我們同樣將其轉成C++觀察。

``` C++
void EncryptLoop() {
    char* tmp;      // %rdx
    char msg[6];    // %rsp
    char userinput[6];
    for (int i = 0; i < 6; i++) {
        *tmp = userinput[i] & 0xf; // 1111
        tmp = (char*)(0x4024b0 + (int)tmp);
        msg[i+0x10] = *tmp;
    }
}
```

我們發現在`0x401096`處的`and`指令，只取`%rdx`的最低一位。`0x401099`處的代碼中發現一個內存地址`0x4024b0`，查看其中內容。

![[Pasted image 20250506225952.png]]

我們用不到那麼長的內容，只取前面第一串內容即可。

``` C++
tmp = (char*)(0x4024b0 + (int)tmp);
msg[i+0x10] = *tmp;
```

對於這兩段代碼，作用是將從`0x4024b0`開始的第`(int)tmp`個字符放入`msg[i+0x10]`(`M[%rsp+0x10]`)中，作為後續字符串對比的輸入。

![[Pasted image 20250506231018.png]]

觀察`0x4010ae`~`0x4010bd`處代碼，我們可以發現`strings_not_equal`調用的兩個參數分別是處理後的用戶輸入`M[%rsp+0x10]`與硬性寫入的內存地址`0x40245e`。查看`0x40245e`存放的內容。

![[Pasted image 20250506230832.png]]

對比`0x4024b0`處的字符串，我們需要計算如何使用`"maduiersnfotvbylSo"`湊出`"flyers"`。通過計算我們很容易可以得出每個字浮需要的偏移為`"0x9 0xf 0xe 0x5 0x6 0x7"`。(即：`0x4024b0 + 0x9`為`'f'`，`0x4024b0 + 0xf`為`'l'`...其餘類推)

現在我們需要思考甚麼輸入可以造成`%rdx`依序為`"0x9 0xf 0xe 0x5 0x6 0x7"`。我們需要`<輸入> & 0xf`後，可以得到所需的偏移，查詢[ASCII碼對照表](https://c.biancheng.net/c/ascii/)後，我們可以找到其中一組解：`9/.567`(十六進制為：`39 2f 2e 35 36 37`)。

# Phase_6

這題有點難度，讀者們可以先去休息下，精神充沛後我們繼續解phase_6。

我們可以看到phase_6中又出現了熟悉的`read_six_numbers`函數。打上斷點，隨便輸入六個數字，我們開始分析。

![[Pasted image 20250508094949.png]]

觀察代碼，我們可以看到`0x40110e`~`0x401151`是一個以`%r12d`為計數器的大循環(`Check 1 Loop`)。在這個大循環裡面，還套嵌著另一層循環`0x401135`~`0x401148`(`Loop 1`)。

`Loop 1`的作用是利用循環檢測`userinput[i]`之後的所有數字是否有任何一個數字與`userinput[i]`相等。`Check 1 Loop`的作用在遞增`i`，確保整個數組中的數字都不相等且皆不大於6。相等於以下代碼：

``` C++
for (int i = 0; i < 6; i++) {
	for(int j = i+1; j < 6; j++) {
		if (userinput[i] == userinput[j])
			explode_bomb();
	}
}
```

![[Pasted image 20250508095829.png]]

`0x401153`~`0x40116d`處代碼遍歷`userinput`，將每一項修改為`0x7 - userinput[i]`。相當於以下代碼：

``` C++
for(int i = 0; i < 6; i++) {
	userinput[i] = 0x7 - userinput[i];
}
```

![[Pasted image 20250508100221.png]]

在`0x401183`處我們發現一個內存地址`0x6032d0`，通過gdb我們查看一下該內存地址內儲存的值。

![[Pasted image 20250508100708.png]]

通過名字與內存中的值，我們可以猜測這是一個鏈表的頭節點。鏈表的定義如下：

``` C++
struct Node {
	int val;
	int key;        // 說明該節點為node幾
	Node *next;     // 佔8字節，指向下一個鏈表節點的地址
};
```

首先看一進入此部分就跳轉到的地址`0x401197`處的代碼：首次執行時如果修改後的`userinput[0]`等於`0x1`則將`M[%rsp+0x20]`處寫入`0x6032d0`(即Node 1的內存地址)，否則則跳轉到`Loop 4`執行循環。觀察`Loop 4`的循環，我們可以發現這一段代碼就是讀取第`%ecx`個鏈表節點。`Loop 3`則將讀取的節點存入`M[%rsp + %rsi*2 + 0x20]`中。

我們可以將其轉換成等價的C++代碼觀察。

``` C++
// 令%rsp+0x20 ~ %rsp+0x48為指向鏈表的指針，即：Node **NodeList[6]
// 令原本的鏈表按數字排序(即Node1後接Node2...依此類推)
// 此處的userinput為處理過的(0x7 - userinput[i])的數組
Node *head;
for (int i = 0; i < 6; i++) {
	head = 0x6032d0;    // Node類型為指針，所以可以直接將第一個節點的內存地址賦予它
	for (int j = 0; j < userinput[i]; j++) {
		head = head->next;
	}
	*NodeList[i] = head;
}
```

![[Pasted image 20250508223727.png]]

這一段代碼稍微較好了解，比較容易困惑的點在`0x4011b5`處的`%rsp + 0x50`。讀者可能會想這個值好像不在我們的鏈表範圍內，但是仔細閱讀代碼後可以發現`0x4011c4`與`0x4011c8`處的代碼使用的是`%rax(計數器) + 0x8`的值與`%rsp + 0x50`比對，所以循環真正運行的範圍在`%rsp + 0x20`~ `%rsp + 0x48`的40個字節。

``` C++
Node *head = *NodeList[0];
for (int i = 1; i < 6; i++) {
	Node *next = *NodeList[i];
	head -> next = next;
	head = head -> next;
}
head -> next = nullptr;
```

![[Pasted image 20250508230253.png]]

`Loop 6`的功能是取得每個節點的值，並檢驗鏈表是否依節點的值由大排到小。與以下C++代碼功能相等

``` C++
Node *head = 0x6032d0;
Node *next = head -> next;
for (int i = 0; i < 5; i++) {
	if (head -> val < next -> val) {
		explode_bomb();
	}
	head = head -> next;
	next = next -> next;
}
```

綜合以上分析，可以得知我們需要讓鏈表依據節點的值由大排到小，首先查看各節點的值。

![[Pasted image 20250508231152.png]]

``` plaintext
Node1->val: 0x14c = 332

Node2->val: 0xa8 = 168

Node3->val: 0x39c = 924

Node4->val: 0x2b3 = 691

Node5->val: 0x1dd = 477

Node6->val: 0x1bb = 443
```

所以我們可以得知，被程序修改過的`userinput(0x7 - userinput[i])`應該為`3 4 5 6 1 2`。反推原始值我們可以得到答案：`4 3 2 1 6 5`。

以上，phase_1到phase_6全部被我們解開。

![[Pasted image 20250508231914.png]]

![[Pasted image 20250508231930.png]]

Lab在最後還留有一個secret_phase，在此就留作讀者讀完本文的課後練習。筆者寫完這篇題解準備溜去早點休息，為讀者們寫下一個Attack Lab題解做準備與學習。

# 後記

筆者仍是一位正在學習的菜鳥，正利用高中畢業後與上大學前的空閒時間增強學習稍微底層一點的東西。這段時間也會是筆者發文的高發期，不知道進入大學後還有沒有這麼多時間進行創作或自由時間學習。若發現本文某些地方代碼錯誤或分析邏輯錯誤，歡迎各位大佬指正，筆者會虛心學習。日後可能會發一些CSAPP相關Lab的題解、密碼學、逆向工程相關的筆記或者教學創作，雖然筆者學識尚淺，但是仍希望可以將這些知識傳遞給擁有相同困惑或相同興趣的網友們。