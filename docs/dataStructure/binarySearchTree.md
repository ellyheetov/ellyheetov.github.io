---
layout: default
title: Binary Search Tree
parent: Data Structure 
nav_order: 4
---

# Binary Search Tree(BST)

* [이진탐색트리(Binary Search Tree)란?](#이진탐색트리(Binary-Search-Tree)란?)
* [BST의 특성](#BST의-특성)
* [Operation](#Operation)
    * [Insert](#Insert)
    * [Delete](#Delete)
        * [삭제하려는 노드가 단말노드일 경우](#삭제하려는-노드가-단말노드일-경우)
        * [삭제하려는 노드가 하나의 서브트리만 가지는 경우](#삭제하려는-노드가-하나의-서브트리만-가지는-경우)
        * [삭제하려는 노드가 두 개의 서브트리를 모두 가지고 있는 경우](#삭제하려는-노드가-두-개의-서브트리를-모두-가지고-있는-경우)
* [BST의 시간 복잡도 및 한계점](#BST의-시간-복잡도-및-한계점)


## 이진탐색트리(Binary Search Tree)란?
이진탐색트리란 이진탐색(Binanry Search)와 연결리스트(Linked list)를 결합한 자료구조의 일종이다. 이진탐색의 효율적인 탐색능력을 유지하면서도, 빈번한 자료의 삽입과 삭제를 가능하게끔 고안되었다.

이진탐색의 경우 탐색에 소요되는 시간은 ```O(logN)```으로 빠르지만, 자료의 삽입과 삭제가 불가능하다. 연결리스트의 경우 삽입과 삭제는 ```O(1)``` 만에 가능하지만, 탐색의 경우 ```O(N)```의 시간이 소요된다. 이 둘의 장점을 살리고자 설계된 것이 이진탐색트리이다.

## BST의 특성

<img width=300 src="https://leetcode.com/explore/learn/card/introduction-to-data-structure-binary-search-tree/140/introduction-to-a-bst/Figures/binary_search_tree/BST_example.png">

- 각 노드의 왼쪽 서브트리에는 해당 노드의 값보다 작은 값을 지닌 노드들로 이루어져 있다.
- 각 노드의 오른쪽 서브트리에는 해당 노드의 값보다 큰 값을 지닌 노드들로 이루어져 있다.
- 중복된 노드가 없어야 한다.
- 왼쪽 서브트리, 오른쪽 서브트리 또한 이진탐색트리이다.

## Operation

### Insert

원하는 값을 넣기 위해서는 들어갈 특정 위치를 먼저 알아내야 한다. 또한, 내가 넣고자 하는 데이터가 이미 존재하는 것일 수도 있기 때문에 먼저 탐색을 해야한다. 결과적으로 탐색을 실패한 위치가 새로운 노드를 삽입하는 위치가 된다. 

### Delete

삭제도 삽입과 마찬가지로 내가 삭제하고자 하는 값이 어느 위치에 있는지를 먼저 탐색해야한다. 노드를 탐색했다면, 아래의 3가지 경우를 고려해야 한다. 삭제시 발생할 수 있는 상황 3가지다.

- 삭제하려는 노드가 단말노드일 경우 (자식 노드가 없을 경우) (no child)
- 삭제하려는 노드가 하나의 서브트리만 가지는 경우 (왼쪽 혹은 오른쪽 둘 중 하나만) (one child)
- 삭제하려는 노드가 두 개의 서브트리를 모두 가지고 있는 경우 (two child)

#### 삭제하려는 노드가 단말노드일 경우

부모노드를 찾아서 부모 노트 안의 해당 링크 필드를 NULL로 만들어 연결을 끊어주면 된다.
동적으로 할당된 노드였을 경우, 메모리 반납을 하고 링크필드를 NULL로 만들어주면 된다.

#### 삭제하려는 노드가 하나의 서브트리만 가지는 경우

<img width=300 src="https://leetcode.com/explore/learn/card/introduction-to-data-structure-binary-search-tree/140/introduction-to-a-bst/Figures/binary_search_tree/BST_example.png">

위와 같은 예시에서 6을 삭제 하고자 한다면, 5의 오른쪽 link를 7을 가리키게 수정하면 된다. 동적할당된 노드였다면, 6을 먼저 반납해주고 부모의 오른쪽 링크에 7을 붙여주면된다.

#### 삭제하려는 노드가 두 개의 서브트리를 모두 가지고 있는 경우

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile3.uf.tistory.com%2Fimage%2F99CE0533598965C70117C3">


위와 같은 예시에서 18을 삭제하려고 한다. 삭제한 이후에 35의 left 에는 어떤 노드를 연결시켜야 할까? 왼쪽 서브트리에서 가장 큰 값, 혹은 오른쪽 서브트리에 있는 가장 작은 값을 연결시켜 주어야 한다.

## BST의 시간 복잡도 및 한계점

평균적인 경우 이진 탐색 트리에서의 탐색, 삽입, 삭제 연산의 시간복잡도는 ```O(h)``` = ```O(logN)```이 된다. 

하지만, 균형을 이루지 않는 경사 이진 트리의 경우 N개의 노드르 가지는 트리의 높이는 ```O(N)```과 같게 되어 탐색, 삽입, 삭제시 선형 탐색과 동일하게 ```O(N)```이 나오기도 한다.

<img src="https://www.gatevidyalay.com/wp-content/uploads/2018/07/Skewed-Binary-Tree-Example.png">

경사 이진 트리(편향 트리)의 경우 선형 탐색에 비하여 시간적으로 전혀 이득이 없다. 이러한 최악의 경우를 방지하기 위해 트리의 높이를 균형있게 만드는 것이 필요하다. 

균형을 잡기 위한 트리 구조의 재조정을 ```Rebalancing```이라 한다. 
이러한 기법이 ```AVL 트리```, ```Red Black Tree```를 등 여러 기법들이 존재한다.
