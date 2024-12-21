+++
title = '四次方程韦达定理'
date = 2024-12-21T14:03:29+08:00
draft = false
tags = ["复数","方程"]
+++

## 已知
方程
$$
f(x)=x^4+a_3x^3+a_2x^2+a_1x+a_0=0
$$
有四个根$z_1,z_2,z_3,z_4$，并且这四个根在复平面上恰好是某个单位圆内接正方形的顶点。问在1到2024的范围内，有多少个互不相等的整数组合$\\{a_0,a_1,a_2,a_3\\}$可以满足条件？
<!--more-->

## 题解

实系数方程取共轭依然为0：
$$
f(x)=0 \iff f(\bar x) = 0
$$

所以方程的四个根要么是实根，要么是成对出现的共轭复根。

所以方程的四个根在复平面上一定**关于实数轴对称**（要么本身在实轴上，要么共轭——也就是关于实轴对称）。

根据题设，四个根恰好是某个单位圆内接正方形的顶点，所以根的分布要么是：
<iframe src="https://www.desmos.com/calculator/vwb5h39hq2?embed" width="500" height="500" style="border: 1px solid #ccc" frameborder=0></iframe>

要么是：
<iframe src="https://www.desmos.com/calculator/x5r1gn3kxj?embed" width="500" height="500" style="border: 1px solid #ccc" frameborder=0></iframe>

不妨设单位圆的圆形是$(a,0)$。

### Case1
<iframe src="https://www.desmos.com/calculator/vwb5h39hq2?embed" width="500" height="500" style="border: 1px solid #ccc" frameborder=0></iframe>

这时候，不难发现$z_{1,2,3,4}$就是下面方程的四个根：
$$
(z-a)^4=1
$$

> 把单位圆左移到原点，那么四个根其实就是1的四次方根。

直接展开就得到：
$$
z^4-4az^3+6a^2z^2-4a^3z+a^4-1=0
$$

所以：
$$
\begin{aligned}
&a_0 = a^4-1\\\\
&a_1 = -4a^3\\\\
&a_2 = 6a^2\\\\
&a_3 = -4a
\end{aligned}
$$

### Case2
<iframe src="https://www.desmos.com/calculator/x5r1gn3kxj?embed" width="500" height="500" style="border: 1px solid #ccc" frameborder=0></iframe>

这时候，不难发现$z_{1,2,3,4}$就是下面方程的四个根：
$$
(\phi (z-a))^4=1, \quad \phi = e^{\frac{\pi}{4}i} = \frac{\sqrt{2}}{2}+\frac{\sqrt{2}}{2}i
$$

我们知道$\phi^4=-1$，所以这方程可以化简为：
$$
(z-a)^4=-1
$$
直接展开就得到：
$$
z^4-4az^3+6a^2z^2-4a^3z+a^4+1=0
$$

所以：
$$
\begin{aligned}
&a_0 = a^4+1\\\\
&a_1 = -4a^3\\\\
&a_2 = 6a^2\\\\
&a_3 = -4a
\end{aligned}
$$

> 其实一些同学来说，还是很难发现的？
> 
> 实际上，从我们之前的Case1出发，这里的根就是以$(a,0)$为圆心**旋转**了$\frac{\pi}{4}$。这在复平面上就对应于乘以$\phi = \frac{\sqrt{2}}{2}+\frac{\sqrt{2}}{2}i$
>


又或者，我们从**单位圆八等分点**的角度来理解：
$$
(z-a)^8=1
$$
有两组解：
$$
(z-a)^4=\pm 1
$$
分别对应于我们这里的Case1和Case2

### 最后一步

综上所述：

$$
\begin{aligned}
&a_0 = a^4\pm1\\\\
&a_1 = -4a^3\\\\
&a_2 = 6a^2\\\\
&a_3 = -4a
\end{aligned}
$$

结合1-2024的范围，很容易知道$a$取值只能是$-2,-3,-4,-5,-6$，因此总计只有十组$\\{a_0,a_1,a_2,a_3\\}$可以满足条件。