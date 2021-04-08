---
layout: post
title: Programmers-01
category: study
image:
  path: /assets/study/programmers.png
related_posts:
  - study\_posts\2021-04-07-programmers-02.md
description: >
  Programmers Algorithm Study from level 1
---


- Table of Contents
{:toc .large-only}

## 크레인 인형뽑기
- [프로그래머스 사이트](https://programmers.co.kr/learn/courses/30/lessons/64061)
- level : 1


```python
def solution(board, moves):
    answer = 0
    col = [[] for _ in range(len(board))]
    for row in board[::-1]:
        for i, doll in enumerate(row):
            if doll != 0:
                col[i].append(doll)

    basket = []
    for move in moves:
        if len(col[move - 1]) <= 0:
            continue
        basket.append(col[move - 1].pop())
        if len(basket) >= 2 and basket[-2] == basket[-1]:
            basket.pop()
            basket.pop()
            answer += 2

    return answer
```


## 두개 뽑아서 더하기
- [프로그래머스 사이트](https://programmers.co.kr/learn/courses/30/lessons/68644?language=python3)
- level : 1

```python
def solution(numbers):
    answer = []
    for i, a in enumerate(numbers):
        for b in numbers[i+1:]:
            answer.append(a+b)
    answer = sorted(list(set(answer)))
    return answer
```


## 완주하지 못한 선수
- [프로그래머스 사이트](https://programmers.co.kr/learn/courses/30/lessons/42576?language=python3)
- level : 1

```python
def solution(participant, completion):
    answer = ''
    new_participant = {}
    for person in participant:
        if person not in new_participant:
            new_participant[person] = 0
        new_participant[person] += 1

    for complete in completion:
        new_participant[complete] -= 1

    for person in new_participant:
        if new_participant[person] != 0:
            answer = person
            break
    return answer
```

## 신규 아이디 추천
- [프로그래머스 사이트](https://programmers.co.kr/learn/courses/30/lessons/72410?language=python3)
- level : 1

```python
import re


def rule_1(new_id):
    out = ""
    for c in new_id:
        out += c.lower()
    return out


def rule_2(new_id):
    out = ""
    for c in new_id:
        if c.isalpha() == False and c.isdigit() == False and c not in ("-", "_", '.'):
            continue
        out += c
    return out


def rule_3(new_id):
    return re.sub("[..]+", ".", new_id)


def rule_4(new_id):
    start, end = 0, len(new_id)
    if new_id[0] == ".":
        start = 1
    if new_id[-1] == ".":
        end -= 1
    return new_id[start:end]


def rule_5(new_id):
    if len(new_id) == 0:
        return "a"
    return new_id


def rule_6(new_id):
    new_id = new_id[:15]
    new_id = rule_4(new_id)
    return new_id


def rule_7(new_id):
    if len(new_id) <= 2:
        return new_id + new_id[-1]*(3 - len(new_id))
    return new_id


def solution(new_id):
    answer = rule_1(new_id)
    answer = rule_2(answer)
    answer = rule_3(answer)
    answer = rule_4(answer)
    answer = rule_5(answer)
    answer = rule_6(answer)
    answer = rule_7(answer)
    return answer
```

## 모의고사
- [프로그래머스 사이트](https://programmers.co.kr/learn/courses/30/lessons/42840?language=python3)
- level : 1

```python
def solution(answers):
    answer = []
    person_1 = "12345"
    person_2 = "21232425"
    person_3 = "3311224455"
    checker = {1:0, 2:0, 3:0}
    for i, ans in enumerate("".join(list(map(str, answers)))):
        checker[1] += 1 if person_1[i % 5] == ans else 0
        checker[2] += 1 if person_2[i % 8] == ans else 0
        checker[3] += 1 if person_3[i % 10] == ans else 0

    _max = max(checker.values())
    for key in checker:
        if _max == checker[key]:
            answer.append(key)
    return sorted(answer)
```
