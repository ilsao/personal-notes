
# Attraction and Repulsion of Charges

Electroscope：驗電器。

Conductor：導體。

Insulator：絕緣體。

# Coulomb's Law

同性電相斥：like charge repel

異性電相吸：unlike charge attract

庫倫定律說：

$$
F=\frac{1}{4\pi\epsilon_{0}} \frac{q_{1}q_{2}}{r^{2}}
$$

其中：

$$
\frac{1}{4\pi\epsilon_{0}}=9\times 10^{9}\text{ N-m}^{2}\text{/C}^{2}
$$

且一個電子帶的電量為：

$$
e=-1.6\times 10^{-19}\text{ C}
$$

# Superposition Principle

**疊加原理(Superposition Principle)**：對於多個電荷所成的系統來說，某個指定電荷受到的總力就是其他所有電荷對他做的力的總和。

# Tips

- 記得寫單位。

# 威儀指定習題

![[Pasted image 20251201195809.png]]

Sol:
**注意單位。**
(a)
記得：萬有引力常數 $G\approx 6.7\times 10^{-11}$。
$\frac{GMm}{r^{2}}=\frac{kQq}{r^{2}}\implies q=5\sqrt{ \frac{G}{k} }\approx 4.3\times 10^{-11}\text{ C}$ 
(b)
$\frac{q}{1.6\times 10^{-19}}\approx 2.7\times 10^{9}\text{ e}$ 

![[Pasted image 20251201200321.png]]

Sol:
不食哥們。
令 $q'$ 為 $q$ 被分走了多少，則要求：$F=\frac{kq'(q-q')}{r^{2}}$ 最大。
求極值，一次微分等於零：$\frac{dF}{dq'}=\frac{k}{r^{2}}(q-2q')=0\implies q'=\frac{q}{2}$。(注意我們這邊要對變數 $q'$ 微分，而不是定值 $q$ 微分)

![[Pasted image 20251201201844.png]]

![[Pasted image 20251201201902.png]]

Sol:
令 $r=\sqrt{ x^{2}+\frac{d^{2}}{4} }$。
我們在腦中想像一下 $q'$ 的受力，會有一個受 $+q$ 而向右下的力，與一個受 $-q$ 而向左下的力。(假設 $q'$ 為正電荷，若為負電荷則受力方向應該上下左右相反)
那麼因為左右的力互相抵銷，所以剩下兩倍的向下的力。
我們連線 $q'q$，取此線與 $x$ 軸的銳角為 $\theta$，則 $\sin \theta= \frac{\frac{d}{2}}{r}=\frac{d}{2r}$。
那麼合力為 $2F\sin \theta=2 \frac{kq'q}{r^{2}}\cdot \frac{d}{2r}=\frac{1}{4\pi\epsilon_{0}} \frac{\mu_{e}q'}{\left[ x^{2}+\frac{d^{2}}{4} \right]^{3/2}}$。

A fixed conducting ball has a charge $q_{1}$  $3 \times 10^{-6}\text{ C}$. An identical ball with charge $q_{2}$ is held at a distance $x$ away from $q_{1}$. The two balls attract each other with a force of $13.5\text{ N}$. The balls are then connected by a conducting wire. After the wire is removed, the balls repel each other with a force of $0.9\text{ N}$. (a) What was the charge $q_{2}$ of the second ball? (b) What is the separation $x$ between the balls?

Sol:
數字醜。。。
令 $q_{2}$ 帶電 $q'$。
因為 wire 連接兩球後會自動達到電荷平衡，所以可推得：$\begin{cases}13.5= \frac{k(3\times 10^{-6})q'}{x^{2}} \\ -0.9= \frac{k\left( \frac{3\times 10^{-6}+q'}{2} \right)^{2}}{x^{2}}\end{cases}$ 
解完就是答案，懶得算。
Ans: (a) $-5\times 10^{-6}\text{ C}$ (b) $0.01\text{ m}$ 