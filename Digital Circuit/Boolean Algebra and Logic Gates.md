# Axiomatic Definitions of Boolean Algebra

![[Pasted image 20260319164027.png|717]]
![[Pasted image 20260319164052.png|610]]

Boolean Algebra 與 Ordinary Algebra 有什麼差別？
- Boolean Algebra 的 $+$ 可以 distributive over $\cdot$，但 Ordinary Algebra 不行。
- Boolean Algebra 沒有加與乘的逆，所以無法定義減法與除法。
- Boolean Algebra 可以取反，Ordinary Algebra 不行。

# Basic Theorems and Properties

**二元性(Duality)**：給定某式若成立，則將操作符 $\text{AND}\Leftrightarrow\text{OR}$ 與 identity element $1\Leftrightarrow0$ 交換， 等式仍成立。

![[Pasted image 20260319165517.png]]

proof:
Theorem 1:
$x+x=(x+x)1=(x+x)(x+x')=x+xx'=x+0=x$ 
Theorem 2:
$x+1=x+(x+x')=x+x'=1$ 
Theorem 5 (b):
$\begin{cases}(xy)(x'+y')=0 \\ (xy)+(x'+y')=1\end{cases}$ 即證明互為補數。
$(xy)(x'+y')=(xyx'+xyy')=0$ 
$(xy)+(x'+y')=x'+(xy+y')=x'+(x+y')+(y+y')=x'+x+y'=1+y'=1$ 
Theorem 6:
$x+xy=x(1+y)=x(1)=x$ 

Boolean Algebra 的操作符**優先級**：
1. 括號
2. 取反
3. 且
4. 或

# Algebraic Manipulation

**literal**：變量或取反變量，例如 $x$，$y'$。

term：項，一個 AND 或兩個 OR 組合，例如 $xy, y+z$。(包含輸入的單個門電路)

化簡 boolean 表達式，就是減少 literal 與 term 的過程 $\implies$ 電路更優。

有個化減技巧：

$$a+bc=(a+b)(a+c)$$ 
proof:
吸收律：$a+ab=a$。
$(a+b)(a+c)=aa+ac+ba+bc=a+ac+ba+bc=a+ba+bc=a+ab+bc=a+bc$ 

> [!note]
> 適合用來解 $A+A'F=(A+A')(A+F)=A+F$。

![[Pasted image 20260319172611.png|825]]

特別注意 Ex2, Ex5。

說明 Ex5 的思路：
觀察式子，前兩項減無可減，但多了 $yz$。
想辦法讓 $yz$ 與前兩項有相同項，於是利用 $1=x+x'$。

![[Pasted image 20260324230043.png]]

Sol:
難難的。
before: 24 literals
after: 8 literals
$BCDEF+ABDF+BCDF'+CD'EF+CD'EF'+BDF'$ 
$=BCDEF+ABDF+BCDF'+CD'E(F+F')+BDF'$ 
$=BCDEF+ABDF+CD'E+BD(CF'+F')$ 
$=BCDEF+ABDF+CD'E+BDF'$ 
$=BD(CEF+AF+F')+CD'E$ 
$=BD(CEF+(A+F')(F+F'))+CD'E$ 
$=BD(CEF+A+F')+CD'E$ 
$=BD((CE+F')(F+F')+A)+CD'E$ 
$=BD(CE+A+F')+CD'E$ 
$=BD(A+F')+BDCE+CD'E$ 
$=BD(A+F')+CE(BD+D')$ 
$=BD(A+F')+CE(B+D')$ 

化減 $(x+y'+z')(x'+z)$。

Sol:
$xx'+x'y'+x'z'+xz+y'z+zz'$ 
$=x'y'+x'z'+xz+y'z$ 注意此處容易忘記繼續化減
$=x'y'+x'z'+xz+(x+x')y'z$ 
$=x'y'+x'z'+xz+xy'z+x'y'z$ 
$=x'y'+x'z'+xz$ 

# Complement of a Function

> [!warning] 注意
> 在化減表達式時，注意操作符間的優先級。

例如：$(A\lor B\land C)'=A'\land(B'\lor C')$ 而不是直接 $A'\land B'\lor C'=(A'\land B')\lor C'$ 喔！

# Canonical and Standard Forms

- Minterm (或稱 standard product)：由 AND 將所有變量結合在一起的項。例如：$xy,xy'z$。
- Maxterm：由 OR 將所有變量結合在一起的項。例如：$x+y,x+y'+z$。

$n$ 個變量可以組成 $2^{n}$ 個 minterms 或 maxterms。

![[Pasted image 20260319204818.png|958]]

對 minterm，使用 complement 代表值 $0$。用原變量代表值 $1$。使用 $m_{n}$ 代表第 $n$ 項 minterm。

對 maxterm，使用原變量代表值 $0$，complement 代表值 $1$。使用 $M_{n}$ 代表第 $n$ 項 maxterm。

兩者變量表達有關係：$\overline{ m_{0} }=M_{0}$ 

一個 boolean function 可用真值表或 minterm 或 maxterm 表達，稱為 canonical form：

![[Pasted image 20260319205522.png|668]]

其中 $f_{2}=x'yz+xy'z+xyz'+xyz=m_{3}+m_{5}+m_{6}+m_{7}=\sum(3,5,6,7)$ 

將 $f_{1}=\sum(1,4,7)$ 從 minterm 表達轉為 maxterm 表達：

已知 $f_{1}=(f_{1}')'$，又 $M_{n}=m_{n}'$。

$f_{1}'=m_{0}+m_{2}+m_{3}+m_{5}+m_{6}=\sum(0,2,3,5,6)$ 
$\implies f_{1}=(f_{1}')'=M_{0}M_{2}M_{3}M_{5}M_{6}=\prod(0,2,3,5,6)$ 

我們將 product of maxterms 視為：排除法。因為 $f=M_{0}=x+y+z$ 實際代入時為 $0$，於是 product of maxterms 可以將列出的 maxterms 對應全部置零。

將  sum of minterms 視為：挑選。因為 $f=m_{0}=x'y'z'$ 實際代入時為 $1$，於是 sum of minterms 可將所有對應值全部置一。

我們通過以下操作將某化減過的表達式轉為 sum of minterms：

$F=A+B'C$ 
$=A(B+B')+B'C=AB+AB'+B'C$ 
$=AB(C+C')+AB'(C+C')+B'C(A+A')$ 
$=ABC+ABC'+AB'C+AB'C'+AB'C+A'B'C$ 
$=ABC+ABC'+AB'C+AB'C'+A'B'C$ 
$=m_{7}+m_{6}+m_{5}+m_{4}+m_{1}$ 
$=\sum(1,4,5,6,7)$ 

先轉換為 sum of minterms 再轉 product of maxterms：

$f=xy+x'z$ 
$f'=(x'+y')(x+z')$ 
$=xx'+x'z'+xy'+y'z'$ 
$=x'z'(y+y')+xy'(z+z')+(x+x')y'z'$
$=x'yz'+x'y'z'+xy'z+xy'z'$ 
$f=(x+y'+z)(x+y+z)(x'+y+z')(x'+y+z)$ 
$=M_{2}M_{0}M_{5}M_{4}$ 
$=\prod(0,2,4,5)$ 

實際上 canonical form 很少用，standard form 用較多。

- sum of products：$F=y'+xy+x'yz'$ 
- product of sums：$F=x(y'+z)(x'+y+z)$ 

對於 $n$ 個變量，會有 $2^{n}$ 個 row 的真值表。

對於 $2^{n}$ 的 row 的真值表，會有 $2^{2^{n}}$ 個函數。

即，對 $2$ 個變量，有 $16$ 個函數。

![[Pasted image 20260319224241.png|812]]

![[Pasted image 20260319224538.png|795]]

考慮 $16$ 個函數
- null and identity：常數
- inhibition, implication, transfer, complement：重複了兩次
- transfer, complement, AND, OR, NAND, NOR, XNOR, equivalence 作為基本門電路出現
- complement: inverter
- transfer: buffer (增強信號)
- equivalence: XNOR

若一個電路可從 $2$ 個輸入拓展到 $n$ 個輸入，該電路表示的操作必須**滿足交換律 (commutative) 與結合律 (associative)**。

因為，$n$ 個輸入的結果必須獨立於輸入順序與運算先後。

所以，**AND 與 OR 可以拓展。NAND 與 NOR 不滿足結合律，所以不能拓展**。

例如：
$(x\text{ NOR }y)\text{ NOR }z=((x+y)'+z)'=(x+y)z'$ 
$x\text{ NOR }(y\text{ NOR }z)=(x+(y+z)')'=x'(y+z)$ 

於是，我們定義 $n$ 個輸入的 NAND 與 NOR 為原 AND 與 OR 輸出取反。

將 cascaded NAND 操作視為 sum of products，將 cascaded NOR 操作視為 products of sums。

例如：$[(ABC)'\cdot(DE)']'=ABC+DE$ 

![[Pasted image 20260319230442.png|811]]

因為 **XOR 與 XNOR 都可交換與結合，可拓展。** 

positive logic：$1$ 表示高電壓，$0$ 表示低電壓。

negative logic：$0$ 表示高電壓，$1$ 表示低電壓。

# 練習題

![[Pasted image 20260417150915.png]]

Sol:
(a)
$(x'+x)y'z'+y=y+y'z'=(y+y')(y+z')=y+z'$ 
可能會沒化減完！

![[Pasted image 20260417160657.png]]

Sol:
那時候忘記 F' 要怎麼變 POS。
SOP 直接展開：$x'w'+yw'+x'y+x'z$ 
POS 先取 SOP 的補：
$F'=(x'+w')(x'+y)(w'+y+z')=x'w'+yw'+x'y+x'z$ 
再取 $F=(F')'=(x+w)(y'+w)(x+y)(x+z')$ 

使用 minterms 表示下圖 $y$：
![[Pasted image 20260417162257.png|631]]

Sol:
$y=(a'+bcd+e')'=a(b'+c'+d')e=ab'e+ac'e+ad'e$ 
注意到這邊初始是 $e'$，因為第二個 NAND 的 $e$ 前面沒有相對應的 circle，得插入一個 inverter。
注意到全部都是 $a$ 開始，所以可以畫 $a=1$ 時的 k-map。應該要從 $16$ 開始數，所以每個數都要 $+16$。
$y=\sum(17,19,21,23,25,27,29)$ 