+++
title = '椭圆的焦点弦'
date = 2024-12-06T18:07:28+08:00
draft = false
tags = ["几何"]
+++

## 已知
椭圆$\Gamma$
$$
\frac{x^2}{a^2}+\frac{y^2}{b^2}=1
$$
已知$A(-a,0)$、$B(a,0)$,现有一过焦点$F(c,0)$的直线$l$交$\Gamma$于点$P$、$Q$。

证明存在常数$\lambda$使得：
$$
k_{PA}+\lambda k_{QB}=0
$$
<!--more-->

## 题解

<iframe src="https://www.desmos.com/calculator/pr6h5w80uc?embed" width="500" height="500" style="border: 1px solid #ccc" frameborder=0></iframe>

### 韦达定理 法一
设直线$l$的方程为：
$$
x=my+c
$$
和椭圆方程联立得到：
$$
\frac{(my+c)^2}{a^2}+\frac{y^2}{b^2}=1
$$
也就是：
$$
(\frac{m^2}{a^2}+\frac{1}{b^2})y^2+\frac{2mc}{a^2}y+\frac{c^2}{a^2}-1=0
$$
设$P(x_1,y_1),Q(x_2,y_2)$，则
$$
\begin{aligned}
&y_1y_2 = \frac{\frac{c^2}{a^2}-1}{\frac{m^2}{a^2}+\frac{1}{b^2}}\\\\
&y_1+y_2 = \frac{-\frac{2mc}{a^2}}{\frac{m^2}{a^2}+\frac{1}{b^2}}
\end{aligned}
$$

所求的$\lambda$：
$$
-\lambda = \frac{k_{PA}}{k_{QB}} = \frac{y_1(x_2-a)}{y_2(x_1+a)}
$$

这是一个**非对称的**式子，注意到：
$$
\frac{x^2}{a^2}+\frac{y^2}{b^2}=1
$$
可以变形为：
$$
\frac{y^2}{b^2}=\frac{a^2-x^2}{a^2}
$$
所以：
$$
\frac{y}{a+x}=\frac{b^2}{a^2}\frac{a-x}{y}
$$
> 这是非对称韦达定理题目中常用的技巧！

于是：
$$
-\lambda = \frac{y_1(x_2-a)}{y_2(x_1+a)} = -\frac{b^2}{a^2}\frac{(x_1-a)(x_2-a)}{y_1y_2}
$$

带入韦达定理立即得到：
$$
\lambda = -\frac{(a-c)^2}{b^2}
$$


### 韦达定理 法二
所求的$\lambda$：
$$
-\lambda = \frac{k_{PA}}{k_{QB}} = \frac{y_1(x_2-a)}{y_2(x_1+a)}
$$

我们可以直接带入$x=my+c$得到：
$$
-\lambda= \frac{my_1y_2+(c-a)y_1}{my_2y_1+(c+a)y_2}
$$
利用$y_1y_2$和$y_1+y_2$之间的关系：
$$
\begin{aligned}
&y_1y_2 = \frac{\frac{c^2}{a^2}-1}{\frac{m^2}{a^2}+\frac{1}{b^2}}\\\\
&y_1+y_2 = \frac{-\frac{2mc}{a^2}}{\frac{m^2}{a^2}+\frac{1}{b^2}}
\end{aligned}
$$
我们知道：
$$
my_1y_2 = -\frac{a^2}{2c}(\frac{c^2}{a^2}-1)(y_1+y_2)
$$

> 这就完成了**降次**

于是：
$$
-\lambda= \frac{-\frac{a^2}{2c}(\frac{c^2}{a^2}-1)(y_1+y_2)+(c-a)y_1}{-\frac{a^2}{2c}(\frac{c^2}{a^2}-1)(y_1+y_2)+(c+a)y_2}
$$
消去分母：
$$
-\lambda= \frac{-(c^2-a^2)(y_1+y_2)+2c(c-a)y_1}{-(c^2-a^2)(y_1+y_2)+2c(c+a)y_2}
$$
整理一下：
$$
-\lambda= \frac{(a^2+c^2-2ac)y_1+(a^2-c^2)y_2}{(a^2-c^2)y_1+(a^2+c^2+2ac)y_2}
$$
提出因子：
$$
-\lambda=\frac{a-c}{a+c} \cdot \frac{(a-c)y_1+(a+c)y_2}{(a-c)y_1+(a+c)y_2}
$$
所以：
$$
-\lambda=\frac{a-c}{a+c} 
$$
证毕。

### 椭圆第三定义
实际上我们知道：
$$
k_{PA}k_{PB} = -\frac{b^2}{a^2}
$$
> 实际上这就是我们之前对椭圆方程做的变形：
> $$
> \begin{aligned}
> &\frac{x^2}{a^2}+\frac{y^2}{b^2}=1\\\\
> \implies &\frac{y}{a+x}=\frac{b^2}{a^2}\frac{a-x}{y}\\\\
> \implies &\frac{y}{x+a}\cdot \frac{y}{x-a}=-\frac{b^2}{a^2}
> \end{aligned}
> $$
为定值，且：
$$
k_{PB}k_{QB} = -\frac{b^4}{a^2(a-c)^2}
$$
也是定值。
> 这个定值通过韦达定理不难证明

从这两个式子出发，显然有：
$$
\frac{k_{PB}}{k_{QB}} = \frac{(a-c)^2}{b^2}
$$