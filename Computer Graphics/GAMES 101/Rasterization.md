# Perspective Projection

上篇筆記中有些東西我們還沒講，現在補充下哈。

在上一篇筆記中，我們在正交投影中提到了我們會把一個長方體變換為一個正立方體。而該長方體是由長寬高定義的，但是在此我們提出一個實際在使用的定義方式。

我們使用 field-of-view (fovY) 與 aspect ratio (寬 / 高) 定義。

考慮下圖情況，這是用側面去看該長方體。

![[Computer Graphics/pic/GAMES 101/Rasterization/1.png]]

我們可以列出一些關係，可以幫助我們計算：

$$
\tan\left( \frac{\text{fovY}}{2} \right)=\frac{t}{|n|}\quad \text{aspect}=\frac{r}{t}
$$

# What's after MVP? 

當我們做完 MVP 後，我們可以得到一個正立方體。然後呢？我們想要把它映射到螢幕上。

想要把東西映射到螢幕上，我們必須給螢幕定義一個螢幕空間。那麼我們就令原點處於螢幕的最左下角，$+x$ 向右，$+y$ 向上。

我們還定義一個像素的座標為該像素左下角的座標，而像素的正中心為該像素座標 $(x,y)$ 各自偏移 $0.5$。也就是說 $(x+0.5, y+0.5)$。

那麼，我們現在的任務就變成了將 $[1,1]^{2}$ 映射到 $[0,\text{width}]\times[0,\text{height}]$ 上。

注意到，這個變換與 $z$ 座標無關。我們可以得出此變換的矩陣：

$$
\begin{bmatrix}
\frac{\text{width}}{2} & 0 & 0 & \frac{\text{width}}{2} \\
0 & \frac{\text{height}}{2} & 0 & \frac{\text{height}}{2} \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
$$

# Canonical Cube to Screen

# Triangles - Fundamental Shape Primitives

# Sampling

# Aliasing