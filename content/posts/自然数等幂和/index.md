+++
title = '自然数等幂和'
date = 2024-11-11T20:23:49+08:00
draft = false
tags = ["数列"]
+++

## 求和
$$
S_m(n) = \sum_{k=1}^n  k^m = 1^m+2^m+\cdots+n^m
$$

<!--more-->

## 题解

### 二项式定理（递推解）

我们知道
$$
S_0(n) = n
$$

实际上根据二项式定理：
$$
(1+k)^m  = \sum_{i=0}^m C_m^ik^i
$$

于是：
$$
(1+k)^m-k^m = \sum_{i=0}^{m-1} C_m^ik^i
$$

两侧累加即可：
$$
\sum_{k=1}^n \left[(1+k)^m-k^m\right] = \sum_{k=1}^n\sum_{i=0}^{m-1} C_m^ik^i
$$

也就是：
$$
{\color{red}(1+n)^m-1 = \sum_{i=0}^{m-1}C_m^i S_i(n)}
$$

令$m=2$得到：
$$
(1+n)^2-1=C_2^0S_0(n)+C_2^1S_1(n)
$$
所以：
$$
S_1(n) = \frac{n(n+1)}{2}
$$

令$m=3$得到：
$$
(1+n)^3-1=C_3^0S_0(n)+C_3^1S_1(n)+C_3^2S_2(n)
$$

也就是：
$$
(1+n)^3-1 = n+\frac{3n(n+1)}{2}+3S_2(n)
$$
所以：
$$
S_2(n) = \frac{n(n+1)(2n+1)}{6}
$$

以此类推，我们可以递归地求出所有的$S_m(n)$

### 指数生成函数（解析解）

研究此类数列我们一般还有一种手段：生成函数（也叫母函数）。

也就是考虑无穷级数：
$$
G(x) = \sum_{n=0}^\infty a_nx^n
$$

当然，对于我们这里的$S_m(n)$，这个生成函数不收敛。

这种情况下我们还可以考虑指数生成函数，也就是无穷级数：
$$
E(x) = \sum_{n=0}^\infty \frac{a_n}{n!}x^n
$$

下面我们来计算$S_m(n)$的指数生成函数（固定$n$，认为它是关于$m$的一个数列）。

$$
F_n(x) = \sum_{m=0}^\infty \frac{S_m(n)}{m!}x^m
$$

也就是：
$$
F_n(x) = \sum_{m=0}^\infty \sum_{k=1}^n  k^m\frac{x^m}{m!}
$$

交换求和顺序：
$$
F_n(x) = \sum_{k=1}^n\sum_{m=0}^\infty   k^m\frac{x^m}{m!} = \sum_{k=1}^n e^{kx} = \frac{e^x(1-e^{nx})}{1-e^x}
$$

所以：
$$
F_n(x)+1 = \frac{1-e^{(n+1)x}}{1-e^x} = {\color{blue}\frac{x}{e^x-1}}\frac{e^{(n+1)x}-1}{x}
$$

考虑左右两侧的展开式（左侧是通过指数生成函数展开，右侧为泰勒级数）：
$$
1+\sum_{m=0}^\infty \frac{S_m(n)}{m!}x^m = \left[{\color{blue}\sum_{i=0}^\infty \frac{B_i}{i!}x^i}\right]\left[\sum_{j=1}^\infty \frac{(n+1)^jz^{j-1}}{j!}\right]
$$

> 其中$B_i$是伯努利数，它的指数生成函数就是$\frac{x}{e^x-1}$

也就是：
$$
1+\sum_{m=0}^\infty \frac{S_m(n)}{m!}x^m = \left[\sum_{i=0}^\infty \frac{B_i}{i!}x^i\right]\left[\sum_{j=0}^\infty \frac{(n+1)^{j+1}z^{j}}{(j+1)!}\right]
$$

对比左右两侧$x^m$系数，我们就知道（$m\ge 1$时）：

$$
\frac{S_m(n)}{m!} = \sum_{i=0}^m \frac{B_i}{i!} \frac{(n+1)^{m-i+1}}{(m-i+1)!}
$$

也就是：
$$
S_m(n) = m!\sum_{i=0}^m \frac{B_i}{i!} \frac{(n+1)^{m-i+1}}{(m-i+1)!}
$$
凑一个组合数就得到最终的解析解：
$$
S_m(n) = \frac{1}{m+1} \sum_{i=0}^m B_iC_{m+1}^i(n+1)^{m+1-i}
$$
例如：
$$
\begin{aligned}
&S_1(n) \\\\
= &\frac{1}{2} (B_0C_2^0(n+1)^2 + B_1C_2^1(n+1)^1)\\\\
= &\frac{1}{2} (n^2+2n+1 - n-1) = \frac{n(n+1)}{2}
\end{aligned}
$$

$$
\begin{aligned}
&S_2(n) \\\\
= &\frac{1}{3} (B_0C_3^0(n+1)^3 + B_1C_3^1(n+1)^2+B_2C_3^2(n+1)^1)\\\\
= &\frac{1}{3} ((n+1)^3-\frac{3}{2}(n+1)^2+\frac{1}{2}(n+1)) \\\\
= &\frac{n+1}{6}(2(n+1)^2-3(n+1)+1)\\\\
= &\frac{n(n+1)(2n+1)}{6}
\end{aligned}
$$

其中$B_0=1,B_1=-\frac{1}{2},B_2=\frac{1}{6}$。

### 伯努利数

我们此前提到的$B_i$是伯努利数，它的指数生成函数就是$\frac{x}{e^x-1}$。

实际上，我们可以通过泰勒级数的定义：
$$
f(x) = \sum_{i=0}^\infty \frac{f^{(i)}(x_0)}{i!}(x-x_0)^i
$$

知道（非严谨的，在极限意义下）：
$$
B_i = f^{(i)}(0)
$$

也就是$i$阶导数在$x=0$处的取值。

有一种记忆方法：
$$
f(x) = \frac{x}{e^x-1}\implies
e^xf(x)-f(x)=x
$$
不断求导数即可得到：
$$
\begin{aligned}
&e^x(f+f')-f'=1\\\\
&e^x(f+2f'+f'')-f''=0\\\\
&e^x(f+3f'+3f''+f''')-f'''=0\\\\
\end{aligned}
$$

然后全部令$x=0$就可以得到：
$$
\begin{aligned}
&(f+f')-f'=1\\\\
&(f+2f'+f'')-f''=0\\\\
&(f+3f'+3f''+f''')-f'''=0\\\\
\end{aligned}
$$

也就是$f(0)=1,f'(0)=-\frac{1}{2},f''(0)=\frac{1}{6}$

实际上从上面的式子很容易观察到：
$$
\sum_{i=0}^m B_iC_{m+1}^i = 0\quad m\ge 1
$$
这也是最常见的伯努利递推公式。