
# 作用域枚舉

普通的 `enum`：

``` C++
// buggy! 
enum egg {small, medium, large};
enum shirt {small, medium, large, xlarge};
```

因為二者處於相同作用域內，所以會發生衝突。

而且普通的 `enum` 可以轉為 `int` 類型。

枚舉類(`enum class`)：

``` cpp
enum class egg {small, medium, large};
enum class shirt {small, medium, large, xlarge};
```

二者的作用域為類，所以不會衝突。

注意，**枚舉類無法被隱式的轉為 `int` 類型**。(只能顯式轉)

默認情況下枚舉類的底層類型為 `int`，但你可以自己定義：

``` cpp
enum class : short egg {small, medium, large};
```

# 成員初始化列表(member intializer list)

如下所示：

``` cpp
...
public:
	Test(int n) : val(n) {}
...
```

why? 初始化列表會直接在構造中賦值，而正常在構造函數中賦值會導致先呼叫預設的構造函數才賦值。

# 運算符重載

假設有以下類：

``` cpp
// Test.h
#pragma once

class Test {
private:
	int val;
public:
	Test operator+(const Test & t) const;
}
```

則可以如下重載運算符 `+`：

``` cpp
#include "Test.h"

// 取引用避免複製一個新對象，而 const 確保被引用的原對象不會被修改
Test Test::operator+(const Test & t) const
{
	Test sum;
	sum.val = val + t.val;
	return sum;
}
```

# 友元

友元有三類：
- 友元函數
- 友元類
- 友元成員函數

友元函數可以用來**支援運算符重載**。

``` cpp
A = B * 2.75; // A = B.operator*(2.75);
A = 2.75 * B; // Error! 
```

當程序在 case 1 中可以正確運行，但 case 2 中卻會出現錯誤，因為 2.75 顯然不是一個對象。

可以通過友元解決此問題。

首先將聲明放在類定義中：

``` cpp
// Test.h
...
friend Test operator*(double m, const Test & t);
...
```

然後因為此函數不是成員函數，所以不需要 `Test::` 限定符：

``` cpp
Test operator*(double m, const Test & t)
{
	// do something...
}
```

注意，友元函數的項數比成員函數的多一個，因為若只有一個參數友元函數無法得到運算符右側的對象。

# 轉換函數

使得對象可以被轉換成其他類型。

比如：

``` cpp
...
public:
	...
	operator double() const
	{
		return (double) val;
	}
...
```

然後可以這樣調用：

``` cpp
Test A;
A.val = 10;

// output 10
cout << (double) A << '\n';
```

以上方法可以接受顯式 / 隱式 轉換，可以使用 `explicit` 關鍵字使得只能使用顯式轉換：

``` cpp
...
public:
	...
	explicit operator double() const
	{
		return (double) val;
	}
...
```

使得：

``` cpp
double a = (double) A;    // explicit, work! 
double b = A;             // implicit, doesn't work...
```

# 繼承

## 訪問控制

- `public`：所有人都可以訪問。
- `private`：除了自己和友元，誰都不可以訪問。
- `protect`：自己、友元和子類可以訪問。

我們可以如下使用繼承：

``` cpp
class Test_more : public Test 
{
	...
}
```

其中，cpp 有三種繼承方式：

| 寫法             | public 成員    | protected 成員 | private 成員 |
| -------------- | ------------ | ------------ | ---------- |
| `public` 繼承    | 保持不變         | 保持不變         | 不可訪問       |
| `protected` 繼承 | 變成 protected | 保持不變         | 不可訪問       |
| `private` 繼承   | 變成 private   | 變成 private   | 不可訪問       |

通常我們使用 `public` 繼承，因為符合 "is-a" 關係。即子類是父類的一種。

構造順序：父類 -> 子類。

析構順序：子類 -> 父類。

# 