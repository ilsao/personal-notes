
# 威儀指定習題

1. A uniform wooden board of mass 20kg rests on two supports. A 30kg steel block is placed to the right of support A. How far to the right of A can the steel block be placed without tipping the board? 

```
<---11---><-3-><---8--->
                   口
------------------------
               i
```

2. A wheel of moment of inertia $60kg-m^2$ and radius 1.5m is rotating about an axis through its center with an angular velocity $\omega=30$rev/s. A brake is applied producing a normal force of 450N agianst the rim. The coefficient of friction between the wheel and the brake is 0.5. (a) How long will it take for the wheel to stop? (b) Calculate the work done by friction and show that this is equal to the change in the kinetic energy of the wheel.

Sol:
需要注意，(b) 中，位移的對位是 $\theta$ ！所以想要算真正的路徑長，需要用 $r\theta$ 求。

3. The torque of the motor is turned at right angles to the wheels by the differential gear. Assume that in low gear the angular velocity of the rear wheels is 0.1 that of the motor. If the motor has 200hp and is turning over at a rate of 1400rev/min, how much torque is delivered to the rear wheels?

Sol:
需要注意的是，這題英文會讀不懂。
首先將 hp 轉 watt：$200hp=200\times 746 W=149200W$。
然後求 $1400rev/min= \frac{140\pi}{3} rad$。
利用公式：$W=\tau\omega\implies{1}49200=\tau \cdot \frac{140\pi}{3}\implies \tau \approx 1018$。
因為傳動過去的功率沒有改變，但是 $\omega$ 變成 0.1 倍，那麼相對應的 $\tau$ 應該變為 10 倍。
所以答案：$\tau'\approx 10180$N-m。

4. A children's merry-go-round of radius 4m and mass 100kg has an 80kg man standing at the rim. The merry-go-round coasts on a frictionless bearing at 0.2rev/sec. The man walks inward 2m toward the center. That is the new rotational speed of the merry-go-round? What is the source of this energy? (The moment of inertia of a solid disk is $I=\frac{1}{2}mr^{2}$).

Sol:
這題有個要注意的地方，旋轉木馬的 $I$ 我們要用 $\frac{1}{2}mr^{2}$ 算，但是人的要當成質點算。
還有，能量的來源是人克服慣性向前施的功，轉變為旋轉的動能。