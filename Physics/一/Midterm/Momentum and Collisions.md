
# Center of Mass

我們定義兩個物體組成的系統的質心如下：

如果重量 $m_{1}$ 的物體距離質心 $a$，重量 $m_{2}$ 的物體距離質心 $b$，則：

$$
m_{1}a=m_{2}b
$$

如果將物體放在座標軸上，則 $a=x_{cm}-x_{1}, b=x_{2}-x_{cm}$。

帶回 $m_{1}(x_{cm}-x_{1})=m_{2}(x_{2}-x_{cm})$，整理得到：

$$
x_{cm}= \frac{m_{1}x_{1}+m_{2}x_{2}}{m_{1}+m_{2}}
$$

這種關係對任意多個物體接成立，通用形式為：

$$
x_{cm}= \frac{\sum_{k=1}^{n}m_{k}x_{k}}{\sum_{k=1}^{n}m_{k}}
$$

因為我們有 $\sum_{k=1}^{n}m_{k}=M$，所以：

$$
x_{cm}= \frac{1}{M}\sum_{k=1}^{n}m_{k}x_{k}
$$

以此類推，如果該物體存在於三維空間，則質心為各軸分量依公式求解。

# Motion of the Center of Mass

由上述公式，我們可以改寫為：

$$
Mx_{cm}=\sum _{k=1}^{n}m_{k}x_{k}
$$

然後，對時間微分：

$$
M \frac{dx_{cm}}{dt}=\sum_{k=1}^{n}m_{k} \frac{dx_{k}}{dt}\implies Mv_{cm}=\sum_{k=1}^{n}m_{k}v_{cm}
$$

可以看到，如果將質心視為一個重量為 $M$ 的物體，則其動量為整個系統的動量總和。

然後，如果我們繼續對時間微分，我們有：

$$
M \frac{dv_{cm}}{dt}=\sum_{k=1}^{n}m_{k} \frac{dv_{cm}}{dt}\implies Ma_{cm}=\sum_{k=1}^{n}m_{k}a_{k}=\sum_{k=1}^{n}F_{k}
$$

同時，由於牛頓第三定律，我們還知道存在系統中的內力必定有一個大小相等方向相反的作用力抵銷。由於系統中內力的合力為零，所以此處的力的總和為外力總和。

# Momentum and its Conservation

在此，我們將動量簡寫為 $p$。

由第四章所說，我們有：

$$
F\Delta t=\Delta p
$$

也就是說，如果不施力的話，動量守恆：

$$
p_{0}=p_{f}
$$

那麼，對於質心來說此結論仍然成立，因為我們可以將質心視為一個質量為 $M$ 的物體。

所以，在**不受外力**的情況下，動量守恆。(內力合總是為零)

也就是：

$$
\left( \sum_{k=1}^{n}p_{k} \right)_{\text{before}}=\left( \sum_{k=1}^{n}p_{k} \right)_{\text{after}}
$$

但這不代表系統中每個物體的動量皆為定值，這些物體的動量會因為內力而改變。

# Collisions

碰撞分為兩類：
- 彈性碰撞：動能守恆，沒有能量進出系統。
- 非彈性碰撞：非動能守恆，有能量減少。

## Elastic Collisions

以下我們來推導當質量差距極大時，碰撞後速度的變化。

假設 $M\gg m$。

首先，使用動量守恆：

$$
mv_{0}+MV_{0}=mv_{f}+MV_{f}\implies M(V_{0}-V_{f})=m(v_{f}-v_{0})
$$

然後，使用動能守恆：

$$
\frac{1}{2}mv_{0}^{2}+\frac{1}{2}MV_{0}^{2}=\frac{1}{2}mv_{f}^{2}+\frac{1}{2}MV_{f}^{2}\implies M(V_{0}^{2}-V_{f}^{2})=m(v_{f}^{2}-v_{0}^{2})
$$

展開：

$$
M(V_{0}-V_{f})(V_{0}+V_{f})=m(v_{f}-v_{0})(v_{f}+v_{0})
$$

然後將上式除以 $M(V_{0}-V_{f})=m(v_{f}-v_{0})$，得到：

$$
V_{0}+V_{f}=v_{f}+v_{0}
$$

我們在此假設 $V_{0}=0$，帶回第一條式子：

$$
-M(v_{f}+v_{0})=m(v_{f}-v_{0})\implies v_{f}=-v_{0} \frac{(M-m)}{M+m}
$$

因為 $M\gg m$，那麼 $v_{f} \approx v_{0}$。

在解彈性碰撞的題目時，大概率動量守恆與動能守恆都要用到喔！

通常先 (1) 使用動量守恆推速度，然後 (2) 帶入動能守恆求質量。

我們總結一下彈性碰撞的幾個情況：

![[Pasted image 20251008163258.png]]

跟你說說第三點是怎麼推的吧！

我們要站在大質量粒子的角度，且使用相對速度的概念。我們將大質量物體視為靜止，那麼就相等於小質量粒子撞向大質量粒子，然後以 $v$ 的速度反彈。如果我們從相對速度的視角返回真正的情況，則小質量物體的速度為 $v(\text{大質量粒子的速度})+v(小質量粒子的速度)=2v$。

![[Pasted image 20251008164626.png]]

讓我們說明 slingshot 的原理叭～

對於兩個互相靠近的物體，用大物體靜止的觀點來觀測相對速度，那麼小物體靠近的速度是 $v+ V$，反彈過後的速度應該也是 $v+U$，但是方向相反。

但是捏，重點就在這。雖然相對速度大小相同，但是轉到實際速度時，方向十分重要。因此，轉到實際速度時，小物體的速度是 $v+V+V=v+2V$。

如果還是不懂，可以去看威儀的影片 6-2 第 30 分鐘。

## Inelastic Collisions

非彈性碰撞必會損失動能。

如果兩個東東碰撞後黏在一起，那麼損失的動能會最大。

如果兩個東東碰撞後沒黏在一起，但仍屬於非彈性碰撞時，雖然會損失動能，但是捏，不是最大滴。

# 威儀指定習題

1. Three boys stand on a 10kg wagon resting on a frictionless horizontal surface. The boys take turns running off the same end of the wagon with a velocity of 1.5/sec relative to the wagon. The mass of each of the boys is 40kg. What is the final velocity of the wagon? 

Sol:
ASKKKKKKKKK

2. A 2kg block rests on the ground. The coefficient of friction between the block and the ground is 0.4. A man fire a 0.01kg bullet parallel to the ground. It lodges in the block, and the block and bullet are observed to slide 2m before coming to rest. What was the velocity of the bullet?

Sol:
分兩步，首先假設 $v_{b}$ 為子彈初速度，然後假設 $v$ 為子彈射入木塊後二者共同的速度。
然後利用第三章的公式計算由摩擦力引起的加速度，利用位移與加速度就可以算 $v$，然後反推 $v_{b}$。
這題還有一個法二，就是讓射入後動能等於摩擦力所作的功。

# 重要例題

1. A fire hose delivers water at the rate of 20kg/sec with a speed of 25m/sec. A riot police officer uses the hose to control an unruly crowd. The water from the hose strikes a person horizontally and then falls down to the ground. What is the average force experienced by that person?

Sol:
$F=\dot{m}(v_{\text{in}}-v_{\text{out}})=20 \times 25=500N$ 

2. An atom of mass 10u strikes a stationary atom of mass M and rebounds elastically with one half its original velocity. What is the mass of the atom it struck?

Sol:
這題要使用動量守恆與動能守恆。
首先利用動量守恆得到：
$10\times v=10\left( -\frac{1}{2}v \right)+Mv'\implies v'=\frac{15v}{M}$ 
帶入動能守恆公式：
$\frac{1}{2}10v^{2}=\frac{1}{2}10\left( -\frac{1}{2}v \right)^{2}+\frac{1}{2}M\left( \frac{15v}{M} \right)^{2}\implies M=30$ 