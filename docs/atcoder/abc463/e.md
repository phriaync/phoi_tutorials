# [Roads and Gates](https://atcoder.jp/contests/abc463/tasks/abc463_e)

先做一遍 Dijkstra 求出不用传送门时的单源最短路径 $dis_{1,i}$，考虑依此刻画答案。

首先我们至多使用一次传送门，否则对于一个中转点至少会多出 $X_i + Y$ 的贡献，严格劣于跳过这个中转点。于是设这次传送的入口为 $p$，出口为 $q$，城市 $1$ 与 $k$ 间的最短路径长度为 $d_{1,k}$，则：
$$
d_{1,k} = \min(dis_{1, k}, dis_{1, p} + X_p + X_q + Y + dis_{q, k})
$$
其中 $dis_{1, p} + X_p + Y$ 与终点 $k$ 无关，于是我们可以预处理出 $p$。那么我们可以从 $p$ 对每个点 $k$ 连一条权值为 $X_p + X_k + Y$ 的边，在这张图上再做一遍 Dijkstra 即可。

时间复杂度 $O((N + M) \log (N+M))$。