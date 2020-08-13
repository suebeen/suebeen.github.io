---
title: "백준 10844번: 쉬운 계단 수"
date: 2020-08-13 18:42:00 -0400
categories: baekjoon algorithm dp python
---

### 문제
45656이란 수를 보자.

이 수는 인접한 모든 자리수의 차이가 1이 난다. 이런 수를 계단 수라고 한다.

세준이는 수의 길이가 N인 계단 수가 몇 개 있는지 궁금해졌다.

N이 주어질 때, 길이가 N인 계단 수가 총 몇 개 있는지 구하는 프로그램을 작성하시오. (0으로 시작하는 수는 없다.)

### 입력
첫째 줄에 N이 주어진다. N은 1보다 크거나 같고, 100보다 작거나 같은 자연수이다.

### 출력
첫째 줄에 정답을 1,000,000,000으로 나눈 나머지를 출력한다.

```python
N = int(input())
num_arr =  [[0 for i in range(10)] for j in range(N+1)]
for i in range(10):
    num_arr[1][i] = 1

for i in range(2, N+1):
    for j in range(10):
        if j == 0:
            num_arr[i][j] = num_arr[i-1][1]
        elif j == 9:
            num_arr[i][j] = num_arr[i-1][8]
        else :
            num_arr[i][j] = num_arr[i-1][j-1] + num_arr[i-1][j+1]

print(int((sum(num_arr[N])-num_arr[N][0]) % 1000000000))
```

문제출처 : [baekjoon10844]

[baekjoon10844]: https://www.acmicpc.net/problem/10844
