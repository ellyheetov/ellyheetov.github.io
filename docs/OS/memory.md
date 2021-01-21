---
layout: default
title: 메모리 구조
parent: Operating System
nav_order: 1
---

# 메모리 구조

운영체제(OS)는 메모리에(RAM)에 프로그램을 위한 공간을 할당한다. 이러한 메모리는 어떠한 구조에 대해서 알아보자.
<p align="center">
<img width="200" src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbi8l3l%2FbtqHT0cnh4Z%2FdFE5Pm9zRmlLFe1XGdKFGK%2Fimg.png">
</p>

## 코드(Code)영역

- 작성한 소스코드가 기계어 형태로 저장된다.
- Compile time에 결정된다.
- Compile time에 결정되기 때문에 무한히 할당 할 수 없다.
- 중간에 코드가 변경되지 않도록 Read-Only 형태로 저장된다.

## 데이터(Data) 영역
- 전역변수, static 변수가 저장된다.
- 프로그램 시작과 동시에 할당되고, 프로그램 종료시 메모리가 해제된다.
- 실행 도중 변수 값이 변경될 수 있으므로 Read-Wrtie로 지정된다.

## 힙(Heap) 영역
- 프로그래머가 할당/해제 하는 메모리 영역
- 동적할당된 데이터들 (malloc, calloc)
- 사용하고 난 후에 반드시 메모리 해제를 해줘야 한다.
- 해제하지 않을 경우 메모리 누수(memory leak)가 발생한다.
- Code, Data, Stack중 유일하게 Run time시 결정된다.
- 데이터의 크기가 확실하지 않을 때 사용한다.

## 예시

```swift
class Human{
    var name : String?
    var age : Int?
}
var human : Human? = Human() // 인스턴스로 힙 영역에 할당
```

- 코드를 실행하기 전에 Stack에는 human에 대한 메모리가 할당된다. 
- Human()이라는 인스턴스(여기서는 human)를 만들게 되면 Heap에 메모리가 할당되고 Stack에는 해당 heap의 메모리 주소가 저장된다. 스택에 저장된 변수 human이 힙에 저장된 Human 인스턴스를 참조하고 있는 형태이다.

<p align="center">
<img width="700" src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fba175F%2FbtqIqmFWibx%2FFbWtt2NGRRExKphVwkBtP0%2Fimg.png">
</p>

## 힙과 스택의 메모리 관계

<p align="center">
<img width="400" src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcZLkE0%2FbtqHR7wpUtQ%2FB94lHrkyUvqj1GwUHxojUK%2Fimg.png">
</p>

힙과 스택은 사실 메모리 영역을 공유한다. 같은 메모리 공간이지만, 이와 같이 할당받는다.

- 힙 영역은 낮은 메모리 주소부터 할당받음
- 스택 영역은 높은 메모리 주소부터 할당받음

따라서 무리하게 영역을 넓히다 보면 서로의 영역을 침법하게 되는데 이때 발생하는 오류가 `힙 오버 플로우(Heap Overflow)`, `스택 오버 플로우(Stack Overflow)`이다. 당연하게도 스택영역이 넓어지면 힙영역이 줄어들고, 힙 영역이 넓어지면 스택영역이 줄어들게 된다.

#### REFERENCE
https://babbab2.tistory.com/25
