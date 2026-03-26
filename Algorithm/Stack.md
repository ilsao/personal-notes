# Stack

## Infix and Postfix

Infix: 中序，平時寫表達式的方法。`A + B * C` 

Postfix: 後序 (逆波蘭表達式)，符號在後。`A B C * +` 

將 Infix 轉 Postfix 的規則如下：
- 遇到數字： 直接輸出
- 遇到 `(`：入棧
- 遇到 `)`：持續彈出棧中元素，直到 `st.top() == '('` 
- 遇到運算符：
	- `while (!st.empty())` 取 `st.top()` 
		- 棧頂優先級 `<` 自己：入棧
		- 棧頂優先級 `>=` 自己：一直出棧直到條件不滿足
- 字符串尾：彈空棧

```cpp
class Solution {
public:
    int precedence(char op) {
        if (op == '+' || op == '-') return 1;
        if (op == '*' || op == '/') return 2;
        return 0;
    }

    bool isOperator(char c) {
        return c == '+' || c == '-' || c == '*' || c == '/';
    }

    string toPostfix(string s) {
        string postfix;
        postfix.reserve(s.size());

        stack<char> st;

        for (char c : s) {
            if (c >= '0' && c <= '9') {
                postfix += c;
            }
            else if (c == '(') {
                st.push(c);
            }
            else if (c == ')') {
                while (!st.empty() && st.top() != '(') {
                    postfix += st.top();
                    st.pop();
                }
                if (!st.empty()) st.pop();
            }
            else if (isOperator(c)) {
                while (!st.empty() && st.top() != '(' &&
                       precedence(st.top()) >= precedence(c)) {
                    postfix += st.top();
                    st.pop();
                }
                st.push(c);
            }
        }

        while (!st.empty()) {
            postfix += st.top();
            st.pop();
        }

        return postfix;
    }
};
```

## Problems

- 括號匹配
- 表達式解析
- 延後計算 (中間結果暫存，遇到某個條件才結算)
- 回朔

# Monotonic Stack

棧中僅存放遞增或遞減元素。

``` cpp
for (int i = 0; i < n; i++) {
    while (!st.empty() && 破壞單調性事件) {
	    // some operation or calculation
        st.pop();
    }
    // 注意到通常存下標，這樣既可得位置資訊，也可得值資訊。
    st.push(i);
}
```

## Problems

- 尋找 (右邊 / 左邊) 下一個更大 / 更小
- 接雨水
- 最大直方圖面積