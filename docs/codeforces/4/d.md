# [Mysterious Present](https://codeforces.com/problemset/problem/4/D)

二维 LIS 问题，排序后因为第一维已经有序，可以归约为一维 LIS 问题。
由于本题需要满足两维都严格增，$O(n\log n)$ 的单调栈二分做法不可行，考虑 $O(n^2)$ 暴力枚举转移。

具体地，设 $f_i$ 表示排序后前 $i$ 个信封能形成的最大链长度，则有转移：
$$
f_i = \begin{cases}
\max_{0 \le j < i \land w_j < w_i \land h_j < h_i}(f_j + 1) & \exists 0 \le j < i, w_j < w_i \land h_j < h_i \newline
0 & \text{otherwise}
\end{cases}
$$

因此 $f_i$ 不一定单调，需要维护其最大值。同时维护 $f_i$ 从哪个 $j$ 转移即可递归得到方案。