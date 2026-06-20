# [Commentator problem](https://codeforces.com/problemset/problem/2/C)

先翻译题目。

???+ note "题意"
    给定平面上三个圆心不共线的圆，问是否存在点 $T$，满足：

    * 三个圆都存在两条过 $T$ 的切线；
    * 三个圆的两条切线的夹角相等。

    若存在多个满足条件的 $T$，取切线夹角最大的一个。

### 夹角
记三个圆分别为 $A, B, C$，先尝试刻画切线的夹角。记圆 $A$ 的两条切线为 $A_1T, A_2T$，切点分别为 $A_1, A_2$，则有：
$$
\sin \frac{1}{2}\angle A_1TA_2 = \frac{r_A}{dis_{A, T}}
$$
对于 $B, C$ 同理，于是：
$$
\frac{r_A}{dis_{A, T}} = \frac{r_B}{dis_{B, T}} =\frac{r_C}{dis_{C, T}} < 1
$$
不等号实际上是保证了 $T$ 在圆外，其为圆有两条过 $T$ 的切线的充要条件。

### 轨迹
不妨先只考虑 $\frac{r_A}{dis_{A, T}} = \frac{r_B}{dis_{B, T}}$，记此时 $T$ 的轨迹为 $U$，由于：
$$
\frac{r_A}{dis_{A, T}} = \frac{r_B}{dis_{B, T}} \iff \frac{dis_{A, T}}{dis_{B, T}} = \frac{r_A}{r_B}
$$
得 $r_A = r_B$ 时，$U$ 是直线；$r_A \neq r_B$ 时，$U$ 是阿波罗尼奥斯圆。具体地，记 $\frac{r_A^2}{r_B^2} = k$，我们有：
$$
\frac{dis_{A, T}}{dis_{B, T}} = \frac{r_A}{r_B}
$$
$$
\iff\frac{(x_T - x_A)^2 + (y_T - y_A) ^ 2}{(x_T - x_B)^2 + (y_T - y_B) ^ 2} = k
$$
$$
\iff(1 - k)x_T^2 + (1 - k)y_T^2 - 2(x_A - kx_B)x_T - 2(y_A - ky_B)y_T + x_A^2 + y_A^2 - k(x_B^2 + y_B^2) = 0
$$
对 $B$ 和 $C$，$C$ 和 $A$ 同理，得到轨迹 $V$, $W$，于是 $T \in U \cap V \cap W$。
由于可以证明 $|U \cap V \cap W| \le 2$，因此分别判断 $T$ 是否在圆外，并比较任意一圆的 $r/dis$ 得到最大夹角即可。

### 求交
考虑两两求交，不妨先求 $U \cap V$。

当 $U, V$ 均为直线时，由圆心不共线，$U, V$ 有且仅有一个交点。具体地，设：
$$
\begin{aligned}
U:a_1x+b_1y+c_1=0 \newline
V:a_2x+b_2y+c_2=0
\end{aligned}
$$
则：
$$
U\cap V=(\frac{b_1c_2-c_1b_2}{a_1b_2-b_1a_2}, \frac{a_1c_2-c_1a_2}{b_1a_2-a_1b_2})
$$

当 $U, V$ 中有一个圆时，不妨设 $V$ 是圆，则 $U \cap V \neq\emptyset$ 的充要条件为 $dis_{U,V} \le r_V$。考虑圆心 $V$ 在 $U$ 上的投影，注意到其为圆 $V$ 所截出的弦的中点，若已知该点和弦长，容易求出弦的两个端点。又弦的中垂线过圆心 $V$，我们容易求出中垂线的方程，于是问题化归到求线与线的交。具体地，设：
$$
U:ax+by+c=0
$$
$$
V:(x-x_V)^2+(y-y_V)^2=r_V^2
$$
中垂线为 $n$，弦长为 $L$，则：
$$
dis_{U,V} = \frac{|ax_V+by_V+c|}{\sqrt{a^2+b^2}}
$$
$$
n:b(x-x_V)-a(y-y_V)=0
$$
$$
L=2\sqrt{r_V^2-dis_{U,V}^2}
$$
记 $n \cap U = M$，于是：
$$
U \cap V = (x_M\pm\frac{b}{2\sqrt{a^2+b^2}}L, y_M\mp\frac{a}{2\sqrt{a^2+b^2}}L)
$$

当 $U, V$ 均为圆时，将两圆方程相减即可得到过两圆交点的直线，问题化归到对直线与圆求交。若两圆外离，可以证明该直线与两圆没有交点。若两圆内含，显然不存在符合题目要求的 $T$。

对 $V\cap W, W\cap U$ 同理，最后找 $T$ 即可。

显然讨论时间复杂度没有意义。