
# The Area and Distance Problems

## The Area Problem

將一個曲線水平切成 $n$ 份，如果每塊的高取**右端點(right end point)**，我們將這種估計記為：$R_{n}$。

相反，如果高取**左端點(left end point)**，則記為 $L_{n}$。

若在區間 $[a,b]$ 上定義定義 $\Delta x = \frac{b-a}{n}$，而 $x_{i}$ 為：$a+i\Delta x$。則當 $n\to \infty$ 時，所預估出來的值會等於欲求面積，也就是：

$$
A=\lim_{ n \to \infty } R_{n}=\lim_{ n \to \infty } [f(x_{1})\Delta x+\dots+f(x_{n})\Delta x]=\lim_{ n \to \infty } L_{n}
$$

除了使用左右端點，我們可以在 $[x_{i-1}, x_{i}]$ 之中隨機選擇一個點 $x_{i}^{*}$ 當作 sample point。

那麼，我們有：

$$
A=\lim_{ n \to \infty } [f(x_{1}^{*})\Delta x+\dots+f(x_{n}^{*})\Delta x]
$$

讓我們用求和記號表達這些公式：

$$
A=\lim_{ n \to \infty } \sum_{i=1}^{n}f(x_{i})\Delta x=\lim_{ n \to \infty } \sum_{i=1}^{n}f(x_{i-1})\Delta x=\lim_{ n \to \infty } \sum_{i=1}^{n}f(x_{i}^{*})\Delta x
$$

# The Definite Integral

## The Definite Integral

## Evaluating Definite Integrals

## The Midpoint Rule

## Properties of the Definite Integral

