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

設$c=1$，$L=2$，$f(x)=5x-3$，則需要找到符合的$\delta$與$\epsilon$。

$$
0<|x-1|<\delta \implies |f(x) - L| < \epsilon
$$

利用$\epsilon$到推$\delta$：

$$
\begin{align}
|(5x-3) - 2| = |5x-5| < \epsilon \\
5|x-1| < \epsilon \\
|x-1|< \frac{\epsilon}{5}
\end{align}
$$

我們取$\delta=\frac{\epsilon}{5}$，若$0<|x-1|<\delta=\frac{\epsilon}{5}$則：

$$
|5x-5| < \epsilon
$$

證畢。

$$
\lim_{ x \to 1 } \frac{f(x)-8}{x-1}=10, \text{求} \lim_{ x \to 1 } f(x)
$$
$$
\because \lim_{ x \to 1 } \frac{f(x)-8}{x-1} \text{ exist, }
\therefore f(x)-8 \text{可以被 }x-1\text{整除，即}f(1)-8=0 \implies f(1)=8 \implies \lim_{ x \to 1 } f(x)=8
$$

# 單側極限

定義左極限：

$$
\lim_{ x \to a^{-} } f(x) = L
$$

對於所有數字 $\epsilon >0$，存在數字 $\delta > 0$ 使得

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

## 利用代數對給定的$\epsilon$求$\delta$

1. 解不等式$|f(x)-L|<\epsilon$，找到一個開區間$(a,b)$包含$c$且當所有$x\neq c$時不等式皆成立。
2. 找到一個$\delta>0$使得在開區間$(a,b)$中的$c$在$(c-\delta, c+\delta)$中間，且不等式$|f(x)-L|<\epsilon$對所有$x\neq c$皆成立。

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
$\frac{1}{x^{2}} > M \Leftrightarrow x^{2} < \frac{1}{M} \Leftrightarrow |x| < \frac{1}{\sqrt{ M }}$
取 $\delta = \frac{1}{\sqrt{ M }}$
因此，對於所有正數 $M$ 存在 $\delta = \frac{1}{\sqrt{ M }}$ 使得 $0<|x|<\delta \implies \frac{1}{x^{2}} > M$

# 證明 limit law

首先，我們來證明：

$$
\lim_{ x \to a } [f(x) + g(x)] = L + M
$$

proof:
根據 $\epsilon \cdot \delta$ 定義，$\forall \epsilon > 0, \exists\delta>0$ 使得
$$
\text{If }0<|x-a|<\delta \text{, then }|f(x) + g(x) - L - M| < \epsilon
$$
$|f(x) + g(x) - L - M|=|f(x)-L + g(x) - M|$
根據三角不等式 $|x+y| \leq |x| + |y|$，我們可以寫出：$|f(x)-L + g(x) - M| \leq |f(x)-L| + |g(x)-M|$
令 $\delta_{1} > 0 \text{, } \delta_{2} > 0$ 且 $0<|x-a|<\delta_{1}$ 使得 $|f(x)-L|<\frac{\epsilon}{2}$，與 $0<|x-a|<\delta_{2}$ 使得 $|g(x)-M|<\frac{\epsilon}{2}$
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

# 小 tip

- When denominator approaches 0 as $x\to a$, the limit will exist only if the numerator also approaches 0 as $x\to a$. 
- $\lim_{ x \to 0 } \frac{\sin x}{x}=1$。利用單位圓，$\tan x, \sin x$夾擠可得。
- $\lim_{ x \to 0 } \frac{\sin ax}{\sin bx}=\frac{a}{b}$
proof:
   利用經典極限：$\lim_{ x \to 0 }\frac{\sin x}{x}=1$。
   將 $ax \text{ } bx$ 代換，$\lim_{ x \to 0 } \frac{\sin ax}{\sin bx}= \\lim_{ x \to 0 } \frac{\sin u}{\sin v}$。
   展開 $\frac{\sin u}{u} \frac{u}{v} \frac{v}{\sin v}$，可得 $\lim_{ x \to 0 } \frac{\sin u}{\sin v}=1 \cdot \frac{u}{v} \cdot 1 = \frac{u}{v}$。
# 經典例題

1. $\text{If }\lim_{ x \to 1 } \frac{f(x)-8}{x-1}=10 \text{, find }\lim_{ x \to 1 }f(x).$

Sol:
$\lim_{ x \to 1 }[f(x)-8]=\lim_{ x \to 1 } [{\frac{f(x)-8}{x-1}\times(x-1)}]=\lim_{ x \to 1 }[f(x)-8] \times \lim_{ x \to 1 }(x-1)=0$
$\lim_{ x \to 1 }[f(x)-8 + 8]=0 + \lim_{ x \to 1 }8=8$

2. If 

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

3. 求 $\lim_{ x \to  0} \frac{\sin 3\theta}{\tan 2\theta}$。

Sol:
法一：
$\frac{\sin 3\theta}{\frac{\sin 2\theta}{\cos 2\theta}}=\frac{\sin 3\theta \cos 2\theta}{\sin 2\theta}$
又 $\lim_{ x \to 0 }\cos x=1 \therefore\lim_{ x \to 0 }\cos 2x=1$ 等於求 $\lim_{ \theta \to 0 } \frac{\sin 3\theta}{\sin 2\theta}$。
利用 $\lim_{ \theta \to 0 } \frac{\sin ax}{\sin bx}=\frac{a}{b}$，則 $\lim_{ x \to 0 } \frac{\sin 3x}{\sin 2x}=\frac{3}{2}$。


法二：洛必達
$\because \lim_{ \theta \to 0 } \frac{\sin 3\theta}{\tan 2\theta} \in \text{0/0類型} \therefore \text{可以套用洛必達}$
$\lim_{ \theta \to 0 } \frac{\sin 3\theta}{\tan 2\theta}=\lim_{ \theta \to 0 }\frac{\sin^{'} 3\theta}{\tan^{'}2\theta}=\lim_{ \theta \to 0 } \frac{3 \cos 3\theta}{2\sec^{2}2\theta}=\frac{3}{2}$。

4. Prove that $\lim_{ x \to 3 }x^{2}=9$.

Sol:
From the $\epsilon \cdot \delta$ definition, $\forall \epsilon > 0, \exists \delta >0$ such that: 
$\text{If }0<|x-3| < \delta \text{, then } |x^{2}-9| < \epsilon$
$|x^{2}-9|=|x+3||x-3|$
Take $\delta \leq 1$, then
$2 < x < 4 \implies |x+3| < 7$
Thus, take $\delta = \text{min}\{1,\frac{\epsilon}{7}\}$. 
So, $\lim_{ x \to 3 }x^{2}=9$ by the definition of a limit. 

4.  Verify that $\delta=\text{min}\left\{ 2, \frac{\epsilon}{8} \right\}$ showing that $\lim_{ x \to 3 }x^{2}=9$

Sol:
Given $\epsilon >0$, we let $\delta=\text{min}\left\{ 2, \frac{\epsilon}{8} \right\}$. 
If $0<|x-3|<\delta \text{, then } 0<|x-3|<2\implies|x+3|<8.$
Also $|x-3|< \frac{\epsilon}{8}$, so $|x^{2}-9| = |x+3||x-3| = 8 \cdot \frac{\epsilon}{8}=\epsilon$
Thus, $\lim_{ x \to 3 }x^{2}=9$ by the definition of a limit. 

5. Verify, by a geometric argument, that the largest possible choice of $\delta$ for showing that $\lim_{ x \to 3 }x^{2}$ is $\delta=\sqrt{ 9+\epsilon }-3$

![[Pasted image 20250918160953.png]]

Sol:
From the graph, our choice for $\delta$ are $\delta_{1}=3-\sqrt{ 9-\epsilon }$ and $\delta_{2} = \sqrt{ 9+\epsilon }-3$. The possible choice of $\delta$ is the minimum value of $\delta_{1}$ and $\delta_{2}$. So, $\delta=\delta_{2}=\sqrt{ 9+\epsilon }-3$. 

6. Prove $\lim_{ x \to 6^{-} }(6+x)^{1/8}=0$

Sol:
From the $\epsilon \cdot \delta$ definition, $\forall \epsilon > 0, \exists \delta > 0$ such that
If $0<x+6<\delta$ then $|(6+x)^{1/8}|<\epsilon$
`~~~~~^ key`
Remain are the same content as before. 

7. Prove $\lim_{ x \to a }\sqrt{ x }=\sqrt{ a }$, if $a>0$

Sol:
... skip ...
$|\sqrt{ x }-\sqrt{ a }|=|x-a|| \frac{1}{\sqrt{ x }+\sqrt{ a }}|$.
We let $|x-a| < \frac{a}{2}\implies \frac{1}{\sqrt{ x }-\sqrt{ a }}< \frac{1}{\sqrt{ \frac{1}{2}a }+\sqrt{ a }}$ (若令 $|x-a|<1$，化簡後會得到 $a\geq 1$ 的條件)
`~~~~~~~~~~~~~^ key`
... skip ...

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
$0<|x-a|<\delta \implies f(x)+g(x)>(M - c + 1) + c＝M$
Thus, $\lim_{ x \to a }(f(x)+g(x))=\infty$

(b)
Let $M > 0$ be given.
Since $\lim_{ x \to a }f(x)=\infty$, there exists $\delta_{1} \ni$
If $0<|x-a|<\delta_{1}$ then $f(x) > \frac{2M}{c}$
Since $\lim_{ x \to a }g(x)=c$, for any $\epsilon>0$ there exists $\delta_{2} \ni$
If $0<|x-a|<\delta_{2}$ then $|g(x)-c| < \epsilon$。
Take $\epsilon \leq \frac{c}{2}$ we can get $\frac{c}{2}<g(x)< \frac{3c}{2}$
Take $\delta = \text{min}\{\delta_{1}, \delta_{2}\}$, we have
$0<|x-a|<\delta\implies f(x)g(x)> \frac{2M}{c}\cdot \frac{c}{2}=M$
Thus, $\lim_{ x \to a }f(x)g(x)=\infty$. 

(c)
Let $M<0$ be given.
Since $\lim_{ x \to a }f(x)=\infty$, there exists $\delta_{1} \ni$
If $0<|x-a|<\delta_{1}$ then $f(x) < \frac{2M}{c}$ (Note that M < 0 and c < 0 then M/c > 0)
Since $\lim_{ x \to a }g(x)=c$, for any $\epsilon>0$ there exists $\delta_{2} \ni$
If $0<|x-a|<\delta_{2}$ then $|g(x)-c| < \epsilon$. 
Take $\epsilon \leq \frac{-c}{2}$ we can get $\frac{3c}{2}<g(x)< \frac{c}{2}$.
Take $\delta = \text{min}\{\delta_{1}, \delta_{2}\}$, we have
$0<|x-a|<\delta\implies f(x)g(x)< \frac{2M}{c}\cdot \frac{c}{2}=M$
Thus, $\lim_{ x \to a }f(x)g(x)=-\infty$. 