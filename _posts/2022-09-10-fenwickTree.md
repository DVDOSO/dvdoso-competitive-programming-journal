---
title: "Fenwick Tree (Binary Indexed Tree)"
date: 2022-09-10
---

### Sample Problem:  
You are given an array "a" with n cells.  
You must support two operations: 
```
update(x, i)    a[i] += x  
query(x)        a[1] + a[2] + ... a[x]  
```
  
If we use a regular array,  
```
update(x, i)    O(1)  
query(x)        O(n)  
```
  
If we use a prefix sum array, 
```
update(x, i)    O(n)  
query(x)        O(1)  
```
  
If we use a Fenwick tree,  
```
update(x, i)    O(logn)  
query(x)        O(logn)  
```
  
Best of both worlds!  
  
### Storage  
We store the Fenwick tree inside of an array of size N  
  
```
bit[1] = a[1]                       (1)   Binary value of i  
bit[2] = a[1] + a[2]                (10)  
bit[3] = a[3]                       (11)  
bit[4] = a[1] + a[2] + a[3] + a[4]  (100)  
bit[5] = a[5]                       (101)  
bit[6] = a[5] + a[6]                (110)  
bit[7] = a[7]                       (111)  
bit[8] = a[1] + a[2] + a[3] + a[4] 
       + a[5] + a[6] + a[7] + a[8]  (1000)  
```
  
Every cell[i] stores the sum of the last r values where r is the value of the last bit 1 in i's binary  
  
To get last bit 1: use two's complement  
`i&-i`  
  
### query()  
We don't need to query every cell   
```
query(13) =   
bit[13] + bit[12] + bit[8] =   
bit[1101] + bit[1100] + bit[1000]  
```
  
Start from the index and remove the last bit 1 every time until index = 0  
  
### update()  
Similar idea to query()  
```
update(1, 5)  
bit[5] += 1     bit[00101]  
bit[6] += 1     bit[00110]  
bit[8] += 1     bit[01000]  
bit[16] += 1    bit[10000]  
... until n  
```
  
Start from the index and add the last bit 1 every time until index > n  
  
### Sample Code  
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

### Counting Inversions With a Fenwick Tree
The amount of inversions in an array is the number of cases where `a[i] < a[j]` and `i > j`  
We can count the number of inversions in an array using a Fenwick tree  
Use the Fenwick tree like a freqency array  

Loop through every element of the original array. For each element: 
1. For each element i, `query(maxValue) - query(i)` will give the number of elements strictly greater than it currently in the array
2. Add `query(maxValue) - query(i)` to the total amount of inversions
3. `update(1, i)`  
  
### Sample Code
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

const int MM = 17; //Max possible number in the array + 1
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
    
    int a[17] = {0, 8, 3, 7, 10, 15, 13, 16, 4, 2, 6, 1, 11, 5, 12, 9, 14};

    int total = 0;
    for(int i = 1; i <= 16; i++){
        total += query(MM-1) - query(a[i]);
        update(1, a[i]);
    }
    
    cout << "The number of inversions is " << total << '\n'; //55

    return 0;
}
```

### Practice Problems:
- [Binary Indexed Tree Test](https://dmoj.ca/problem/ds1)
- [CCC '05 S5 - Pinball Ranking](https://dmoj.ca/problem/ccc05s5)
- [DMOPC '16 Contest 1 P5 - Blood Tubes](https://dmoj.ca/problem/dmopc16c1p5)
- [DMOPC '18 Contest 4 P4 - Dr. Henri and Lab Data](https://dmoj.ca/problem/dmopc18c4p4)
- [COCI '08 Regional #6 Cvjetici](https://dmoj.ca/problem/crci08p6)
- [DMOPC '14 Contest 2 P6 - Selective Cutting](https://dmoj.ca/submission/4870870)
- [DMOPC '19 Contest 3 P3 - Majority](https://dmoj.ca/problem/dmopc19c3p3)
- [IOI '01 P1 - Mobile Phones](https://dmoj.ca/problem/ioi01p1)
- [Checkerboard Summation (Hard)](https://dmoj.ca/problem/checkerhard)
