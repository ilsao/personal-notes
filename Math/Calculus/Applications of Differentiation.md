
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

ok啊，在了解完以上高中就了解過的東西，我們就可以來學習**極值定理**(The Extreme Value Theorem)啦！

先給出定義：如果 $f$ 在**閉區間** $[a,b]$ 中**連續**，那麼 $f$ 必定包含一個**全局**最大值 $f(c)$ 與**全局**最小值 $f(d)$，且 $c,d \in [a,b]$。

注意，**如果一個函數在 $x=b$ 有漸進線，那麼就不能說在 $[a,b]$ 中連續。因為其在 $x=b$ 根本沒有定義。**

但是，這並不代表一個非連續函數一定沒有極值，某些非連續函數也有極值喔！

## Critical Numbers and the Closed Interval Method

好的，我們來到一個名字聽起來很牛逼其實我感覺一般定理：Fermat's Theorem。

**Fermat's Theorem** 說：如果 $f$ 上一點 $c$ 是**局部**極值且 $f'(c)$ 存在，那麼 $f'(c)=0$。(注意此處條件要求 $c$ 是局部極值，所以 $c$ 不可能處于端點。這點需要與極值定理做區分)

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

# The Mean Value Theorem

## Rolle's Theorem

**Rolle's Theorem** 說，若：
1. $f$ 在閉區間 $[a,b]$ 連續。
2. $f$ 在開區間 $(a,b)$ 可導。
3. $f(a)=f(b)$。

則在開區間 $(a,b)$ 上存在一個數 $c$ 使得：$f'(c)=0$。

proof:
情況一：$f(x)=k$，$k$ 為常數。
可以得到 $f'(x)=0$，所以對於所有在 $(a,b)$ 上的數字 $c$ ，$f'(c)=0$ 必成立。
情況二：$f(x)>f(a)$，$x$ 是某個在 $(a,b)$ 上的數字。
那麼根據極值定理，$f$ 在 $[a,b]$ 上必有一個最大值。且因為 $f(a)=f(b)$，所以此最大值必定位於 $(c,f(c))$ 且 $c\in(a,b)$。而且，$(c,f(c))$ 同時也是局部最大值。
因為 $f$ 在 $c$ 可導，所以根據 Fermat's Theorem 我們有 $f'(c)=0$。
情況三：$f(x)<f(a)$，$x$ 是某個在 $(a,b)$ 上的數字。
根據極值定理，$f$ 在 $[a,b]$ 上必有一個最小值。因為 $f(a)=f(b)$，此最小值必定位於 $c,f(c)$ 且 $c\in(a,b)$。而且，此最小值必定同時也是局部最小值。
由于 $f$ 在 $c$ 可導，根據 Fermat's Theorem 我們有 $f'(c)=0$。

### Example

1. Prove that the equation $x^{3}+x-1=0$ has exactly one real solution. 

Sol:
此題我們使用中間值定理與 Rolle's Theorem 反證法來證明。
令 $f(x)=x^{3}+x-1$，則 $f(0)=-1<0$, $f(1)=1>0$。因為 $f$ 為多項式，所以 $f$ 在 $[0,1]$ 連續。根據中間值定理，一定存在一個數 $c\in(0,1)$ 使得 $f(c)=0$，所以存在至少一個實數解。
假設 $f$ 有兩個實數解(**不是設 $f$ 不僅有一個實數解！**)，即 $f(a)=0=f(b)$。
因為 $f$ 為多項式，所以其在 $[a,b]$ 上連續，在 $(a,b)$ 上可導。
根據 Rolle's Theorem，一定存在一個數 $d\in(a,b)$ 使得 $f'(d)=0$。
但是 $f'(x)=2x^{3}+1>0 \neq0$ ，產生矛盾。所以，$f$ 僅有一個實數解。

## The Mean Value Theorem

# Summary of Curve Sketching

## Guidelines for Sketching a Curve

A. Domain and **Range**

B. Intercepts

C. Symmetry

D. Asymptotes

Slant Asymptotes: $\lim_{ x \to \infty }[f(x)-(mx+b)]=0$ => (i) $\lim_{ x \to \infty } \frac{f(x)}{x}=m$ (ii) $\lim_{ x \to \infty }[f(x)-mx]=b$ 

E. Interval of Increase or Decrease

F. Local Maximum or Minimum Values

G. Concavity and Points of Inflection

H. Sketch the Curve