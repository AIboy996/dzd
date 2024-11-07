+++
title = '利用对称性求最值'
date = 2024-11-07T14:29:21+08:00
draft = false
tags = ["函数"]
+++

## 已知
$$
f(x)=\frac{1}{\cos(x)}+\frac{1}{\cos(\pi/3-x)}
$$
求$f(x)$的最小值，其中$x\in (0,\pi/2)$

<!--more-->

## 题解

### 作图
最直观的解法就是画个图看看：
<iframe src="https://www.desmos.com/calculator/kardcvzytj?embed" width="500" height="500" style="border: 1px solid #ccc" frameborder=0></iframe>

不难发现最小值就在$x=\pi/6$的时候取到最小值$f(\pi/6)=4/\sqrt{3}$。

实际上我们不需要精确的作图就可以知晓这个函数的大概形状，不难发现：
$$
f(x)=\frac{1}{\cos(x)}+\frac{1}{\cos(\pi/3-x)}
$$
是关于$x=\pi/6$对称的，例如$x=0$和$x=\pi/3$的取值是完全相同的。

而且，在$x>\pi/6$的时候，随着$x$的增大，$1/\cos x$不断增大，$1/\cos(\pi/3-x)$不断减小。可以想象，前者增大的幅度是超过后者的（因为在反比例函数中，靠近0的地方是很陡峭的，远离0的地方是很平缓的）。

所以，我们就可以大胆论断，$x=\pi/6$就是原函数的最小值点。

### 平移
根据上述观察，稍带技巧的解法是：
$$
y=\frac{1}{\cos(x)}+\frac{1}{\cos(\pi/3-x)}
$$
中，做换元$x=\pi/6-t$，$t\in (-\pi/3,\pi/6)$（实际上也就是平移函数图像）。

得到：
$$
y=\frac{1}{\cos(\pi/6-t)}+\frac{1}{\cos(\pi/6+t)}
$$

所以
$$
\begin{aligned}
y&=\frac{1}{\cos(\pi/6-t)}+\frac{1}{\cos(\pi/6+t)}\\\\
&=\frac{\cos(\pi/6-t)+\cos(\pi/6+t)}{\cos(\pi/6-t)\cos(\pi/6+t)}\\\\
&=\frac{\sqrt{3}\cos t}{(\sqrt{3}/2\cos t)^2-(1/2\sin t)^2}\\\\
&=\frac{\sqrt{3}\cos t}{\cos^2t-0.25}\\\\
&=\frac{\sqrt{3}}{\cos t-0.25/\cos t}
\end{aligned}
$$
显然
$$
g(s)=\frac{\sqrt{3}}{s-0.25/s}
$$
是关于$s$单调减的。

所以当且仅当$t=0$时，$s=\cos t$取最大值$1$，原函数$y=g(\cos t)$取到最小值。

也即是$x=\pi/6$时原函数取到最小值$4/\sqrt{3}$。

这个解法当中第一步的换元操作是至关重要的。这么换是为了增加函数的对称性。

### 导数
如果读者有微积分的背景，那么这题也是易如反掌。
$$
y=\frac{1}{\cos(x)}+\frac{1}{\cos(\pi/3-x)}
$$
只需要求它的导数：
$$
y'=\frac{\sin x}{\cos^2x}-\frac{\sin(\pi/3-x)}{\cos^2(\pi/3-x)}
$$
令导数为0，可以得到极值点的方程：
$$
\sin x\cos^2(\pi/3-x)=\cos^2x\sin(\pi/3-x)
$$
不难得到在$(0,\pi/2)$上有唯一的极值点$x=\pi/6$，并且在它的左侧导数小于0，在它的右侧导数大于0，从而这就是所求函数的最小值点。
