## DataLab 題解

### 環境配置

#### 1. 安裝虛擬機

使用VMare 安裝 Ubuntu，具體步驟可參考https://blog.csdn.net/apple_74262176/article/details/141781652

#### 2. 安裝GCC

``` shell
sudo apt-get install build-essential
sudo apt-get install gcc-multilib
sudo apt-get install gdb
```

#### 3.下載lab

官網鏈接: http://csapp.cs.cmu.edu/3e/labs.html

點擊Data Lab後的Self-Study Handout下載tar文件並解壓

#### 4.測試

在文件解壓處右鍵，Open in Terminal

輸入，並查看能否順利運行:

``` shell
make btest
./btest
```

### 實驗限制

``` C++
*
 * Instructions to Students:
 *
 * STEP 1: Read the following instructions carefully.
 */

You will provide your solution to the Data Lab by
editing the collection of functions in this source file.

INTEGER CODING RULES:
 
  Replace the "return" statement in each function with one
  or more lines of C code that implements the function. Your code 
  must conform to the following style:
 
  int Funct(arg1, arg2, ...) {
      /* brief description of how your implementation works */
      int var1 = Expr1;
      ...
      int varM = ExprM;

      varJ = ExprJ;
      ...
      varN = ExprN;
      return ExprR;
  }

  Each "Expr" is an expression using ONLY the following:
  1. Integer constants 0 through 255 (0xFF), inclusive. You are
      not allowed to use big constants such as 0xffffffff.
  2. Function arguments and local variables (no global variables).
  3. Unary integer operations ! ~
  4. Binary integer operations & ^ | + << >>
    
  Some of the problems restrict the set of allowed operators even further.
  Each "Expr" may consist of multiple operators. You are not restricted to
  one operator per line.

  You are expressly forbidden to:
  1. Use any control constructs such as if, do, while, for, switch, etc.
  2. Define or use any macros.
  3. Define any additional functions in this file.
  4. Call any functions.
  5. Use any other operations, such as &&, ||, -, or ?:
  6. Use any form of casting.
  7. Use any data type other than int.  This implies that you
     cannot use arrays, structs, or unions.

 
  You may assume that your machine:
  1. Uses 2s complement, 32-bit representations of integers.
  2. Performs right shifts arithmetically.
  3. Has unpredictable behavior when shifting if the shift amount
     is less than 0 or greater than 31.


EXAMPLES OF ACCEPTABLE CODING STYLE:
  /*
   * pow2plus1 - returns 2^x + 1, where 0 <= x <= 31
   */
  int pow2plus1(int x) {
     /* exploit ability of shifts to compute powers of 2 */
     return (1 << x) + 1;
  }

  /*
   * pow2plus4 - returns 2^x + 4, where 0 <= x <= 31
   */
  int pow2plus4(int x) {
     /* exploit ability of shifts to compute powers of 2 */
     int result = (1 << x);
     result += 4;
     return result;
  }

FLOATING POINT CODING RULES

For the problems that require you to implement floating-point operations,
the coding rules are less strict.  You are allowed to use looping and
conditional control.  You are allowed to use both ints and unsigneds.
You can use arbitrary integer and unsigned constants. You can use any arithmetic,
logical, or comparison operations on int or unsigned data.

You are expressly forbidden to:
  1. Define or use any macros.
  2. Define any additional functions in this file.
  3. Call any functions.
  4. Use any form of casting.
  5. Use any data type other than int or unsigned.  This means that you
     cannot use arrays, structs, or unions.
  6. Use any floating point data types, operations, or constants.


NOTES:
  1. Use the dlc (data lab checker) compiler (described in the handout) to 
     check the legality of your solutions.
  2. Each function has a maximum number of operations (integer, logical,
     or comparison) that you are allowed to use for your implementation
     of the function.  The max operator count is checked by dlc.
     Note that assignment ('=') is not counted; you may use as many of
     these as you want without penalty.
  3. Use the btest test harness to check your functions for correctness.
  4. Use the BDD checker to formally verify your functions
  5. The maximum number of ops for each function is given in the
     header comment for each function. If there are any inconsistencies 
     between the maximum ops in the writeup and in this file, consider
     this file the authoritative source.

/*
 * STEP 2: Modify the following functions according the coding rules.
 * 
 *   IMPORTANT. TO AVOID GRADING SURPRISES:
 *   1. Use the dlc compiler to check that your solutions conform
 *      to the coding rules.
 *   2. Use the BDD checker to formally verify that your solutions produce 
 *      the correct answers.
 */
```



### 題解

#### bitXor

##### 題目翻譯(個人翻譯，可能有部分不精確)：

僅用~與&實現x^y

示範：bitXor(4, 5) = 1

合法運算符：~ &

最多可使用運算符數：14

評分：1

##### 題解：

x ^ y等價於(x&~y | ~x&y)，因為無法使用' | '所以使用迪摩根定律：(~A | ~B) = ~(A & B)

``` C++
/* 
 * bitXor - x^y using only ~ and & 
 *   Example: bitXor(4, 5) = 1
 *   Legal ops: ~ &
 *   Max ops: 14
 *   Rating: 1
 */
int bitXor(int x, int y) {
  /*
  * 010111001
  * 110100101
  * 
  * 100011100
  */

  return ~(~(x&~y) & ~(~x&y));
}
```

#### tmin

##### 題目翻譯：

返回補碼的最小值

##### 題解：

有符號數與無符號數的表示：參考我的文章第1.1.0.3.2節https://ilsao.github.io/2025/02/07/CSAPP-U2-%E7%AD%86%E8%A8%98%E8%88%87-%E9%83%A8%E5%88%86-%E7%B7%B4%E7%BF%92%E9%A1%8C%E8%A7%A3%E7%AD%94/

由此可知：最小的補碼數為10000000000000000000000000000000，可由1左移31位得到

``` C++
/* 
 * tmin - return minimum two's complement integer 
 *   Legal ops: ! ~ & ^ | + << >>
 *   Max ops: 4
 *   Rating: 1
 */
int tmin(void) {
  return 1<<31;
}
```

#### isTmax

##### 題目翻譯：

若x為補碼的最大值則返回1，否則返回0

##### 題解：

由定義知，最大值為：01111111111111111111111111111111

此時~(x+1)會等於自身，因為無法使用條件判斷"if"，所以使用xor判斷是否相等

注：a ^ a = 0

注意，若x = -1亦可使上述條件成立，必須討論此情況

``` C++
/*
 * isTmax - returns 1 if x is the maximum, two's complement number,
 *     and 0 otherwise 
 *   Legal ops: ! ~ & ^ | +
 *   Max ops: 10
 *   Rating: 1
 */
int isTmax(int x) {
  //01111111111111111111111111111111
  int tmp = ~(x+1);

  int cond1 = !(x^tmp);

  // if x == -1 can causes cond1 = 1, thus we need to tackle it.
  int isNegOne = !((~x)^0);
  int result = cond1&(!isNegOne);

  return result;
}
```

#### allOddBits

##### 題目翻譯:

若所有奇數位都被設置為1，則返回1，否則返回0

##### 題解：

1. 生成掩碼

   因為規定無法使用超過255的常數，所以需要手動生成32位形如1010...1010的掩碼

   因為1010 = 10，使用10來左移就可以生成這樣的位向量

2. 使用&過濾

   因為0 & 1 = 0，所以x & mask可以確定x是形如1* 1 * ... 1 * 1 *的樣子

``` c++
/* 
 * allOddBits - return 1 if all odd-numbered bits in word set to 1
 *   where bits are numbered from 0 (least significant) to 31 (most significant)
 *   Examples allOddBits(0xFFFFFFFD) = 0, allOddBits(0xAAAAAAAA) = 1
 *   Legal ops: ! ~ & ^ | + << >>
 *   Max ops: 12
 *   Rating: 2
 */
int allOddBits(int x) {
  //1010 = 10 = A
  int partOfMask = 10;
  int mask = partOfMask + (partOfMask << 4);
  mask += (mask << 8);
  mask += (mask << 16);
  return !((x & mask) ^ mask);
}
```

#### negate

##### 題目翻譯：

返回-x

##### 題解：

使用定義：~x = -x -1移項

``` C++
/* 
 * negate - return -x 
 *   Example: negate(1) = -1.
 *   Legal ops: ! ~ & ^ | + << >>
 *   Max ops: 5
 *   Rating: 2
 */
int negate(int x) {
  /* 0001 => 1111
  *  0010 => 1110
  *  0011 => 1101
  */
  return (~x)+1;
}
```

#### isAsciiDigit

##### 題目翻譯：

若0x30 <= x <= 0x39(即ASCII碼的'0'~'9')，則返回1

##### 題解：

法1(我的寫法，較不佳)：

1. 分析

   0x30轉二進制為：0011 0000

   0x39轉二進制為：0011 1001

   我們可以將合理的x劃分成兩段，即0...00011 * * * *

2. 分類討論

   1. 0...00011 * * * *

      將x右移4位，因為是有符號數，所以為算數右移

      若x為合理值，則x = 0x3，可用xor判斷是否等於0x3

   2.  *... * * * * *0000 <= x <=  * ... * * * * *1001

      1. *00 *

         先用x & 0xF(1111)保留低4位，並將其他位設為零

         再將這個數與1001做**或**運算，並使用xor判斷結果是否與1001相同

      2. 0 * * *

         將x保留低4位並右移3位，看結果是否等於0

法2：

參考網絡資源：https://blog.csdn.net/qq_45677541/article/details/123955438

``` C++
/* 
 * isAsciiDigit - return 1 if 0x30 <= x <= 0x39 (ASCII codes for characters '0' to '9')
 *   Example: isAsciiDigit(0x35) = 1.
 *            isAsciiDigit(0x3a) = 0.
 *            isAsciiDigit(0x05) = 0.
 *   Legal ops: ! ~ & ^ | + << >>
 *   Max ops: 15
 *   Rating: 3
 */
int isAsciiDigit(int x) {
  /*
  *  0x30 = 00110000
  *  0x39 = 00111001
  */

  int maskThree = 3; // 0011
  int maskNine = 9;  // 1001

  /*
  * 1. 0...00011****
  * 2. *...*****0000 <= x <= *...*****1001
  *   - *00*
  *   - 0***
  */
  int cond1, cond2;

  cond1 = !(maskThree ^ (x >> 4));
  cond2 = !((maskNine | (x & 0xF)) ^ maskNine) | !(((x & 0xF) >> 3) ^ 0);
  
  return cond1 & cond2;
}
```

#### conditional

##### 題目翻譯：

如同x ? y : z (用conditional這個函數實現? : 的功能)

##### 題解：

此題需要兩個mask來判斷該輸出x還是y，且此二mask與x相關聯

聯想到：若x為零則Y的mask應為全1，Z的mask應為全0

則可以設一個變量isXTrue，用"!!"兩次取反來將值規定為0或1

maskY可用isXTrue左移31位再右移得到(此為算數右移，所以會形成全1)，而maskZ則設為~maskY，代表若maskY為全1則maskZ為全0

``` C++
/* 
 * conditional - same as x ? y : z 
 *   Example: conditional(2,4,5) = 4
 *   Legal ops: ! ~ & ^ | + << >>
 *   Max ops: 16
 *   Rating: 3
 */
int conditional(int x, int y, int z) {

  int isXTrue = !!(x ^ 0);

  int maskY = (isXTrue << 31) >> 31;
  int maskZ = ~maskY;

  return (maskY & y) | (maskZ & z);
}
```

#### isLessOrEqual

##### 題目翻譯：

若x <= y，則返回1，否則返回0

##### 題解：

**第一次嘗試：**

1. 將y移項，判斷x - y <= 0
2. 判斷是否負溢出(x < 0, y > 0, x - y > 0)
3. 確定x - y <= 0不是因為正溢出(x > 0, y < 0, x - y < 0)

通過測試，但不幸超出最多可使用運算符數(規定24，使用26)，費盡心力無法減少操作符，只可尋求它解

``` C++
/* 
 * isLessOrEqual - if x <= y  then return 1, else return 0 
 *   Example: isLessOrEqual(4,5) = 1.
 *   Legal ops: ! ~ & ^ | + << >>
 *   Max ops: 24
 *   Rating: 3
 */
int isLessOrEqual(int x, int y) {
	/*
	* 1. x-y < 0
	* 2. or x-y = 0
  	* 
  	* negOverflow: x < 0, y > 0, x-y < 0
  	* posOverflow: x > 0, y < 0, x-y > 0
  	* 
	*/

	int mask = (1 << 31) >> 31;
	int xMinusY = x + ((~y) + 1);

    int xMinusYRShift = xMinusY >> 31;
    int xMinusYEQZero = !(xMinusY ^ 0);
    int xMinusYLTZero = !(xMinusYRShift ^ mask);
    int xMinusYGTZero = !(xMinusYRShift ^ 0);

	int negOverflow, posOverflow, xNLTZero, yNLTZero;

	xNLTZero = ((x >> 31) ^ mask);
	yNLTZero = ((y >> 31) ^ mask);
	negOverflow = !xNLTZero & yNLTZero & xMinusYGTZero;
	posOverflow = xNLTZero & !yNLTZero & xMinusYLTZero;

	return (xMinusYLTZero | xMinusYEQZero | negOverflow) & !posOverflow;
}
```

**第二次嘗試：**

分四類討論，可以避免討論溢出的情況

但如果使用變量isXPos會造成符號數超過限制(26)，故更改為isXNotPos替代!isXPos，可節省三個"!"(23)

``` C++
int isLessOrEqual(int x, int y) {
  /*
  * 1. x = y ========================> true
  * 2. x > 0, y < 0 =================> false
  * 3. x < 0, y > 0 =================> true
  * 4. x > 0, y > 0 || x < 0, y < 0 => analyze
  */

  int equal, isXNotPos, isYPos, isXMinusYPos, analyzePass, xMinusY, signX, signY, signXMinusY;

  xMinusY = x + ((~y) + 1);
  
  signX = x >> 31;
  signY = y >> 31;
  signXMinusY = xMinusY >> 31;

  equal = !(x ^ y);
  isXNotPos = (signX ^ 0);
  isYPos = !(signY ^ 0);
  isXMinusYPos = !(signXMinusY ^ 0);
  analyzePass = ((!isXNotPos & isYPos) | (isXNotPos & !isYPos)) & !isXMinusYPos;

	return equal | (isXNotPos & isYPos) | analyzePass;
}
```

#### logicalNeg

##### 題目翻譯：

使用"!"以外的操作符實現"!"操作符

##### 題解:

本題思路與先前conditional類似，難點在無法使用"!!"規格化isXTrue = !!(x ^ 0)

聯想0與!0的區別 => 若x = !0則x | (-x)的符號位必為1，否則符號位必為0，可使用此性質生成mask

``` C++
/* 
 * logicalNeg - implement the ! operator, using all of 
 *              the legal operators except !
 *   Examples: logicalNeg(3) = 0, logicalNeg(0) = 1
 *   Legal ops: ~ & ^ | + << >>
 *   Max ops: 12
 *   Rating: 4 
 */
int logicalNeg(int x) {
  // x = true  => false
  // x = false => true

  int mask = (x | ((~x) + 1)) >> 31;

  return (~mask & 1) | (mask & 0);
}
```

#### howManyBits

##### 題目翻譯：

返回表示補碼x所需的最少位

##### 題解：

1. 剔除符號位與負數時高位多個重複填充的1，因為補碼中1111與11與1接表示-1
2. 使用類似二分法的概念，逐步判斷哪些區塊含有1，需要保留
   1. 因為補碼位數有限(32位)，此處又限制循環的使用，所以命名變量bit16, bit8...
   2. 注意此處使用左移的意義，1 << 4即等於2 ** 4
   3. 表示補碼x所需的最少位即所有bitxx變量的和加一(將符號位補回)

``` C++
/* howManyBits - return the minimum number of bits required to represent x in
 *             two's complement
 *  Examples: howManyBits(12) = 5
 *            howManyBits(298) = 10
 *            howManyBits(-5) = 4
 *            howManyBits(0)  = 1
 *            howManyBits(-1) = 1
 *            howManyBits(0x80000000) = 32
 *  Legal ops: ! ~ & ^ | + << >>
 *  Max ops: 90
 *  Rating: 4
 */
int howManyBits(int x) {
  int signX = x >> 31;

  /* 
  * x > 0: save all bits of x
  * 
  * x < 0: 11110001 => 00001110
  * => overlook excess ones (in this case, we only need 4 + 1(sign) bits to represent)
  */
  int minXBitPresent = (~signX & x) | (signX & (~x));

  int bit16, bit8, bit4, bit2, bit1, bit0;


  // Determine if there's a 1 in high 16 bits,
  // if so, bit16 = 16(1 << 4 = 2 ** 4), and x right shift 16
  // else, don't move x.
  bit16 = (!(!!(minXBitPresent >> 16) ^ 1)) << 4;
  minXBitPresent >>= bit16;

  // If we shifted when analyzing bit16, we only need to analyze high 8 bits
  // else, we have to analyze high (32 - 8) = 24 bits
  bit8 = (!(!!(minXBitPresent >> 8) ^ 1)) << 3;
  minXBitPresent >>= bit8;

  bit4 = (!(!!(minXBitPresent >> 4) ^ 1)) << 2;
  minXBitPresent >>= bit4;

  bit2 = (!(!!(minXBitPresent >> 2) ^ 1)) << 1;
  minXBitPresent >>= bit2;

  bit1 = !(!!(minXBitPresent >> 1) ^ 1);
  minXBitPresent >>= bit1;

  bit0 = minXBitPresent;

  return bit16 + bit8 + bit4 + bit2 + bit1 + bit0 + 1;  // +1 is for the sign bit
}
```

#### floatScale2

##### 題目翻譯：

返回與浮點參數f表達式2 * f相同的字節級

參數與結果都由unsigned int傳遞，但它們都會被解釋為單精度浮點數

當參數為NaN時，返回此參數

##### 題解：

想要解決此題，需要先了解IEEE 754二進制浮點數的表現方法
$$
V = (-1)^s \times 2^E \times M
$$
其中

- 符號(sign): s決定正(s=0)負(s=1)
- 階碼(exponent): E對浮點數加權，權重為2的E次幂(E可<0)
- 尾數(significand): M為二進制小數，範圍在1<=M<2，或0<=M<1

 又浮點數的位表示分為三個字段:

- 符號位s，編碼符號s
- k位的編碼字段exp，編碼階碼E
- n位的小數字段frac，編碼尾數M，編碼出來的值依賴於階碼字段的值是否為零

因為此題為float類型，所以**s = 1, k = 8, n = 23**

根據exp的值，我們可以將浮點數分為:

1. 規格化的值

   **exp位不全為0(0)或全為1(255)**時屬之，階碼字段(E)為以偏置形式表示的有符號整數

   **E = e - Bias**，其中，e為無符號數(exp的值)，**Bias為2^{k-1}-1**(float: 127, double: 1023)

   故，E取值範圍: float: -126~+127，double: -1022~+1023

   frac被解釋為小數值f，其中0<=f<1，其二進制表示為0.fn-1…f1f0。**M=1 + f** (implied leading 1)

2. 非規格化的值

   **exp位全為0**時屬之，階碼**E = 1 - Bias**，**尾數M = f**，**不包含隱含的開頭1**

   用途: 1.表示0 2.表示非常接近0.0的數

3. 特殊值

   **exp位全為1**時屬之，當frac全為0時表示無窮。s=1表示負無窮，s=0表示正無窮

   當二非常大的數相乘，或除以零時，無窮可以表示溢出的結果。

   當frac為非零時，即”NaN (Not a number)”，比如sqrt(-1)或無窮-無窮，亦可表示位初始化數據

此題解法先將s, exp, frac用移位分隔儲存，然後判斷浮點數屬於哪種分類

* 若為規格化的值，直接將exp為加一，因為最後值為$2^E$所以exp+1就等於2 * f

* 若為非規格化的值，因為exp固定，無法影響到E，所以改用將frac位乘以2

* 若為特殊值，正/負無窮 * 2 = 正/負無窮，所以此情況下直接返回參數uf即可

``` C++
unsigned floatScale2(unsigned uf) {

  /*
  * float (31 ~ 0)
  *   - sign = 31
  *   - exp = 30 ~ 23 
  *   - frac = 22 ~ 0
  * 
  * 1. Normalize
  *   - exp are not all 0 or 1(255)
  * 2. Denormalize
  *   - exp are all 0
  * 3. Pos infinte
  *   - exp are all 1, frac are all 0, and sign = 0
  * 4. Neg infinite
  *   - exp are all 1, frac are all 0, and sign = 1
  * 5. NaN
  *   - exp are all 1, but frac are not all 0 or 1
  */

  int sign, exp, frac;

  sign = uf >> 31;
  exp = (uf >> 23) - (sign << 8);
  frac = uf - ((exp + (sign << 8)) << 23);

  if(exp == 255) {
    return uf;
  }
    
  if(exp == 0) {
    // Denormalize
    frac *= 2;
    return ((sign << 31) + (exp << 23) + (frac));
  }

  // Normalize
  exp += 1;
  return ((sign << 31) + (exp << 23) + (frac));
}
```

#### floatFloat2Int

##### 題目翻譯：

返回與浮點參數f表達式(int) f相同的字節級

任何超過範圍的數字(包括NaN 和 無窮)都應該返回0x80000000u

##### 題解：

1. 判斷此數是否為NaN或無窮
2. 判斷此數是否為0
3. 若此數為非規格化數，因為E = 1 - Bias = -126，且M必小於1，所以轉為int必返回0
4. 若E > 31，則此數M(>1) * (2 **E)必溢出，返回0x80000000u
5. 若E < 0，則此數M(<2) * (2 ** E)轉int必返回0
6. 若E >= 23，因為M在此處以int儲存，不包含小數點位置，所以(原本)正確的小數點位置應該左移(E - 23)位
7. 反之，E < 23，同理可推應右移(23 - E)位
8. 利用符號位判斷，若=1則取反，使用性質-x = ~x + 1

``` C++
/* 
 * floatFloat2Int - Return bit-level equivalent of expression (int) f
 *   for floating point argument f.
 *   Argument is passed as unsigned int, but
 *   it is to be interpreted as the bit-level representation of a
 *   single-precision floating point value.
 *   Anything out of range (including NaN and infinity) should return
 *   0x80000000u.
 *   Legal ops: Any integer/unsigned operations incl. ||, &&. also if, while
 *   Max ops: 30
 *   Rating: 4
 */
int floatFloat2Int(unsigned uf) {

  int sign, exp, frac, error, result, E, M;

  sign = uf >> 31;
  exp = (uf >> 23) - (sign << 8);
  frac = uf - ((exp + (sign << 8)) << 23);
  error = 1 << 31;

  if(exp == 255) {
    // Special value
    return error;
  }

  if(exp == 0 && frac == 0) {
    return 0;
  }

  if(exp == 0) {
    // Denormalize
    // E = 1 - Bias = -126
    // M = 0.xx < 1
    return 0;
  }

  E = exp - 127;
  M = frac + (1 << 23); // Implied leading 1

  // Overflow
  if(E > 31) {
    return error;
  }
  if(E < 0) {
    return 0;
  }

  if(E >= 23) {
    // M * (2 ** E), since 1.xx => 1 xx we have to use (E - 23) in lieu of E
    result = M << (E - 23);
  }
  else {
    result = M >> (23 - E);
  }

  result = sign == 0 ? result : (~result + 1);

  return result;
}
```

#### floatPower2

##### 題目翻譯：

返回與32位int x 表達式2.0 ^ x相同的字節級

返回的unsigned值應與單精度浮點數2.0 ^ x有相同的字節級表示

如果結果太小，使得要被表示為非規格化數，則返回0

如果太大，返回正無窮

##### 題解：

1. 若x < 0，代表2.0 ^ x為分數，則必為非規格化數，返回0
2. 若表示exp需要超過8位，則返回正無窮
   * 因為E = exp - Bias，所以E = x的最大值為255(8位exp皆為1時值為255) - 127(Bias) = 128
3. 否則反推exp = E + Bias = x + 127，最後返回exp << 23即可(因為必為正數所以sign必為0，且因為V = (-1)^s * 2^E * M，所以M必為0，只需要以2^E的E反推為exp表示即可)

``` C++
/* 
 * floatPower2 - Return bit-level equivalent of the expression 2.0^x
 *   (2.0 raised to the power x) for any 32-bit integer x.
 *
 *   The unsigned value that is returned should have the identical bit
 *   representation as the single-precision floating-point number 2.0^x.
 *   If the result is too small to be represented as a denorm, return
 *   0. If too large, return +INF.
 * 
 *   Legal ops: Any integer/unsigned operations incl. ||, &&. Also if, while 
 *   Max ops: 30 
 *   Rating: 4
 */
unsigned floatPower2(int x) {
  int posInfinite, exp;

  posInfinite = 0x7f800000;

  if(x < 0) {
    return 0;
  }

  if(x > 128){
    return posInfinite;
  }

  // E = exp - bias = x
  exp = x + 127;

  return (exp << 23);
}
```