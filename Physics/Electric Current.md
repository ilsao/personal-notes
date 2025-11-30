
# Motion of Charges in an Electric Field

結合牛頓第二運動定律與電場公式，我們有：

$$
F=qE=ma\implies a=\frac{qE}{m}
$$

需要注意的是，計算時 $q$ 需要取絕對值。因為電場中的方向與實際方向不同，所以正負號可以計算後一判斷加上。

# Electric Current

電子在實際運動中，會因為與原子碰撞，導致加速 -> 碰撞 -> 再加速 -> 碰撞，的一系列加減速使得速度一直在變化。

我們使用**飄移速度(drift velocity)** 表示平均速度。

我們定義電流 $i$ 為單位時間內通過某截面的電荷量：

$$
i= \frac{dq}{dt}
$$

電流以安培(Ampere)為單位 (SI 制)，而 $1\text{ A}$ 超大。

考慮如下場景：

![[Pasted image 20251130224328.png]]

設：
- 每單位體積有 $N_{p}$ 個正電荷，飄移速度為 $v_{p}$，每個電荷帶電量 $q_{p}$。
- 每單位體積有 $N_{n}$ 個負電荷，飄移速度為 $v_{n}$，每個電荷帶電量 $q_{n}$。

則圖中陰影部分面積包含的正電荷帶電量為：

$$
\Delta q_{p}=q_{p}N_{p}Av_{p}\Delta t
$$

代入電流公式：

$$
i_{p}=\frac{\Delta q_{p}}{\Delta t}=q_{p}N_{p}Av_{p}
$$

同理可得負電荷的電流：

$$
i_{n}=q_{n}N_{n}Av_{n}
$$

需要注意的是，因為 $q_{n}$ 與 $v_{n}$ 都是負的，所以最終負電荷向左流的效果等於正電荷項右流的效果。

也就是說，總電流為：

$$
i=i_{p}+i_{n}=(q_{p}N_{p}Av_{p})+(q_{n}N_{n}Av_{n})
$$

我們把單位**截面積(cross-section)** 的電流定義為**電流密度(current density)**：

$$
J=\frac{i}{A} \ (\text{A/m}^{2})
$$

# Resistance and Resistivity

# Resistance in Series and Parallel

# Kirchhoff's Rule

# Power Dissipation By Resistors