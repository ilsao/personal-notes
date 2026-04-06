![[Pasted image 20260403203302.png|710]]![[Pasted image 20260403203246.png|361]]

Sol:
注意表達方式：
$1331=1001\times 1+330$ 
$1001 = 330\times 3+11$ 
$330=11\times 30+0$ 
$\implies\text{gcd}(1001,1331)=11$ 

![[Pasted image 20260403203444.png|951]]![[Pasted image 20260403203456.png|244]]

Sol:
先做輾轉相除法：
$89=34\times 2+21$ 
$34=21\times 1+13$ 
$21=13\times 1+8$ 
$13=8\times 1+5$ 
$5=3\times 1+2$ 
$3=2\times 1+1$ 
$2=1\times 2+0$ 
然後反向做：
$1=3-2$ 
$=3-(5-3)=3\times 2-5$ 
$=2\times(8-5)-5=2\times 8-3\times 5$ 
$=2\times 8-3\times (13-8)=5\times 8-3\times 13$ 
$5\times(21-13)-3\times 13=5\times 21-8\times 13$ 
$=5\times 21-8\times (34-21)=13\times21-8\times34$ 
$=13\times(89-34\times 2)-8\times34$ 
$13\times 89-34 \times 34$ 
$\implies \bar{a}\equiv-34\equiv 55\ (\text{mod }89)$ 
注意：$\bar{a}$ 帶負號，還有如何取 $\mathbb{Z}_{m}$ 的方法。($m-\bar{a}$)

![[Pasted image 20260403204007.png|827]]

Sol:
因為 $-10\equiv1\equiv 12\ (\text{mod }11)$ 
所以 $12x^{2}+25x-10\equiv 12x^{2}+25x+12\equiv(3x+4)(4x+3)\equiv 0\ (\text{mod }11)$ 
(由 $ab\text{ mod }m=((a\text{ mod }m)(b\text{ mod }m))\text{ mod }m$)
$[(3x+4)(4x+3)]\text{ mod }11=[(3x+4)\text{ mod }11][(4x+3)\text{ mod }11]\text{ mod }11$ 
$\implies(3x+4)\text{ mod 11}=0$ 或 $(4x+3)\text{ mod }11=0$  且 $\bar{3}=4$，$\bar{4}=3$ 
$\implies3\cdot \overline{ 3 }x\equiv-4\cdot \overline{ 3 }\equiv-16\equiv 6\equiv x\ (\text{mod }11)$ 或 $4\cdot \overline{ 4 }x\equiv-3\cdot \overline{ 4 }\equiv-9\equiv2\equiv x\ (\text{mod }11)$ 
$\implies x=2\text{ or }6\ (\text{mod 11})$ 

![[Pasted image 20260403204802.png]]

Sol:
提醒你：$y_{i}=\overline{ M_{i} }$ 而非 $\overline{ a_{i} }$。
$m=3\times 4\times 5=60$ 
$M_{1}=4\times5=20$ $M_{2}=3\times 5=15$ $M_{3}=3\times4=12$ 
在 $\text{mod 3}$ 上 $\overline{ 20 }=2$，在 $\text{mod 4}$ 上 $\overline{ 15 }=3$，在 $\text{mod 5}$ 上 $\overline{ 12 }=3$。
於是 $a_{1}M_{1}y_{1}+a_{2}M_{2}y_{2}+a_{3}M_{3}y_{3}=2\times 20\times 2+1\times 15\times 3+3\times 12\times 3=233$ 
又 $233\equiv 53\ (\text{mod }60)$ 
$\implies x=53+60k, k\in \mathbb{Z}$ 