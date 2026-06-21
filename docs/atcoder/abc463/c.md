# [Tallest at the Moment](https://atcoder.jp/contests/abc463/tasks/abc463_c)

按$L_i$排序，预处理后缀最大 $H_i$。每次询问时二分出最小的 $L_x > T_i$，然后取后缀最大 $H_i$ 即可。

题目已经对 $L$ 排好序，时间复杂度 $O(N + Q\log N)$。