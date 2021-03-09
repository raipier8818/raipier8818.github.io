---
title : Digital Logic
categories:
- Computer Science
  tags:
   - HYU CSE Grade 2
---

<details>

<summary>Number System</summary>

<div markdown="1">

<h2>Conversion to Number System</h2>

<h4>Conversion to Decimal to Base-R</h4>

<br>

```python

for i in range(5):
    # 실수 입력
    N = input()

    # 소수점 부분 확인
    if('.' in N):
        A,B = map(int,N.split('.'))
    else:
        A = int(N)
        B = 0

    # r 입력
    r = int(input())

    # 0 ~ 15
    num = ['0','1','2','3','4','5','6','7','8','9','A','B','C','D','E','F'] 

    # 정수부분 변환
    ans_one = []

    # 소수부분 변환
    ans_two = []


    # 정수 부분을 r진수로 변환하는 과정
    while(A != 0):
        C = A % r
        A = int(A/r)

        ans_one.append(num[C])

    # 정수 부분을 역순으로 정렬
    if(len(ans_one) != 0):
        ans_one.reverse()

    # 정수부분이 없을 때 0을 추가
    else:
        ans_one.append('0')

    # B를 소수로 변환
    B = B / 10**len(str(B))
    count = 0

    # 소수 부분을 r진수로 변환하는 과정
    while(B != 0):
        # 최대 소수점 여섯자리까지
        if(count == 6):
            break
        D = int(B * r)
        B = B*r - D
        ans_two.append(num[D])
        count += 1

    # 정수 부분 출력
    for i in ans_one:
        print(i, end="")

    # 소수점 출력
    if(len(ans_two) != 0):
        print('.',end="")

    # 소수 부분 출력
    for i in ans_two:
        print(i, end="")
    print()

```

</div>


</details>