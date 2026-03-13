$[(p\to q)\land(q\to r)]\to(p\to r)$ 
$\equiv \neg[(\neg p\lor q)\land(\neg q\lor r)]\lor(\neg p\lor r)$ 
$\equiv[(p\land \neg q)\lor(q\land \neg r)]\lor(\neg p\lor r)$ 
$\equiv \neg p\lor r\lor(p\land \neg q)\lor(q\land \neg r)$ 
$\equiv (\neg p\lor(p\land \neg q))\lor(r\lor(q\land \neg r))$ 
$\equiv[(\neg p\lor p)\land(\neg p\lor \neg q)]\lor[(r\lor q)\land(r\lor \neg r)]$ 
$\equiv(\neg p\lor \neg q)\lor(r\lor q)$ 
$\equiv T$ 

假設 $x$ 有貓記做 $P(x)$，有狗記做 $D(x)$，有魚記做 $F(x)$。若定義域為全班同學，如何表示 for each animal, there is a student who has this animal as a pet.

Sol:
$(\exists xP(x))\land(\exists xD(x)\land(\exists F(x)))$ 

![[Pasted image 20260312163427.png]]

Sol:
我們證明 $\forall x(\neg R(x)\to P(x))\equiv \forall x(R(x)\lor P(x))$。
取 $a$ 在定義域中，且滿足：
- $P(a)\lor Q(a)\equiv T$ $(i)$
- $(\neg P(a)\land Q(a))\to R(a)$ $(ii)$
由 $(ii)$，得知 $P(a)\lor \neg Q(a)\lor R(a)\equiv T$ $(iii)$。
假設 $Q(a)\equiv T$，則：
由 $(iii)$ 得：$P(a)\lor R(a)\equiv T$。
綜合上式，得 $P(a)\lor R(a)\equiv T$。
假設 $Q(a)\equiv F$，則：
由 $(i)$ 得：$P(a)\equiv T$。
由上式與 $(iii)$ 得：$P(a)\lor R(a)\equiv T$ 
所以，$P(a)\lor R(a)$ 成立。由於 $a$ 為任意定義域中的值，所以有 $\forall x(\neg R(x)\to P(x))\equiv T$。