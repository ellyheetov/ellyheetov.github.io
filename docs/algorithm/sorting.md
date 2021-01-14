---
layout: default
title: Sorting
parent: Algorithm
nav_order: 2
---

# Sorting Algorithm

* [Bubble Sort](#Buble-Sort)
* [Selection Sort](#Selection-Sort)
* [Insertion Sort](#Insertion-Sort)
* [Merge Sort](#Merge-Sort)
* [Heap Sort](#Heap-Sort)
* [Quick Sort](#Quick-Sort)
* [Counting Sort](#Counting-Sort)
* [Radix Sort](#Radix-Sort)

<img src="https://d2.naver.com/content/images/2020/01/img.png">   
 * stable - 동일한 정렬기준을 가진 것은 정렬하기 전의 순서와 정렬 후의 순서가 같다.

## Buble Sort

## Selection Sort

## Insertion Sort

## Merge Sort

Merge Sort는 Divide and Conquer 방식을 이용한다. 정렬하고자 하는 배열을 작은 단위로 나누어 정렬하고자 하는 배열의 크기를 줄이는 원리를 사용한다. 더이상 나누어 지지 않을 만큼 쪼개며, 더이상 나눌 수 없는 경우 가지 자신(원소)를 반환한다. 원소가 하나인 경우에는 정렬할 필요가 없기 때문이다. 이렇게 반환된 값을 결합(combine)할때 비교가 일어난다. 비교 결과를 기반으로 정렬되어 임시 배열에 저장된다. 

리스트의 길이가 1 이하이면 이미 정렬된 것으로 본다. 그렇지 않은 경우에는  
- ```분할(divide)``` : 정렬되지 않은 리스트를 절반으로 잘라 비슷한 크기의 두 부분 리스트로 나눈다.
- ```정복(conquer)``` : 각 부분 리스트를 재귀적으로 합병 정렬을 이용해 정렬한다.
- ```결합(combine)``` : 두 부분 리스트를 다시 하나의 정렬된 리스트로 합병한다. 이때 정렬 결과가 임시배열에 저장된다.
- ```복사(copy)``` : 임시 배열에 저장된 결과를 원래 배열에 복사한다.

Time Complexity: O(NlogN)  
Space Compexity: O(NlogN)

## Heap Sort

Heap 트리 구조를 이용한 정렬방법이다. 주어진 데이터로 힙을 만든 후, 루트의 값을 가장 마지막으로 보낸다. (이때 힙의 사이즈를 하나 줄여야한다.) 마지막으로 옮긴 값은 이미 정렬된 상태임을 뜻한다. 루트가 비어있으므로 다시 힙 트리를 구성하기 위해 heapify를 진행한다. 이와 같은 과정을 반복하면 추가 공간 할당 없이 정렬을 수행할 수 있다.

DownHeap과 UpHeap의 과정은 한 노드에 대해 logN만큼 내려갈 수 있다. 내려가면서 2번의 비교를 진행하므로 2logN이다. N개에 데이터에 대해서 2logN번의 비교를 수행하므로 즉, 2NlogN번의 비교를 수행하게 된다. 따라서 힙 정렬의 시간 복잡도는 2NlogN + N(초기 힙을 생성하는 과정)이된다.

Time Complexity: O(NlogN)  
Space Compexity: O(1)

## Quick Sort

Sorting 중에서도 가장 빠르기 때문에 Quick sort라는 이름이 붙여졌다.
Quick Sort는 Divide and Conquer 방식을 이용한다. 오름차순으로 정렬할 경우 pivot을 기준으로 좌측에는 pivot보다 작은 값이, 우측에는 pivot보다 큰 값을 가진다. 이렇게 나눈 좌 우 partition에 대하여 재귀적으로 또다시 quick sort를 진행한다. 한가지 주의할 점은 partition을 나누는 과정에서 pivot은 다음 partition에 추가되어서는 안된다. 이미 partition과정에서 pivot은 정렬된 위치를 찾았기 때문이다.
더이상 분할 할 수 없을때까지 반복한 후 정렬된 결과를 얻을 수 있다.

Quick sort는 2개의 partition으로 나누어 sorting을 진행하므로 O(NlogN)의 시간복잡도를 갖는다. 하지만, 최악의 경우 O(N^2)의 시간복잡도를 가질 수 있다. (pivot이 배열에서 항상 작은 값, 큰 값이 선택될 수 있기 때문)

Time Complexity: O(NlogN)  
Space Compexity: O(N)

## Counting Sort

## Radix Sort


# Sorting Algorithm 비교하기

## Merge Sort VS Quick Sort

### Merge Sort
- Stable
- 성능은 퀵 정렬보다 전반적으로 뒤떨어짐
- 최대의 장점은 데이터의 상태에 별 영향을 받지 않는다는 것
- 추가 공간 필요

### Quick Sort
- Unstable
- 참조의 지역성 성질을 가지고 있음
- 추가 공간 필요 없음

*참조의 지역성 : 짧은 시간동안 반복적으로 접근하는 데이터
지역성을 띄는 데이터들은 더 빨리 접근하기 위해서 캐쉬라는 하드웨어를 사용한다.



#### Reference

https://ko.wikipedia.org/wiki/%ED%95%A9%EB%B3%91_%EC%A0%95%EB%A0%AC  
https://zeddios.tistory.com/56  
https://ratsgo.github.io/data%20structure&algorithm/2017/09/27/heapsort/    
https://d2.naver.com/helloworld/0315536
