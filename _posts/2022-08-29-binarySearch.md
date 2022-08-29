---
title: "Breadth First Search (BFS)"
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

    int arr[] = {1, 2, 3, 4, 5, 6, 7, 9, 10, 11};

    int l = 0, r = 9, target = 8;

    while(l <= r){
        int mid = (l+r)/2;
        if(arr[mid] == target){
            cout << "Found\n";
            break;
        }
        else if(arr[mid] < target){
            l = mid + 1;
        }
        else{
            r = mid - 1;
        }
    }

    return 0;
}
```
