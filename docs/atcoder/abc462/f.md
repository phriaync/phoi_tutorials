# [More ABC](https://atcoder.jp/contests/abc462/tasks/abc462_f)

下记 $N = |S|$；$S'$ 表示操作后的串；$c_i$ 表示 $S[1, i]$ 中 `ABC` 的数量，$c'_i$ 表示 $S'[1, i]$ 中 `ABC` 的数量；$g_s$ 表示将 $s$ 化为 `ABC` 需要的操作次数。

设 $dp_{i, j}$ 表示 $c'_i - c_i = j$ 时的最小操作数量，则答案为 $dp_{N, K}$。

考虑从 $i - 1$ 转移到 $i$。具体地，考虑以下两种情况：

- $S'[i - 2, i] = \text{ABC}$，即 $c'_i = c'_{i - 1} + 1$。
这时我们要考虑操作是否破坏了 $S$ 中原本的 `ABC`，转移方程为：
$$
dp_{i, j} = dp_{i - 3, j - 1 + c_i - c_{i - 3}} + g_{S[i - 2, i]}
$$
- $S'[i - 2, i] \neq \text{ABC}$，即 $c'_i = c'_{i - 1}$。
此时我们一定没有操作 $S_i$，因为不操作时 `ABC` 数量不减，而操作数减少。因此转移方程为：
$$
dp_{i, j} = dp_{i - 1, j + c_i - c_{i - 1}}
$$
转移时两者取最小即可，注意边界情况。$dp$ 的初值为：
$$
dp_{i, j} = \begin{cases}
0 & j = 0 \newline
+\infty & j \ge 1
\end{cases}
$$

时间复杂度 $O(NK)$。