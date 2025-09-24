
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