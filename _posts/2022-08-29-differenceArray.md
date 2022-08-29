---
title: "Difference Array"
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

    int arr[] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 0};
    int dif[12] = {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0};

    for(int i = 1; i <= 10; i++){
        dif[i] = arr[i] - arr[i-1];
    }

    //Update index 4-8 by 1
    dif[4]++; dif[8+1]--;

    //Run prefix sum array
    for(int i = 1; i <= 10; i++){
        dif[i] += dif[i-1];
    }

    //psa(dif(arr)) == arr; dif(psa(arr)) == arr
    for(int i = 1; i <= 10; i++){
        cout << dif[i] << ' ';
    }

    return 0;
}
```
