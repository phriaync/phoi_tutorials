# [Lorry](https://codeforces.com/problemset/problem/3/b)

枚举 $t = 1$ 的载具选 $x$ 个，则 $t = 2$ 的载具选 $\min(c_2, (v - x)/2)$ 个，其中 $c_2$ 为 $t = 2$ 的载具数量。
两种载具中分别贪心，使用前缀和优化可以在每次枚举时 $O(1)$ 得到答案。

时间复杂度 $O(n\log n)$，瓶颈在于排序。

