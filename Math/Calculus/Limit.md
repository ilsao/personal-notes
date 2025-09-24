# If $p(x)$ is a polynomial, then:

$$
\lim_{ x \to a }p(x) = p(a)
$$

proof: 
Let $p(x)=a_{0} + a_{1}x + a_{2}x^{2}+ \dots +a_{n}x^{n}$ .
Thus, by Limit Laws
$\lim_{ x \to a }p(x)=a_{0}+a_{1}\lim_{ x \to a }x+a_{2}\lim_{ x \to a }x^{2}+\dots +a_{n}\lim_{ x \to a }x_{n}$ 
$= a_{0}+a_{1}a+a_{2}a^{2}+ \dots +a_{n}a^{n}$
$=p(a)$
Thus, for any polynomial $p$, $\lim_{ x \to a }p(x)=p(a)$. 

# Rational Function:

$$
f(x) = \frac{P(x)}{Q(x)},\text{其中}P(x)\text{和}Q(x)皆為多項式，
$$
$$
\text{且}Q(x)\neq 0
$$

# If $r(x)$ is a rational function, then

$$
\lim_{ x \to a } r(x) = r(a)
$$

proof:
Let $r(x) = \frac{p(x)}{q(x)} \text{ and }q(x) \neq 0$.
Thus, $\lim_{ x \to a }r(x)=\lim_{ x \to a }{\frac{p(x)}{q(x)}}$. 
By Limit Laws, we have $\frac{\lim_{ x \to a }p(x)}{\lim_{ x \to a }q(x)}=\frac{p(a)}{q(a)}=r(a)$.
Thus, for any rational function r, $\lim_{ x \to a }r(x)=r(a)$.


# 極限的精確定義

我們稱$f(x)$在$x$趨近於$c$時的極限為$L$，記做：

$$
\lim_{ x \to c } f(x) = L
$$

若$\forall\epsilon > 0 ， \exists \text{相應的}\delta > 0$使得所有的$x$滿足：

$$
0 < |x-c| < \delta \implies 0 < |f(x) - L| < \epsilon
$$

例：

證明：
$$
\lim_{ x \to 1 } (5x-3)=2
$$

解：

設$c=1$，$L=2$，$f(x)=5x-3$，則需要找到符合的 $\delta$ 與 $\epsilon$ 使得：

$$
0<|x-1|<\delta \implies |f(x) - L| < \epsilon
$$

利用$\epsilon$到推$\delta$：

$$
|(5x-3) - 2| = |5x-5| = 5|x-1|
$$

取 $\delta=\frac{\epsilon}{5}$。

若 $0<|x-c|<\delta$，則 $|x-c| < \frac{\epsilon}{5}$。

$$
|5x-5|=5|x-1| < 5 \cdot \frac{\epsilon}{5}=\epsilon
$$

所以，由極限的精確定義 $\lim_{ x \to 1 }f(x)=2$ 。

# 單側極限

定義左極限：

$$
\lim_{ x \to a^{-} } f(x) = L
$$

對於所有 $\epsilon >0$，存在 $\delta > 0$ 使得

$$
\text{If } a-\delta<x<a \text{ then } |f(x) - L| < \epsilon
$$

定義右極限：

$$
\lim_{ x \to a^{+} } f(x) = L
$$

對於所有數字 $\epsilon >0$，存在數字 $\delta > 0$ 使得

$$
\text{If } a<x<a+\delta \text{ then } |f(x) - L| < \epsilon
$$

# 無限極限的精確定義

$$
\lim_{ x \to a } f(x) = \infty
$$

即，對於所有正數 $M$ 存在 $\delta > 0$ 使得

$$
\text{If } 0<|x-a|<\delta \text{, then } f(x) > M
$$

$$
\lim_{ x \to a } f(x) = -\infty
$$

即，對所有負數 $N$ 存在 $\delta > 0$ 使得

$$
\text{If } 0<|x-a|<\delta \text{, then } f(x) < N
$$

例子：
證明 $\lim_{ x \to  0} \frac{1}{x^{2}}=\infty$。

Sol:
令 $M$ 為任意正數，我們需要尋找 $\delta > 0$ 使得
$\text{If }0<|x|<\delta \text{ then } \frac{1}{x^{2}} > M$ 
$\frac{1}{x^{2}}=(|x|)^{-2}$ 
取 $\delta = M^{-1/2}$ 
若 $0<|x|<\delta$ 則 $|x| < M^{-1/2}$ 
$\frac{1}{x^{2}}=|x|^{-2} > (M^{-1/2})^{-2}=M$ (取倒數變號) 
因此，對於所有正數 $M$ 存在 $\delta = \frac{1}{\sqrt{ M }}$ 使得 $0<|x|<\delta \implies \frac{1}{x^{2}} > M$

# 證明 limit law

若

$$
\lim_{ x \to a } f(x)=L,\lim_{ x \to a } g(x)=M
$$

證明：

$$
\lim_{ x \to a } [f(x) + g(x)] = L + M
$$

proof:
根據 $\epsilon - \delta$ 定義，$\forall \epsilon > 0, \exists\delta>0$ 使得
$\text{If }0<|x-a|<\delta \text{, then }|f(x) + g(x) - L - M| < \epsilon$ 
$|f(x) + g(x) - L - M|=|f(x)-L + g(x) - M|$ 
根據**三角不等式** $|x+y| \leq |x| + |y|$，我們可以寫出：$|f(x)-L + g(x) - M| \leq |f(x)-L| + |g(x)-M|$
`~~~~~~~^ key` 
令 $\delta_{1} > 0 \text{, } \delta_{2} > 0$ 且 $0<|x-a|<\delta_{1}$ 使得 $|f(x)-L|<\frac{\epsilon}{2}$，與 $0<|x-a|<\delta_{2}$ 使得 $|g(x)-M|<\frac{\epsilon}{2}$ 
`~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^ key` 
取 $\delta = \text{min}\{\delta_{1}, \delta_{2}\}$ 
因此，對於任何給定的 $\epsilon$，存在$\delta = \text{min}\{\delta_{1}, \delta_{2}\}$ 使得 $0<|x-a|<\delta \implies |f(x) + g(x) - L - M| < \epsilon$

# 連續

$$
\text{A function }f \text{ is continuos at a number }a \text{ if}
$$
$$
\lim_{ x \to a } = f(a) \equiv \lim_{ h \to 0 } f(a+h) = f(a)
$$

若 $f$ 在 $a$ 連續，必須滿足以下三個條件：
- $f(a)$ 有定義，即 $a$ 在 $f$ 的定義域中
- $\lim_{ x \to a }f(x)$ 存在
- $\lim_{ x \to a }f(x) = f(a)$

需要注意的是，若為端點情況下，連續僅需考慮單邊極限。

$$
\text{A function }f \text{ is continuous from the right at a number }a \text{ if }
$$
$$
\lim_{ x \to a^{+} } f(x) = f(a)
$$
$$
\text{and }f \text{ is continuous from the left at a number }a \text{ if}
$$
$$
\lim_{ x \to a^{-} } f(x)=f(a)
$$

當函數 $f$ 在區間中連續，則代表 $f$ 在區間中處處連續。需要確認以下兩點：
- 在一般情況下連續
- 在端點情況下仍連續

若函數 $f, g$ 在 $a$ 點連續，且 $c$ 是一個常數。則以下函數皆在 $a$ 點連續：
- $f+g$
- $f-g$
- $cf$
- $fg$
- $\frac{f}{g}\text{ If } g(a)\neq 0$

proof:
Since $f(x)$ and $g(x)$ are continuous at $a$, we have:
$\lim_{ x \to a }f(x)=f(a)$ and $\lim_{ x \to a }g(x)=g(a)$ 
Therefore
$\lim_{ x \to a }[f(x)+g(x)]=\lim_{ x \to a }f(x)+\lim_{ x \to a }g(x)$
$=f(a)+g(a)$
$=(f+g)(a)$
This shows that $f+g$ is continuous at $a$. 

以上結論可以推導出我們在 2.3 節使用的特性：
- 多項式處處連續
- 有理函數(rational function)處處連續，除了令分母等於零那點。

還有，所有一對一連續函數的反函數也連續。因為反函數由原函數對稱 $y=x$ 得到，不可能因為做對稱而由連續變為不連續。

若 $\lim_{ x \to a }g(x)=b$ ，且$f$ 在 $b$ 點處連續, 那麼 $\lim_{ x \to a }f(g(x))=f(b)$。即：

$$
\lim_{ x \to a }f(g(x))=f(\lim_{ x \to a } g(x))
$$

若 $g$ 在 $a$ 點連續，且 $f$ 在 $g(a)$ 處連續，則 $(f \circ g)(x)=f(g(x))$ 在$a$ 點連續(由以上定理推導得到)。也可以表達為：一個連續函數包裹著一個連續函數還是一個連續函數。

proof:
因為 $\lim_{ x \to a }f(g(x))= f(\lim_{ x \to a }g(x)) = f(g(a))$，所以此函數連續。

# 中值定理

若 $f$ 在區間 $[a,b]$ 連續，$N$ 介於 $f(a), f(b)$ 之間且 $f(a) \neq f(b)$。則存在 $c \in (a,b)$ 使得 $f(c)=N$。

需要注意的是，$c$ 的值可能唯一，也可能有很多組解。

# 水平漸進線

當 $f$ 在區間 $(a, \infty)$ 有定義，則

$$
\lim_{ x \to \infty } f(x)=L
$$

代表只要 $x$ 足夠大， $f(x)$ 可以無限接近 $L$ 。

也可以表示為：

$$
f(x) \to L \text{ as } x\to \infty
$$

此極限的精確定義如下：

$$
\begin{align}
 & \forall \epsilon>0,\exists N>0 \ni \\
 & \text{If } x>N\text{ then } |f(x)-L|<\epsilon
\end{align}
$$

一個在 $x\to \infty$ 時趨近於 $\infty$ 的極限定義如下：

$$
\lim_{ x \to \infty } f(x)=\infty
$$
$$
\text{means that } \forall M>0, \exists N>0 \ni
$$
$$
\text{If } x>N \text{ then }f(x)>M
$$

## 計算趨近於無限的極限

我們需要使用以下結論：
$$
\text{If }r>0 \text{ is a rational number, then}
$$
$$
\lim_{ x \to \infty } \frac{1}{x^{r}}=0
$$
$$
\text{If }r>0 \text{ is a rational number such that }x^{r} \text{ is defined for all }x\text{, then}
$$
$$
\lim_{ x \to -\infty } \frac{1}{x^{r}}=0
$$

至於為何二者的成立條件不同，是因為當 $x\to-\infty$ 時，如果對負數開偶數次方($r$ 為偶數為底的分數)無意義，必須開奇數次方。

我們還需要掌握以下變體：

$$
\lim_{ x \to \infty } f(x)=\lim_{ t \to 0^{+} } f\left( \frac{1}{t} \right)
$$

### 例題

尋找 $f(x)= \frac{\sqrt{ 2x^{2}+1 }}{3x-5}$ 的水平漸進線。

Sol:
首先尋找 $x\to \infty$ 時的水平漸進線：$\lim_{ x \to \infty } \frac{\sqrt{ 2x^{2}+1 }}{3x-5}$。
$\lim_{ x \to \infty } \frac{\sqrt{ 2+\frac{1}{x^{2}} }}{3-\frac{5}{x}}=\frac{\sqrt{ 2 }}{3}$. 
接著尋找 $x\to -\infty$ 時的水平漸進線：$\lim_{ x \to -\infty } \frac{\sqrt{ 2x^{2}+1 }}{3x-5}$
需要注意的是，$\because x<0 \therefore x=-\sqrt{ x^{2} }$. 
$\lim_{ x \to -\infty } \frac{\sqrt{ 2x^{2}+1 }}{3x-5}=\lim_{ x \to -\infty } \frac{\frac{\sqrt{ 2x^{2}+1 }}{-\sqrt{ x^{2} }}}{3-\frac{5}{x}}=\lim_{ x \to -\infty } \frac{-\sqrt{ 2+\frac{1}{x^{2}} }}{3-\frac{5}{x}}=\frac{-\sqrt{ 2 }}{3}$
亦或者令 $h=-x$ 求 $\lim_{ h \to \infty } \frac{\sqrt{ 2h^{2}+1 }}{-3h-5}= \frac{\sqrt{ 2 }}{-3}$ 

求 $\lim_{ x \to 2^{+} }\arctan\left( \frac{1}{x-2} \right)$

Sol:
$\because \lim_{ x \to 2^{+} } \frac{1}{x-2}=\infty \text{( doesn't exist )} \therefore \text{we cannot use the Theorem 8 in section 2.5}$.
However, we can use the definition of arctan that its horizontal asymptote as $x\to \infty$ is $\frac{\pi}{2}$.
Thus, we get the answer $\lim_{ x \to 2^{+} }\arctan\left( \frac{1}{x-2} \right)=\lim_{ t \to \infty }\arctan t=\frac{\pi}{2}$.

求 $\lim_{ x \to \infty }(x^{2}-x)$

Sol:
需要注意，因為 $\infty$ 不是一個數字，並且 $\lim_{ x \to \infty }x=\infty$ 極限未定義，所以不能使用 Limit Law 來解此題。
但是，我們可以將其分解為 $\lim_{ x \to \infty }x(x-1)=\infty$. 

# 小 tip

- 當帶入 $x=a$ 時函數分母等於 0，此時分為兩種狀況：
	- 分子與分母都有 $(x-a)$ 項，可以消掉 => 圖形在該點有空洞，但不是漸進線。因為 $\lim_{ x \to a }f(x)$ 有定義。
	- 分子沒有 $(x-a)$ 項 => 圖形在該點為垂直漸進線。因為 $\lim_{ x \to a }f(x)$ 沒定義(趨近於正負無窮)。
- When denominator approaches 0 as $x\to a$, the limit will exist only if the numerator also approaches 0 as $x\to a$. 
- $\lim_{ x \to 0 } \frac{\sin x}{x}=1$。利用單位圓，$\tan x, \sin x$夾擠可得。
- $\lim_{ x \to 0 } \frac{\sin ax}{\sin bx}=\frac{a}{b}$
proof:
   利用經典極限：$\lim_{ x \to 0 }\frac{\sin x}{x}=1$。
   將 $ax \text{ } bx$ 代換，$\lim_{ x \to 0 } \frac{\sin ax}{\sin bx}= \lim_{ x \to 0 } \frac{\sin u}{\sin v}$。
   展開 $\frac{\sin u}{u} \frac{u}{v} \frac{v}{\sin v}$，可得 $\lim_{ x \to 0 } \frac{\sin u}{\sin v}=1 \cdot \frac{u}{v} \cdot 1 = \frac{u}{v}=\frac{a}{b}$。
   - 洛必達：$\lim_{ x \to a } \frac{f(x)}{g(x)}=\lim_{ x \to a } \frac{f'(x)}{g'(x)}$
   - 注意，就算某點非連續，其極限仍可能存在。(比如某點未定義，但其左右極限相同)
   - 若 $f=\frac{1}{x}, g=\frac{1}{x^{2}}$ 則 $(f \circ g)(x)=x^{2}$ ，且$(f \circ g)(x)$ 在 $x=0$ 處不連續(未定義)。不要看到 $x^{2}$ 就以為處處連續！
   - 若要證明「當且僅當」成立，需要雙向證明。

# 經典練習題

1. $\text{If }\lim_{ x \to 1 } \frac{f(x)-8}{x-1}=10 \text{, find }\lim_{ x \to 1 }f(x).$

Sol:
By Limit Laws, we have:
$\lim_{ x \to 1 }[f(x)-8]=\lim_{ x \to 1 } [{\frac{f(x)-8}{x-1}\times(x-1)}]=\lim_{ x \to 1 }[f(x)-8] \times \lim_{ x \to 1 }(x-1)=0$
$\lim_{ x \to 1 }[f(x)-8 + 8]=0 + \lim_{ x \to 1 }8=8$

2. Determine the infinite limit $\lim_{ x \to 3^{-} } \frac{x^{2}+4x}{x^{2}-2x-3}$

Sol:
$\lim_{ x \to 3^{-} } \frac{x^{2}+4x}{x^{2}-2x-3}=\lim_{ x \to 3^{-} } \frac{x(x+4)}{(x-3)(x+1)}=-\infty$

3. Determine the infinite limit $\lim_{ x \to 0 }(\ln x^{2}-x^{-2})$

Sol:
$\lim_{ x \to 0 }(\ln x^{2}-x^{-2})=\lim_{ x \to 0 }\left( \ln \frac{x^{2}}{e^{1/x^{2}}} \right)=-\infty$

4. If 

$$
f(x)= \begin{cases}
x^{2}， \text{if x is ratoinal} \\
0 \ \text{ }， \text{if x is irrational}
\end{cases}
$$
   prove that $\lim_{ x \to 0 }f(x)=0$. 

Sol:
$0 \leq f(x) \leq x^{2}$ 
By Squeeze Theorem, we have $\lim_{ x \to 0 }0=0=\lim_{ x \to 0 }x^{2}=\lim_{ x \to 0 }f(x)$. 
Thus, by Squeeze Theorem we have $\lim_{ x \to 0 }f(x)=0$. 

3. 求 $\lim_{ \theta \to  0} \frac{\sin 3\theta}{\tan 2\theta}$。

Sol:
法一：
$\frac{\sin 3\theta}{\frac{\sin 2\theta}{\cos 2\theta}}=\frac{\sin 3\theta \cos 2\theta}{\sin 2\theta}$ 
又 $\lim_{ x \to 0 }\cos x=1 \therefore\lim_{ x \to 0 }\cos 2x=1$ 等於求 $\lim_{ \theta \to 0 } \frac{\sin 3\theta}{\sin 2\theta}$。
利用 $\lim_{ \theta \to 0 } \frac{\sin a\theta}{\sin b\theta}=\frac{a}{b}$ ($\lim_{ \theta \to 0 } \frac{\sin 3\theta}{\sin 2\theta}=\lim_{ \theta \to 0 }\left( \frac{\sin 3\theta}{3\theta} \cdot \frac{3\theta}{2\theta} \cdot \frac{2\theta}{\sin 2\theta} \right)= \frac{3}{2}$ )，則 $\lim_{ \theta \to 0 } \frac{\sin 3\theta}{\sin 2\theta}=\frac{3}{2}$。

法二：洛必達
$\because \lim_{ \theta \to 0 } \frac{\sin 3\theta}{\tan 2\theta} \in \text{0/0類型} \therefore \text{可以套用洛必達}$
$\lim_{ \theta \to 0 } \frac{\sin 3\theta}{\tan 2\theta}=\lim_{ \theta \to 0 }\frac{\sin^{'} 3\theta}{\tan^{'}2\theta}=\lim_{ \theta \to 0 } \frac{3 \cos 3\theta}{2\sec^{2}2\theta}=\frac{3}{2}$。

4. Prove that $\lim_{ x \to 3 }x^{2}=9$.

Sol:
From the $\epsilon - \delta$ definition, $\forall \epsilon > 0, \exists \delta >0$ such that: 
$\text{If }0<|x-3| < \delta \text{, then } |x^{2}-9| < \epsilon$ 
$|x^{2}-9|=|x+3||x-3|$ 
Take $\delta \leq 1$, then
$2 < x < 4 \implies |x+3| < 7$ 
Thus, take $\delta = \text{min}\{1,\frac{\epsilon}{7}\}$. 
So, $\lim_{ x \to 3 }x^{2}=9$ by the definition of a limit. 

4.  Verify that $\delta=\text{min}\left\{ 2, \frac{\epsilon}{8} \right\}$ showing that $\lim_{ x \to 3 }x^{2}=9$

Sol:
Given $\epsilon >0$, we let $\delta=\text{min}\left\{ 2, \frac{\epsilon}{8} \right\}$. 
If $0<|x-3|<\delta \text{, then } 0<|x-3|<2\implies|x+3|<8$.
`~^ Be aware of the sentence that we use`
Also $|x-3|< \frac{\epsilon}{8}$, so $|x^{2}-9| = |x+3||x-3| = 8 \cdot \frac{\epsilon}{8}=\epsilon$.
`~^ Also notice here`
Thus, $\lim_{ x \to 3 }x^{2}=9$ by the definition of a limit. 

5. Verify, by a geometric argument, that the largest possible choice of $\delta$ for showing that $\lim_{ x \to 3 }x^{2}$ is $\delta=\sqrt{ 9+\epsilon }-3$

![[Pasted image 20250918160953.png]]

Sol:
From the graph, our choice for $\delta$ are $\delta_{1}=3-\sqrt{ 9-\epsilon }$ and $\delta_{2} = \sqrt{ 9+\epsilon }-3$. The possible choice of $\delta$ is the minimum value of $\delta_{1}$ and $\delta_{2}$. So, $\delta=\delta_{2}=\sqrt{ 9+\epsilon }-3$. 

6. Prove $\lim_{ x \to 6^{-} }(6-x)^{1/8}=0$

Sol:
From the $\epsilon - \delta$ definition, $\forall \epsilon > 0, \exists \delta > 0$ such that
If $6-\delta<x<6$ then $|(6-x)^{1/8}|<\epsilon$
`~~~~~^ key` 
Remain are the same contents as before. 

7. Prove $\lim_{ x \to a }\sqrt{ x }=\sqrt{ a }$, if $a>0$

Sol:
From the $\epsilon \cdot \delta$ definition, $\forall \epsilon > 0, \exists \delta > 0$ such that
If $0<|x-a|<\delta$ then $|\sqrt{ x }-\sqrt{ a }|<\epsilon$.
$|\sqrt{ x }-\sqrt{ a }|=|x-a|| \frac{1}{\sqrt{ x }+\sqrt{ a }}|$ 
We let $|x-a| < \frac{a}{2}\implies \frac{1}{\sqrt{ x }-\sqrt{ a }}< \frac{1}{\sqrt{ \frac{1}{2}a }+\sqrt{ a }}$ (若令 $|x-a|<1$，化簡後會得到 $a\geq 1$ 的條件)
`~~~~~~~~~~~~~^ key`
Thus, we take $\delta = \text{min}\left\{ \frac{a}{2}, \left( \sqrt{ \frac{a}{2} }+\sqrt{ a } \right)\epsilon \right\}$.
If $0<|x-a|<\delta$, then $|x-a|< \frac{a}{2} \implies \sqrt{ x }+\sqrt{ a } > \sqrt{ \frac{a}{2} }+\sqrt{ a }$.
Also, $|x-a|< \left( \sqrt{ \frac{a}{2} }+\sqrt{ a } \right)\epsilon$.
Thus, $|\sqrt{ x }-\sqrt{ a }|= \frac{|x-a|}{\sqrt{ x }+\sqrt{ a }}< \left( \sqrt{ \frac{a}{2} }+\sqrt{ a } \right)\epsilon \cdot \frac{1}{\sqrt{ \frac{a}{2} }+\sqrt{ a }}=\epsilon$.
Therefore, $\lim_{ x \to a }\sqrt{ x }=\sqrt{ a }$ if $a > 0$ by the definition of a limit. 

8. Prove the Heaviside function that $\lim_{ x \to 0 }f(x)$ does not exist.

Sol:
Suppose that $\lim_{ x \to 0 }f(x)=L$. Given $\epsilon=\frac{1}{2}$, there exists $\delta>0$ such that:
If $0<|x|<\delta$ then $|f(x)-L|<  \frac{1}{2}$
$|f(x)-L|< \frac{1}{2} \implies L- \frac{1}{2} < f(x) < L + \frac{1}{2}$
For $0<x<\delta$, we have $f(x)=1 \implies L> \frac{1}{2}$
For $-\delta < x < 0$, we have $f(x)=0\implies L < \frac{1}{2}$
This contradicts $L> \frac{1}{2}$. Therefore $\lim_{ x \to 0 }f(x)$ does not exist. 

9. Given $\lim_{ x \to a }f(x)=\infty$ and $\lim_{ x \to a }g(x)=c$, prove the limit below: 
- (a) $\lim_{ x \to a }f(x)+g(x)=\infty$
- (b) $\lim_{ x \to a }f(x)g(x)=\infty$ if $c>0$
- (c) $\lim_{ x \to a }f(x)g(x)=-\infty$ if $c<0$

Sol:
(a)
Let $M>0$ be given. 
Since $\lim_{ x \to a }f(x)=\infty$, there exists $\delta_{1} \ni$
If $0<|x-a|<\delta_{1}$ then $f(x) > M -c + 1$
Since $\lim_{ x \to a }g(x)=c$, for any $\epsilon>0$ there exists $\delta_{2} \ni$
If $0<|x-a|<\delta_{2}$ then $|g(x)-c|<\epsilon$
Take $\epsilon \leq 1$, then we can get $c-1<g(x)<c+1$
Take $\delta = \text{min}\{\delta_{1}, \delta_{2}\}$, we have
$0<|x-a|<\delta \implies f(x)+g(x)>(M - c + 1) + c-1＝M$
Thus, $\lim_{ x \to a }(f(x)+g(x))=\infty$

(b)
Let $M > 0$ be given.
Since $\lim_{ x \to a }f(x)=\infty$, there exists $\delta_{1} \ni$
If $0<|x-a|<\delta_{1}$ then $f(x) > \frac{2M}{c}$
Since $\lim_{ x \to a }g(x)=c$, for any $\epsilon>0$ there exists $\delta_{2} \ni$
If $0<|x-a|<\delta_{2}$ then $|g(x)-c| < \epsilon$。
Take $\epsilon \leq \frac{c}{2}$ we can get $\frac{c}{2}<g(x)< \frac{3c}{2}$.
`~~~~~~~^ key`
Take $\delta = \text{min}\{\delta_{1}, \delta_{2}\}$, we have
$0<|x-a|<\delta\implies f(x)g(x)> \frac{2M}{c}\cdot \frac{c}{2}=M$
Thus, $\lim_{ x \to a }f(x)g(x)=\infty$. 

(c)
Let $M<0$ be given.
Since $\lim_{ x \to a }f(x)=\infty$, there exists $\delta_{1} \ni$
If $0<|x-a|<\delta_{1}$ then $f(x) >\frac{2M}{c}$ (Note that M < 0 and c < 0 then M/c > 0)
Since $\lim_{ x \to a }g(x)=c$, for any $\epsilon>0$ there exists $\delta_{2} \ni$ 
If $0<|x-a|<\delta_{2}$ then $|g(x)-c| < \epsilon$. 
Take $\epsilon \leq \frac{-c}{2}$ we can get $\frac{3c}{2}<g(x)< \frac{c}{2}$.
`~~~~~~~^ notice that c < 0, thus epsilon must smaller than -c/2 but not c/2`
Take $\delta = \text{min}\{\delta_{1}, \delta_{2}\}$, we have
$0<|x-a|<\delta\implies f(x)g(x)< \frac{2M}{c}\cdot \frac{c}{2}=M$
Thus, $\lim_{ x \to a }f(x)g(x)=-\infty$.

10. 證明 $f$ 在 $a$ 處連續 $\iff \lim_{ h \to 0 }f(a+h)=f(a)$

Sol:
Let x = a + h, and $h \to 0 \iff x \to a$
Then we have $\lim_{ h \to 0 }f(a+h)=\lim_{ x \to a }f(x)$. 
($\implies$) If $f$ is continuous at $a$, then $\lim_{ h \to 0 }f(a+h)=\lim_{ x \to a }f(x)=f(a)$. 
($\impliedby$) If $\lim_{ h \to 0 }f(a+h)=f(a)$, then by substitution $\lim_{ x \to a }f(x)=f(a)$. i.e., $f$ is continuous at $a$. 

11. prove that cosine is a continuous function. 

Sol:
因為使用定義 $\lim_{ x \to a }\cos x=\cos a$ 不好操作，使用 $\lim_{ h \to 0 }\cos(a+h)=\cos(a)$ 證明。
$\lim_{ h \to 0 }\cos(a+h)=\lim_{ h \to 0 }[\cos a \cos h-\sin a\sin h]=\cos a$
Thus, cosine is a continuous function. 

12. Suppose $f$ is continuous on $[1,5]$ and the only solutions of the equation $f(x)=6$ are $x=1$ and $x=4$. If $f(2)=8$, explain why $f(3)>6$.

Sol:
Suppose that $f(3) < 6$. 
By the I.V.T., in $(2,3)$ we have a number $c$ such that $f(c)=6$. 
However, this contradicts that the only solution of $f(x)=6$ is $x=1$ and $x=4$. 
Hence $f(3) < 6$ is incorrect.
It follows that $f(3) \geq 6$. However, $f(3)=6$ also contradicts that the only solution of $f(x)=6$ is $x=1$ and $x=4$. 
Thus, $f(3) > 6$. 

13. If $a$ and $b$ are positive numbers, prove that the equation $\frac{a}{x^{3}+x^{2}-1}+\frac{b}{x^{3}+x-2}=0$ has at least one solution in the interval $(-1, 1)$. 

Sol:
We have to notice that $\frac{a}{x^{3}+x^{2}-1}+\frac{b}{x^{3}+x-2}=0$ can be convert as $a(x^{3}+x-2)+b(x^{3}+x^{2}-1)=0$. (Hard to realize this for me)
Let the formula above be $f(x)$, $f(-1)=-4a<0, f(1)=2b>0$.
Since $f(-1) < 0<f(1)$, and $f$ is continuous in $[-1, 1]$, there exists $c \in (-1, 1)$ such that $f(c)=0$ by Intermediate Value Theorem.

14. Show that the absolute value function $F(x)=|x|$ is continuous everywhere.

Sol:
$\lim_{ x \to 0^{-} }F(x)=0, \lim_{ x \to 0^{+} }F(x)=0\implies \lim_{ x \to 0 }F(x)=0$. Thus, $F(x)$ is continuous at 0.
For $a > 0$, $\lim_{ x \to a }F(x)=\lim_{ x \to a }x=a=F(a)$. Thus, $F(x)$ is continuous in $(0, \infty)$.
For $a<0, \lim_{ x \to a }F(x)=\lim_{ x \to a }(-x)=-a=F(a)$. Thus, $F(x)$ is continuous in $(-\infty, 0)$. 
Hence, $F(x)$ is continuous everywhere.

15. Prove that if $f$ is a continuous function on an interval, then so is $|f|$.

Sol:
Assume $f$ is continuous in interval $I$. For $a \in I$, $\lim_{ x \to a }|f(x)|=|\lim_{ x \to a }f(x)|=|f(a)|$.  (If $a$ is the endpoint of $I$, use the appropriate one-sided limit. ) So $|f|$ is continuous in $I$. 