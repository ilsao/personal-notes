# 奇與偶函數

奇函數：對稱原點。$f(-x)=-f(x)$。

偶函數：對稱 y 軸。$f(-x)=f(x)$。

# 多項式

quadratic：二次的

cubic：三次的

多項式的次方不可為負數，若為負數則為有理函數。

# 有理函數(rational function)

兩多項式相除，其中分母多項式不可等於0。

令 $r(x)$ 為有理函數，則與多項式相同，具有 $\lim_{ x \to a }r(x)=r(a)$ 的特性。

# 冪函數 (power function)

形如：

$$
f(x)=x^{a}，\text{其中}a \in \mathbb{Z}。
$$

## 根號函數 (root function)

若 $a=\frac{1}{n}$ 且 $n \in \mathbb{N}$ (正整數)，則屬根號函數。

# 指數函數 (exponential function)

形如：

$$
f(x) = a^{x}，\text{其中}a>0\text{且}a\neq 1
$$

# 代數函數 (algebraic function)

可以由以下操作，在有限步驟內構造出的函數，即代數函數：
- 加法、減法、乘法、除法
- 整數次方、根號

# 超越函數 (transcendental function)

不是代數函數，則皆為超越函數：
- 指數函數：$e^{x}$
- 對數函數：$\ln x$
- 三角函數：$\sin x$
- 反三角函數：$\arcsin x$

# 一對一函數 (one-to-one function)

當：

$$
x_{1} \neq x_{2} \text{ 且 } f(x_{1}) \neq f(x_{2})
$$

則稱 $f(x)$ 為一對一函數。

可以使用以下方法來檢測函數是否為一對一函數：
- 由定義出發
- 水平線測試 (horizontal line test)

## 例題

判斷 $f(x)=x^{3}$ 是否為一對一函數。

Sol：
設 $x_{1}、x_{2}$ 且 $x_{1}\neq x_{2}$。
由一對一函數的定義可知 $f(x_{1}) \neq f(x_{2}) \implies x_{1}^{3}-x_{2}^{3}\neq0$

$x_{1}^{3}-x_{2}^{3}$
$=(x_{1}-x_{2})(x_{1}^{2}+x_{1}x_{2}+x_{2}^{2})$
$=(x_{1}-x_{2})\left[ \left( x_{1}-\frac{1}{2}x_{2} \right)^{2}+\frac{3}{4}x_{2}^{2} \right]$
$\neq 0$
$\implies f(x)\text{是一對一函數}$。

# 三角函數

$$
\sec x=\frac{1}{\cos x}
$$

$$
\csc x=\frac{1}{\sin x}
$$

$$
\cot x = \frac{1}{\tan x}
$$

$$
\cos^2 x = \frac{1}{1 + \tan^{2} x} \iff \sec^{2}=1 + \tan^{2}x
$$

proof:
$\sin^{2}x + \cos^{2}x = 1$
同除 $\cos^{2}x$: $\frac{\sin^{2}x}{\cos^{2}x}+\frac{\cos^{2}x}{\cos^{2}x}=\frac{1}{\cos^{2}x}$
$\implies \tan^{2}x + 1 = \sec^{2}x$

$$
\sin 2x = \frac{2t}{1+t^{2}}，t=\tan x
$$

proof:
$\sin 2x=2\sin x\cos x=2\tan x\cos^{2}x$
$=2\tan x \times \frac{1}{1+\tan^{2}x}=\frac{2t}{1+t^{2}}$

$$
\cos 2x = \frac{1-t^{2}}{1+t^{2}}，t=\tan x
$$

proof:
$\cos 2x=2\cos^{2}x - 1=2 \times \frac{1}{1+\tan^{2}x}-1$
$=\frac{2-1-\tan^{2}x}{1+\tan^{2}x}=\frac{1-t^{2}}{1+t^{2}}$

# 反三角函數 (inverse trigonometric functions)

$$
\arcsin x = y \iff \sin y=x \text{ and } \frac{-\pi}{2}\leq y\leq \frac{\pi}{2}
$$

$$
\arccos x=y \iff \cos y=x \text{ and } 0 \leq y \leq \pi
$$

$$
\arctan x=y \iff \tan y=x \text{ and } \frac{-\pi}{2}\leq y \leq \frac{\pi}{2}
$$
## 例題

求 $\tan\left( \arcsin \frac{1}{3} \right)$ 的值。

Sol I:
令 $\arcsin \frac{1}{3} = y \iff \sin y= \frac{1}{3} \text{ and } \frac{-\pi}{2} \leq y \leq \frac{\pi}{2}$
$\implies \tan\left( \arcsin \frac{1}{3} \right)=\tan(y)=\frac{\sin y}{\cos y}$
$\implies \frac{\frac{1}{3}}{\sqrt{ \frac{8}{9} }}=\frac{\frac{1}{3}}{\frac{2\sqrt{ 2 }}{3}}=\frac{1}{2\sqrt{ 2 }}$

Sol II:
$\text{令} \arcsin \frac{1}{3} = \theta$，則可得，斜邊為 3 ，底邊為 $2\sqrt{ 2 }$，高為 1 的直角三角形。
則 $\tan \theta=\frac{1}{2\sqrt{ 2 }}$。

# 換底公式

$$
\log_{a}b = \frac{\log b}{\log a}
$$

proof:
$a^{\log_{a} b}=b$
$\implies \log a^{\log_{a} b}=\log b$
$\implies \log_{a}b \times \log a = \log b$
$\implies \log_{a}b = \frac{\log b}{\log a}$

# 易錯知識

- 給定 $f$ 的定義域為 $A$，$g$ 的定義域為$B$。
	$(f+g)(x)、(f-g)(x)、(fg)(x)$ 的定義域為 $A \cap B$。
	$\left( \frac{f}{g} \right)(x)$ 的定義域為 $\{x \in A \cap B | g(x)\neq 0\}$。

- 指數函數、拋物線：如何選擇擬合曲線？
	指數擬合：長期增加爆炸快。
	拋物線擬合：長期雖快，但仍沒指數快。