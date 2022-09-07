---
title: "Levenshtein Distance"
date: 2022-09-07
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

/*
a -> b
dp[A][B] -> A is length of a, B is length of b
dp[i][j] -> best answer for a[1,i] and b[1,j]
if i == 0: must insert all characters -> cost of insert * j
if j == 0: must delete all characters -> cost of delete * i
if a[i] == b[j]: do nothing -> dp[i][j] = dp[i-1][j-1]
else: select best answer{
    insert: dp[i][j-1] + cost of insert
    delete: dp[i-1][j] + cost of delete
    replace: dp[i-1][j-1] + cost of replace
}
*/

const int MM = 1e3+4;
int D, I, R, dp[MM][MM];
string a, b;

int main(){
    ios::sync_with_stdio(0);
    cin.tie(0);
    
    cin >> D >> I >> R >> a >> b;
    for(int i = 1; i <= a.size(); i++){
        dp[i][0] = i*D;
    }
    for(int i = 1; i <= b.size(); i++){
        dp[0][i] = i*I;
    }

    for(int i = 1; i <= a.size(); i++){
        for(int j = 1; j <= b.size(); j++){
            if(a[i-1] != b[j-1]){
                dp[i][j] = min(dp[i-1][j] + D, min(dp[i][j-1] + I, dp[i-1][j-1] + R));
            }
            else dp[i][j] = dp[i-1][j-1];
        }
    }

    /*for(int i = 0; i <= a.size(); i++){
        for(int j = 0; j <= b.size(); j++){
            cout << dp[i][j] << '\t';
        }
        cout << '\n';
    }*/

    cout << dp[a.size()][b.size()] << '\n';

    return 0;
}
```
Practice Problems:
- [VM7WC '16 #4 Gold - Restoring Reputation](https://dmoj.ca/problem/vmss7wc16c4p3)
