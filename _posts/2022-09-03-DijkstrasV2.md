---
title: "Dijkstra's Algorithm O(V<sup>2</sup>) Implementation"
date: 2022-09-03
---

```
#include <bits/stdc++.h>
using namespace std;

#define MEM(a, b) memset(a, (b), sizeof(a))
#define REP(Q) for(int _ = 0; _ < Q; _++)
#define all(cont) cont.begin(), cont.end()
#define rall(cont) cont.end(), cont.begin()
#define pb push_back
#define ppb pop_back
#define pf push_front
#define ppf pop_front
#define F first
#define S second
typedef pair<int, int> pi;
typedef vector<int> vi;
typedef vector<string> vs;
typedef vector<pi> vii;
typedef set<int> seti;
typedef long long ll;

const int MM = 1e3+4;
int n, m;
vii adj[MM];
bool vis[MM];
int dis[MM];

int main(){
    ios::sync_with_stdio(0);
    cin.tie(0);
    
    cin >> n >> m;
    for(int i = 0, u, v, w; i < m; i++){
        cin >> u >> v >> w;
        adj[u].pb({w, v});
        adj[v].pb({w, u});
    }

    fill(dis, dis+n+1, INT_MAX);
    dis[1] = 0;

    REP(n){
        int u, d = INT_MAX;
        for(int i = 1; i <= n; i++){
            if(!vis[i] && dis[i] < d){
                u = i; d = dis[i];
            }
        }
        
        vis[u] = true;
        for(pi x : adj[u]){
            int v = x.S, w = x.F;
            dis[v] = min(dis[v], dis[u] + w);
        }
    }

    for(int i = 1; i <= n; i++){
        cout << (dis[i] == INT_MAX? -1 : dis[i]) << '\n';
    }

    return 0;
}
```

Practice Problems:
- [Single Source Shortest Path](https://dmoj.ca/problem/sssp)
