
# Maximum and Minimum Values

## Absolute and Local Extreme Values

讓我們定義一波：

令 $c$ 是 $f$ 定義域 $D$ 上的一個數字，那麼 $f(c)$ 是：
- Absolute(Global) Maximum：$f(c)\geq f(x) \quad \forall x \in D$ 
- Absolute(Global) Minimum： $f(c)\leq f(x)\quad \forall x \in D$ 
- Local Maximum：$f(c)\geq f(x)\quad\text{if x near c}$ 
- Local Minimum： $f(c)\leq f(x)\quad\text{if x near c}$ 

注意，此處的 x near c 表示該值落在**包含 $c$ 的某個開區間中**。也就是說，**local maximum 與 minimum 不可能出現在端點處**。

一個數可以可以同時是局部最大/小值也是全局最大/小值。

ok啊，在了解完以上高中就了解過的東西，我們就可以來學習極值定理(The Extreme Value Theorem)啦！

先給出定義：如果 $f$ 在**閉區間** $[a,b]$ 中**連續**，那麼 $f$ 必定包含一個全局最大值 $f(c)$ 與全局最小值 $f(d)$，且 $c,d \in [a,b]$。

注意，**如果一個函數在 $x=b$ 有漸進線，那麼就不能說在 $[a,b]$ 中連續。因為其在 $x=b$ 根本沒有定義。**

但是，這並不代表一個非連續函數一定沒有極值，某些非連續函數也有極值喔！

## Critical Numbers and the Closed Interval Method

好的，我們來到一個名字聽起來很牛逼其實我感覺一般定理：Fermat's Theorem。

他說：如果 $f$ 上一點 $c$ 是**局部**極值且 $f'(c)$ 存在，那麼 $f'(c)=0$。

proof:
假設在 $c$ 點發生局部最大值，且 $h$ 足夠接近 $0$。我們有 $f(c)\geq f(c+h)\implies f(c+h)-f(c)\leq0$。
等式同除 $h$，如果 $h>0$，那麼有 $\frac{f(c+h)-f(c)}{h}\leq 0$。
對此式取右極限 $\lim_{ h \to 0^{+} } \frac{f(c+h)-f(c)}{h} \leq 0$。
因為 $f'(c)$ 存在，所以 $f'(c)=\lim_{ h \to 0 } \frac{f(c+h)-f(c)}{h}=\lim_{ h \to 0^{+} } \frac{f(c+h)-f(c)}{h}\geq 0$。
如我 $h<0$，我們有 $\frac{f(c+h)-f(c)}{h}\geq 0$。
對此式取左極限 $\lim_{ h \to 0^{-} } \frac{f(c+h)-f(c)}{h} \leq 0$。
同理，我們有 $f'(c)\leq 0$。
總結 $f'(c)\geq 0$ 且 $f'(c)\leq 0$，那麼 $f'(c)=0$。
對於 $c$ 點發生局部最小值，同樣的結論亦成立。請去參考 Exercise 81，如果微積分教學小組沒有要求寫，請也一定寫寫看，謝謝！

需要注意的是，我們無法通過費馬引理找到所有極值。也就是說，費馬引理反過來說不一定正確。

我們引入關鍵點(critical number) 的概念，關鍵點代表了極值**可能**出現的的地方，並不代表關鍵點一定會出現極值。

一個函數 $f$ 的關鍵點是一個在其定義域中的數字 $c$，使得 $f'(c)=0$ 或 $f'(c) \ \not\exists$。

那我們重新整理以上兩個定義：若 $f$ 在 $c$ 有**局部**極值，那麼 $c$ 是 $f$ 的一個關鍵點。

讓我們說明如何使用封閉區間法(The Closed Interval Method) 尋找一個在閉區間 $[a,b]$ 上連續的函數 $f$ 的**全局**最大/小值：
1. 在開區間 $(a,b)$ 上尋找 $f$ 的關鍵點。
2. 尋找端點時 $f$ 的值。
3. 比較在第一與第二步上尋找的值，最大者為全局最大值，反之為全局最小值。