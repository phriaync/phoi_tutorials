# [Shortest path of the king](https://codeforces.com/problemset/problem/3/A)

记 $x = x_t - x_s, y = y_t-y_s$，由于每次移动能独立使 $|x|, |y|$ 减 $1$，答案为 $\max(|x|, |y|)$。

移动方式按 $x, y$ 符号讨论即可。时间复杂度 $O(\max(|x|,|y|))$。