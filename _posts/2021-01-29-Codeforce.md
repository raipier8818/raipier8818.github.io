---
title : Codeforce Round 698
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

모든 공에 색을 칠하고, 한가지 색상을 골랐을 때, 그 색상으로 칠해진 공들은 전부 증가하는 경우여야 한다.<br>
따라서 이 문제는 모든 a에서 가장 많이 나타난 수의 개수를 구하면 된다. <br>
그 수의 개수만큼 색을 하나씩 칠한다면, 나머지 공들의 경우는 생각할 필요가 없다.

<br>

```cpp
#include <bits/stdc++.h>
using namespace std;

int t,n;
int ball[1000];

int main(){
    ios::sync_with_stdio(0);
    cin.tie(0);
    
    cin >> t;
    while(t--){
        cin >> n;
        memset(ball,0,sizeof(ball));

        int count = 1;
        int ans = 0;

        for(int i = 0; i < n; i++){
            int b;
            cin >> b;

            ball[b-1] += 1;
        }

        for(int i = 0; i < n; i++){
            ans = max(ans,ball[i]);
        }

        cout << ans << "\n";

    }
 
 
}
```


</div>


</details>