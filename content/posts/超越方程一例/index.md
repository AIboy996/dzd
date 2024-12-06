+++
title = '超越方程一例'
date = 2024-12-06T18:43:30+08:00
draft = false
tags = ["导数","函数","方程"]
+++

## 已知
$f(x)=xe^{-x}$以及$g(x)=x^{-1}\ln x$

如果$y=a$和$y=f(x)$以及$y=g(x)$共有三个交点$(x_1,a), (x_2,a), (x_3,a)$
且$ x_1 \lt x_2 \lt x_3 $
证明：
$$
x^2_2 = x_1x_3
$$
<!--more-->

## 题解

<iframe src="https://www.desmos.com/calculator/kgdmqavbox?embed" width="500" height="500" style="border: 1px solid #ccc" frameborder=0></iframe>

图像很容易通过导数绘制。

不难证明，$f$和$g$的图像在$(1,e)$之间有唯一的交点$B$，实际上这个交点就是$(x_2,a)$。

也就是说：
$$
\frac{x_1}{e^{x_1}} = \frac{x_2}{e^{x_2}} = a = \frac{\ln x_2}{x_2}= \frac{\ln x_3}{x_3}
$$

注意到：
$$
a ={\color{red}  \frac{x_2}{e^{x_2}} = \frac{\ln e^{x_2}}{e^{x_2}}}
$$
也就是说：
$$
e^{x_2}
$$
是方程
$$
\frac{\ln x}{x} = a 
$$
的一个根，而我们知道这个方程只有两个根$x_2,x_3$。

根据大小关系（$e^{x_2} \gt x_2$）我们知道：
$$
e^{x_2} = x_3
$$

同理：
$$
e^{x_1} = x_2
$$
于是：
$$
\begin{aligned}
&\frac{x_2}{e^{x_2}} = a = \frac{\ln x_2}{x_2}\\\\
\implies & x^2_2 = e^{x_2}\ln x_2\\\\
\implies & x^2_2 = x_3\ln(e^{x_1}) = x_1x_3
\end{aligned}
$$
证毕。