---
title: "Largest Square In Grid Without Holes"
date: 2022-09-08
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

const int MM = 1003;
int g[MM][MM], dp[MM][MM], n;

int main(){
    ios::sync_with_stdio(0);
    cin.tie(0);
    
    int ans = -1, cnt = 0;

    cin >> n;
    for(int i = 1; i <= n; i++){
        for(int j = 1; j <= n; j++){
            cin >> g[i][j];
        }
    }

    for(int i = 1; i <= n; i++){
        for(int j = 1; j <= n; j++){
            if(g[i][j] == 0) dp[i][j] = 0;
            else dp[i][j] = min(dp[i][j-1], min(dp[i-1][j], dp[i-1][j-1])) + 1;
            ans = max(ans, dp[i][j]);
        }
    }

    //ans is the dimension of the square

    for(int i = 1; i <= n; i++){
        for(int j = 1; j <= n; j++){
            if(dp[i][j] == ans) cnt++;
        }
    }

    //cnt is the # of such squares that can be made

    cout << ans << ' ' << cnt << '\n';

    return 0;
}
```

Practice Problems:
- [IOI '14 Practice Task 1 - Square](https://dmoj.ca/problem/ioi14pp1)
