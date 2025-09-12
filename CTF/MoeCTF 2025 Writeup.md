
# upx

文件下載後查殼，發現是upx殼，直接 `upx -d` 脫掉。

運行程序，程序提示"please input your flag: "，有了字符串，我們就可以開始分析了。

把程序拖到IDA中，按shift+f12打開字符串窗口，找到"please input your flag: "字樣的字符串並雙擊進去。

可以看到有交叉引用 `; DATA XREF: sub_1400118A0+148↑o` ，雙擊函數名就可以跳轉到引用函數。

按下tab鍵即可將彙編轉換為C語言：

``` C
__int64 encode()
{
  char *v0; // rdi
  __int64 i; // rcx
  FILE *v2; // rax
  char v4[32]; // [rsp+0h] [rbp-20h] BYREF
  char v5; // [rsp+20h] [rbp+0h] BYREF
  int check_msg[44]; // [rsp+30h] [rbp+10h]
  char Buffer[132]; // [rsp+E0h] [rbp+C0h] BYREF
  int size; // [rsp+164h] [rbp+144h]
  char encoded_msg[60]; // [rsp+188h] [rbp+168h]
  int j; // [rsp+1C4h] [rbp+1A4h]
  int tmp; // [rsp+1E4h] [rbp+1C4h]
  int k; // [rsp+204h] [rbp+1E4h]

  v0 = &v5;
  for ( i = 130i64; i; --i )
  {
    *(_DWORD *)v0 = -858993460;
    v0 += 4;
  }
  sub_140011375(&unk_14002200E);
  /* 將加密後的 flag 寫入 check_msg */
  check_msg[0] = 35;
  check_msg[1] = 43;
  check_msg[2] = 39;
  check_msg[3] = 54;
  check_msg[4] = 51;
  check_msg[5] = 60;
  check_msg[6] = 3;
  check_msg[7] = 72;
  check_msg[8] = 100;
  check_msg[9] = 11;
  check_msg[10] = 29;
  check_msg[11] = 118;
  check_msg[12] = 123;
  check_msg[13] = 16;
  check_msg[14] = 11;
  check_msg[15] = 58;
  check_msg[16] = 63;
  check_msg[17] = 101;
  check_msg[18] = 118;
  check_msg[19] = 41;
  check_msg[20] = 21;
  check_msg[21] = 55;
  check_msg[22] = 28;
  check_msg[23] = 10;
  check_msg[24] = 8;
  check_msg[25] = 33;
  check_msg[26] = 62;
  check_msg[27] = 60;
  check_msg[28] = 61;
  check_msg[29] = 22;
  check_msg[30] = 11;
  check_msg[31] = 36;
  check_msg[32] = 41;
  check_msg[33] = 36;
  check_msg[34] = 86;
  printf("please input your flag: ");
  v2 = _acrt_iob_func(0);
  fgets(Buffer, 100, v2);    /* 注意，fgets 會將'\n'一起複製到 Buffer */*
  size = j_strlen(Buffer);
  /* 加密循環 */
  for ( j = 0; j < size; ++j )
  {
    tmp = Buffer[j] ^ 0x21;
    if ( j < size - 1 )
      tmp ^= Buffer[j + 1];
    encoded_msg[j] = tmp;
  }
  /* 將加密後的用戶輸入與加密後的 flag 對比 */
  for ( k = 0; k < 35; ++k )
  {
    if ( encoded_msg[k] != check_msg[k] )
    {
      printf("you will never get the flag!!!!\n");
      break;
    }
  }
  sub_140011311(v4, &unk_14001AD00);
  return 0i64;
}
```

可以看出主加密循環如下：

``` C
for ( j = 0; j < size; ++j )
{
    tmp = Buffer[j] ^ 0x21;
    if ( j < size - 1 )
      tmp ^= Buffer[j + 1];
    encoded_msg[j] = tmp;
}
```

需要注意的是，`fgets`會把輸入字符串最後的 '\n' 也包含在內！因為漏了這個我調了好久...

我們只要寫出解密循環即可：

``` C
#include <stdio.h>
#include <string.h>

void decrypt(unsigned int *in, size_t size)
{
    unsigned int result[36];
    for (int i = 0; i < size; i++) {
        result[i] = in[i];
    }

    result[size-1] ^= 0x21;

    for (int i = size-2; i >= 0; i--) {
        result[i] ^= 0x21;
        result[i] ^= result[i+1];
    }

    printf("after: ");
    for (int i = 0; i < size; i++) {
        printf("%c", result[i]);
    }
}

int main()
{
    unsigned char encrypt[108] = "23 2B 27 36 33 3C 03 48 64 0B 1D 76 7B 10 0B 3A 3F 65 76 29 15 37 1C 0A 08 21 3E 3C 3D 16 0B 24 29 24 56 2B";
    unsigned int tmp[36];
    for (int i = 0; i < 108; i += 3) {
        sscanf(encrypt + i, "%X", &tmp[i/3]);
    }
    decrypt(tmp, 36);

    return 0;
}
```

得到 flag: moectf{Y0u_c4n_unp4ck_It_vvith_upx}

# ez3

此題考察 z3 求解器相關操作。

在IDA中尋找字符串 "Input your flag："，雙擊跳轉到引用函數：

``` C
int __fastcall main(int argc, const char **argv, const char **envp)
{
  char v3; // bl
  bool v4; // r12
  __int64 flag_footer; // rbx
  __int64 flag_header; // rax
  char flag_body; // [rsp+Fh] [rbp-71h] BYREF
  __int64 input_start; // [rsp+10h] [rbp-70h] BYREF
  __int64 input_end; // [rsp+18h] [rbp-68h] BYREF
  char usrinput[32]; // [rsp+20h] [rbp-60h] BYREF
  char prefix[40]; // [rsp+40h] [rbp-40h] BYREF
  unsigned __int64 v13; // [rsp+68h] [rbp-18h]

  v13 = __readfsqword(0x28u);
  printf("Input your flag:\n> ", argv, envp);
  fflush(stdout);
  std::string::basic_string(usrinput);
  std::operator>><char>(&std::cin, usrinput);
  if ( std::string::length(usrinput) == 42 )
  {
    v3 = 0;
    v4 = 1;
    if ( (unsigned __int64)std::string::length(usrinput) > 7 )
    {
      std::string::substr(prefix, usrinput, 0LL, 7LL);// substr "moectf{"
      v3 = 1;
      if ( !(unsigned __int8)std::operator!=<char>(prefix, "moectf{") && *(_BYTE*)std::string::back(usrinput) == 125 )
        v4 = 0;
    }
    if ( v3 )
      std::string::~string(prefix);
    if ( v4 )
    {
      puts("FORMAT ERROR!");
    }
    else
    {
      std::allocator<char>::allocator(&flag_body);
      input_end = std::string::end(usrinput);
      flag_footer = __gnu_cxx::__normal_iterator<char *,std::string>::operator-(&input_end, 1LL);
      input_start = std::string::begin(usrinput);
      flag_header = __gnu_cxx::__normal_iterator<char *,std::string>::operator+(&input_start, 7LL);
      std::string::basic_string<__gnu_cxx::__normal_iterator<char *,std::string>,void>(
        prefix,
        flag_header,
        flag_footer,
        &flag_body);
      std::string::operator=(usrinput, prefix);
      std::string::~string(prefix);
      std::allocator<char>::~allocator(&flag_body);
      std::string::basic_string(prefix, usrinput);
      LOBYTE(flag_footer) = check(prefix);
      std::string::~string(prefix);
      if ( (_BYTE)flag_footer )
      {
        puts("OK");
        puts("But I don't know what the true flag is");
      }
      else
      {
        puts("try again~");
      }
    }
  }
  else
  {
    puts("Length error!");
  }
  std::string::~string(usrinput);
  return 0;
}
```

在此，我們把 "moectf{" 稱 `flag_header`，"}" 稱 `flag_footer`，大擴號之間的內容稱 `flag_body` 。

可以看到，函數把 `flag_body` 當作參數傳入了 `check()` 函數中。我們去 `check()` 中看看內容：

``` C
__int64 __fastcall check(__int64 a1)
{
  int i; // [rsp+1Ch] [rbp-4h]

  for ( i = 0; i <= 33; ++i )
  {
    check(std::string)::b[i] = 47806 * (*(char *)std::string::operator[](a1, i) + i);// b[i] = 47806 * (a[i] + i);
    if ( i )
      check(std::string)::b[i] ^= check(std::string)::b[i - 1] ^ 0x114514;// b[i] ^= b[i-1] ^ 0x114514;
    check(std::string)::b[i] %= 51966;          // b[i] %= 51966;
    if ( check(std::string)::b[i] != a[i] )
      return 0LL;
  }
  return 1LL;
}
```

以上函數操作對參數 `a1` 做一系列位運算並暫存在 `b` 中，然後用出題人設置好的變量 `a` 對 `b` 檢查。

查看 `a` 的內容：

``` C
.data:00000000005D9140 a               dd 0B1B0h, 5678h, 7FF2h, 0A332h, 0A0E8h, 364Ch, 2BD4h
.data:00000000005D915C                 dd 0C8FEh, 4A7Ch, 18h, 2BE4h, 4144h, 3BA6h, 0BE8Ch, 8F7Eh
.data:00000000005D917C                 dd 35F8h, 61AAh, 2B4Ah, 6828h, 0B39Eh, 0B542h, 33ECh, 0C7D8h
.data:00000000005D919C                 dd 448Ch, 9310h, 8808h, 0ADD4h, 3CC2h, 796h, 0C940h, 4E32h
.data:00000000005D91BC                 dd 4E2Eh, 924Ah, 5B5Ch
```

有了這些資訊，我們就可以使用 z3 求解：

``` python
import z3

x = [z3.BitVec(f"a_{i}", 32) for i in range(34)]
b = [z3.BitVec(f"b_{i}", 32) for i in range(34)]
ahex = ['0B1B0', '5678', '7FF2', '0A332', '0A0E8', '364C', '2BD4',
'0C8FE', '4A7C', '18', '2BE4', '4144', '3BA6', '0BE8C', '8F7E',
'35F8', '61AA', '2B4A', '6828', '0B39E', '0B542', '33EC', '0C7D8',
'448C', '9310', '8808', '0ADD4', '3CC2', '796', '0C940', '4E32',
'4E2E', '924A', '5B5C']

s = z3.Solver()
a = [int(h, 16) for h in ahex]

for i in range(34):
    s.add(z3.UGE(x[i], z3.BitVecVal(32, 32)), z3.ULE(x[i], z3.BitVecVal(126, 32)))
    
    tmp = z3.BitVecVal(47806, 32) * (x[i] + z3.BitVecVal(i, 32))
    if i:
        tmp = tmp ^ b[i-1] ^ z3.BitVecVal(0x114514, 32)
    s.add(b[i] == z3.URem(tmp, z3.BitVecVal(51966, 32)))
    s.add(b[i] == z3.BitVecVal(a[i], 32))
    
check = s.check()
print("solving...")
while check == z3.sat:
    model = s.model()
    cur = [model[x[i]].as_long() for i in range(34)]
    s.add(z3.Or(x[j] != z3.BitVecVal(cur[j], 32) for j in range(34)))
    print("moectf{", end='')
    print(''.join(chr(model[x[i]].as_long()) for i in range(34)), end='')
    print("}")
    check = s.check()

print("No more valid flag...")
```

需要注意的是，本題存在多組解可能通過驗證，但是只有一組解可以通過評測。

嘗試幾個 flag 之後得到唯一解：moectf{Y0u_Kn0w_z3_S0Iv3r_N0w_a1f2bdce4a9} 

# flower

此題考察花指令相關內容。

在 IDA 中查找字符串，並定位到引用函數處。嘗試 f5 時，提示：Decompiler error: 4048E9: positive value sp has been found，表示堆棧不平衡。

``` asm
.text:00000000004048E5 loc_4048E5:                             ; CODE XREF: solve(std::string)+A6↑j
.text:00000000004048E5                 jz      short Label
.text:00000000004048E7                 jnz     short Label
.text:00000000004048E9                 call    near ptr Label+1
.text:00000000004048EE
.text:00000000004048EE Label:                                  ; CODE XREF: solve(std::string):loc_4048E5↑j
.text:00000000004048EE                                         ; solve(std::string)+DA↑j ...
.text:00000000004048EE                 lea     rax, [rbp+var_59]
.text:00000000004048EE _Z5solveNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEE endp ; sp-analysis failed
```

注意看 `0x4048E5` 與 `0x4048E7` 處代碼，可以發現不管運算結果如何，都會跳轉到 `Label`。那麼， `0x4048E9` 處的 `call` 便是花指令，我們把他 `nop` 掉。注意，後面的 `0x00` 也必須用 `0x90` 填充。

然後，回到函數頂部，使用 `U` 轉為數據，然後再按 `C` 轉回代碼，並按 `P` 創建函數 。這樣可使IDA重新分析此處代碼。此時，再按 f5 就可以正常顯示了：

``` C
unsigned __int64 __fastcall solve(__int64 a1)
{
  char v1; // bl
  bool v2; // r12
  __int64 v3; // rax
  __int64 v4; // rbx
  __int64 v5; // rax
  char *v6; // rax
  __int64 v7; // rax
  char v9; // [rsp+17h] [rbp-59h] BYREF
  int i; // [rsp+18h] [rbp-58h]
  int v11; // [rsp+1Ch] [rbp-54h]
  __int64 v12; // [rsp+20h] [rbp-50h] BYREF
  __int64 v13; // [rsp+28h] [rbp-48h] BYREF
  char v14[40]; // [rsp+30h] [rbp-40h] BYREF
  unsigned __int64 v15; // [rsp+58h] [rbp-18h]

  v15 = __readfsqword(0x28u);
  v1 = 0;
  v2 = 1;
  if ( (unsigned __int64)std::string::length(a1) > 7 )
  {
    std::string::substr(v14, a1, 0LL, 7LL);
    v1 = 1;
    if ( !(unsigned __int8)std::operator!=<char>(v14, "moectf{") && *(_BYTE *)std::string::back(a1) == 125 )
      v2 = 0;
  }
  if ( v1 )
    std::string::~string(v14);
  if ( v2 )
  {
    v3 = std::operator<<<std::char_traits<char>>((std::ostream *)&std::cout);
    std::ostream::operator<<(v3, std::endl<char,std::char_traits<char>>);
  }
  else
  {
    std::allocator<char>::allocator(&v9);
    v13 = std::string::end(a1);
    v4 = __gnu_cxx::__normal_iterator<char *,std::string>::operator-(&v13, 1LL);
    v12 = std::string::begin(a1);
    v5 = __gnu_cxx::__normal_iterator<char *,std::string>::operator+(&v12, 7LL);
    std::string::basic_string<__gnu_cxx::__normal_iterator<char *,std::string>,void>(v14, v5, v4, &v9);
    std::string::operator=(a1, v14);
    std::string::~string(v14);
    std::allocator<char>::~allocator(&v9);
    v11 = std::string::length(a1);
    if ( v11 == 32 )
    {
      for ( i = 0; i < v11; ++i )
      {
        v6 = (char *)std::string::operator[](a1, i);
        if ( (unsigned int)encode(*v6) != enc[i] )
          break;
      }
    }
    v7 = std::operator<<<std::char_traits<char>>((std::ostream *)&std::cout);
    std::ostream::operator<<(v7, std::endl<char,std::char_traits<char>>);
  }
  return v15 - __readfsqword(0x28u);
}
```

可以看到，調用了 `encode` 將輸入加密後與 `enc` 逐個對比。

看看加密部分：

``` C
__int64 __fastcall encode(int a1)
{
  int v1; // eax

  v1 = key++;
  return a1 ^ (unsigned int)v1;
}
```

可以看到，使用 `key++` 對輸入異或。

現在我們需要的是，`key` 的值與 `enc` 的值：

``` asm
.data:00000000005D92D0 key             dd 23h                  ; DATA XREF: encode(int)+B↑r

.data:00000000005D9140 enc             dd 4Fh, 1Ah, 59h, 1Fh, 5Bh, 1Dh, 5Dh, 6Fh, 7Bh, 47h, 7Eh
.data:00000000005D9140                                         ; DATA XREF: solve(std::string)+1F4↑o
.data:00000000005D9140                                         ; solve(std::string)+250↑o
.data:00000000005D916C                 dd 44h, 6Ah, 7, 59h, 67h, 0Eh, 52h, 8, 63h, 5Ch, 1Ah, 52h
.data:00000000005D919C                 dd 1Fh, 20h, 7Bh, 21h, 77h, 70h, 25h, 74h, 2Bh, 44h dup(0)
```

然後我們就可以編寫簡單的解密代碼：

``` python
key = 0x23
enc_hex = ['4F', '1A', '59', '1F', '5B', '1D', '5D', '6F', '7B', '47', '7E',
       '44', '6A', '7', '59', '67', '0E', '52', '8', '63', '5C', '1A', '52',
       '1F', '20', '7B', '21', '77', '70', '25', '74', '2B']
enc = [int(i, 16) for i in enc_hex]

de_enc = [enc[i] ^ (key + i) for i in range(32)]

check = [de_enc[i] ^ (key + i) for i in range(32)]

print("moectf{", end="")
print("".join(chr(i) for i in de_enc), end="")
print("}")
```

但是腳本跑出來的數據卻怎麼也不像正確的 flag：moectf{l>|9|5tEPkSjE7hU=f=Uk"k%IOe5i}，甚至包含不可打印字符，推測是 `key` 的值中途被修改了。

只好去動態調試尋找問題。第一次調試發現在 `check` 函數裡有簡單的反調試，我們在 gdb 裡給 `check` 打上斷點，然 後修改 `al` 的值即可解決問題，很簡單不再贅述。

給 `key` 打上內存斷點 `watch *(int*)0x5D92D0`，然後運行。我們可以發現 `key` 的值被從 `0x23` 修改成 `0x29`，讓我們使用這個值重新跑一次腳本，得到 flag：moectf{f0r3v3r_JuMp_1n_7h3_a$m_a9b35c3c}

# A cup of tea

此題考察 `tea` 加密算法。

通過 IDA，我們可以觀察到以下代碼：

``` C
__int64 sub_1400162E0()
{
  char *v0; // rdi
  __int64 i; // rcx
  char v3[32]; // [rsp+0h] [rbp-20h] BYREF
  char v4; // [rsp+20h] [rbp+0h] BYREF
  int v5[12]; // [rsp+28h] [rbp+8h] BYREF
  int v6[20]; // [rsp+58h] [rbp+38h]
  int usrinput[20]; // [rsp+A8h] [rbp+88h] BYREF
  int usrinput_encrypted[20]; // [rsp+F8h] [rbp+D8h] BYREF
  char Str[64]; // [rsp+148h] [rbp+128h] BYREF
  size_t Size; // [rsp+188h] [rbp+168h]
  int j; // [rsp+1A4h] [rbp+184h]
  int v12; // [rsp+1C8h] [rbp+1A8h] BYREF
  int v13; // [rsp+1CCh] [rbp+1ACh]
  int v14; // [rsp+1E4h] [rbp+1C4h]
  int k; // [rsp+204h] [rbp+1E4h]

  v0 = &v4;
  for ( i = 130i64; i; --i )
  {
    *(_DWORD *)v0 = -858993460;
    v0 += 4;
  }
  sub_140011384(&unk_140023015);
  v5[0] = 289739801;
  v5[1] = 427884820;
  v5[2] = 1363251608;
  v5[3] = 269567252;
  v6[0] = 2026214571;
  v6[1] = 578894681;
  v6[2] = 1193947460;
  v6[3] = -229306230;
  v6[4] = 73202484;
  v6[5] = 961145356;
  v6[6] = -881456792;
  v6[7] = 358205817;
  v6[8] = -554069347;
  v6[9] = 119347883;
  v6[10] = 0;
  memset(usrinput, 0, 0x2Cui64);
  memset(usrinput_encrypted, 0, 0x2Cui64);
  print(&unk_14001AED0);                        //  "輸入你的flag"
  scanf(&Format, Str);                          // scanf("%s", &Str)
  Size = j_strlen(Str);
  j_memcpy(usrinput, Str, Size);
  for ( j = 0; j < 5; ++j )
  {
    v12 = usrinput[2 * j];
    v13 = usrinput[2 * j + 1];
    j_tea_encrypt((unsigned int *)&v12, v5);
    usrinput_encrypted[2 * j] = v12;
    usrinput_encrypted[2 * j + 1] = v13;
  }
  v14 = 1;
  for ( k = 0; k < 11; ++k )
  {
    if ( usrinput_encrypted[k] != v6[k] )
    {
      v14 = 0;
      print("You are wrong!!");
      break;
    }
  }
  if ( v14 == 1 )
    print("Congratulations!!!!");
  sub_140011320(v3, &unk_14001AE60);
  return 0i64;
}
```

讓我們跳進 `j_tea_encrypted`(函數經過手動重命名) 查看具體內容：

``` c
// attributes: thunk
__int64 __fastcall j_tea_encrypt(unsigned int *plaintext, _DWORD *key)
{
  return tea_encrypt(plaintext, key);
}
```

發現其中還調用 `tea_encrypt`(函數經過手動重命名)：

``` c
__int64 __fastcall tea_encrypt(unsigned int *plaintext, _DWORD *key)
{
  __int64 result; // rax
  int v3; // [rsp+24h] [rbp+4h]
  unsigned int v4; // [rsp+44h] [rbp+24h]
  unsigned int v5; // [rsp+64h] [rbp+44h]
  int i; // [rsp+A4h] [rbp+84h]

  sub_140011384(&unk_140023015);
  v3 = 0;
  v4 = *plaintext;
  v5 = plaintext[1];
  for ( i = 0; i < 32; ++i )
  {
    v3 += 1131796;                              //  0x114514
    v4 += (key[1] + (v5 >> 5)) ^ (v3 + v5) ^ (*key + 16 * v5);
    v5 += (key[3] + (v4 >> 5)) ^ (v3 + v4) ^ (key[2] + 16 * v4);
  }
  *plaintext = v4;
  result = 4i64;
  plaintext[1] = v5;
  return result;
}
```

可以觀察出這就是 `tea` 加密算法，其中本來用以實現 `tea` 的常數 `0x9e3779b9` 被替換成 `0x114514`。

由以上資訊，我們可以寫出以下代碼：

``` cpp
#pragma once
#include <cstdint>

class tea
{
private:
	uint32_t *_plaintext, *_key;
	uint32_t _delta = 0x9e3779b9;
public:
	tea(uint32_t* plaintext, uint32_t* key) : _plaintext(plaintext), _key(key) {};
	tea(uint32_t* plaintext, uint32_t* key, uint32_t delta) : _plaintext(plaintext), _key(key), _delta(delta) {};
	~tea() = default;

	void set_tea(uint32_t *plaintext, uint32_t *key, uint32_t delta = 0x9e3779b9)
	{
		_plaintext = plaintext;
		_key = key;
		_delta = delta;
	}
	void encrypt();
	void decrypt();
};
```

``` c++
#include "tea.h"

void tea::encrypt()
{
	uint32_t v0 = _plaintext[0], v1 = _plaintext[1], sum = 0, i = 0;
	uint32_t k0 = _key[0], k1 = _key[1], k2 = _key[2], k3 = _key[3];
	for (i = 0; i < 32; i++) {
		sum += _delta;
		v0 += ((v1 << 4) + k0) ^ (v1 + sum) ^ ((v1 >> 5) + k1);
		v1 += ((v0 << 4) + k2) ^ (v0 + sum) ^ ((v0 >> 5) + k3);
	}
	_plaintext[0] = v0;
	_plaintext[1] = v1;
}

void tea::decrypt()
{
	uint32_t v0 = _plaintext[0], v1 = _plaintext[1], sum = _delta * 32, i = 0;
	uint32_t k0 = _key[0], k1 = _key[1], k2 = _key[2], k3 = _key[3];
	for (i = 0; i < 32; i++) {
		v1 -= ((v0 << 4) + k2) ^ (v0 + sum) ^ ((v0 >> 5) + k3);
		v0 -= ((v1 << 4) + k0) ^ (v1 + sum) ^ ((v1 >> 5) + k1);
		sum -= _delta;
	}
	_plaintext[0] = v0;
	_plaintext[1] = v1;
}
```

``` cpp
#include <iostream>
#include "tea.h"

int main()
{
	uint32_t v5[4];
	v5[0] = 289739801;
	v5[1] = 427884820;
	v5[2] = 1363251608;
	v5[3] = 269567252;

	uint32_t v6[20];
	v6[0] = 2026214571;
	v6[1] = 578894681;
	v6[2] = 1193947460;
	v6[3] = -229306230;
	v6[4] = 73202484;
	v6[5] = 961145356;
	v6[6] = -881456792;
	v6[7] = 358205817;
	v6[8] = -554069347;
	v6[9] = 119347883;
	v6[10] = 0;

	for (int i = 0; i < 11; i += 2) {
		tea my_tea(v6 + i, v5, 0x114514);
		my_tea.decrypt();
	}
	printf("%s\n", v6);
	return 0;
}
```

flag 為：`moectf{h3r3_4_cuP_0f_734_f0R_y0U!!!!!!}`。