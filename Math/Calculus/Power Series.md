# Power Series

power series 形如：

$$
\sum_{n=0}^{\infty}c_{n}x^{n}=c_{0}+c_{1}x+c_{2}x^{2}+\dots
$$

其中 $c_{i}$ 為常數係數，$x$ 為變量。

power series 的和是一個函數：

$$
f(x)=c_{0}+c_{1}x+c_{2}x^{2}
$$

$f$ 的**定義域是所有使級數收斂的 $x$**。注意到 $f$ 跟多項式很像，唯一的區別是 $f$ 有無限多項。

更一般地，級數形如：

$$
\sum_{n=0}^{\infty}c_{n}(x-a)^{n}=c_{0}+c_{1}(x-a)+c_{2}(x-a)^{2}+\dots
$$

稱為 power series in $(x-a)$ 或以 $a$ 為中心的 power series 或關於 $a$ 的 power series。

> [!note]
> 注意到當 $x=a$ 時對 $n\geq1$ 的項都為零，所以此時 power series 必收斂。

> [!note]
> 注意，power series 形如：$\sum_{n=0}^{\infty}c_{n}(x-a)^{n}$。
> 所以，與 $n$ 無關的常數應該提到 $\sum$ 前面

我們通常對 power series 使用 Ratio / Root Test 來找到使其收斂的 $x$。

> [!note]
> 注意到 $\lim_{ n \to \infty } | \frac{a_{n+1}}{a_{n}}|=L<1$ 時發散，但是 $L=1$ 時必須特別判斷，Ratio Test 無法得知收斂性。

## Interval of Convergence

有個定理：

對於 power series $\sum_{n=0}^{\infty}c_{n}(x-a)^{n}$，有三種可能：
1. 僅在 $x=a$ 時收斂
2. 對所有 $x$ 都收斂
3. 存在一個正數 $R$ 使得若 $|x-a|<R$ 則收斂，若 $|x-a|>R$ 則發散 (因為 $|x-a|>R$ 發散，所以不可能有 $x$ 在發散半徑外，但仍收斂的可能性)

我們稱 $R$ 為 power series 的**收斂半徑(radius of convergence)**。在第一種情況時 $R=0$，第二種情況時 $R=\infty$。

而 power series 的**收斂區間(interval of convergence)** 則是由所有可使級數收斂的 $x$ 組成的區間。第一種情況下收斂區間為單點 $a$，第二種情況下是 $(-\infty,\infty)$，第三種則是 $(a-R,a+R)$。注意到，當 $x$ 為端點時 (即 $x=a\pm R$)，級數可能收斂也可能發散。

> [!error]
> 看看定理 4 的證明，可能會考。

> [!warning] 注意
> 做 Ratio Test 時，只能考慮 $a_{n}\neq 0$ 的情況，所以必須額外**假設**並考慮 $x=a$ 時的情況。

> [!note]
> 若使用 Ratio Test 解出來 $\lim_{ n \to \infty }| \frac{a_{n+1}}{a_{n}}|=0<1$，代表 $\forall x$ 都使級數收斂 $\implies R=\infty$ 

# Representations of Functions as Power Series

## Representations of Functions using Geometric Series

我們從無窮級數開始。這次我們不將無窮級數的和視為 $\frac{1}{1-x}$，而將 $\frac{1}{1-x}$ 視為展開的無窮級數：

$$
\frac{1}{1-x}=1+x+x^{2}+x^{3}+\dots=\sum_{n=0}^{\infty} x^{n}\quad|x|<1
$$

我們將其稱為：power series representation of $\frac{1}{1-x}$ on the interval $(-1,1)$ centered at $0$。

## Differentiation and Integration of Power Series

根據下列定理，我們可以對 power series term-by-term 微分或積分。

若 power series $\sum c_{n}(x-a)^{n}$ 有收斂半徑 $R>0$，則如下定義的函數 $f$：

$$
f(x)=c_{0}+c_{1}(x-a)+c_{2}(x-a)^{2}+\dots=\sum_{n=0}^{\infty} c_{n}(x-a)^{n}
$$

在區間 $(a-R,a+R)$ 可導且連續。

$$
\begin{align}
 & (i)\ f'(x)=c_{1}+2c_{2}(x-a)+3c_{3}(x-a)^{2}+\dots=\sum_{n=1}^{\infty} nc_{n}(x-a)^{n-1} \\
 & (ii)\ \int f(x) \ dx=C+c_{0}(x-a)+c_{1} \frac{(x-a)^{2}}{2}+c_{2} \frac{(x-a)^{3}}{3}+\dots=C\sum_{n=0}^{\infty} c_{n} \frac{(x-a)^{n+1}}{n+1}
\end{align}
$$

並且，$f'$ 與 $\int f(x)\ dx$ 的收斂半徑與原函數相同為 $R$。

> [!warning] 注意
> 這邊積分常數不總是 0，記得檢查呀！

> [!error] 小心
> 雖然上述定理說，積分或微分後的收斂半徑與原函數相同。
> 但，這不代表收斂**區間**與函數相同。注意端點收斂情況。

> [!warning] 注意
> 若 power series 不是由 $\frac{1}{1-r}$ 轉換而來，不要亂套 $|r|<1$。
> 用 Ratio Test 較為保險。

> [!warning] 注意
> 雖然 power series 定義出的函數一定無限可微，但一個無限可微的函數，不一定可表達為 power series。

給你補個範例，防止忘記怎麼算：

![[Pasted image 20260318230511.png|661]]

> [!note]
> $\ln(1+z)=-\ln[(1+z)^{-1}]=-\ln\left( \frac{1}{1+z} \right)=-\ln\left( 1+ \frac{1}{1+z}-1 \right)=-\ln\left( 1  -\frac{z}{1+z} \right)$  就可以計算任意 $z$ 的值。

## Functions Defined by Power Series

有些特別重要的函數無法被基本函數表達，必須由 power series 表達。

例如：Bessel function。

$$
J_{0}(x)=\sum_{n=0}^{\infty} \frac{(-1)^{n}x^{2n}}{2^{2n}(n!)^{2}}
$$

> [!note] Index Shift
> $\sum_{n=1}^{\infty}a_{n}=\sum_{n=0}^{\infty}a_{n+1}$ 
> 如果形如 $\sum_{n=1}^{\infty} x^{2n-1}=\sum_{n=0}^{\infty}x^{2n+1}$，考慮將 $n=1$ 時代入 $2n-1=1$，並用 $n=0$ 代入 index shift 後的式子應該與前者相同：$2n+k=1\implies k=1$。

# Taylor and Maclaurin Series

## Definition of Taylor Series and Maclaurin Series

若 $f$ 在 $a$ 處有 power series representation，即：

$$
f(x)=\sum_{n=0}^{\infty} c_{n}(x-a)^{n}
$$

則其係數如下計算：

$$
c_{n}= \frac{f^{(n)}(a)}{n!}
$$

即原函數可如下展開：

$$
\begin{align}
f(x) & =\sum_{n=0}^{\infty}  \frac{f^{(n)}(a)}{n!}(x-a)^{n} \\
 & =f(a)+\frac{f'(a)}{1!}(x-a)+ \frac{f''(a)}{2!}(x-a)^{2}+ \frac{f'''(a)}{3!}(x-a)^{3}+\dots
\end{align}
$$

上式稱為 Taylor Series of the function $f$ at $a$ (or about $a$ or centered at $a$)。

而 Maclaurin Series 則是 Taylor Series 的特例，即 $x=0$ 時的展開：

$$
f(x)=\sum_{n=0}^{\infty} \frac{f^{(n)}(0)}{n!}x^{n}= f(0)+\frac{f'(0)}{1!}x+\frac{f''(0)}{2!}x^{2}+\frac{f'''(0)}{3!}x^{3}+\dots
$$

> [!note]
> 我們可以對任意函數執行泰勒展開，但這些泰勒展開不一定與原函數相等。
> 你得判斷泰勒級數的收斂性與是否收斂到與原函數相等。

> [!note]
> 無論某函數的 power series 是如何找到的，power series 都是唯一的。(對相同 $a$ 為中心展開的係數會相同)

## When Is a Function Represented by Its Taylor Series?

我們定義殘差 (Remainder)：

$$
R_{n}(x)=f(x)-T_{n}(x)
$$

其中，$T_{n}(x)$ 為 $f(x)$ 泰勒展開的 partial sum。

若 $R$ 為收斂半徑，則：

$$
\lim_{ n \to \infty } R_{n}(x)=0\quad\text{for }|x-a|<R
$$

代表 $f$ 與其泰勒展開在區間 $|x-a|<R$ 中相等。

因為 $f(x)=T_{n}(x)+R_{n}(x)$，若 $\lim_{ n \to \infty }R_{n}(x)=0$ 則：

$f(x)=\lim_{ n \to \infty }f(x)=\lim_{ n \to \infty }[T_{n}(x)+R_{n}(x)]=\lim_{ n \to \infty }T_{n}(x)$ 

為了檢測 $\lim_{ n \to \infty }R_{n}(x)$，我們有 Taylor Inequality：

若對 $|x-a|\leq d$ 有 $|f^{(n+1)}(x)|\leq M$，則：

$$
|R_{n}(x)|\leq \frac{M}{(n+1)!}|x-a|^{n+1}\quad\text{for }|x-a|\leq d
$$

proof:
此處只證 $n=1$ 的情況，作為歸納法的第一步。
假設對 $|x-a|\leq d$ ($a-d\leq x\leq a+d$) 有 $|f''(x)|\leq M$。
先考慮 $f''(x)\leq M$：
則：$\int_{a}^{x}f''(t) \ dt\leq \int_{a}^{x}M\ dt\implies f'(x)-f'(a)\leq M(x-a)$ 
移項：$f'(x)\leq f'(a)+M(x-a)$ 
則有：$\int_{a}^{x}f'(t)\ dt\leq \int_{a}^{x}[f'(a)+M(t-a)]\ dt$ 
$\implies f(x)-f(a)\leq f'(a)(x-a)+M\frac{(x-a)^{2}}{2}\implies f(x)-f(a)-f'(a)(x-a)\leq M \frac{(x-a)^{2}}{2}$ 
注意到 $R_{1}(x)=f(x)-T_{1}(x)=f(x)-f(a)-f'(a)(x-a)$，所以有 $R_{1}(x)\leq M \frac{(x-a)^{2}}{2}$。
考慮 $f''(x)\geq-M$，易得：$R_{1}(x)\geq-M \frac{(x-a)^{2}}{2}$。
所以：$|R_{1}(x)|\leq \frac{M}{2}(x-a)^{2}$。
儘管我們假設 $x>a$，但當 $x<a$ 易得相同結果。
接下來只要繼續完成歸納法即可。

下列結論幫你解題：

$$
\lim_{ n \to \infty } \frac{x^{n}}{n!}=0
$$

## Taylor Series of Important Functions

常用函數的泰勒展開如圖：

![[Pasted image 20260320173647.png|985]]

注意，我們定義 binomial coefficient 為：

$$
\binom{k}{n}= \frac{k(k-1)(k-2)\dots(k-n+1)}{n!}
$$

所以：

$$
(1+x)^{k}=\sum_{n=0}^{\infty} \frac{k(k-1)(k-2)\dots(k-n+1)}{n!}x^{n}
$$

> [!warning] 注意
> 當 $n=0$ 時，定義 $\binom{k}{0}=1$。

> [!error] 小心
> $(1+x)^{k}=\sum_{n=0}^{\infty} \frac{k(k-1)(k-2)\dots(k-n+1)}{n!}x^{n}$，$n!$ 很容易忘記加。

對上式來說，$|x|<1$ 時總是收斂。

端點的收斂性取決於 $k$：
- $k\geq0$：$[-1,1]$ 
- $-1<k\leq 0$：$(-1,1]$ 
- $k\leq -1$：$(-1,1)$ 

對於 $k\in \mathbb{N}$，泰勒展開退化為二項式定理。

> [!note]
> 對於 Maclaurin Series，$f^{(n)}(0)=c_{n}\times n!$。
> 但是注意，$c_{n}$ 不等於直接把 $n$ 代入 Maclaurin Series，而是 $x^{n}$ 的係數！

## Multiplication and Division of Power Series

我們可以對 power series 進行乘法與除法。

# Exercise

![[Pasted image 20260316202212.png|1004]]
![[Pasted image 20260316212331.png|542]]

Sol:
這題倒在了處理 $x=a\pm R$ 的判斷上。
由 Ratio Test 易得 $R=2$，我們得判斷 $x=\pm2$ 時的收斂性。
注意力驚人的做題家，注意到：$|a_{n}|= \frac{n!2^{n}}{1\cdot 3\cdot 5\cdot\dots \cdot(2n-1)}= \frac{(1\cdot 2\cdot 3\cdot \dots \cdot n)2^{n}}{1\cdot 3\cdot 5\cdot \dots \cdot (2n-1)}= \frac{2\cdot 4 \cdot 6\cdot \dots \cdot 2n}{1 \cdot 3 \cdot 5 \cdot \dots \cdot (2n-1)}>1$。
所以，當 $x=\pm 2$ 時級數發散 By test for divergence。
於是收斂區間為 $(-2,2)$。

![[Pasted image 20260316214529.png]]

Sol:
感慨下，這題太妙了。
主要的思路是，先找到一個滿足閉合關係的最基本級數，然後再對它做偏移。
想使得區間被滿足，取中點 $m= \frac{p+q}{2}$，收斂半徑 $r= \frac{q-p}{2}$。
(a)
滿足左右端點都是閉區間 $(-1,1)$ 的最基本級數是：$\sum x^{n}$。
偏移到中點：$\sum(x-m)^{n}$。
使收斂半徑為 $r$：$\sum\left( \frac{x-m}{r} \right)^{n}$。
(b)
注意到 $\sum \frac{x^{n}}{n}$ 收斂區間為 $[-1,1)$。
想令左右端點閉合關係調轉：$\sum(-1)^{n} (\frac{x^{n}}{n})$。
於是答案為 $\sum(-1)^{n}\left( \frac{1}{n} \right)\left( \frac{x-m}{r} \right)^{n}$。
(c)
與上小題類似，但不乘 $(-1)^{n}$：$\sum \frac{1}{n}\left( \frac{x-m}r{} \right)^{n}$。
(d)
注意到 $\sum \frac{x^{n}}{n^{2}}$ 收斂區間為 $[-1,1]$。
於是答案為：$\sum \frac{1}{n^{2}} (\frac{x-m}{r})^{n}$。

![[Pasted image 20260317223325.png|989]]
![[Pasted image 20260317223357.png|294]]
![[Pasted image 20260317223421.png|344]]

Sol:
11.
$f(x)= \frac{x-1}{x+2}= \frac{(x+2)-3}{x+2}=1- \frac{3}{x+2}=1-\frac{3}{2}\cdot \frac{1}{1+\frac{x}{2}}=1- \frac{3}{2}\sum_{n=0}^{\infty}\left( -\frac{x^{}}{2} \right)^{n}＝1-\sum_{n=0}^{\infty} \frac{3(-1)^{n}}{2^{n+1}}x^{n}$ 
無窮級數 $\sum_{n=0}^{\infty}\left( -\frac{x}{2} \right)^{n}$ 在 $|-\frac{x}{2}|< 1$ 時收斂 $\implies|x|<2\implies R=2\implies$ 收斂區間為 $(-2,2)$。
12.
不要害怕提出 $x$，硬提 $\frac{x+a}{a^{2}}$ 就好。
$f(x)= \frac{x+a}{x^{2}+a^{2}}=\frac{x+a}{a^{2}}\cdot \frac{1}{1-\left( -\frac{x^{2}}{a^{2}} \right)}= \frac{x+a}{a^{2}}\sum_{n=0}^{\infty}\left( -\frac{x^{2}}{a^{2}} \right)^{n}= \frac{x+a}{a^{2}}\sum_{n=0}^{\infty}(-1)^{n}\left( \frac{x}{a} \right)^{2n}$ 
$=\left( \frac{x}{a^{2}}+\frac{1}{a} \right)\sum_{n=0}^{\infty}(-1)^{n}\left( \frac{x}{a} \right)^{2n}=\sum_{n=0}^{\infty} \frac{(-1)^{n}x^{2n+1}}{a^{2n+2}}+\sum_{n=0}^{\infty} \frac{(-1)^{n}x^{2n}}{a^{2n}+1}$ 
收斂條件 $|-\frac{x^{2}}{a^{2}}|<1\implies|x|<a\implies R=a\implies$ 收斂區間為 $(-a,a)$。

![[Pasted image 20260318201951.png|771]]

Sol:
(a)
不要做 11.9 的題目做傻了，這明顯不能視為 geometric series 然後 $|r|<1$ 吧！
用 Ratio Test 才是正解！
(b) 略，不會，就賭大會考不考。噢不，大會考考了。但解答就寫了幾項，然後前幾項都符合就覺得符合...
(c)
$J_{0}= \sum_{n=0}^{\infty} \frac{(-1)^{n}x^{2n}}{2^{2n}(n!)^{2}}$ 
$J_{0}'=\sum_{n=0}^{\infty} \frac{(-1)^{n}(2n)x^{2n-1}}{2^{2n}(n!)^{2}}$ 注意到當 $n=0$ 時，該項為零。
$=\sum_{n=1}^{\infty} \frac{(-1)^{n}x^{2n-1}}{2^{2n-1}n!(n-1)!}$         注意到若以 $n=0$ 化簡，會出現 $(-1)!$ 這種為定義行為
$=-\sum_{n=0}^{\infty} \frac{(-1)^{n}x^{2n+1}}{2^{2n+1}(n+1)!n!}=-J_{1}(x)$ 

![[Pasted image 20260318204240.png|727]]

Sol:
(a)
觀察一下，感覺很像一次微分。嗯，沒錯你說得對。
$\sum_{n=1}^{\infty}nx^{n-1}=\frac{d}{dx}\left( \sum_{n=0}^{\infty} x^{n}\right)=\frac{d}{dx}\left( \frac{1}{1-x} \right)= \frac{1}{(1-x)^{2}}$ 
(b)
(i) 這個簡單，補個 $x$ 就好 $\implies \frac{x}{(1-x)^{2}}$。不教。
(ii) 觀察一波，喔，原來是 $x=\frac{1}{2}$ 帶進去 (i) 就行 $\implies \frac{\frac{1}{2}}{\left( 1-\frac{1}{2} \right)^{2}}=2$ 
(c)
(i)
看到 $n(n-1)$，思考一下。感覺像二次微分。
$\sum_{n=2}^{\infty}n(n-1)x^{n}=x^{2} \frac{d^{2}}{dx^{2}}\left( \sum_{n=0}^{\infty}x^{n} \right)=x^{2} \frac{d^{2}}{dx^{2}}\left( \frac{1}{1-x} \right)=\frac{2x^{2}}{(1-x)^{3}}$ 
(ii) 帶看看得到 $4$ 
(iii) 有點難度。將 $n^{2}=(n^{2}-n)+n$ 帶入，得到 $4+2=6$。

![[Pasted image 20260318213840.png|841]]
Sol:
(a)
這邊英文沒看懂：completing the square 表示配方。
$\int_{0}^{1/2} \frac{1}{\left( x-\frac{1}{2} \right)^{2}+\frac{3}{4}}\ dx=\int_{0}^{1/2} \frac{1}{\left( x-\frac{1}{2} \right)^{2}+\left( \frac{\sqrt{ 3 }}{2} \right)^{2}} \ dx$ 看著有種 $\int \frac{1}{x^{2}+a^{2}}\ dx=\frac{1}{a}\tan^{-1}\left( \frac{x}{a} \right)+C$ 的樣子
令 $u=x-\frac{1}{2}\ du=dx$ 
$\int_{-1/2}^{0} \frac{1}{u^{2}+\left( \frac{\sqrt{ 3 }}{2} \right)^{2}} \ du=\left[ \frac{2}{\sqrt{ 3 }}\tan^{-1}\left( \frac{2u}{\sqrt{ 3 }} \right) \right]^{0}_{-\frac{1}{2}}=-\frac{2}{\sqrt{ 3 }}\cdot \frac{-\pi}{6}=\frac{\pi}{3\sqrt{ 3 }}$ 
(b) 寫到這，很痛苦。於是直接貼上解答，等你心情好再看吧。
![[Pasted image 20260318214744.png|712]]

![[Pasted image 20260320200505.png|1194]]
![[Pasted image 20260320200439.png|386]]

Sol:
注意，第 $n$ 項為 $c_{n}(x-a)^{n}$。就算前面幾項是零，也要算。
$f=\cos x=1$ 
$f'=-\sin x=0$ 
$f''=-\cos x=-1$ 
$f'''=\sin x=0$  
四個一循環。
$\cos x=0+ -\frac{1}{1!}\left( x-\frac{\pi}{2} \right)+0+\frac{1}{3!}\left( x-\frac{\pi}{2} \right)^{3}+\dots=\sum_{n=0}^{\infty} \frac{(-1)^{n+1}}{(2n+1)!}\left( x-\frac{\pi}{2} \right)^{2n+1}$ 

![[Pasted image 20260320204522.png|1127]]
![[Pasted image 20260320204508.png|274]]

Sol:
注意 $\binom{k}{0}=1$ 即可。
$(1-x)^{3/4}=(1+(-x))^{3/4}=\sum_{n=0}^{\infty}\binom{k}{n}(-x)^{n}$ 
$=1-\frac{\frac{3}{4}}{1!}x+\frac{\frac{3}{4}\left( -\frac{1}{4} \right)}{2!}x^{2}- \frac{\frac{3}{4}\left( -\frac{1}{4} \right)\left( -\frac{5}{4} \right)}{3!}x^{3}+\dots$ 
$1-\frac{3}{4}x- \frac{3}{4}\sum_{n=2}^{\infty} \frac{1\times5\times\dots\times(4n-7)}{4^{n-1}n!}x^{n}$ 注意，不是 $(4n-7)!$ 
$=1-\frac{3}{4}-\sum_{n=2}^{\infty} \frac{3(1\times5\times\dots \times(4n-7))}{4^{n}n!}x^{n}$ 

![[Pasted image 20260320205937.png|342]]

Sol:
$\sin^{2}x=\frac{1}{2}(1-\cos2x)$ 
$\cos2x=\sum_{n=0}^{\infty}(-1)^{n} \frac{(2x)^{2n}}{(2n)!}$ 
$\sin^{2}x=\frac{1}{2}\left( 1-\sum_{n=0}^{\infty} (-1)^{n} \frac{2^{2n}x^{2n}}{(2n)!} \right)=\frac{1}{2}\left( 1-1-\sum_{n=1}^{\infty} \frac{(-1)^{n}2^{2n}x^{2n}}{(2n)!} \right)$ 注意此處與 index shift 的區別
$=\sum_{n=1}^{\infty} \frac{(-1)^{n+1}2^{2n-1}x^{2n}}{(2n)!}$ 
$R=\infty$ 

![[Pasted image 20260321211133.png]]

Sol:
$\lim_{ x \to 0} \frac{\sqrt{ 1+x }-1-\frac{1}{2}x}{x^{2}}=\lim_{ x \to 0 } \frac{\left( 1-\frac{1}{2}x-\frac{1}{8}x^{2}+\frac{1}{16}x^{3}+\dots \right)-1-\frac{1}{2}x}{x^{2}}=\lim_{ x \to 0 } \frac{-\frac{1}{8}x^{2}+\frac{1}{16}x^{3}+\dots}{x^{2}}$ 
$=\lim_{ x \to 0 }\left( -\frac{1}{8}+\frac{1}{16}x+\dots \right)=-\frac{1}{8}$ 

![[Pasted image 20260321211947.png|827]]
![[Pasted image 20260321212002.png|290]]

Sol:
感覺右半是 $e^{x^{4}}$，但左邊多了個 $(-1)^{n}$。
沒想到直接合併為 $e^{-x^{4}}$ 就好。

# 大會考

![[Pasted image 20260316223935.png|1240]]

Sol:
這題卡在不知道 $f'$ 應該對誰微分，實際上應該對 $x$ 微分。
注意力驚人的我，注意到對 $f(x)=\sum_{n=1}^{\infty} \frac{x^{n}}{n^{2}}$ 應該包含兩個端點。
$f'(x)=\sum_{n=1}^{\infty} \frac{nx^{n-1}}{n^{2}}=\sum_{n=1}^{\infty} \frac{x^{n-1}}{n}$ 
顯然當 $x=-1$ 時根據 alternating series test 收斂。
而當 $x=1$ 時為調和級數，發散。
$f''(x)=\sum_{n=1}^{\infty} \frac{(n-1)x^{n-2}}{n}$ 
顯然因為 $\lim_{ n \to \infty } \frac{(n-1)x^{n-2}}{n}=x^{n-2}$，在端點時 ($x=\pm 1$) 不為零。
所以兩個端點都發散 by the test for divergence。

![[Pasted image 20260316230314.png|968]]

Sol:
雖然聰明如我，立馬注意到了答案，但是放這怕你忘記。
這裡無論 $\alpha$ 的值，收斂半徑都是 $1$。
這裡要 $x=1$ 發散，$x=-1$ 時收斂，顯然是在考我們：在什麼情況下 $\sum \frac{1}{n^{p}}$ 發散，但 $\sum \frac{(-1)^{n}}{n^{p}}$ 收斂？
簡單，立馬注意到當 $0<p\leq1$ 時會成立。
所以秒選 (B) 好吧。

![[Pasted image 20260316231634.png|1091]]

Sol:
不難，算的時候有點腦子混掉了。
問使得兩級數都一定收斂的最大區間。
二者收斂區間最少包含：
$2-R_{1}<x_{1}<2+R_{1}$ 
$3-R_{2}<x_{2}<3+R_{2}$ 
因為在 $x=6$ 收斂，所以有二者收斂半徑最少有：$R_{1}=4$，$R_{2}=3$。
於是二者收斂區間最少包含：
$-2<x_{1}\leq6$ 
$0<x_{2}\leq 6$ 
取交集得：$0<x\leq6$。
注意，$6$ 有等號。因為在該點收斂呀！

![[Pasted image 20260320001234.png|876]]

Sol:
小小陷阱題，看我拿捏你。
$\tan x=\int \frac{1}{1+x^{2}}\ dx=\sum_{n=0}^{\infty} \frac{(-1)^{n}}{2n+1}x^{2n+1}$ 
$f(x)=\sum_{n=0}^{\infty} \frac{(-1)^{n}}{(2n+1)(2n+2)}x^{2n+2}$ 
注意，這邊是 $a_{8}$，即 $x^{8}$ 的項。不是直接代入 $n=8$！
$2n+2=8\implies n=3$ 
$\implies a_{8}= -\frac{1}{7\times8}=-\frac{1}{56}$ 

![[Pasted image 20260321215042.png|901]]

Sol:
小陷阱一波，這個積分的積分常數 $C\neq 0$。
$f(x)=\cos^{-1}(x)=-\int \frac{1}{\sqrt{ 1-x^{2} }}\ dx=-\int\left( 1+\frac{1}{2}x^{2}+\frac{3}{4}x^{4}+\dots \right)\ dx=-\left( x+\frac{1}{6}x^{3}+\frac{3}{20}x^{5}+\dots \right)+C$ 
因為 $f(0)=\cos^{-1}(0)=\frac{\pi}{2}$，所以前三項非零項為 $\frac{\pi}{2}-x-\frac{1}{6}x^{3}$。

![[Pasted image 20260321221857.png|999]]

Sol:
$2(1-x)^{-3}=2\left( 1+3x+(-3)(-4) \frac{x^{2}}{2!} +(-3)(-4)(-5) -\frac{x^{3}}{3!}+\dots\right)$ 
$=2\left( \sum_{n=0}^{\infty} \frac{(n+2)!}{n!2!}x^{n} \right)=\sum_{n=0}^{\infty}(n+1)(n+2)x^{n}$ 
$\implies a_{n}=(n+1)(n+2)$ 

![[Pasted image 20260321223339.png|1061]]

Sol:
忘記將 $\frac{1}{1-x}$ 展開了。
$f(x)=\left( \sum_{n=0}^{\infty} \frac{x^{2n}}{(2n)!} \right)\left( \sum_{n=0}^{\infty}x^{n} \right)$ 
$=\left( 1-\frac{x^{2}}{2!}+\dots \right)(1+x+x^{2}+x^{3}+\dots)$ 
$=1+x+\frac{x^{2}}{2}+\frac{x^{3}}{2}+\dots$ 

![[Pasted image 20260321224336.png|936]]

Sol:
題目要求 $a_{1}$，即 $k^{2}$ 的係數。
$T(k)=4\int_{0}^{\pi/2}(1-k^{2}\sin^{2}x)^{-1/2}\ dx$ 
$=4\int_{0}^{\pi/2}\left( 1+\frac{1}{2}k^{2}\sin^{2}x +\dots\right)\ dx$ 
因此 $a_{1}=4\cdot \frac{1}{2}\int^{\pi/2}_{0}\sin^{2}x\ dx$ 
$=4\left[ x+\frac{k^{2}}{2}\left( \frac{1}{2}x-\frac{1}{4}\sin2x \right) \right]^{\pi/2}_{0}$ 
$=4\times \frac{1}{2}\times\left( \frac{1}{2} \times \frac{\pi}{2} \right)=\frac{\pi}{2}$ 
補：
$\int \sin^{2}x\ dx=\int\left( \frac{1}{2}(1-\cos2x) \right)\ dx$ 解即可。