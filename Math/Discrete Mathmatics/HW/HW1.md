![[Pasted image 20260312230505.png]]

Sol:
b)
$f(m,n)=m^{2}-n^{2}=(m+n)(m-n)$ 
因為 $(m+n)-(m-n)=2n$ 為偶數，所以 $(m+n)$ 與 $(m-n)$ 必定同奇偶。
若 $m^{2}-n^{2}=y$，則 $y$ 應可被寫成兩同奇偶整數乘積。
取 $y=2$，因為 $2$ 只能被分解為 $1\times2$ $(-1)\times(-2)$ $2\times1$ $(-2)\times(-1)$，為兩不同奇偶整數乘積。
所以不存在整數 $m,n$ 使得 $f(m,n)=m^{2}-n^{2}=2$，所以 $f(m,n)=m^{2}-n^{2}$ 不是映成函數。

![[Pasted image 20260312234922.png]]

Sol:
只證 $\lfloor -x \rfloor=-\lceil x \rceil$，後面同理可證。
令 $n=\lceil x \rceil$，則 $n-1<x\leq n$。
$\implies-(n-1)>-x\geq-n$ 
$\implies-n$ 是比 $-x$ 小的最大整數
$\implies$ $-n=-\lceil x \rceil=\lfloor -x \rfloor$ 

![[Pasted image 20260313004548.png|870]]
![[Pasted image 20260313004621.png|827]]

Sol:
e) countably infinite
$f:\mathbb{Z}^{+}\to A\times\mathbb{Z}^{+}$ 
取 $f(2k)=(2,k)$ 與 $f(2k-1)=(3,k)\quad k\in \mathbb{Z}^{+}$。
則 $1\mapsto(3,1)\ 2\mapsto(2,1)\ 3\mapsto(3,2)\ 4\mapsto(2,2)\dots$ 一一對應。
或
$f:A\times \mathbb{Z}^{+}\to \mathbb{Z}^{+}$ 
$f(x,y)=\begin{cases}2y & \text{if }x=2 \\ 2y-1 & \text{if }x=3\end{cases}$ 
f) countably infinite
$f:\mathbb{Z}^{+}\to \{ x|x=10k,k\in \mathbb{Z} \}$ 
取 $f(2k)=10k$ 與 $f(2k+1)=-10k\quad k\in \mathbb{Z}^{+}$ 
則 $1\mapsto0\ 2\mapsto 10\ 3\mapsto -10\ \dots$ 一一對應。