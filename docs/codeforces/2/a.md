# [Winner](https://codeforces.com/problemset/problem/2/a)

大模拟。

先模拟一遍游戏，记最后的最大分数为 $m$，若只有一位玩家分数为 $m$，则将其输出即可。
若有多位玩家分数为 $m$，则再模拟一遍游戏，找到第一位分数 $\le m$ 的 **最后分数为 $m$ 的玩家**。

时间复杂度 $O(n \log n)$，是否有 $\log$ 取决于你用 `map` 还是哈希。