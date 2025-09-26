
# Velocity

Here we define **instantaneous velocity** as follow equation(notice that $r$ represents displacement):

$$
v=\lim_{ \Delta t \to 0 } \frac{\Delta r}{\Delta t}=\frac{dr}{dt}
$$

# Acceleration

We define instantaneous acceleration as:

$$
a=\lim_{ \Delta t \to 0 } \frac{\Delta v}{\Delta t}=\frac{dv}{dt}=\frac{d^{2}r}{dt^{2}}
$$

# Linear Motion

If $a$ remain constant, from the define of acceleration, we have:

$$
v=v_{0}+at
$$

proof:
$a=\frac{dv}{dt}\implies a\ dt=dv$ 
$v_{f}-v_{0}=\Delta v_{1}+\Delta v_{2}+\dots+\Delta v_{n}$ 
$a_{1}\Delta t+a_{2}\Delta t+\dots+a_{n}\Delta t$ 
= the area under the a-t curve
$\int_{t_{0}}^{t}a \ dt = \int_{v_{0}}^{v}dv$ 
Since $a$ is a constant,
$\int^{v}_{v_{0}}dv=a\int^{t}_{0}dt$ 
This integrates to 
$v-v_{0}=at$

And still, if $a$ remain constant, we have:

$$
\bar{v}=\frac{v+v_{0}}{2}
$$

and the displacement x becomes:

$$
x= \bar{v}t = \frac{v+v_{0}}{2}t
$$

The three equations above define linear motion for constant acceleration.

Let's obtain two auxiliary equations to help us solve the problem.

$$
v^{2}-v_{0}^{2}=2ax
$$

proof:
(I)
$v=v_{0}+at\implies t=\frac{v-v_{0}}{a}$ 
substitute $t$,
$x=\frac{v+v_{0}}{2}t=\frac{v+v_{0}}{2} \frac{v-v_{0}}{a}=\frac{v^{2}-v_{0}^{2}}{2a}$ 
(II)
$a=\frac{dv}{dt}=\frac{dv}{dx} \frac{dx}{dt}=\frac{dv}{dx}v$ 
$\implies\int^{v}_{v_{0}}v\ dv=a\int^{x}_{x_{0}}dx$ 
$=v^{2}-v_{0}^{2}=2a(x-x_{0})$ 

$$
x=v_{0}t+\frac{1}{2}at^{2}
$$

proof:
(I)
$v=v_{0}+at\implies x=\frac{v_{0}+at+v_{0}}{2}t=v_{0}+\frac{1}{2}at^{2}$ 
(II)
$v=\frac{dx}{dt}$ 
$\implies \int^{x}_{x_{0}}dx=\int^{t}_{0}v\ dt=\int^{t}_{0}(v_{0}+at)dt=v_{0}\int^{t}_{0}dt+a\int^{t}_{0}t\ dt$ 
$x-x_{0}=v_{0}t+\frac{1}{2}at^{2}$ 

# Projectile Motion

平拋運動符合以下方程：

$$
\begin{cases}
x=v_{0x}t \\
y=v_{0y}t+\frac{1}{2}a_{y}t^{2}
\end{cases}
$$

斜拋運動符合以下方程：

$$
\begin{cases}
x=v_{0}\cos \theta t \\
y=v_{0}\sin \theta t-\frac{1}{2}gt^{2}
\end{cases}
$$

以下給出一些重要結論的推導過程：

飛行時間：
$y$ 分量位移為零。
$0=v_{0}\sin \theta t - \frac{1}{2}gt^{2}\implies \boxed{t=\frac{2v_{0}\sin \theta}{g}}$ 

射程：
將 $t=\frac{2v_{0}\sin \theta}{g}$ 帶入 $x$ 分量方程。
$x=v_{0}\cos \theta\left( \frac{2v_{0}\sin \theta}{g} \right)=\boxed{\frac{v_{0}^{2}\sin 2\theta}{g}}$ 

最大高度：
將 $\frac{t}{2}$ 帶入 $y$ 分量方程。
$y=v_{0}\sin \theta\left( \frac{v_{0}\sin \theta}{g} \right)-\frac{1}{2}g\left( \frac{v_{0}^{2}\sin^{2}\theta}{g^{2}} \right)=\frac{v_{0}^{2}\sin^{2}\theta}{g}-\frac{v_{0}^{2}\sin^{2}\theta}{2g}$ 
$=\boxed{\frac{v_{0}^{2}\sin^{2}\theta}{2g}}$ 

# Tips

- 注意，當固定射程尋找斜拋角度時，$\theta$ 的值會有兩個，分別是 $\alpha$ 與 $90^{\circ}-\alpha$。

# 威儀指定習題

1. The position of a particle moving in a straight line is given by $x = 5+2t+4t^{2}-t^{3}$, where $x$ is in meters. (a) Find an expression for the instantaneous velocity as a function of time. (b) Find the position of the particle at $t=0,1,0.1$ and $0.01$ sec. (c) What is the average velocity between $t=0$ sec and $t=1$ sec, between $t=0$ sec and $t=0.1$ sec, between $t=0$ sec and $t=0.01$ sec (d) What is the instantaneous velocity at $t=0$ sec. (e) What conclusion do you draw from the answers in (c) and (d)?

Ans:
(a) $v(t)=t+8t-3t^{2}$
(b) $x(0)=5,x(1)=10,x(0.1)=5.239,x(0.01)=5.020399$ 
(c) $5,2.39,2.0399$ 
(d) $2m/s$
(e) 當時間間隔縮短，時間變化率變小。這正符合極限的定義。

2. A car moving at 25m/s strikes a tree, and the tree is seen to dent the front by 0.5m. Assume that the deceleration of the car was constant. Find the deceleration and time it took the car to stop.

Ans:
$a=625$ m/s
$t=\frac{1}{25}$ s

3. An electron is set in motion horizontally with a velocity $v_{x}=4 \times 10^{6}$ m/s. How far will it fall while traveling a horizontal distance of 10m?

Ans:
$y \approx \frac{1}{32}\times 10^{-9}$ m

4. An artillery gunner wishes to have a projectile land at a point on level ground 20,000 m away from the gun. If the muzzle velocity is 500m/s and the muzzle is assumed to be at ground level, at what angle above the horizontal should the gun be aimed?

Ans:
$\theta \approx \frac{57^{\circ}}{2} \text{ or } 90^{\circ}- \frac{57^{\circ}}{2}$ 

還好，都會。