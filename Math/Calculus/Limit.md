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

## 利用代數對給定的$\epsilon$求$\delta$

1. 解不等式$|f(x)-L|<\epsilon$，找到一個開區間$(a,b)$包含$c$且當所有$x\neq c$時不等式皆成立。
2. 找到一個$\delta>0$使得在開區間$(a,b)$中的$c$在$(c-\delta, c+\delta)$中間，且不等式$|f(x)-L|<\epsilon$對所有$x\neq c$皆成立。