---
layout: default
title: Linked List
parent: Data Structure 
nav_order: 2
---

- [Linked List](#Linked-List)
    - [Linear List](#Linear-List)
    - [Single Linked List](#Single-Linked-List)
    - [Double Linked List](#Double-Linked-List)
    - [Circular Linked List](#Circular-Linked-List)

# Linked List
Array의 단점을 해결하기 위한 자료구조이다. 각각의 원소들은 자신 다음에 어떤 원소를 가지고 있는지 기록하고 있다. 각 원소들은 다음 원소에 대한 정보도 가지고 있어야 하므로 배열에 비해 메모리를 추가적으로 사용한다는 단점이 있다. 데이터의 중간에 삽입 및 삭제를 하더라도 전체를 돌지 않아도 이전 값과 다음값이 가르켰던 주소값만 수정하여 연결시켜 주면 된다.

### 특징
- 동적으로 메모리 사용가능
- 메모리 효율적 사용
- 데이터 재구성 용이

## Linear List
일반적인 배열 Array를 말한다.

## Single Linked List

<img src="https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2013/03/Linkedlist.png">

```c
struct LinkedList{
    int data;
    struct LinkedList *next;
};
```

### 탐색 O(N)
가장 첫번제 원소부터 찾고자 하는 원소까지 list를 따라 탐색해야 한다. 

### 삽입, 삭제 O(N)
현재 원소의 다음값을 가리키는 주소만 수정하여 연결하면 삽입과 삭제가 가능하다. 하지만, 삽입 및 삭제를 원하는 원소를 찾아야 하므로 O(N)의 시간이 소요된다.

### Array와 같은 복잡도, 그런데 왜 Linked List를 사용할까?
Tree 구조의 근간이 되는 자료구조이다. Tree에서 사용되었을 때 그 유용성이 드러난다.

### 언제 사용할까?
- 대용량 데이터를 처리해야 할 때

## Doubly Linked List
<img src="https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2014/03/DLL1.png">

```c
struct Node {
    int data;
    struct Node* next; 
    struct Node* prev;
};
```
이중 연결 리스트는 다음 원소 뿐만 아니라 이전 원소의 정보도 가지고 있다. 때문에 앞, 뒤 방향으로 탐색이 가능하다. 

## Circular Singly Linked List

<img src="https://media.geeksforgeeks.org/wp-content/uploads/CircularSinglyLinkedList.png">

```c
struct Node
{
    int data;
    struct Node *next;
};
```

일반적인 Linked List와 같은 Node를 사용 하지만 마지막 노드와 처음 노드를 연결시켜 원형으로 만든 구조이다.

### 특징
- 모든 노드가 시작점이 될 수 있다.

### 언제 사용할까?
- Queue
- 이미 할당된 메모리 공간을 삭제하고 재할당 하는 부담이 없다.
- 고급 데이터 구조를 구현하는 데 사용된다. (ex. Fibonacci Heap)
