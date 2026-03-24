![[Pasted image 20260324153234.png]]

Sol:
前一個必須是後一個的 big-O，即 $f_{1}=O(f_{2})$，$f_{2}=O(f_{3})\dots$ 
回憶 big-O 定義：
若
$f(n)\leq cg(n)\quad\forall n\geq n_{0}$ 
則
$f(n)=O(g(n))$ 
所以，必須從小排到大。
$(\log n)^{3},\sqrt{ n }\log n,n^{99}+n^{98},n^{100},(1.5)^{n},10^{n},(n!)^{2}$ 

> [!note]
> 兩點要注意：
> - each function is big-O of the next function 確實很容易讓人誤會，背起來。
> - $O(n!)$ 很快，僅次於 $O(n^{n})$。

![[Pasted image 20260324155406.png]]

Sol:
粗心，想成 $n^{3/2}=O(n)$ 了，但實際上不等。
$\lim_{ n \to \infty } \frac{n\log n}{n^{3/2}}=0\implies n\log n\ll n^{3/2}\text{ as }n\to \infty$ 
第一個算法更佳。