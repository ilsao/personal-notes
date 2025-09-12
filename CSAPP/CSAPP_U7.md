
# 編譯器驅動程序

考慮以下代碼：

``` C
// main.c
int sum(int *a, int n);

int array[2] = { 1, 2 };

int main()
{
	int val = sum(array, 2);
	return val;
}
```

``` C
// sum.c 
int sum(int *a, int n)
{
	int i, s = 0;
	for (i = 0; i < n; i++) {
		s += a[i];
	}
	return s;
}
```

編譯系統提供**編譯器驅動程序(compile driver)**，幫助用戶調用語言預處理器、編譯器、匯編器與鏈接器。

若要使用GNU編譯系統構造以上代碼，輸入以下指令：

``` bash
gcc -Og -o prog main.c sum.c
```

![[Pasted image 20250719131241.png]]

上圖蓋擴了驅動程序將代碼翻譯成可執行目標文件的行為。

驅動程序首先使用**C預處理器(C preprocessor, cpp)** 將`main.c`翻譯成ASCII碼的中間文件`main.i`：

``` bash
cpp [other arguments] main.c /tmp/main.i
```

緊接著使用**C編譯器(C compiler, cc1)** 將`main.i`翻譯成匯編文件`main.s`：

``` bash
gcc -Og -S /tmp/main.i [other arguments] -o /tmp/main.s
```

然後，使用**匯編器(assembler, as)** 將`main.s`翻譯成**可重定位目標文件(relocatable object file)** `main.o`：

``` bash
as [other arguments] -o /tmp/main.o /tmp/main.s
```

通過同樣的過程生成`sum.o`，然後運行鏈接器程序`ld`創建一個**可執行目標文件(executable object file)** `prog`：

``` bash
gcc -o prog main.o sum.o
```

# 靜態鏈接

如`ld`這樣的**靜態鏈接器(static linker)** 以一組可重定位目標文件和命令行參數作為輸入，生成一個完全鏈接且可以加載和運行的可執行目標文件作為輸出。

鏈接器完成兩個主要任務：
* **符號解析(symbol resolution)**：每個符號對應一個函數、全局變量或靜態變量。符號解析將每個符號引用和符號定義關聯起來。
* **重定位(relocation)**：編譯器和匯編器生成從地址開始的代碼和數據節，鏈接器通過把每個符號定義與一個內存位置關聯，從而重定位這些節，然後修改所有對這些符號的引用，使引用指向該內存地址。

# 目標文件

目標文件分三種：
* **可重定位目標文件**
* **可執行目標文件**
* **共享目標文件**：在加載或運行時被動態地加載進內存並鏈接。

**目標模塊(object module)**：一個字節序列。

**目標文件(object file)**：以文件形式存放在磁盤中的目標模塊。

# 可重定位目標文件

我們可以通過以下指令生成可重定位目標文件(僅進行編譯和匯編，不執行鏈接)：

``` bash
gcc -c main.c
```

我們可以使用以下指令查看目標文件包含多少字節，其中`-c`代表字節：

``` bash
wc -c main.o
```

![[Pasted image 20250719142006.png]]

上圖是一個典型ELF文件。

**ELF頭(ELF header)** 以一個16字節序列開始，內容如下：

![[Pasted image 20250719142249.png]]

我們可以使用以下指令查看ELF header中的具體內容：

``` bash
readelf -h main.o
```

使用以下指令查看節頭部表中的具體信息：

``` bash
readelf -S main.o
```

![[Pasted image 20250719151245.png]]

我們列點說明常用的節：

`.text`：存放已編譯的代碼。

`.rodata`：存放只讀數據，如`printf`中的格式串。

`.data`：已初始化的全局或靜態變量。

`.bss`：未初始化的全局或靜態變量，以及所有被初始化為零的全局或靜態變量。在目標文件中這個節不占空間，只是個佔位符。因為未初始化變量會在運行時在內存中分配這些變量並初始化零。

`.symtab`：符號表。

`.rel.text`：代碼重定位條目。

`.rel.data`：數據重定位條目。

`.strtab`：字符串表，包括`.symtab`節的符號表中各項的名字，以及節頭部中的節名字。

# 符號和符號表

在鏈接器上下文中，有三種不同的符號：
* 全局符號：由模塊定義且能被其他模塊引用的符號，對應非靜態的函數和全局變量。
* 外部符號：由其他模塊定義且能被模塊引用的全局符號，對應其他模塊中定義的非靜態函數和全局變量。
* 局部符號：由模塊定義但不能被其他模塊引用的符號，對應帶`static`屬性的函數或全局變量。

我們可以使用以下指令查看符號表中的內容：

``` bash
readelf -s main.o
```

![[Pasted image 20250719151313.png]]

以下是符號表條目的數據結構：

``` C
typedef struct {
	int name;        /* String table offset */
	char type:4,     /* Function or data (4 bits) */
		 binding:4;  /* Local or global (4 bits) */
	char reserved;   /* Unused */
	short section;   /* Section header index */
	long value;      /* Section offset or absolute address */
	long size;       /* Object size in bytes */
} Elf64_Symbol;
```

`name`：對應到`.strtab`的偏移，裡面存放著對應變量或函數名。

`type`：該項是函數還是變量。

`binding`：該項符號是局部還是全局的。

`section`：對應節頭部表的索引，指出該項存放在對應哪個節中。此項有三個特殊的**偽節(pseudosection)**，它們在節頭部表中沒有對應條目。`ABS`表示不該被重定位的符號；`UNDEF`表示未定義的符號，即在本模塊引用但在其他模塊定義的符號；`COMMON`表示未初始化的數據。只有可重定位目標文件中才有這些偽節，可執行目標文件無。

`value`：相對於`.text`起始位置的偏移量。對於`COMMON`符號，給出對其要求。

`size`：目標的大小(字節)。對於`COMMON`符號，給出最小的大小。

gcc使用以下規則區分`COMMON`和`.bss`：
* `COMMON`：未初始化的全局變量。(弱符號，後面會提到定義)
* `.bss`：未初始化的靜態變量和初始化為零的全局或靜態變量。

## 練習題

7.1

| 符號      | `.symtab`條目? | 符號類型 | 在哪個模塊中定義 | 節        |
| ------- | ------------ | ---- | -------- | -------- |
| `buf`   | 有            | 外部   | `m.o`    | `.data`  |
| `bufp0` | 有            | 全局   | `swap.o` | `.data`  |
| `bufp1` | 有            | 全局   | `swap.o` | `COMMON` |
| `swap`  | 有            | 全局   | `swap.o` | `.text`  |
| `temp`  | 無            |      |          |          |

# 符號解析

## 解析多重定義的全局符號

對於局部符號的引用，編譯器只允許每個模塊中每個局部符號只有一個定義。

但對於全局符號的引用就麻煩許多。編譯器遇到不是在當前模塊定義的符號時，會假設該符號在其他模塊定義從而生成一個鏈接器符號表條目，並交給鏈接器處理。

編譯時，編譯器像匯編器輸出全局符號與強弱。匯編器將符號的強弱隱含地編碼在可重定位目標文件中的符號表中。

**強符號**：函數和已初始化的全局變量。

**弱符號**：未初始化的全局變量。

根據強弱符號的定義，鏈接器使用以下規則處你多重定義的符號名：
* 不允許多個同名的強符號。
* 如果有一個強符號和多個弱符號同名，選擇強符號。
* 如果有多個弱符號同名，隨機選擇一個。

注意，第二和第三條規則容易帶來不意察覺的運行時錯誤。

``` C
/* foo.c */
#include <stdio.h>
void f(void);
int x = 12345;
int main()
{
	f();
	printf("x = %d\n", x);
	return 0;
}

/* bar.c */
int x;
void f()
{
	x = 54321;
}
```

如果編譯鏈接以上兩程序，會輸出`x = 54321`。使得函數的運行與`main`編寫者的預期相悖。

若重複定義的符號是不同類型，會發生更無法預期的行為。

``` C
/* foo5.c */
#include <stdio.h>

void f(void);
int x = 1, y = 2;

int main()
{
	f();
	printf("x = 0x%x y = 0x%x \n", x, y);
	return 0;
}

/* bar5.c */
double x;

void f()
{
	x = -0.0;
}
```

由於`int`是4字節而`double`是8字節，對`double x`的賦值可能會導致溢出到`y`而更改`y`的值。

而且此時鏈接器僅會觸發警告，所以很容易讓人們忽視，然而這是很危險的。

我們可以使用`gcc -fno -common`標誌調用鏈接器，告訴它當遇到多重定義的全局符號時觸發錯誤。或使用`-Werror`選項將所有警告視為錯誤。

回到上一節的內容，為何編譯器需要將符號分配為`COMMON`或`.bss`呢？

因為當編譯器遇到一個弱符號時，它並不知道其他模塊是否也定義了該符號，也無法知道鏈接器使用多重定義的哪一個。所以它把弱符號分配成`COMMON`，把決定權留給鏈接器。

而當編譯器遇到一個強符號時，因為強符號必須唯一，所以可以直接將其分配成`.bss`。同樣，靜態變量因為是局部符號所以必須唯一，也可以直接將其分配成`.bss`。

### 練習題

7.2

A.

(a) (main.1)

(b) (main.1)

B.

(a) 錯誤

(b) 錯誤

C.

(a) (x.2)

(b) (x.2)

## 靜態庫鏈接

編譯系統提供一種機制，把所有相關的目標模塊打包成一個單獨的文件，稱為**靜態庫(static library)**，可作為鏈接器的輸入。

在Linux中，靜態庫以一種稱**存檔(archive)** 的文件格式存放在磁盤中。存檔文件是一組連接起來的可重定位目標文件的集合，後輟以`.a`標示。

考慮以下代碼

``` C
/* addvec.c */
int addcnt = 0;

void addvec(int *x, int *y, int *z, int n)
{
	int i;
	addcnt++;
	for (i = 0; i < n; i++)
		z[i] = x[i] + y[i];
}

/* multvec.c */
int multcnt = 0;

void multvec(int *x, int *y, int *z, int n)
{
	int i;
	multcnt++;
	for (i = 0; i < n; i++)
		z[i] = x[i] * y[i];
}
```

要創建靜態庫，我們使用`ar`：

``` bash
gcc -c addvec.c multvec.c
ar rcs libvector.a addvec.o multvec.o
```

為了使用這個庫，我們需要編寫一個頭文件定義`libvector.a`中的函數原型。

``` C
/* vector.h */
#ifndef VECTOR_H
#define VECTOR_H
void addvec(int *x, int *y, int *z, int n);
void multvec(int *x, int *y, int *z, int n);
#endif
```

``` C
#include <stdio.h>
#include "vector.h"

int x[2] = { 1, 2 };
int y[2] = { 3, 4 };
int z[2];

int main()
{
	addvec(x, y, z, 2);
	printf("z = [%d %d]\n", z[0], z[1]);
	return 0;
}
```

為了編譯和鏈接`main.o`和`libvector.a`，輸入以下指令：

``` bash
gcc -c main2.c
gcc -static -o prog2 main2.o ./libvector.a
```

`-static`告訴編譯器驅動程序應該鏈接一個完全鏈接的可執行目標文件，它可以加載到內存並運行，在加載時無須進一步的鏈接。

## 用靜態庫解析引用

在符號解析階段，鏈接器從左到右掃描命令行中出現的可重定位目標文件和存檔文件。

同時，鏈接器維護三個集合。一個可重定位目標文件集合$E$(此集合內的文件會被合併成可執行文件)，一個未解析符號集合$U$(引用了但還未定義)，一個已定義符號集合$D$。初始時，三個集合皆為空。

鏈接器依照以下規則鏈接：
* 對命令行中每個輸入文件$f$，依照$f$為目標文件還是存檔文件區分。若$f$為目標文件，那麼鏈接器把$f$添加到$E$，並修改$U$和$D$來反映$f$的符號定義與引用。
* 若$f$為存檔文件，則鏈接器嘗試匹配$U$中未解析符號是否有由存檔文件成員定義的符號。若存檔文件成員$m$中意義了一個符號可用來解析$U$中的一個引用，則將$m$加入$E$中，並修改$U$和$D$來反映$m$中的符號定義和引用。遍歷$f$所有成員執行以上操作。之後任何不在$E$中的$f$成員目標文件都會被丟棄，不被鏈接。
* 若完成對命令行文件掃描後，$U$非空，則鏈接器輸出錯誤並終止。否則，合併與$E$中的目標文件並輸出可執行文件。

注意，命令行中文件出現的順序極為重要，否則這種算法會導致一些鏈接時錯誤。若定義符號的庫出現在符號引用的目標文件之前，那麼引用就無法被解析，鏈接就會失敗。

考慮以下命令：

``` bash
gcc -static ./libvector.a main2.c
```

因為處理`libvector.a`時$U$是空的，所以沒有任何成員目標文件會被添加到$E$中。因此，對`addvec`的引用無法被解析，導致鏈接器產生錯誤信息。

對於庫的鏈接準則是將它們放在命令行的結尾。若各個庫的成員互相獨立(沒有成員引用另一個成員定義的符號)，那麼這些庫就可以用任意順序放置在尾部。若不獨立，則需要對它們排序。若兩個庫相互依賴，則先出現的庫需要被引用兩次。比如`foo`調用`1.a`，且`1.a`和`2.a`相互依賴，則需要使用以下命令：

```bash
gcc foo.c 1.a 2.a 1.a
```

或者，將兩個互相依賴的庫合併成單獨的存檔文件。

### 練習題

7.3

A.

``` bash
gcc -static -Og -o prog p.o libx.a
```

B.

``` bash
gcc -static -Og -o prog p.o libx.a liby.a
```

C.

(錯誤)
``` bash
gcc -static -Og -o prog p.o libx.a liby.a libx.a p.o
```

(正確)
``` bash
gcc -static -Og -o prog p.o libx.a liby.a libx.a
```

因為`p.o`是目標文件，一定會被完整包含在可執行文件中，所以當`libx.a`需要尋找定義時，可以直接在全局符號表中找到，無須再次掃描`p.o`。

# 重定位

重定位由兩步組成：
* 重定位節和符號定義
* 重定位節中的符號引用

## 重定位條目

匯編器生成一個目標文件時，它不知道數據和代碼最終放在內存的哪個位置，也不知道引用的外部定義函數或全局變量的位置。所以，當匯編器遇到最終位置未知的目標引用就會生成一個**重定位條目(relocation entry)**，告知鏈接器在合併時如何修改這個引用。

以下代碼展示了ELF重定位條目的格式：

``` C
typedef struct {
	long offset;        /* Offset of the reference to relocate */
	long type:32,       /* Relocation type */
	     symbol:32;     /* Symbol table index */
	long addend;        /* Constant part of relocation expression */
} Elf64_Rela;
```

`offset`：需要被修改的引用的節偏移。

`type`：告知鏈接器如何修改引用。

`symbol`：標示被修改引用應指向的符號。

`addend`：有符號常數，某些類型的重定位需要它對修改的值做偏移。

ELF定義了32種重定位類型，以下我們著重關心兩種基本類型：
* `R_X86_64_PC32`：重定位使用32位PC相對地址的引用，即相對尋址。
* `R_X86_64`：重定位使用32位絕對地址的引用，即絕對尋址。

## 重定位符號引用

以下代碼為鏈接器重定位算法的偽代碼：

``` C
foreach section s {
	foreach relocation entry r {
		refptr = s + r.offset;    /* 指向需要重定位的引用的物理地址指針 */

		if (r.type == R_X86_64_PC32) {
			refaddr = ADDR(s) + r.offset;    /* 需要重定位的引用的運行時地址 */
			/* 相對循址 = ADDR(r.symbol) - PC */
			/* PC = refaddr - r.addend */
			*refptr = (unsigned) (ADDR(r.symbol) - refaddr + r.addend);
		}

		if (r.type == R_X86_64)
			*refptr = (unsigned) (ADDR(r.symbol) + r.addend);
	}
}
```

### 練習題

7.4

A. `0x4004df`

B. `0x5`

7.5

`refaddr = 0x4004da`

`ADDR(swap) = 0x4004e8`

`0x4004e8 - 0x4004da - 4 = a`

答：`0xa`

# 可執行目標文件

下圖展示了一個典型ELF可執行文件中的各類信息。

![[Pasted image 20250720155449.png]]

ELF頭描述文件總體格式且包含**入口點(entry point)**。

`.init`定義了一個函數，稱`_init`，程序初始化代碼會調用它。

因為程序是**完全鏈接的(已被重定位)**，所以不再需要`rel`節。

**程序頭部表(program header table)** 描述了如何將可執行文件連續的片(chunk)映射到連續的內存段。

![[Pasted image 20250720165729.png]]

上圖展示了可執行文件`prog`的程序頭部表。

`off`：目標文件中的偏移。

`vaddr/paddr`：內存地址。

`align`：對齊要求。

`filesz`：目標文件中的段大小。

`memsz`：內存中的段大小。

`flag`：運行時訪問權限。

對於任何段$s$，鏈接器必須選擇一個起始地址`vaddr`，使得：

$$
vaddr \ mod \ align = off \ mod \ align
$$

# 加載可執行目標文件

執行程序時，會調用稱為**加載器(loader)** 的操作系統代碼來運行。Linux程序可以通過調用函數`execve`來調用加載器。

加載器將可執行文件的代碼與數據複製到內存中，然後跳轉到程序的第一條指令或**入口點(entry point, EP)** 來運行該程序。這種將程序複製到內存並運行的行為稱**加載**。

每個程序都有一個**運行時內存映像(run-time memory image)**，如下圖所示。

![[Pasted image 20250721124602.png]]

雖然圖中代碼段和數據段相鄰，但實際上`.data`段因為有對齊要求，所以代碼段與數據段間有間隙。

又因為ASLR，堆、共享庫和棧因為地址空間布局隨機化導致每次運行時地址皆不同，但是相對位置不變。

程序的EP是`_start`函數，此函數在`ctrl.o`中定義。它會調用系統啟動函數`__libc_start_main`，此函數定義在`libc.so`中。它會初始化執行環境，調用用戶層的`main`函數並處理`main`的返回值。

# 動態鏈接共享庫

**共享庫(shared library，或稱共享目標 shared object)** 是一個目標模塊，可以加載到任意內存地址，並和內存中的程序鏈接。此過程稱**動態鏈接(dynamic linking)**，由**動態鏈接器(dynamic linker)** 執行。共享庫在Linux系統以`.so`後輟表示，在Windows系統中以`.dll`後輟表示。

![[Pasted image 20250721130435.png]]

上圖展示了簡略的動態鏈接過程。

我們可以使用以下指令創建共享庫：

``` bash
gcc -shared -fpic -o libvector.so addvec.c multvec.c
```

其中，`-fpic`表示生成與位置無關的代碼。

我們可以使用以下代碼鏈接共享庫：

``` bash
gcc -o prog21 main2.c ./libvector.so
```

# 從程序中加載和鏈接共享庫

Linux為動態鏈接庫提供了接口，允許程序在運行時加載和鏈接共享庫：

``` C
#include <dlfcn.h>
void *dlopen(const char *filename, int flag); /* 返回：成功則為指向句柄的指針，否則為NULL */
```

`flag`參數一定要包含以下兩下之一：
* `RTLD_NOW`：加載時立即解析庫中對外部符號的引用。
* `RTLD_LAZY`：推遲符號解析直到執行來自庫的代碼。

``` C
#include <dlfcn.h>
void *dlsym(void *handle, char *symbol); /* 返回：成功則為指向符號的指針，否則為NULL */
```

``` C
#include <dlfcn.h>
int dlclose(void *handle); /* 返回：成功為0，失敗為-1 */
```

``` C
#include <dlfcn.h>
const char *dlerror(void); /*返回：前幾項函數的錯誤資訊，若函數調用成功則為NULL*/
```

讓我們用以上提到的函數編寫一個示例代碼：

``` C
#include <stdio.h>
#include <stdlib.h>
#include <dlfcn.h>

int x[2] = { 1, 2 };
int y[2] = { 3, 4 };
int z[2];

int main()
{
	void *handle;
	void (*addvec) (int *, int *, int *, int);
	char *error;

	handle = dlopen("./libvector.so", RTLD_LAZY);
	if (!handle) {
		fprintf(stderr, "%s\n", dlerror());
		exit(1);
	}

	addvec = dlsym(handle, "addvec");
	if ((error = dlerror()) != NULL) {
		fprintf(stderr, "%s\n", error);
		exit(1);
	}

	addvec(x, y, z, 2);
	printf("z = [%d %d]\n", z[0], z[1]);

	if (dlclose(handle) < 0) {
		fprintf(stderr, "%s\n", dlerror());
		exit(1);
	}

	return 0;
}
```

並如下編譯程序：

``` bash
gcc -rdynamic -o prog2r dll.c -ldl
```

# 位置無關代碼

**位置無關代碼(Position-Independent Code, PIC)** 是可以加載而不用重定位的代碼，使得共享庫可以被加載到內存中的任意位置而無須鏈接器修改。通過這種方法，無限多個進程可以共享一個共享庫。

## PIC數據引用

編譯器通過以下事實生成對全局變量的PIC引用：無論在內存何處加載目標模塊，數據段與代碼段的距離總是保持一致。

編譯器會在數據段的開始處創建一個**全局偏移量表(Global Offset Table, GOT)**，每個引用全局變量的目標模塊都有自己的GOT。

在GOT中，每個被目標模塊引用的全局變量都有一個8字節條目，且每個條目都有一個重定位紀錄。加載時，動態鏈接器會重定位GOT中的每個條目，使其包含目標的絕對地址。

下圖展示了`libvector.so`共享模塊的GOT。`addvec`通過`GOT[3]`加載`addcnt`並加一。這裡的關鍵思想是對`GOT[3]`和PC相對引用中的偏移量是一個常量。

![[Pasted image 20250721142630.png]]

## PIC函數調用

GNU通過**延遲綁定(lazy binding)** 將函數地址的解析推遲到實際被調用的時候。

延遲綁定通過兩個數據結構的交互實現：GOT和**過程鏈接表(Procedure Linkage Table, PLT)**。

若目標模塊調用了共享庫中的函數，它就會擁有自己的GOT和PLT表。GOT存在數據段，PLT存在代碼段。

PLT是個數組，每個條目是16字節代碼，每個被程序調用的庫函數都有自己的PLT條目。`PLT[0]`是特殊條目，負責跳轉到動態鏈接器中。`PLT[1]`調用系統啟動函數`__libc_start_main`。從`PLT[2]`開始的條目才是用戶代碼調用的函數。

GOT和PLT聯合使用時，`GOT[0]`和`GOT[1]`包含動態鏈接器在解析函數地址時需要使用的信息，`GOT[2]`是動態鏈接器在`ld-linux.so`模塊中的EP。剩餘條目都有對應的PLT條目，且剩餘GOT條目對應每個被調用的函數，而函數的地址在運行時才會被取得。所以初始時，每個GOT條目都指向對應PLT條目的第二條指令(該指令將函數ID入棧，幫助取得函數地址)。

![[Pasted image 20250721151025.png]]

上圖展示了GOT如何和PLT協作。

當`addvec`第一次被調用，延遲解析運行時地址：
1. 程序調用`addvec`時跳轉到`PLT[2]`(`addvec`的PLT條目)。
2. 跳轉到`GOT[4]`，此時`GOT[4]`因為還未取得`addvec`的運行時地址，所以指向`PLT[2]`的下一條指令。將`0x1`(`addvec`的ID)入棧。
3. 跳轉到`PLT[0]`，將`GOT[1]`(重定位入口)入棧。
4. 跳轉到`GOT[0]`(動態鏈接器的EP)，讀取棧中兩個參數並取得`addvec`的運行時地址。最終將該地址寫回`GOT[4]`，並調用`addvec`。

當`addvec`不是初次調用：
1. 跳轉到`PLT[2]`。
2. 跳轉到`GOT[4]`，因為其已經擁有`addvec`運行時地址，會直接調用`addvec`。

# 庫打樁機制

**庫打樁(library interpositioning)** 允許用戶擷取對共享庫的調用，取而代之執行自己的代碼。

打樁可以發生在編譯時，鏈接時或運行時。

以下僅介紹運行時打樁。

## 運行時打樁

運行時打樁依賴於環境變量`LD_PRELOAD`，若該值被設置為一個共享庫路徑名的列表，則當執行程序解析未定義引用時，動態鏈接器會先搜索`LD_PRELOAD`庫才去搜索其他庫。有了這個機制，才使得我們可以在運行時打樁。

同時，我們還要知道一個偽句柄`RTLD_NEXT`。當執行`dlsym`時將該偽句柄傳入，可以獲得鏈接順序中"下一個"定義了該符號的函數地址(下一個才是真正的函數地址，當前這個是我們自己定義的函數)。

``` C
/* mymalloc. */
#ifdef RUNTIME
#define _GNU_SOURCE
#include <stdio.h>
#include <stdlib.h>
#include <dlfcn.h>

/* malloc wrapper funciton */
void *malloc(size_t size)
{
	void *(*mallocp) (size_t size);
	char *error;

	mallocp = dlsym(RTLD_NEXT, "malloc");
	if ((error = dlerror()) != NULL) {
		fputs(error, stderr);
		exit(1);
	}
	char *ptr = mallocp(size); /* Call libc malloc */
	/* 因為printf內部調用malloc，導致無限遞歸 */
	// printf("malloc(%d) = %p\n", (int)size, ptr);
	return ptr;
}

void free(void *ptr)
{
	void (*freep) (void *) = NULL;
	char *error;

	if (!ptr)
		return;

	freep = dlsym(RTLD_NEXT, "free");
	if ((error = dlerror()) != NULL) {
		fputs(error, stderr);
		exit(1);
	}
	freep(ptr);
	/* 因為printf內部調用malloc，導致無限遞歸 */
	// printf("free(%p)\n", ptr);
}
#endif
```

``` C
/* int.c */
#include <stdio.h>
#include <stdlib.h>

int main()
{
	int *p = malloc(32);
	free(p);
	return 0;
}
```

以下指令構建包裝函數的共享庫：

``` bash
gcc -DRUNTIME -shared -fpic -o mymalloc.so mymalloc.c -ldl
```

以下指令編譯主程序：

``` bash
gcc -o intr int.c
```

以下是如何從shell運行程序

``` bash
LD_PRELOAD = "./mamalloc.so" ./intr
```