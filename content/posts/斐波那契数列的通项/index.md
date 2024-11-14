+++
title = '斐波那契数列的通项'
date = 2024-11-14T10:17:24+08:00
draft = false
tags = ["数列"]
+++

## 已知

$$
a_{n+2}=a_{n+1}+a_n\quad \forall n \in \mathbb{N}^*
$$

以及
$$
a_1=a_2=1
$$
求通项公式

<!--more-->

## 题解

### 待定系数法

假设
$$
a_{n+2}-pa_{n+1} = q(a_{n+1}-pa_{n})
$$

其$p,q$是待定系数，满足：
$$
p+q=1\\\\
pq=-1
$$
这个方程显然有解：
$$
p= \frac{1\pm\sqrt{5}}{2},q=\frac{1\mp\sqrt{5}}{2}
$$

所以
$$
a_{n+1}-pa_{n}=q^{n-1}(a_2-pa_1) = q^n
$$

带入两组解得到：
$$
a_{n+1}-\frac{1+\sqrt{5}}{2}a_{n}= {\left(\frac{1-\sqrt{5}}{2}\right)}^n\\\\
a_{n+1}-\frac{1-\sqrt{5}}{2}a_{n}= {\left(\frac{1+\sqrt{5}}{2}\right)}^n
$$

作差即可得到：
$$
\sqrt{5}a_n = {\left(\frac{1+\sqrt{5}}{2}\right)}^n - {\left(\frac{1-\sqrt{5}}{2}\right)}^n
$$

也就得到了斐波那契数列的通项公式：
$$
a_n = \frac{1}{\sqrt{5}}\left[{\left(\frac{1+\sqrt{5}}{2}\right)}^n - {\left(\frac{1-\sqrt{5}}{2}\right)}^n \right]
$$

### 线性空间

我们先假设$a_1,a_2$是未知的。

那么所有满足递推关系：
$$
a_{n+2}=a_{n+1}+a_n\quad \forall n \in \mathbb{N}^* \tag{*}
$$

的数列$\\{a_n\\}$的集合，构成一个线性空间。

实际上：
$$
\begin{aligned}
&a_{n+2}\\\\
=& a_{n+1}+a_n \\\\
=& 2a_n + a_{n-1} \\\\
=& 3a_{n-1}+2a_{n-2}\\\\
=& 5a_{n-2}+3a_{n-3}\\\\
=&\cdots\\\\
=&f_{n+1} a_2+f_na_1
\end{aligned}
$$

也就是：
$$
a_{n+2} = f_{n+1} a_2+f_na_1
$$
其中$f_n$是$1,1,2,3,5,\cdots$斐波那契数列的第$n$项，是一个确定的数列。

从这个式子我们可以更清楚地看到：
$$
\vec a = (a_1,a_2) \to \\{a_n\\}
$$
存在一一对应的线性关系（$x \vec a + y \vec b \to \\{xa_n + y b_n\\}$）。

从而，$\\{a_n\\}$构成的集合和$\mathbb{R}^2$同构，是一个二维线性空间，$f_n$和$f_{n+1}$是它的一组基。

当然这组基不是很好看，我们可以寻求另外一组基。

递推关系(*)很容易找到等比数列解$a_n = x^n$：
$$
x^{n+2} = x^{n+1}+x^n
$$
也就是：
$$
x^2 = x+1
$$
所以
$$
a_n = {\left(\frac{1\pm\sqrt{5}}{2}\right)}^n
$$
是满足递推关系的两个数列。

显然他们线性独立：
$$
\alpha {\left(\frac{1+\sqrt{5}}{2}\right)}^n + \beta {\left(\frac{1-\sqrt{5}}{2}\right)}^n=0 \quad \forall n \iff \alpha=\beta=0
$$

于是可以作为$\\{a_n\\}$的一组基：
$$
a_n = \alpha {\left(\frac{1+\sqrt{5}}{2}\right)}^n + \beta {\left(\frac{1-\sqrt{5}}{2}\right)}^n
$$

于是我们就得到了递推关系(*)的一个通解（在等比数列基下的坐标表示）。

带入初始条件：$a_1=a_2=1$即可解得坐标$\alpha,\beta$。

从这个观点出发，我们可以解决一般情况下[常系数线性齐次差分方程](https://en.wikipedia.org/wiki/Recurrence_relation#difference_equation)的通解问题，本质上这是一个线性代数的问题。

### 生成函数

我们还可以使用生成函数来解决这个问题：
$$
f(x) = \sum_{n=0}^\infty a_nx^n
$$
> 补充定义$a_0=0$

那么根据递推关系(*)，我们知道：
$$
\begin{aligned}
&f(x) \\\\
= &\sum_{n=0}^\infty a_nx^n \\\\
= &a_0+a_1x+\sum_{n=2}^\infty a_nx^n\\\\
= &a_0+a_1x+\sum_{n=2}^\infty (a_{n-1}+a_{n-2})x^n\\\\
= &a_0+a_1x+x\sum_{n=2}^\infty a_{n-1}x^{n-1}+x^2\sum_{n=2}^\infty a_{n-2}x^{n-2}\\\\
= &a_0+a_1x+xf(x)+x^2f(x)\\\\
\end{aligned}
$$

带入初始条件$a_0=0,a_1=1$得到：
$$
f(x)=x+(x+x^2)f(x)
$$
于是斐波那契数列的生成函数为：
$$
f(x) = \frac{x}{1-x-x^2}
$$

做因式分解：
$$
f(x) = \frac{1}{\sqrt{5}}\left[ \frac{1}{1-\frac{1+\sqrt{5}}{2}x} - \frac{1}{1-\frac{1-\sqrt{5}}{2}x}\right]
$$

幂级数展开：
$$
f(x) = \frac{1}{\sqrt{5}}\left[ \sum_{n=0}^\infty (\frac{1+\sqrt{5}}{2}x)^n -\sum_{n=0}^\infty (\frac{1-\sqrt{5}}{2}x)^n \right]
$$
也就是：
$$
f(x) = \sum_{n=0}^\infty \frac{1}{\sqrt{5}}\left[(\frac{1+\sqrt{5}}{2})^n -(\frac{1-\sqrt{5}}{2})^n \right]x^n
$$

对比系数即可知道：
$$
a_n = \frac{1}{\sqrt{5}}\left[{\left(\frac{1+\sqrt{5}}{2}\right)}^n - {\left(\frac{1-\sqrt{5}}{2}\right)}^n \right]
$$

### 延迟算子

我们还可以用延迟算子来解决这个问题。

定义延迟算子：
$$
B a_n = a_{n-1}
$$

它是一个线性算子：
$$
B (xa_n+yb_n) = xa_{n-1}+yb_{n-1}
$$
并且是算子之间是可交换的：
$$
(a+bB)(c+dB)a_n = (c+dB)(a+bB)a_n
$$
定义：
$$
B^2 a_n = B(Ba_n) = a_{n-2}
$$

那么递推关系：
$$
a_{n+2}=a_{n+1}+a_n\quad \forall n \in \mathbb{N}^*
$$
可以写成：
$$
(1-B-B^2)a_n=0
$$

所以我们要求的数列就是算子多项式：
$$
f(B) = 1-B-B^2
$$
的Kernel。不难发现这个Kernel是一个二维线性空间。

> 这个多项式里的1理解为恒等映射：$1\cdot a_n \to a_n$

做因式分解：
$$
(1-\frac{1+\sqrt{5}}{2}B)(1-\frac{1-\sqrt{5}}{2}B)a_n = 0
$$

我们知道：
$$
(1-\frac{1\pm\sqrt{5}}{2}B)a_n = 0
$$
的解是等比数列：
$$
a_n = a_1(\frac{1\pm\sqrt{5}}{2})^{n-1}
$$

所以$a_n$的通解是：
$$
a_n = \alpha {\left(\frac{1+\sqrt{5}}{2}\right)}^{n-1} + \beta {\left(\frac{1-\sqrt{5}}{2}\right)}^{n-1}
$$

### 矩阵迭代

上述递推关系可以写成矩阵形式:
$$
\begin{bmatrix}
	1&1\\\\
	1&0
\end{bmatrix}
\begin{bmatrix}
	a_{n-1}\\\\
	a_{n-2}
\end{bmatrix}
=\begin{bmatrix}
	a_{n}\\\\
	a_{n-1}
\end{bmatrix}
$$
做相似对角化:
$$
M=\begin{bmatrix}
	1&1\\\\
	1&0
\end{bmatrix}
=\begin{bmatrix}
	\frac{1-\sqrt{5}}{2}&\frac{1+\sqrt{5}}{2}\\\\
	1&1
\end{bmatrix}
\begin{bmatrix}
	\frac{1-\sqrt{5}}{2}&0\\\\
	0&\frac{1+\sqrt{5}}{2}
\end{bmatrix}
\begin{bmatrix}
	\frac{1-\sqrt{5}}{2}&\frac{1+\sqrt{5}}{2}\\\\
	1&1
\end{bmatrix}^{-1}
$$
有：
$$
A_n=M^nA_0
$$
也就是：
$$
\begin{aligned}
\begin{bmatrix}
	a_{n}\\\\
	a_{n-1}
\end{bmatrix}
=&M^n
\begin{bmatrix}
	a_{0}\\\\
	a_{1}
\end{bmatrix}\\\\
=&\begin{bmatrix}
	\frac{1-\sqrt{5}}{2}&\frac{1+\sqrt{5}}{2}\\\\
	1&1
\end{bmatrix}
\begin{bmatrix}
	\frac{1-\sqrt{5}}{2}&0\\\\
	0&\frac{1+\sqrt{5}}{2}
\end{bmatrix}^n
\begin{bmatrix}
	\frac{1-\sqrt{5}}{2}&\frac{1+\sqrt{5}}{2}\\\\
	1&1
\end{bmatrix}^{-1}
\begin{bmatrix}
	0\\\\
	1
\end{bmatrix}\\\\
=&\begin{bmatrix}
	\frac{1-\sqrt{5}}{2}&\frac{1+\sqrt{5}}{2}\\\\
	1&1
\end{bmatrix}
\begin{bmatrix}
	\left(\frac{1-\sqrt{5}}{2}\right)^n&0\\\\
	0&\left(\frac{1+\sqrt{5}}{2}\right)^n
\end{bmatrix}
\begin{bmatrix}
	-\frac{\sqrt{5}}{5}&\frac{5+\sqrt{5}}{10}\\\\
	\frac{\sqrt{5}}{5}&\frac{5-\sqrt{5}}{10}
\end{bmatrix}
\begin{bmatrix}
	0\\\\
	1
\end{bmatrix}\\\\
=&\begin{bmatrix}
	\left(\frac{1-\sqrt{5}}{2}\right)^{n+1}&\left(\frac{1+\sqrt{5}}{2}\right)^{n+1}\\\\
	\left(\frac{1-\sqrt{5}}{2}\right)^{n}&\left(\frac{1+\sqrt{5}}{2}\right)^n
\end{bmatrix}
\begin{bmatrix}
	\frac{5+\sqrt{5}}{10}\\\\
	\frac{5-\sqrt{5}}{10}
\end{bmatrix}
\end{aligned}
$$
则：
$$
\begin{aligned}
a_n =& \frac{5+\sqrt{5}}{10}\left(\frac{1-\sqrt{5}}{2}\right)^{n+1}+\frac{5-\sqrt{5}}{10}\left(\frac{1+\sqrt{5}}{2}\right)^{n+1}\\\\
=& \frac{-\sqrt{5}}{5}\left(\frac{1-\sqrt{5}}{2}\right)^{n}+\frac{\sqrt{5}}{5}\left(\frac{1+\sqrt{5}}{2}\right)^{n}\\\\
=& \frac{1}{\sqrt5}\left(\frac{1+\sqrt{5}}{2}\right)^n-\frac{1}{\sqrt5}\left(\frac{1-\sqrt{5}}{2}\right)^n
\end{aligned}
$$

这个相似对角化的方法比较暴力。当然也可以用特征向量来处理，结果也差不多。

实际上从矩阵对角化的过程可以看出我们介绍的第一种**待定系数方法的影子**：

$$
\begin{bmatrix}
	\frac{1-\sqrt{5}}{2}&0\\\\
	0&\frac{1+\sqrt{5}}{2}
\end{bmatrix}
\begin{bmatrix}
	\frac{1-\sqrt{5}}{2}&\frac{1+\sqrt{5}}{2}\\\\
	1&1
\end{bmatrix}^{-1}
\begin{bmatrix}
	a_{n-1}\\\\
	a_{n-2}
\end{bmatrix}
=\begin{bmatrix}
	\frac{1-\sqrt{5}}{2}&\frac{1+\sqrt{5}}{2}\\\\
	1&1
\end{bmatrix}^{-1}\begin{bmatrix}
	a_{n}\\\\
	a_{n-1}
\end{bmatrix}
$$

也就是说我们实际上构造了两个新的数列：
$$
\begin{bmatrix}
	b_{n}\\\\
	c_{n-1}
\end{bmatrix}=\begin{bmatrix}
	\frac{1-\sqrt{5}}{2}&\frac{1+\sqrt{5}}{2}\\\\
	1&1
\end{bmatrix}^{-1}\begin{bmatrix}
	a_{n}\\\\
	a_{n-1}
\end{bmatrix}
$$

满足
$$
\begin{bmatrix}
	\frac{1-\sqrt{5}}{2}&0\\\\
	0&\frac{1+\sqrt{5}}{2}
\end{bmatrix}
\begin{bmatrix}
	b_{n-1}\\\\
	c_{n-2}
\end{bmatrix}
=\begin{bmatrix}
	b_{n}\\\\
	c_{n-1}
\end{bmatrix}
$$
是等比数列。