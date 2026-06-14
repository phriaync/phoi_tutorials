# [Alternating Costs](https://atcoder.jp/contests/abc462/tasks/abc462_e)

$X, Y$ 正负等价，先对其取绝对值，于是 $X \ge 0, Y \ge 0$。

记移动到 $(x - 1, y)$ 为 $x^-$，移动到 $(x + 1, y)$ 为 $x^+$，移动到 $(x, y - 1)$ 为 $y^-$，移动到 $(x, y + 1)$ 为 $y^+$。

若 $A = B$，则所有操作成本相等，答案为 $A(X + Y)$。

若 $A < B$，显然最佳操作方式为 $x^+y^+x^+y^+...$，直到有一维到达终点。
假设 $X < Y$，那么会有 $\lfloor \frac{Y - X}{2} \rfloor$ 个单独的成本为 $A$ 的 $y^+$ 
和 $\lfloor \frac{Y - X + 1}{2} \rfloor$ 个单独的成本为 $B$ 的 $y^+$。而对于成本为 $B$ 的 $y^+$，我们可以将其拆成成本为 $3A$ 的 $x^-y^+x^+$，于是最终答案为：
$$
A(2X + \lfloor \frac{Y - X}{2} \rfloor) + \min(3A, B)\lfloor \frac{Y - X + 1}{2} \rfloor
$$

$X \ge Y$ 以及 $A > B$ 的情况同理，这里不加赘述。

单次询问时间复杂度 $O(1)$。