+++
title = '极值点偏移'
date = 2025-01-01T21:50:10+08:00
draft = false
tags = ["导数"]
+++

## 已知
$x_1,x_2$是$e^x = kx$的两根，求$k$的范围，并且证明：
$$
x_1+x_2 > 2
$$
<!--more-->

## 题解

只需要考虑$y=k$和$y=\frac{e^x}{x}$的交点即可，如图所示：

<iframe src="https://www.desmos.com/calculator/1xuu8eunos?embed" width="500" height="500" style="border: 1px solid #ccc" frameborder=0></iframe>

当且仅当$k\gt 1$的时候，图像有两个交点。

实际上令$f(x)=\frac{e^x}{x}$，那么
$$
f'(x) = \frac{e^x(x-1)}{x^2}
$$

所以$f$在$(-\infty, 0)$单调递减，在$(0, 1)$单调递减，在$(1,+\infty)$单调递增。

接下来证明$x_1+x_2>2$，这是经典的极值点偏移问题。

### 参数化
第一种方法是寻找一个参数同时表示$x_1$和$x_2$。

这里我们可以设$t=x_1 / x_2$，那么根据：
$$
k = \frac{e^{x_1}}{x_1}= \frac{e^{x_2}}{x_2}
$$
立即得到：
$$
t = \frac{x_1}{x_2} = \frac{e^{x_1}}{e^{x_2}} = e^{x_1-x_2}
$$
所以：
$$
x_1-x_2 = \log t
$$

结合
$$
x_1 / x_2 = t
$$
就可以解出
$$
\begin{aligned}
x_1 = \frac{t\log t}{t-1}\\\\
x_2 = \frac{\log t}{t-1}
\end{aligned}
$$
那么要证明的就是：
$$
x_1+x_2 = \frac{(t+1)\log t}{t-1} \gt 2
$$
利用导数不难证明
$$
\frac{t+1}{t-1}\log t \gt 2
$$
这个不等式是恒成立的。

### 构造函数（作对称）
另外一种经典的办法是利用函数单调性证明。

不妨假设$x_1\lt x_2$，从而$0\lt x_1 < 1 < x_2$，这时候$x_2,2-x_1$都是大于1的，那么
$$
f(x_2) > f(2-x_1) \iff x_2 > 2-x_1
$$

而我们知道
$$
f(x_1) = f(x_2) = k
$$
所以只需要证明：
$$
f(x_1)> f(2-x_1)
$$
也就是
$$
\frac{e^x}{x} \gt \frac{e^{2-x}}{2-x}\quad,\forall x \in (0,1)
$$

> 其实上面的问题转化过程在函数图像是显然的，我们实际上就是寻找了$x_1$关于$1$的**对称点的函数值**。
> <iframe src="https://www.desmos.com/calculator/hjk9pnctz1?embed" width="500" height="500" style="border: 1px solid #ccc" frameborder=0></iframe>
这个不等式的证明就很容易了：

$\forall x \in (0,1)$
$$
\frac{e^x}{x} \gt \frac{e^{2-x}}{2-x} \iff x-\log x \gt 2-x-\log(2-x)
$$

令
$$
g(x) = 2x-2-\log x +\log(2-x)
$$
那么只需要证明$g(x)\gt 0$恒成立即可，求导：
$$
g'(x) = 2-\frac{1}{x}-\frac{1}{2-x} = \frac{2x(2-x)-(2-x)-x}{x(2-x)} = \frac{-2(x-2)^2}{x(2-x)}\lt 0
$$
所以$g(x)$在$(0,1)$上单调递减，所以
$$
g(x) \gt g(1) = 0
$$
恒成立，证毕。

## 课后习题
> 来自：[Herself32's Blog](https://www.cnblogs.com/herself32-lyoi/p/14496733.html)

网上很容易找到类似的题目，放几个在这里：

### 1
函数$f(x)= \ln x+ax$，如果$f(x)$有两个零点$x_1,x_2$，求$a$的范围，并且证明：
$$
x_1x_2\gt e^2
$$

### 2

$x_1,x_2$是$e^x = kx$的两根，求$k$的范围，并且证明：
$$
x_1+x_2 > 2x_1x_2
$$

### 3
函数$f(x)= 0.5 x^2+(1-a)x-\ln x$，如果$f(x)$有两个零点$x_1,x_2$，求$a$的范围，并且证明：
$$
x_1+x_2 >2
$$

### 4
函数$f(x)=\ln x+(2-a)x-ax^2$，如果$f(x_1)=f(x_2)$并且$x_1\ne x_2$，证明：
$$
f'(\frac{x_1+x_2}{2})\lt 0
$$

### 5
函数$f(x)=\ln x-x-m$，其中$m\lt -2$。已知$f(x)$有两个零点，证明:
$$
x_1x_2^2\lt 2
$$