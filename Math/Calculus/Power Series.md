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

$f$ 的定義域是所有使級數收斂的 $x$。注意到 $f$ 跟多項式很像，唯一的區別是 $f$ 有無限多項。

更一般地，級數形如：

$$
\sum_{n=0}^{\infty}c_{n}(x-a)^{n}=c_{0}+c_{1}(x-a)+c_{2}(x-a)^{2}+\dots
$$

稱為 power series in $(x-a)$ 或以 $a$ 為中心的 power series 或關於 $a$ 的 power series。

> [!note]
> 注意到當 $x=a$ 時對 $n\geq1$ 的項都為零，所以此時 power series 必發散。

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

> [!note]
> $\ln(1+z)=-\ln(1+z)^{-1}=-\ln\left( \frac{1}{1+z} \right)=-\ln\left( 1+ \frac{1}{1+z}-1 \right)=-\ln\left( 1  -\frac{z}{1+z} \right)$  就可以計算任意 $z$ 的值。

> [!warning] 注意
> 雖然 power series 定義出的函數一定無限可微，但一個無限可微的函數，不一定可表達為 power series。

# Exercise

![[Pasted image 20260316202212.png]]![[Pasted image 20260316212331.png]]

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
注意到 $\sum \frac{x^{n}}{n}$ 收斂區間為 $[p,q)$。
想令左右端點閉合關係調轉：$\sum(-1)^{n} (\frac{x^{n}}{n})$。
於是答案為 $\sum(-1)^{n}\left( \frac{1}{n} \right)\left( \frac{x-m}{r} \right)^{n}$。
(c)
與上小題類似，但不乘 $(-1)^{n}$：$\sum \frac{1}{n}\left( \frac{x-m}r{} \right)^{n}$。
(d)
注意到 $\sum \frac{x^{n}}{n^{2}}$ 收斂區間為 $[-1,1]$。
於是答案為：$\sum \frac{1}{n^{2}} (\frac{x-m}{r})^{n}$。

# 大會考

![[Pasted image 20260316223935.png]]

Sol:
這題卡在不知道 $f'$ 應該對誰微分，實際上應該對 $x$ 微分。
注意力驚人的我，注意到對 $f(x)=\sum_{n=1}^{\infty} \frac{x^{n}}{n^{2}}$ 應該包含兩個端點。
$f'(x)=\sum_{n=1}^{\infty} \frac{nx^{n-1}}{n^{2}}=\sum_{n=1}^{\infty} \frac{x^{n-1}}{n}$ 
顯然當 $x=-1$ 時根據 alternating series test 收斂。
而當 $x=1$ 時為調和級數，發散。
$f''(x)=\sum_{n=1}^{\infty} \frac{(n-1)x^{n-2}}{n}$ 
顯然因為 $\lim_{ n \to \infty } \frac{(n-1)x^{n-2}}{n}=x^{n-2}$，在端點時 ($x=\pm 1$) 不為零。
所以兩個端點都發散 by the test for divergence。

![[Pasted image 20260316230314.png]]

Sol:
雖然聰明如我，立馬注意到了答案，但是放這怕你忘記。
這裡無論 $\alpha$ 的值，收斂半徑都是 $1$。
這裡要 $x=1$ 發散，$x=-1$ 時收斂，顯然是在考我們：在什麼情況下 $\sum \frac{1}{n^{p}}$ 發散，但 $\sum \frac{(-1)^{n}}{n^{p}}$ 收斂？
簡單，立馬注意到當 $0<p\leq1$ 時會成立。
所以秒選 (B) 好吧。

![[Pasted image 20260316231634.png]]

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