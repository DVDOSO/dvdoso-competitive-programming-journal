---
title: "Fenwick Tree (Binary Indexed Tree)"
date: 2022-09-10
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

const int MM = 17;
ll bit[MM];

void update(int val, int idx){
    for(int i = idx; i < MM; i+=i&-i){
        bit[i] += val;
    }
}

ll query(int idx){
    ll ret = 0;
    for(int i = idx; i > 0; i-=i&-i){
        ret += bit[i];
    }
    return ret;
}

int main(){
    ios::sync_with_stdio(0);
    cin.tie(0);
    
    for(int i = 1; i <= 16; i++){
        update(i, i);
    }

    cout << query(10) << '\n'; //sums [1-10]
    cout << query(7)-query(4) << '\n'; //sums (4-7]

    return 0;
}
```

Practice Problems:
- [Binary Indexed Tree Test](https://dmoj.ca/problem/ds1)
- [CCC '05 S5 - Pinball Ranking](https://dmoj.ca/problem/ccc05s5)
