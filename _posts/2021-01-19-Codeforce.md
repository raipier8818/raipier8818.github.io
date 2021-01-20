---
title : Codeforce Round 696
categories:
 - PS
tags:
 - Codeforce
---

<details>

<summary>A번</summary>

<div markdown="1">

<br>

<h2> 풀이 </h2>


`d[i]`의 경우는 `b[i]`의 경우에 따라 0,1,2중 하나로 결정된다. <br><br>
`a[0]`에는 `b[0]`이랑 상관없이 1이 올 수 있다. 그 다음부터는 `d[i-1]`의 경우와 `b[i]`의 경우에 따라 달라진다.<br>

1. `d[i-1] == 0`이면, `b[i]`의 값과 상관없이 `a[i]`의 값은 항상 1이다.
2. `d[i-1] == 1`이고 `b[i] == 0`이면, `a[i]`의 값은 0이다.
3. `d[i-1] == 1`이고 `b[i] == 1`이면, `a[i]`의 값은 1이다.
4. `d[i-1] == 2`이고 `b[i] == 0`이면, `a[i]`의 값은 1이다.
5. `d[i-1] == 2`이고 `b[i] == 1`이면, `a[i]`의 값은 0이다.

이 조건을 만족한다면 연속하는 수가 없는 d의 최댓값을 구할 수 있다.<br>



```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> a;
vector<int> b;
vector<int> v;

int n,t;


int main(){
    ios::sync_with_stdio(0);
    cin.tie(0);

    cin >> t;
    while(t--){
        cin >> n;
        string num;
        cin >> num;

        a.clear();
        d.clear();

        a.resize(n);
        d.resize(n);
        
        b.clear();

        for(int i = 0; i < n; i++){
            if(num[i] == '0') b.push_back(0);
            else b.push_back(1);
        }

        a[0] = 1;
        d[0] = b[0] + a[0];
        for(int i = 1; i < n; i++){
            if(d[i-1] == 0){
                a[i] = 1;
            }
            else if(d[i-1] == 1){
                if(b[i] == 0){
                    a[i] = 0;
                }else{
                    a[i] = 1;
                }
            }
            else{
                if(b[i] == 1){
                    a[i] = 0;
                }else{
                    a[i] = 1;
                }
            }
            d[i] = a[i] + b[i];
        }

        for(int i = 0; i < n; i++){
            cout << a[i];
        }
        cout << "\n";
    }
}

```

</div>


</details>


<details>

<summary>B번</summary>

<div markdown="1">

<br>

<h2> 풀이 </h2>

약수의 개수가 4개 이상이고, 인접한 약수 사이의 차이가 d이상인 수들 중 최솟값을 찾는 것이다. <br>
예를 들어, n의 약수의 집합을 S라고 하면, 1과 n은 S의 원소일 수 밖에 없다.<br>
따라서, 위 조건을 만족하는 n은, d보다 큰 소수 a와, a보다 d이상 큰 소수 b를 곱하면 구할 수 있다.

여기서 주의할 점은 소수를 미리 구해야 한다는 것이다. d가 최대 10000이므로, 넉넉하게 25000정도는 잡아야 한다.


```cpp
#include <bits/stdc++.h>
using namespace std;
 
int t, d;
int decimal[30000];
 
void findDecimal(){
    decimal[2] = 0;
    for(int i = 3; i <= 30000; i++){
        for(int j = 2; j*j <= i; j++){
            if(i % j == 0){
                decimal[i] = -1;
                break;
            }
        }
    }
}
 
 
int main(){
    ios::sync_with_stdio(0);
    cin.tie(0);
    
    cin >> t;
    
    findDecimal();
    
    while(t--){
        cin >> d;
        int first, second;

        first = d+1;
        while(true){
            if(decimal[first] == 0) break;
            first++;
        }
        second = first + d;
        while(true){
            if(decimal[second] == 0) break;
            second++;
        }
 
        cout << first * second << "\n";
    }
 
 
}
```

</div>


</details>