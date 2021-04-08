---
layout: post
title: Programmers-02
category: study
image:
  path: /assets/study/programmers.png
related_posts:
  - study\_posts\2021-04-07-programmers-01.md
description: >
  Programmers Algorithm Study from level 1
---


- Table of Contents
{:toc .large-only}

## 체육복
- [프로그래머스 사이트](https://programmers.co.kr/learn/courses/30/lessons/42862?language=python3)
- level : 1

```python
def solution(n, lost, reserve):
    answer = 0
    new_lost = []
    for i, l in enumerate(lost):
        if l in reserve:
            reserve.pop(reserve.index(l))
        else:
            new_lost.append(l)

    for i, l in enumerate(new_lost):
        if l-1 in reserve:
            answer += 1
            reserve.pop(reserve.index(l-1))
        elif l+1 in reserve:
            answer += 1
            reserve.pop(reserve.index(l+1))

    return n + answer - len(new_lost)
```


## K번째수
- [프로그래머스 사이트](https://programmers.co.kr/learn/courses/30/lessons/42748?language=python3)
- level : 1

```python
def solution(array, commands):
    answer = []
    for command in commands:
        i, j, n = command
        answer.append(sorted(array[i-1:j])[n-1])
    return answer
```

## 2016년
- [프로그래머스 사이트](https://programmers.co.kr/learn/courses/30/lessons/12901?language=python3)
- level : 1

```python
def solution(a, b):
    answer = ''
    week = ['FRI', 'SAT', 'SUN', 'MON', 'TUE', 'WED', 'THU']
    month_31 = {1, 3, 5, 7, 8, 10, 12}
    date = b - 1
    for month in range(1, a):
        if month in month_31:
            date += 31
        elif month == 2:
            date += 29
        else:
            date += 30
    return week[date % 7]
```


## 3진법 뒤집기
- [프로그래머스 사이트](https://programmers.co.kr/learn/courses/30/lessons/68935?language=python3)
- level : 1

```python
def solution(n):
    answer = 0
    tri = []
    while n > 0:
        tri.append(n % 3)
        n //= 3
    tri = "".join(list(map(str, tri)))
    answer = int(tri, 3)
    return answer
```

## 가운데 글자 가져오기
- [프로그래머스 사이트](https://programmers.co.kr/learn/courses/30/lessons/12903?language=python3)
- level : 1

```python
def solution(s):
    length = len(s)
    if length % 2 == 0:
        return s[length//2-1:length//2+1]
    else:
        return s[length//2]
```
