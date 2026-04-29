# Bloch's Theorem

對自由電子來說：

$$
\chi(x)=e^{\pm ikx}
$$

在晶體中，離子規律排列。所以位能滿足：

$$
E_{p}(x)=E_{p}(x+d)
$$

Bloch 定理說這種**週期性位能中**，波函數為：

$$
\boxed{\chi(x)=u_{k}(x)e^{ikx}\quad u_{k}(x)=u_{k}(x+d)}
$$

可想成：平面波 $\times$ 週期性波

而機率密度：

$$
\begin{align}
|\chi(x)|^{2} & =\chi^{*}(x)\chi(x) \\
 & =u^{*}_{k}(x)e^{-ikx}\cdot u_{k}(x)e^{ikx} \\
 & =u^{*}_{k}(x)u_{k}(x)
\end{align}
$$

又：

$$
|\chi(x+d)|^{2}=|u_{k}(x+d)|^{2}=|u_{k}(x)|^{2}=|\chi(x)|^{2}
$$

所以：電子出現在 $x$ 與 $x+d$ 的機率相同。

# The Kronig-Penny Model

考慮一個正電離子 $q$ 與距離 $x$ 的電子，電子的位能為：

$$
E_{p}(x)=-\frac{1}{4\pi\epsilon_{0}} \frac{q|e|}{x}
$$

若多放置幾個離子，位能如下圖：

![[Pasted image 20260425234307.png|300]]![[Pasted image 20260425234331.png|332]]![[Pasted image 20260425234355.png|412]]

為了化簡計算，Kronig-Penny 模型將其視為一系列週期排列的位能井。

![[Pasted image 20260425234549.png|750]]

其中，週期為 $d=b+c$，定原點 $x=0$。

我們對區域 I (井中) 與 II (位能障) 分別討論。

## Region I

井中位能 $E_{p}=0$，解薛丁格方程：

$$
-\frac{\hbar^{2}}{2m} \frac{d^{2}\chi_{I}}{dx^{2}}=E\chi_{I}
$$

整理後得：

$$
\frac{d^{2}\chi_{I}}{dx^{2}}+\gamma^{2}\chi_{I}=0\quad \gamma=\sqrt{ \frac{2mE}{\hbar^{2}} }
$$

由 Bloch 定理 $\chi_{I}=u_{I}(x)e^{ikx}$ 代入解得：

$$
u_{I}(x)=Ae^{i(\gamma-k)x}+Be^{-i(\gamma+k)x}
$$

## Region II

在位能障 $E_{p}=E_{p_{0}}$，解薛丁格方程：

$$
-\frac{\hbar^{2}}{2m} \frac{d^{2}\chi_{II}}{dx^{2}}+E_{p_{0}}\chi_{II}=E\chi_{II}
$$

整理後得：

$$
\frac{d^{2}\chi_{II}}{dx^{2}}-\xi^{2}\chi_{II}=0\quad \xi =\sqrt{ \frac{2m(E_{p_{0}}-E)}{\hbar^{2}} }
$$

由 Bloch 定理 $\chi_{ＩI}=u_{II}(x)e^{ikx}$ 代入解得：

$$
u_{II}(x)=Ce^{(\xi-ik)x}+De^{-(\xi+ik)x}
$$

為了使波函數 well-behave：
1. **波函數連續**：
	- $\chi_{I}\left( \frac{c}{2} \right)=\chi_{II}\left( \frac{c}{2} \right)$ 
	- $\frac{d\chi_{I}}{dx}\left( \frac{c}{2} \right)=\frac{d\chi_{II}}{dx}\left( \frac{c}{2} \right)$ 
2. **週期性條件**：
	- $u_{I}\left( -\frac{c}{2} \right)=u_{II}\left( b+\frac{c}{2} \right)$ 
	- $\frac{du_{I}}{dx}\left( -\frac{c}{2} \right)=\frac{du_{II}}{dx}\left( b+\frac{c}{2} \right)$ 

> [!note]
> 注意到週期性條件中，我們用 
> $u_{I}\left( -\frac{c}{2} \right)=u_{II}\left( b+\frac{c}{2} \right)$，
> 因為這兩點相差一個週期 $a=b+c$，由 Bloch 條件 $u(x+a)=u(x)$ 可知兩者必須相等。
> 由於 $-\frac{c}{2}$ 位於區域 I，而 $b+\frac{c}{2}$ 位於下一個週期中的區域 II，
> 因此分別用 $u_I$ 與 $u_{II}$ 表示。
> 另外，選擇邊界點只是為了方便與區域解做匹配，並不是等號成立的原因。

四個條件解四個變量，解得：

$$
\boxed{P \frac{\sin(\gamma d)}{\gamma d}+\cos(\gamma d)=\cos(kd)}
$$

其中：

$$
\boxed{P=\frac{mE_{p_{0}}bd}{\hbar^{2}},\gamma=\sqrt{ \frac{2mE}{\hbar^{2}} }}
$$

## Allowed and Forbidden Energy Bands

由上面那個含 $P$ 方程：
- 左邊與**能量**有關 ($\gamma=\sqrt{ \frac{2mE}{\hbar^{2}} }$)
- 右邊與**動量**有關 ($\lambda=\frac{h}{p},k=\frac{2\pi}{\lambda}=\frac{p}{\hbar}$)

可視為：

$$
f(\gamma d)=\cos(kd)\implies-1\leq f(\gamma d)\leq1
$$

於是當 $f(\gamma d)$ 不在 $[-1,1]$ 時，方程無解，存在**能隙(forbidden bands, band gaps)**。否則有解，存在**能帶(allowed band)**。

![[Pasted image 20260426002120.png|408]]

## Dispersion Relation

**色散關係：$E$ 與 $k$ 間的關係**。

對自由粒子：

$$
\boxed{E=\frac{\hbar^{2}k^{2}}{2m}}
$$

是一個拋物線。

在 Kronig-Penny Model 中，由 $P \frac{\sin(\gamma d)}{\gamma d}+\cos(\gamma d)=\cos(kd)$ 可畫出：

![[Pasted image 20260426002912.png|573]]

注意到能帶的不連續處出現在 $k=\pm \frac{n\pi}{d}$ 

Kronig-Kenny Model 有以下問題：
- 太數學了，沒有物理意義
- 沒有給出能帶中的能態數 (其實際上為準連續)

# Tight-Binding Approximation

Tight-Binding Approximation：假設電子主要局域於原子附近，其波函數可由各原子軌域線性組合而成，並透過與鄰近原子的重疊形成能帶結構。

若在一個無限深位能井中，波函數 $\chi$ 為滿足薛丁格方程的一個解，則波函數 $-\chi$ 也是一個解。因為解總是線性的 (函數乘以某個常數仍是一個解)。

從物理意義上看，機率密度為 $|\chi|^{2}$，會將負號抹去。所以二者的物理意義相同。

考慮兩個距離很遠的有限位能井 (以模擬晶體)，因為波函數沒有重疊，所以就像兩個獨立的位能井般。此時能量是簡併的。

![[Pasted image 20260426135717.png|328]]

> [!note]
> 注意到 $\chi_{B}$ 與 $\chi_{C}$ 是不相同的波函數，所以二者處於不同量子態。
> 但是兩個位能井完全相同，所以能量相同。
> $\implies$ 簡併

因為兩個井屬於同一個系統，所以會有波函數同時描述他們的行為。我們分為兩類 ($a$ 為 normalization constant)：
- symmetric：$\chi_{S}=a(\chi_{B}+\chi_{C})$ 
- antisymmetric：$\chi_{A}=a(\chi_{B}-\chi_C)$ 

之所以不同排列屬於同類，是因為他們取模平方後相等。

![[Pasted image 20260426140558.png|605]]

![[Pasted image 20260426140610.png|599]]

觀察到兩井距離遠時，$\chi_{S}$ 與 $\chi_{A}$ 簡併 (模平方行為相同)。

逐漸靠近兩井，波函數開始重疊。

$\chi_{S}$ 表現的像一個寬度 $2a$ 的位能井的**基態**波函數：

![[Pasted image 20260426140850.png|528]]

$\chi_{A}$ 表現的像一個寬度 $2a$ 的位能井的第一**激發態**函數：

![[Pasted image 20260426140900.png|524]]

於是，當兩井足夠接近時，簡併態會變成非簡併態，且 $\chi_{S}$ 的能量 $<$ $\chi_{A}$ 的能量。

我們用 $H$ 原子講解這種能量的變化。

考慮兩處於基態 ($1s$) 的 $H$ 原子：

![[Pasted image 20260426141409.png|337]]

兩原子逐漸接近時，會有兩種情況出現：

![[Pasted image 20260426141448.png|514]]

- $\chi_{S}$：電子容易出現在兩原子核間，束縛能較大，能量較低。
- $\chi_{A}$：電子不易出現在兩原子核間，束縛能較小，能量較高。

現考慮六個氫原子，他們可以形成多少個不同的態？

我們有六個波函數 (視為正交基底)，所以會有六種互相獨立的線性組合 (線代沒忘吧)。

![[Pasted image 20260426141729.png|383]]

![[Pasted image 20260426143210.png|265]]

我們用曲率來判別波函數能量的大小，**曲率越高的波函數，波函數包含更多較大的 $k$ 來描述。越大的 $k$ 表示越大的 $p$，動量越大則能量越大**。

推廣到 $N$ 個原子，會有 $N$ 個不同的能階。當 $N$ 接近現實晶體時 $\approx 10^{-23}$，能階間距 $\approx 10^{-23}\text{ eV}$。就會形成準連續的能帶。

![[Pasted image 20260426143233.png|343]]

觀察出：
- 能帶**寬取決於原子的接近程度**，越接近則越寬。
- **能階越高，能帶越寬**。因為較高能階的波函數較寬，電子有更大的機率出現在離原子核較遠處。造成波函數重疊較嚴重，能量差距較明顯。
- **能帶寬度獨立於原子數目 $N$**，因為距離較遠的兩個原子互相影響較少，能帶寬主要由相鄰原子間的耦合決定。

# Conductors, Insulators, and Semiconductors

電子要能導電，需滿足：
- 電子能躍遷到更高的能量態 (被加速)，且該態 allowed and empty。

通過上節的討論，**我們知道一個能帶有 $N$ 個能態，每個能態可放兩個電子，且每個 $m_{l}$ (不同 $m_{l}$ 有不同的波函數) 會展出一個能帶**。所以可放的電子數為：

$$
\boxed{2(2l+1)N}
$$

定義：
- valence band：電子填到的最高能帶
- conduction band：真正讓電子躍遷導電的能帶

## Na

Na：$1s^{2}2s^{2}2p^{6}3s^{1}$ 

![[Pasted image 20260426152125.png|330]]

施加電場後，$3s$ 的電子可以躍遷到更高能態，造成電流。

可以發現，此時 valence band 與 conduction band 是同一個 band。

## Mg

Mg：$1s^{2}2s^{2}2p^{6}3s^{2}$ 

看起來把 $3s^{2}$ 填滿了，電子沒法導電。但實際上，因為 $3s$ 與 $3p$ 的能帶有重疊，所以施加電場時 valence band 中的電子依舊可以越遷到更高能態，造成電流。

![[Pasted image 20260426152558.png|415]]

## C (Diamond)

C：$1s^{2}2s^{2}2p^{2}$ 

看起來能導電？但是能帶合久必分，分久必合。在兩原子過於靠近時，原本重疊的能帶會再次分離，形成混成軌域與**能隙(band gap，指 conduction band 與 valence band 之間的能量差)**。並且，可容納的電子數均分。

![[Pasted image 20260426152854.png|342]]

> [!note]
> $2p$ 最先分裂出能帶，因為波函數最寬，最先開始與其他波函數重疊。

實際上鑽石應該如下填：

![[Pasted image 20260426153200.png|540]]

valence band 與 conduction band 中間隔著巨大能隙，電子難以越遷故而不導電。

## Si

Si/Ge 這類半導體，依舊是混成軌域。但是其間的能隙較小，在將電子激發後能導電。

![[Pasted image 20260426153348.png|510]]

$E_{g}$ 的大小能夠決定一個材料是半導體還是絕緣體。

$E_{g}$：
- $C\approx 6\text{ eV}$ 
- $Si\approx 1.1\text{ eV}$ 
- $Ge\approx 0.7\text{ eV}$ 

在高溫下，某些電子從 valence band 跨越能隙被激發到 conduction band，在 valence band 中造成電洞，並使 conduction band 中包含自由電子。

總結：

![[Pasted image 20260426153930.png|740]]

# Effective Mass

回憶：
- 波包速度 $v=\frac{d\omega}{dk}$ 

又 $\lambda=\frac{2\pi}{k}=\frac{h}{p}\implies k=\frac{p}{\hbar}\implies dk=\frac{dp}{\hbar}$ 與 $\nu=\frac{\omega}{2\pi}=\frac{E}{h}\implies\omega=\frac{E}{\hbar}\implies d\omega=\frac{dE}{\hbar}$ 
$\implies v=\frac{d\omega}{dk}=\frac{dE}{dp}$ 代入 $p=\hbar k$ ：

$$
v_{\text{group}}=\frac{1}{\hbar} \frac{dE}{dk}
$$

我們使用量子 + 古典的觀念說明等效質量。

我們利用等效質量 $m^{*}$ 將電子處於晶體中所受的作用力考慮進去，於是：

$$
a=\frac{qE}{m^{*}}
$$

能量變化等於所受的功：$dE=dW=qE\ dx=qE\ \frac{dx}{dt}dt=qEv_{\text{group}}dt$ 

於是：

$$
\frac{dE}{dt}=qEv_{\text{group}}
$$

又 $a=\frac{dv}{dt}$ 
$=\frac{1}{\hbar} \frac{d}{dt}\left( \frac{dE}{dk} \right)=\frac{1}{\hbar} \frac{d}{dk}\left( \frac{dE}{dt} \right)$ 
$=\frac{1}{\hbar} \frac{d}{dk}(qEv)=\frac{qE}{\hbar} \frac{dv}{dk}$ 
$=\frac{qE}{\hbar^{2}} \frac{d^{2}E}{dk^{2}}$ 
$\implies qE=\frac{\hbar^{2}}{\frac{d^{2}E}{dk^{2}}}a$ 
於是：

$$
\boxed{m^{*}=\frac{\hbar^{2}}{\frac{d^{2}E}{dk^{2}}}}
$$

在 CFE 中，$\sigma$ 被修正為：$\sigma=\frac{q^{2}N\tau}{m^{*}}$ 

既然已經得出等效質量，我們用自由電子檢驗下：

自由電子能量 $E=\frac{\hbar^{2}k^{2}}{2m}$，等效質量 $m^{*}=\frac{\hbar^{2}}{\frac{d^{2}E}{dk^{2}}}=m$ 沒錯！

但是，對於晶體中的電子，等效質量可能：
- $m^{*}>m$ 
- $m^{*}<m$ 
- $m^{*}=\infty$ 
- $m^{*}<0$ 
- ...

注意到，對 $m^{*}<0$ 者，在電場下他們的加速方向與古典電子加速方向相反，具有相反的飄移速度。

![[Pasted image 20260426235642.png|242]]

![[Pasted image 20260426235724.png|618]]

觀察 $E-k$ 圖，分類討論：
- 曲率大於零 (開口向上)：$m^{*}>0$ 
- 曲率小於零 (開口向下)：$m^{*}<0$ 
- 對小 $k$：$m^{*}\approx m$ 
- 當斜率最大：$\frac{d^{2}E}{dk^{2}}=0\implies m^{*}=\infty$ 

![[Pasted image 20260427000446.png|883]]

## 為什麼會有負質量？

用 Bragg 反射理解：$2d\sin \theta=n\lambda$。

我們考慮 **Bragg 反射最強烈時的角度 $\theta=90^{\circ}$**，於是 $2d\sin \theta=2d=n\lambda=n\left( \frac{2\pi}{k} \right)\implies k=\frac{n\pi}{d}$ 時電子波會被反射。

1. $k$ 接近 $0$ 時：不滿足 Bragg 反射條件，不反射。$m^{*}>0$，與電場反向加速。
2. $k$ 接近能帶頂端時，$k=\frac{n\pi}{d}$：滿足反射條件，$m^{*}<0$，與電場同向加速。
3. $k$ 在能帶中間的某值：Bragg 反射與加速互相抵銷，$m^{*}=\infty$，停留在原地。

![[Pasted image 20260427001453.png|783]]

注意到：能帶下半段 (能量較小) 的等效質量 $m^{*}>0$，而上半段 $m^{*}<0$。

對導體：conduction band 與 valence band 是同一個，就算電子填到了 $m^{*}<0$ 的區域，在 $m^{*}>0$ 區域中的電子仍佔多數，所以仍會產生電流。

對非導體 / 半導體：conduction band 與 valence band 分離，$m^{*}>0$ 與 $m^{*}<0$ 各佔一半，沒有淨電流出現。

# Holes

電洞：valence band 中的一個空態。(電子被激發到 conduction band 了)

![[Pasted image 20260427004458.png]]

對理想半導體來說：自由電子的數量 = 電洞數量

本來一個完全填滿的能帶，電流為零。

$$
J_{\text{full}}=0
$$

若移除第 $i$ 個電子：

$$
J_{\text{remaining}}=J_{\text{full}}-J_{i}=-J_{i}
$$

於是剩下的系統電流就是原本電子 $i$ 電流的反向電流。

![[Pasted image 20260427004017.png|405]]

施加電壓後，電洞會被旁邊的電子擬補，從而使電洞反向傳播。

對單一電子 ($v_{i}$ 為飄移速度，可從 $E$ 算得)：

$$
J_{i}=-|e|v_{i}
$$

於是：

$$
J_{\text{remaining}}=+|e|v_{i}=|e|a_{i}\tau_{i}
$$

注意到 $a_{i}=-\frac{|e|E}{m^{*}_{i}}$，其中 $m_{i}^{*}<0$。所以：$a_{i}=\frac{|e|E}{|m_{i}^{*}|}$ 

$$
J_{\text{remaining}}=\frac{|e|^{2}E\tau_{i}}{|m^{*}_{i}|}
$$

就像一個 $m^{*}>0$ 且帶有正電的電荷。

回憶一下：Hall Effect

[[Magnetic Fields and Electromagnetic Waves#^698130]] 

![[Pasted image 20260427005414.png|495]]

![[Pasted image 20260427005513.png|205]]

注意到：

$$
\boxed{V_{H}=\left( \frac{1}{Nq} \right) \frac{iB}{d}=R_{H} \frac{iB}{d}}
$$

定義：$\frac{1}{N{q}}=R_{H}$ 為 Hall Coefficient。

$R_{H}>0$ ：正電荷在流動。

$R_{H}<0$：負電荷在流動。

![[Pasted image 20260427005828.png|598]]

注意到：半導體的 conductivity 與 resistivity 範圍都很大。(因為半導體的自由電子受熱激發，導電性受溫度影響)

# 威儀指定習題

![[Pasted image 20260427220443.png|711]]

Sol:
我把 $++-$ 與 $+--$ 錯誤的認為是兩種了。
![[Pasted image 20260427221254.png|469]]
注意到雖然有三種線性組合，但是第二種是錯誤的，因為他不左右對稱。
正確的 2nd level 應該是 + 0 -。

![[Pasted image 20260427222526.png|720]]

Sol:
![[08bcb1dd00b479d082e3bfe2dffc1788.jpg|292]]

![[Pasted image 20260428102603.png|831]]

Sol:
非導體：band gap 能量較大 (several $\text{eV}$)，通常可見光能量不足以達到 band gap 能量使電子激發。可見光照射時無法被吸收 $\implies$ 物體透明
半導體：band gap 能量較小 ($10^{-1}\sim10^{-4}\text{ eV}$)，可見光足以激發電子，但紅外線不足以激發。紅外線照射時無法被吸收 $\implies$ 物體在可見光下不透明，在紅外線下透明。
導體：沒有 band gap 且具有較高能量的空態，且量子態間能量差距極小。可吸收任意波長的光以躍遷到較高的空態。

![[Pasted image 20260428104506.png|715]]

Sol:
能量最高的可見光波長 $\approx 400\text{ nm}$ 且能量為 $E=\frac{1240}{400}=3.1\text{ eV}$ 
比所有上述物質的 energy gap 能量小，可見光無法被任意物質吸收 $\implies$ 全部在可見光下都透明。
使物質不透明的波長：
KCl: $\frac{1240}{7.6}$ 
KBr: $\frac{1240}{6.3}$ 
KI: $\frac{1240}{5.6}$ 

![[Pasted image 20260428105226.png|799]]

Sol:
(a)
注意這邊 $N=6\times 10^{23}\times\left( \frac{2.7}{26.98}\times 10^{6} \right)\times3$，因為是三價。
代入 $E_{F}=\frac{\hbar^{2}}{2m}(3N\pi^{2})^{2/3}\approx 11.6\text{ eV}$ 
(b)
直接用 $E_{F}'=\frac{\hbar^{2}}{m^{*}}(3N\pi ^{2})^{2/3}\propto \frac{1}{m^{*}}$ 
$\frac{E_{F}}{E_{F}'}=\frac{m^{*}}{m}=\frac{11.6}{12}\approx 0.97$ 
$\implies m^{*}=0.97m$ 其中 $m$ 為自由電子質量

# 威儀考古

1. 假設晶體中有N個鈉 請畫出Na($1s^{2} 2s^{2} 2p^{6} 3s^{1}$) 的價帶並標示出個數與 $E_{F}$ 

Sol:
![[Pasted image 20260428115348.png|348]]

2. 請解釋為何大部分的絕緣體都是透明的 (練習題 5)

3. (a) 請寫出Quantum Mechanic Free Electron Model和Kronig-Penny Model的基本假設有何不同? (b) 和Kronig-Penny Model相比，Tight Binding Approximation 的優點為何?

Sol:
(a)
QMFE Model：假設固體中位能為定值，電子視為自由電子。
Kronig-Penny Model：假設固體中有週期性位能，以描述晶格對電子的影響。
(b)
更具物理意義的表示能帶出現的原因
具體的說明能帶中有多少個量子態 ($N$ 個)，可放入多少電子 ($2N$ 個)。