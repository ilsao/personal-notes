
# Maximum and Minimum Values

## Absolute and Local Extreme Values

讓我們定義一波：

令 $c$ 是 $f$ 定義域 $D$ 上的一個數字，那麼 $f(c)$ 是：
- Absolute(Global) Maximum：$f(c)\geq f(x) \quad \forall x \in D$ 
- Absolute(Global) Minimum： $f(c)\leq f(x)\quad \forall x \in D$ 
- Local Maximum：$f(c)\geq f(x)\quad\text{if x near c}$ 
- Local Minimum： $f(c)\leq f(x)\quad\text{if x near c}$ 

注意，此處的 x near c 表示該值落在**包含 $c$ 的某個開區間中**。也就是說，**local maximum 與 minimum 不可能出現在端點處**。

但是，**局部極值可能出現在非連續的地方**喔！

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
令 $f(x)=x^{3}+x-1$，則 $f(0)=-1<0$, $f(1)=1>0$。因為 $f$ 為多項式，所以 $f$ 在 $[0,1]$ 連續。根據**中間值定理**，一定存在一個數 $c\in(0,1)$ 使得 $f(c)=0$，所以存在至少一個實數解。
假設 $f$ 有兩個實數解(**不是設 $f$ 不僅有一個實數解！**)，即 $f(a)=0=f(b)$。
因為 $f$ 為多項式，所以其在 $[a,b]$ 上連續，在 $(a,b)$ 上可導。
根據 Rolle's Theorem，一定存在一個數 $d\in(a,b)$ 使得 $f'(d)=0$。
但是 $f'(x)=2x^{3}+1>0 \neq0$ ，產生矛盾。所以，$f$ 僅有一個實數解。

## The Mean Value Theorem

**The Mean Value Theorem** 說，若：
1. $f$ 在閉區間 $[a,b]$ 上連續。
2. $f$ 在開區間 $(a,b)$ 上可導。

一定存在一個在 $(a,b)$ 中的數 $c$ 使得：

$$
\boxed{f'(c)= \frac{f(b)-f(a)}{b-a}
}
$$

或，

$$
\boxed{f(b)-f(a)=f'(c)(b-a)}
$$

proof:
首先，我們定義**函數 $h(x)$ 為 $f$ 與直線 $AB$ 的差**。(構造輔助函數 $h$ 使得將兩端拉平，構造出 Rolle's Theorem 的使用條件)
![[Pasted image 20251024114606.png]]
那麼，$h(x)=f(x)-f(a)- \frac{f(b)-f(a)}{b-a}(x-a)$。
我們想要對 $h(x)$ 套用 Rolle's Theorem，所以需要確認：
1. $h$ 在 $[a,b]$ 上連續。因為一個連續函數 $f$ + 一個多項式(連續)得到的函數還是連續。
2. $h$ 在 $(a,b)$ 上可導。因為一個可導函數 $f$ + 一個多項式(可導)得到的函數還是可導。
3. $h(a)=0=h(b)$ 。
套用 Rolle's Theorem，得出必定有一落在 $(a,b)$ 中的數 $c$ 使得 $h'(c)=0$。
因為 $h'(x)=f'(x)- \frac{f(b)-f(a)}{b-a}$，又 $h'(c)=0\implies f'(c)= \frac{f(b)-f(a)}{b-a}$。

我們可以使用幾何觀點來理解這個定理。$\frac{f(b)-f(a)}{b-a}$ 代表的是 $AB$ 的斜率 $m_{AB}$，所以此定理說明的是，函數圖形上一定有某點的切線斜率等於 $m_{AB}$。用圖形解釋也很直觀，我們只要做 $AB$ 線段，將它向上或向下平移，直到與圖形相切。該切點就是 $(c,f(c))$。

或者，我們也可以用物理角度解釋均值定理。一輛車的瞬時速度一定會至少一次等於平均速度。

我們也可以使用均值定理，從導數的資訊中取得原函數的資訊，如以下 Example 1。

需要注意，**如果一個函數在未滿足均值定理的使用條件下套用均值定理，得出來的 $c$ 很可能不在 $(a,b)$ 中**。這種情況下與均值定理並不矛盾，因為根本就不可以在此情況下套用均值定理。有些題目會問你為何某函數套用均值定理得到的 $c$ 不在 $(a,b)$ 中？因為該函數在 $[a,b]$ 上不連續或在 $(a,b)$ 上不可導，不符合均值定理套用條件。

藉由均值定理，我們還可以得出以下定理：**如果所有 $x\in(a,b)$ 都使得 $f'(x)=0$，則 $f$ 在 $(a,b)$ 中為常數**。

proof:
令 $x_{1},x_{2}\in(a,b)$，且 $x_{1}<x_{2}$。因為 $f$ 在 $(a,b)$ 可導，所以必在 $(x_{1},x_{2})$ 可導且在 $[x_{1},x_{2}]$ 連續。
套用均值定理，一定可以找到一個數 $c\in(x_{1},x_{2})$ 使得 $f(x_{2})-f(x_{1})=f'(c)(x_{2}-x_{1})$。
因為 $f'(c)=0$，所以 $f(x_{2})-f(x_{1})=0\implies f(x_{2})=f(x_{1})$。
得到，對任意在 $(a,b)$ 上的兩點，$f$ 都有相同值。這說明 $f$ 在 $(a,b)$ 中為常數函數。

注意：$f(x)=\frac{x}{|x|}$ 的定義域為 $D=\{x|x\neq 0\}$，且對任意 $x\in D$ 我們有 $f'(x)=0$，但 $f$ 卻不是常數函數。這與上述定理並不矛盾，因為 $D$ 顯然不是一個區間。

我們還可以通過均值定理得到以下定理：**如果 $f'(x)=g'(x)$ 對任意 $x\in(a,b)$ 皆成立，則在 $(a,b)$ 上 $f-g$ 為常數函數。即，$f(x)=g(x)+c$，其中 $c$ 為常數。**

proof:
令 $F(x)=f(x)-g(x)\implies F'(x)=f'(x)-g'(x)=0$，則根據上一個定理，$F(x)=f(x)-g(x)=c$，其中 $c$ 為一個常數。

### Example

1. Suppose $f(0)=-3$ and $f'(x)\leq5$ for all values of $x$. How large can $f(2)$ possibly be?

Sol:
因為函數處處可導，所以處處連續。
在閉區間 $[0,2]$ 套用均值定理。說明，一定存在一個數 $c\in(0,2)$ 使得：
$f(2)-f(0)=f'(c)(2-0)\implies f(2)=f(0)+2f'(c)\leq7$ 

2. Prove the identity $\tan^{-1}x+\cot^{-1}x=\frac{\pi}{2}$. 

Sol
令 $f(x)=\tan^{-1}x+\cot^{-1}x$，則 $f'(x)= \frac{1}{1+x^{2}}-\frac{1}{1+x^{2}}=0$。
因為對任意 $x$ 來說 $f'(c)=0$ 都成立，所以 $f(x)$ 是一個常數。
想找到該常數的值很簡單，隨便代一個數字進去就好。
代入 $x=1$，$f(1)=\frac{\pi}{4}+\frac{\pi}{4}=\frac{\pi}{2}$。

# What Derivatives Tell Us about the Shape of a Graph

## What Does $f'$ Say about $f$ ?

根據 $f'$ 的值，我們可以得出以下結論：
- $f'(x)>0$ on an interval, then $f$ is decreasing on that interval. 
- $f'(x)<0$ on an interval, then $f$ is decreasing on that interval. 

以上結論稱為 Increasing/Decreasing Test (I/D Test)，使用均值定理可證。

proof:
令 $x_{1},x_{2}$ 為區間上的兩點，且 $x_{1}<x_{2}$。
假設 $f'(x)>0$，我們想證明 $f(x_{1})<f(x_{2})$。
因為 $f$ 在區間中可導且連續，套用均值定理。可以找到一個數 $c$ 在區間中且使得：
$f(x_{2})-f(x_{1})=f'(c)(x_{2}-x_{1})$ 
因為 $f'(c)>0$ 且 $x_{2}-x_{1}>0$，所以 $f(x_{2})-f(x_{1})>0\implies f(x_{1})<f(x_{2})$ 
證畢。
$f'(x)<0$ 的情況同理可證。

## The First Derivative Test

The First Derivative Test 可以用來檢測該關鍵點是否為局部極值。

若 $x$ 為關鍵點且 $f$ 為連續函數：
- 若(從左側到右側看) $f'$ 從 $f'(x)>0$ 轉為 $f'(x)<0$ 則該關鍵點為局部最大值。
- 若 $f'$ 從 $f'(x)<0$ 轉為 $f'(x)>0$ 則該關鍵點為局部最小值。

## What Does $f''$ Say about $f$ ?

一次微分只能告訴我們函數圖形在區間中是上升還是下降，卻無法告訴我們在該區間的凹向。

我們先來定義圖形的凹向：
- **凹口向上(concave upward)**：$f$ 的圖形始終在切線的上方。
- **凹口向下(concave downward)**：$f$ 的圖形始終在切線的下方。

我們可以使用二次微分來對應函數圖形的凹向，稱為 Concavity Test：
- 若 $f''(x)>0$ 則在區間中函數凹口向上。
- 若 $f''(x)<0$ 則在區間中函數凹口向下。

反曲點：該處 $f''(x)=0$ 且變號。

我們可以使用反曲點處的二次微分變號情況來判斷切線斜率的極值情況：
- $f''(x)$ 從正轉負：切線斜率最大值發生於此。
- $f''(x)$ 從負轉正：切線斜率最小值發生於此。

## The Second Derivative Test

若 $f''$ 在 $c$ 附近連續，可以使用 Second Derivative Test 來取得 $f$ 的資訊：
- 若 $f'(c)=0$ 且 $f''(c)>0$，$c$ 為局部最小值。
- 若 $f'(c)=0$ 且 $f''(c)<0$，$c$ 為局部最大值。

當 Second Derivative Test 失效時，我們需要回歸 First Derivative Test 來判斷該點性質。

# Summary of Curve Sketching

## Guidelines for Sketching a Curve

A. Domain and **Range**

B. Intercepts

當 $x=0$ 時，求 $y$ 值。如果 $y=0$ 時求 $x$ 略難，可略過不求。

C. Symmetry

- 奇函數：$f(-x)=-f(x)$ 對稱原點。
- 偶函數：$f(-x)=f(x)$ 對稱 $y$ 軸。
- 週期函數：$f(x+p)=f(x)$ 且 $p$ 為一個正的常數。

D. Asymptotes

- Horizontal Asymptotes
- Vertical Asymptotes
- Slant Asymptotes: $\lim_{ x \to \infty }[f(x)-(mx+b)]=0$ => (i) $\lim_{ x \to \infty } \frac{f(x)}{x}=m$ (ii) $\lim_{ x \to \infty }[f(x)-mx]=b$ 

E. Interval of Increase or Decrease

利用 critical point，觀察關鍵點左右 $f'$ 正負號。

F. Local Maximum or Minimum Values

G. Concavity and Points of Inflection

在 $f''(x)=0$ 左右測試 $f''$ 的正負，如果變號則為反曲點。

H. Sketch the Curve

# Tips

- 局部極值可能發生在非連續處，但不可能發生在端點數。
- 尋找全局極值時，除了比對關鍵點外，還需要確保該點在給定的區間內。
- $f^{2}$ 在 $(a,b)$ 上可導，並**不代表** $f$ 在 $(a,b)$ 上可導。因為平方可能會抹平在零處的尖角或奇異。例如 $f(x)=|x|$ 在 $x=0$ 不可導，但 $f^{2}(x)=x^{2}$ 可導。
- 就算 $f'(x)$ 沒變號且 $f''(x)=0$ 也不能代表該點是反曲點。反曲點必須要 $f''(x)$ 在該點變號。
- 一個 critical point 可能不是極值也不是反曲點。例如：$x^{2}\sin\left( \frac{1}{x} \right)$ (非連續函數)

# 重要例題

1. Find the critical numbers of the function $F(x)=x^{4/5}(x-4)^{2}$. 

Sol:
這題難在化簡，放上來讓你練練手浪費浪費時間。
$F'(x)=\frac{4}{5}x^{-1/5}(x-4)^{2}+2x^{4/5}(x-4)\implies F'(x)= \frac{(x-4)(14x-16)}{5x^{1/5}}$ 
$F'(x)=0\implies x=4\text{ or } \frac{8}{7}$ . $F'(0)$ 不存在。
所以，關鍵點為：$0,4, \frac{8}{7}$。

2. Show that $2x+\cos x$ has exactly one real solution.

Sol:
這種題目我們分三步寫：
1. 使用中間值定理說明函數最少有一個實數解。
2. 假設函數有兩個不同的實數解，根據均值定理存在一數 $c\in(a,b)$ 使得 $f'(c)=0$。
3. 將函數微分，得到 $f'(x)\neq 0$，與均值定理得到的結果矛盾。所以函數只有一個實數解。

令 $f(x)=2x+\cos x$，$f\left( \frac{\pi}{2} \right)=\pi>0$，$f\left( -\frac{\pi}{2} \right)=-\pi<0$。
因為 $f(x)$ 在 $\left[ -\frac{\pi}{2}, \frac{\pi}{2} \right]$ 連續，根據中間值定理一定存在一個數 $c\in\left( -\frac{\pi}{2}, \frac{\pi}{2} \right)$ 使得 $f(c)=0$。
所以 $f$ 至少有一個實數解。
若 $f$ 有兩個不同的實數解 $a,b$ 且 $b>a$。
因為 $f(x)$ 在 $\left[ -\frac{\pi}{2}, \frac{\pi}{2} \right]$ 連續且在 $\left( -\frac{\pi}{2}, \frac{\pi}{2} \right)$ 可導，根據均值定理我們有 $d\in\left( -\frac{\pi}{2}, \frac{\pi}{2} \right)$ 使得 $f'(d)=0$。
但是 $f'(d)=2-\sin d>0$，與均值定理的結論矛盾，所以 $f$ 只有一個實數解。

3. Show that the equation $x^{3}-15x+c=0$ has at most one solution in the interval $[-2,2]$. 

Sol:
這題與上題有微許的差異，只需要套用 Rolle's Theorem 即可。
令 $f(x)=x^{3}-15x+c$，$x\in[-2,2]$。
若 $f$ 有兩個相異的實數解 $a,b\in[-2,2]$ 且 $b>a$，則 $f(a)=0=f(b)$。
因為多項式 $f$ 在 $[a,b]$ 連續且在 $(a,b)$ 可導，根據 Rolle's Theorem，$\exists d\in(a,b)$ 使得 $f'(d)=0$。
因為 $f'(x)=3x^{2}-15$ 且 $-2<d<2$，所以 $f'(d)<-3\neq 0$。
這與 $f'(d)=0$ 矛盾，所以 $f$ 在 $[-2,2]$ 上最多只能有一組實數解。

4. If $f'(x)=c$ ($c$ a constant) for all $x$, use Corollary 7 to show that $f(x)=cx+d$ ($d$ a constant).

Sol:
令 $g(x)=cx$，則 $g'(x)=c$。
$f'(x)=g'(x)\quad \forall x\in \mathbb{R}$。
根據 Corollary 7，$f(x)-g(x)=d$，($d$ a constant)。
$\implies f(x)=cx+d$ 

# 大會考

1. Let $g(x)=xe^{x}$. Then the absolute maximum value of $g(\sin x+2\cos x)$, $x\in \mathbb{R}$, is?

Sol:
這題需要謹慎思考，不可直接將 $x$ 代入 $\sin x+2\cos x$，會使方程複雜。
因為我們只需要尋找最大值，並不關心 $\sin x+2\cos x$ 的 $x$ 該如何取，所以我們只需要取 $\sin x+2\cos x$ 的範圍即可。
$\sqrt{ 1^{2}+2^{2} }=\sqrt{ 5 }\implies \sin x+2\cos x\in[-\sqrt{ 5 },\sqrt{ 5 }]$ 
$g'(x)=e^{x}+xe^{x}=e^{x}(x+1)$ 
所以，在 $x< -1$ 時，$g$ 嚴格遞減。在 $x>-1$ 時，$g$ 嚴格遞增。而 $x=-1$ 為關鍵點。
顯然，全局最大值發生在 $x=\sqrt{ 5 }\implies g(\sqrt{ 5 })=\sqrt{ 5 }e^{\sqrt{ 5 }}$。

2. Let $f'(x)\geq 3$ for all $x\in[1,4]$. Suppose $f(1)=1, f(4)=10$. Then $f(2)=$ ?

Sol:
我們對 $[1,2]$ 與 $[2,4]$ 各使用一次均值定理，就可以夾出答案。
因為 $f$ 在 $[1,4]$ 連續且 在 $(1,4)$ 可導，所以 $f$ 在 $[1,2]$ 與 $[2,4]$ 連續，在 $(1,2)$ 與 $(2,4)$ 可導。
根據 MVT，我們有 $d\in(1,2)$ 與 $e\in(2,4)$ 使得：
$f(2)-f(1)=f'(d)\implies f(2)=f'(d)+1\geq 4$ 
$f(4)-f(2)=2f'(e)\implies f(2)=10-2f'(e)\leq 4$ 
所以，$f(2)=4$。