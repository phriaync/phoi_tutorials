# [Not Covered Points](https://atcoder.jp/contests/abc462/tasks/abc462_c)

将所有点按照 $x$ 坐标排序，则点 $i$ 确定的长方形不包含任何点当且仅当点 $i$ 的 $y$ 坐标为前缀最小。

于是排完序扫一遍点即可，时间复杂度 $O(N\log N)$。