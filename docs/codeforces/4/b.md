# [Before an Exam](https://codeforces.com/problemset/problem/4/B)

显然如果 $\sum minTime_i \le sumTime \le \sum maxTime_i$，那么一定有解。

如果有解，维护 $sumTime$ 与 $\sum minTime_i$ 的差，每天贪心地减小这个差值，当差为 $0$ 后每一天都花 $minTime_i$ 即可。

$O(d)$。