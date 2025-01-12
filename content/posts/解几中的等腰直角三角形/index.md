+++
title = '解几中的等腰直角三角形'
date = 2025-01-12T16:29:14+08:00
draft = false
tags = ["几何"]
+++

## 已知
> 本题来自2025上海春考

半椭圆$\Gamma$:
$$
\frac{x^2}{4}+y^2=1\quad (y\ge 0)
$$
上有两个动点$P,Q$，点$T$的坐标是$(t,0)$。当$\triangle PQT$是以$T$为直角顶点的等腰直角三角形时，求实数$t$的取值范围。
<!--more-->

## 题解

### 法一：几何关系

<iframe src="https://www.desmos.com/calculator/srsmlkynem?embed" width="500" height="500" style="border: 1px solid #ccc" frameborder=0></iframe>

如图所示，实际上存在如下的全等关系：
$$
\triangle QTQ' \cong TPP'
$$

不妨设$Q$的纵坐标是$q(\ge 0)$，$P$的纵坐是$p(\ge 0)$，那么很容易写出他们的完整坐标：
$$
P(t+q,p),\quad Q(t-p,q)
$$

代入椭圆方程：

$$
\begin{aligned}
(t+q)^2+4p^2=4\tag{*}\\\\
(t-p)^2+4q^2=4
\end{aligned}
$$

两式相减得到：
$$
\begin{aligned}
q^2-p^2+2(p+q)t+4(p+q)(p-q)=0
\end{aligned}
$$
整理得到：
$$
t=\frac{3}{2}(q-p)
$$

代入(*)得到：
$$
\begin{aligned}
(\frac{5}{2}q-\frac{3}{2}p)^2+4p^2=4\\\\
(\frac{3}{2}q-\frac{5}{2}p)^2+4q^2=4
\end{aligned}
$$

整理得到：
$$
\begin{aligned}
\color{red}25p^2+25q^2-30pq=16\\\\
\end{aligned}
$$

所以
$$
25(p-q)^2=16-20pq \le 16
$$

> p,q都是非负的，所以$pq\ge 0$，从而上式显然。
> 
> 实际上我们知道$25p^2+25q^2-30pq=16$，蕴含着$(p,q)$落在一个关于$y=x,x=0,y=0$都对称的椭圆上：
> <iframe src="https://www.desmos.com/calculator/n0nsw0awgz?embed" width="500" height="500" style="border: 1px solid #ccc" frameborder=0></iframe>


于是：
$$
t^2=\frac{9}{4}(q-p)^2 \le \frac{36}{25}
$$

从而$t$的取值范围是：
$$
t\in [-\frac{6}{5}, \frac{6}{5}]
$$

### 法一变种：几何关系 另解

和法一完全一致的过程得到：
$$
t=\frac{3}{2}(q-p)
$$

而后我们可以考虑利用关系：
$$
q = (2t+3p)/3
$$

来把$P$点坐标中的$q$消去：
$$
\begin{aligned}
&(t+q)^2+4p^2=4\\\\
\implies & (5t+3p)^2+36p^2=36\\\\
\implies & 45p^2+30t\cdot p+25t^2-36=0\\\\
\end{aligned}
$$

类似的，利用：
$$
p = (3q-2t)/3
$$

可以吧$Q$点坐标中的$p$消去：
$$
\begin{aligned}
&(t-p)^2+4q^2=4\\\\
\implies & (5t-3q)^2+36q^2=36\\\\
\implies & 45q^2-30t\cdot q+25t^2-36=0\\\\
\end{aligned}
$$

观察到两个方程的相似性：

$$
\begin{aligned}
45p^2+30t\cdot p+25t^2-36=0\\\\
45q^2-30t\cdot q+25t^2-36=0
\end{aligned}
$$

可以发现，$p,-q$可以视为方程：
$$
45x^2+30t\cdot x+25t^2-36=0
$$
的两根。

利用根的判别式即可得到$t$的范围：
$$
\Delta = 900t^2-4\cdot 45(25t^2-36) \ge 0
$$

### 法二：极坐标

这里巧妙利用等腰直角三角形的条件，直接设参数坐标($0\le a \le \frac{\pi}{2},\quad r\gt 0$)：

$$
P(t+r\cos a, r\sin a)\\\\
Q(t+r\cos (a+\frac{\pi}{2}), r\sin (a+\frac{\pi}{2}))
$$

也就是：
$$
P(t+r\cos a, r\sin a)\\\\
Q(t-r\sin a, r\cos a)
$$

这样就直接蕴涵了“等腰”和“直角”两个条件。

带入椭圆方程：
$$
\begin{aligned}
(t+r\cos a)^2+4r^2\sin^2a=4\\\\
(t-r\sin a)^2+4r^2\cos^2a=4
\end{aligned}
$$
两式相加得到：
$$
\begin{aligned}
\color{red}2t^2+5r^2+2rt(\cos a-\sin a)=8
\end{aligned}
$$
两式相减得到：
$$
2rt(\cos a+\sin a)+3r^2(\sin^2a-\cos^2a)=0
$$
也就是($\cos a+\sin a\ne 0 \quad \forall 0\le a\le \pi/2$，直接消去)：
$$
\color{blue}2t = 3r(\cos a-\sin a)
$$

联立：
$$
\begin{aligned}
2t^2+5r^2+2rt(\cos a-\sin a)=8\\\\
2t = 3r(\cos a-\sin a)
\end{aligned}
$$
消去$a$得到：
$$
2t^2+5r^2+2rt\cdot \frac{2t}{3r}=8
$$
所以：
$$
10t^2+15r^2=24
$$

另外：
$$
\color{blue} 2t = 3r(\cos a-\sin a) = 3r\sqrt{2}\sin(\frac{\pi}{4}-a)\in [-3r,3r]
$$
所以：
$$
r^2 \ge \frac{4}{9}t^2
$$
所以：
$$
10t^2+15r^2=24 \ge 10t^2+15\cdot \frac{4}{9}t^2 = \frac{50}{3}t^2
$$
所以：
$$
t^2 \le \frac{36}{25}
$$

### 法三：常规思路

先考虑斜率不为0的情况。

设直线$PQ$的方程为$x=my+n$，点坐标$P(x_1,y_1),Q(x_2,y_2)$，利用和椭圆方程联立的韦达定理得到坐标关系。

然后利用等腰直角的条件：
$$
(x_1-t)(x_2-t)+y_1y_2=0\tag{**}\\\\
\frac{y_1+y_2}{2}=-m(\frac{x_1+x_2}{2}-t)
$$
三个变量，两个等式约束，通过$y_1y_2\ge 0, \Delta \gt 0$可以求解得到$t$的范围。


具体来说$PQ$方程和椭圆方程联立得到：

$$
(m^2+4)y^2+2mny+n^2-4=0
$$
所以：
$$
y_1+y_2 = \frac{-2mn}{m^2+4}\\\\
y_1y_2 = \frac{n^2-4}{m^2+4}
$$
进而：
$$
x_1+x_2 = m(y_1+y_2)+2n = \frac{8n}{m^2+4}\\\\
x_1x_2 = m^2y_1y_2 + mn(y_1+y_2) +n^2= \frac{4n^2-4m^2}{m^2+4}
$$

带入等腰直角的条件(**)得到：
$$
\frac{4n^2-4m^2}{m^2+4}+t^2-t(\frac{8n}{m^2+4})+\frac{n^2-4}{m^2+4}=0\\\\
\frac{-2mn}{m^2+4}=-m(\frac{8n}{m^2+4}-2t)
$$

也就是：
$$
4n^2-4m^2+t^2(m^2+4)-8nt+n^2-4=0\\\\
2n=8n-2t(m^2+4)
$$

所以：
$$
5n^2-4m^2-5nt=4\\\\
t^2(m^2+4)=3nt
$$

所以：
$$
5n^2-4m^2-\frac{15n^2}{m^2+4}=4\\\\
t = \frac{3n}{m^2+4}
$$
第一个式子可以推出：
$$
\begin{aligned}
&(5n^2-4m^2-4)(m^2+4) = 15n^2\\\\
\implies &5n^2m^2+20n^2-4(m^2+1)(m^2+4)=15n^2\\\\
\implies &5n^2m^2+5n^2=4(m^2+1)(m^2+4)\\\\
\implies &5n^2=4(m^2+4)\\\\
\end{aligned}
$$
带入第二个式子得到：
$$
t = \frac{3n}{m^2+4} = \frac{12}{5n}
$$
而根据题设，$PQ$都在x轴上侧：
$$
y_1y_2 = \frac{n^2-4}{m^2+4} \ge 0
$$
所以：
$$
n\in[2,\infty)\cup (-\infty,-2]
$$
所以：
$$
t =  \frac{12}{5n} \in [-\frac{6}{5},0)\cup(0,\frac{6}{5}]
$$

最后，$t=0$显然也可以取到，所以：
$$
t \in [-\frac{6}{5},\frac{6}{5}]
$$