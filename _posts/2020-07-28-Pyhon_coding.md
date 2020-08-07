---
layout: post
title:  "Python HackerRank : Forming a Magic Square"
date:   2020-07-04 15:50:46 +0900
categories: Python
tag: Algorithm
---

`#Data-ssung #coding # Algorithm`

목적 : Magic Square 완성하기 
---

문제
===

- 3 X 3 magic square 만들기: 각 열과 행 그리고 대각 원소의 합이 항상 15가 되는 matrix
- input 3 X 3 matrix가 1부터 9까지 수가 한 번씩만 들어가도록  3 X 3 magic square 바꾸기
- a->b 원소를 바꿀때 |a-b|의 값이 가장 작게 되도록 3 X 3 magic square 만들기

Solution
===
- 3x3 매직스퀘어 모든 열과 행, 대각 행렬의 합이 15가 되는 경우의 수 8가지 입력 (직접해도 되고, 코딩해도 되고)
- input의 값을 8가지 경우와 차이를 구해서 가장 작은 값을 return

code
===
```Python
# version 1: magic square 경우의 수를 직접 입력하기 
def formingMagicSquare(s):

    # magic square 경우의 수
    possibilities = [[8,1,6,3,5,7,4,9,2],
               [6,1,8,7,5,3,2,9,4],
               [4,9,2,3,5,7,8,1,6],
               [2,9,4,7,5,3,6,1,8],
               [8,3,4,1,5,9,6,7,2],
               [4,3,8,9,5,1,2,7,6],
               [6,7,2,1,5,9,8,3,4],
               [2,7,6,9,5,1,4,3,8]]
    
    # input 리스트 만들기
    temp = []
    for i in range(len(s)):
        temp += s[i]
        
    # magic square 경우의 수와 input 리스트 비교
    com_min = sum(range(10))

    for p in possibilities:
        com = 0
        for i in range(len(temp)):
            com += abs(temp[i]-p[i])

        if com < com_min:
            com_min = com
    
    return com_min
```

```Python
# version2: magic square 직접 코딩 해보기
def formingMagicSquare(s):
    
    #  magic square 경우의 수 
    possibilities = []
    for a in range(1, 10):
        for b in range(1, 10):
            if set([a, 15-a-b, b, 5+b-a, 5, 5+a-b, 10-b, a+b-5, 10-a]) == set(range(1, 10)):
                possibilities.append([a, 15-a-b, b,
                                      5+b-a, 5, 5+a-b,
                                      10-b, a+b-5, 10-a])

    # input 리스트 만들기
    temp = []
    for i in range(len(s)):
        temp += s[i]

    # magic square 경우의 수와 input 리스트 비교
    com_min = sum(range(10))

    for p in possibilities:
        com = 0
        for i in range(len(temp)):
            com += abs(temp[i]-p[i])

        if com < com_min:
            com_min = com
    
    return com_min
```


#### 문제는 [해커랭크][H]를 참고하였습니다.

[H]: https://www.hackerrank.com/challenges/magic-square-forming/problem