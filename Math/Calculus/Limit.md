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

# 極限的定義

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

## 利用代數對給定的$\epsilon$求$\delta$

1. 解不等式$|f(x)-L|<\epsilon$，找到一個開區間$(a,b)$包含$c$且當所有$x\neq c$時不等式皆成立。
2. 找到一個$\delta>0$使得在開區間$(a,b)$中的$c$在$(c-\delta, c+\delta)$中間，且不等式$|f(x)-L|<\epsilon$對所有$x\neq c$皆成立。

# 易錯觀念

- When denominator approaches 0 as $x\to a$, the limit will exist only if the numerator also approaches 0 as $x\to a$. 

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