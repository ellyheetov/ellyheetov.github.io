---
layout: default
title: Priority Queue
parent: Data Structure 
nav_order: 3
---

# Priority Queue
* [Priority Queue(우선순위 큐)란?](#Priority-Queue(우선순위-큐)란?)
* [구현방법](#구현방법)
    * [배열(Array)을 기반으로 구현](#배열(Array)을-기반으로-구현)
    * [연결 리스트(Linked List)를 기반으로 구현](#연결-리스트(Linked-List)를-기반으로-구현)
    * [힙(Heap)을 이용하는 방법](#힙(Heap)을-이용하는-방법)


## Priority Queue(우선순위 큐)란?

큐의 경우 먼저들어 간 원소가 가장 먼저 나오는 FIFO의 특성을 가지고 있다. 하지만 우선순위  큐는 원소들이 우선순위를 가지고 있어서 우선순위가 높은 원소가 가장 먼저 나오는 방식이다.

## 구현방법

- Array 
- Linked List
- Heap

### 배열(Array)을 기반으로 구현


1. 삽입 : O(N)
2. 삭제 : O(N)

단점
- 데이터 삽입 및 삭제 과정에서 데이터를 한 칸씩 당기거나 미는 연산을 계속 해야한다.
- 삽입의 위치를 찾기 위해 배열에 저장된 모든 데이터와 우선순위를 비교해야 한다.

### 연결 리스트(Linked List)를 기반으로 구현

1. 삽입 : O(N)
2. 삭제 : O(1)
 
단점
- 삽입의 위치를 찾기 위해 첫번째 노드에서 부터 우선순위를 비교해야한다.

### 힙(Heap)을 이용하는 방법

우선순위 큐는 주로 힙(Heap)을 이용해서 구현하는 것이 일반적이다.

#### 1. 삽입 : Time Complexity O(logN)
삽입은 새로운 데이터가 우선순위가 가장 낮다는 가정하에서 마지막 위치에 저장된다. 이후 제자리를 찾을 때까지 ```UpHeap``` 과정을 거치게 된다.

<img width="300" alt="스크린샷 2020-10-08 오후 1 15 55" src="https://user-images.githubusercontent.com/60229909/95414257-6757fb00-0968-11eb-93ba-c09cff34e9e1.png">
<img width="300" alt="스크린샷 2020-10-08 오후 1 18 53" src="https://user-images.githubusercontent.com/60229909/95414419-d2093680-0968-11eb-94cf-b15ba1e7eaff.png">

#### 2. 삭제 : Time Complexity O(logN)


삭제는 우선순위가 가장 높은 root 데이터를 삭제하게 된다. 빈 루트를 채우기 위해서 마지막 노드를 루트 노드의 자리로 옮긴 후 ```DownHeap```과정을 통해 제자리를 찾아간다.

<img width="300" alt="스크린샷 2020-10-08 오후 1 16 31" src="https://user-images.githubusercontent.com/60229909/95414290-7ccd2500-0968-11eb-8a8e-e93ae7efde4a.png">
<img width="300" alt="스크린샷 2020-10-08 오후 1 16 48" src="https://user-images.githubusercontent.com/60229909/95414301-86ef2380-0968-11eb-8002-c7d3e918b464.png">
<img width="300" alt="스크린샷 2020-10-08 오후 1 17 44" src="https://user-images.githubusercontent.com/60229909/95414358-a8500f80-0968-11eb-8b6f-cb1e59135439.png">

#### Reference 
https://hannom.tistory.com/36  
https://www.crocus.co.kr/379
