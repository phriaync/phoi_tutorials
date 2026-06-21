# [Maximize the Gap](https://atcoder.jp/contests/abc463/tasks/abc463_d)

二分答案，`check` 是经典贪心问题。

将区间以 **右端点** 为第一关键字、左端点为第二关键字排序，考虑二分最大可能分数 $x$。
检查 $x$ 是否合法时，每次选择与上一段区间距离 $\ge x$ 的右端点最小的区间，判断最后可选区间数是否 $\ge K$ 即可。

这样贪心正确是因为右端点最小的区间对后续区间影响最小，时间复杂度 $O(N\log N + N\log(\max R))$。


