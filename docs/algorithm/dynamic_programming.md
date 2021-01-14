---
layout: default
title: Dynamic Programming
parent: Algorithm
nav_order: 1
---

# DP(Dynamic Programming)

* [Dynamic Programming(동적프로그래밍)이란?](#Dynamic-Programming(동적프로그래밍)이란?)
* [Divide and Conqure(분할정복)과 비교](#Divide-and-Conqure(분할정복)과-비교)
* [Dynamic Programming의 조건](#Dynamic-Programming의-조건)
* [Memoization](#Memoization)
* [구현방법](#구현방법)
    * [Bottom-up](#Bottom-up)
    * [Top-down](#Top-down)


## Dynamic Programming(동적프로그래밍)이란?
큰 문제를 한번에 해결하기 힘들 때 작은 여러개의 문제로 나누어서 푸는 기법중에 하나이다. 작은 문제들을 풀다보면 같은 문제들을 반복해서 푸는 경우가 발생한다. 그 문제들을 매번 재계산 하지 않고 값을 저장해 두었다가(Memoization) 재사용하는 기법이 동적 프로그래밍이다.

## Divide and Conqure(분할정복)과 비교
큰 문제를 여러개의 작은 문제를 나누어 푼다는 개념에서 Divide and Conqure의 개념과 비슷하다. 하지만, 결정적인 차이점이 있다. 작은 문제가 중복해서 일어나느냐 일어나지 않느냐의 차이이다. 분할정복의 경우 단지 큰 문제를 해결하기 작은 문제로 나누어 푸는 것이다. 작은 문제에서 반복이 일어나지 않는 다는 점이다. 반면, 동적 프로그래밍 기법의 경우 작은 문제들이 반복되는 것(답이 바뀌지 않음)을 이용해 풀어나가는 기법이다.

작은 문제로 나누었을때 해당 문제를 단 한번만 풀어야 한다. 따라서 정답을 구한 작은 문제를 어딘가에 메모해 놓는다. 다시 그보다 큰 문제를 풀어나갈때 똑같은 작은 문제가 나타난다면 앞서 메모한 작은 문제의 결과값을 이용하게된다.

## Dynamic Programming의 조건
- 작은 문제가 반복해서 일어난다.
- 같은 문제는 구할 때마다 정답이 같다.

위와 같은 조건을 만족하느 경우에만 동적 프로그래밍을 사용할 수 있다.

## Memoization
앞서 말했듯 동적프로그래밍에서는 작은 문제들이 반복되고 이 작은 문제들의 결과값이 항상 같다. 때문에 이점을 이용하여 한번 계산한 작은 문제들을 저장해 놓고 다시 사용한다. 이것을 Memoization이라고 한다.

## 구현방법

### Bottom-up
작은 문제부터 차근차근 구해나아가는 방법이다.

### Top-down
재귀함수로 구현하는 경우가 대부분 Top-down이라고 보면된다. 큰 문제를 풀 때 작은 문제가 아직 풀리지 않았다면 그제서야 작은문제를 해결한다.

#### Reference
https://galid1.tistory.com/507
