---
title: "Prefix Sum Array"
date: 2022-08-29
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

int main(){
    ios::sync_with_stdio(0);
    cin.tie(0);

    int arr[] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
    int psa[] = {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0};

    for(int i = 1; i <= 10; i++){
        psa[i] = arr[i] + psa[i-1];
    }

    //Query sum from index 4-8
    cout << psa[8] - psa[4-1] << '\n';

    return 0;
}
```
