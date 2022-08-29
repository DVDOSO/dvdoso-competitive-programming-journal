---
title: "Sieve of Eratosthenes"
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

const int MM = 1e6+6;
bool sieve[MM];

void isPrime(int x){
    cout << x << " is " << (sieve[x]? "Prime\n" : "Not Prime\n");
}

int main(){
    ios::sync_with_stdio(0);
    cin.tie(0);

    MEM(sieve, true);

    sieve[0] = sieve[1] = false;

    for(int i = 2; i*i < MM; i++){
        for(int j = i+i; j < MM; j+=i){
            sieve[j] = false;
        }
    }

    for(int i = 0; i < 30; i++){
        isPrime(i);
    }

    return 0;
}
```

```
0 is Not Prime
1 is Not Prime
2 is Prime
3 is Prime
4 is Not Prime
5 is Prime
6 is Not Prime
7 is Prime
8 is Not Prime
9 is Not Prime
10 is Not Prime
11 is Prime
12 is Not Prime
13 is Prime
14 is Not Prime
15 is Not Prime
16 is Not Prime
17 is Prime
18 is Not Prime
19 is Prime
20 is Not Prime
21 is Not Prime
22 is Not Prime
23 is Prime
24 is Not Prime
25 is Not Prime
26 is Not Prime
27 is Not Prime
28 is Not Prime
29 is Prime
```
