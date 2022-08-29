---
title: "Depth First Search (DFS)"
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

const int MM = 7; //Max # of nodes
vi adj[MM]; //Adjacency list
bool vis[MM];

void addEdge(int u, int v){
    adj[u].pb(v);
    adj[v].pb(u);
}

void dfs(int u){
    vis[u] = true;
    cout << u << " --> ";
    for(int x : adj[u]){
        if(!vis[x]) dfs(x);
    }
}

int main(){
    ios::sync_with_stdio(0);
    cin.tie(0);
    addEdge(1, 3);
    addEdge(1, 5);
    addEdge(1, 6);
    addEdge(2, 5);
    addEdge(2, 6);
    addEdge(3, 4);
    addEdge(3, 5);
    addEdge(5, 6);

    dfs(1);

    return 0;
}
```
