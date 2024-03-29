---
layout: default
title: Thread
parent: Operating System
nav_order: 3
---

# Thread

## 스레드(Thread)
스레드는 프로세스의 실행 단위라고 할 수 있다. 한 프로세스 내에서 동작하는 여러 실행 흐름이다. 스레드는 프로세스 내의 주소공간이나 자원을 공유할 수 있다. 스레드는 thread ID, 프로그램 카운터, 레지스터 집합, 그리고 스택으로 구성된다. 같은 프로세스에 속한 다른 스레드와 코드, 데이터 섹션, 그리고 열린 파일이나 신호와 같은 운영체제 자원들을 공유한다. 

- 한 프로세스 내에서 실행되는 여러 흐름의 단위
- 프로세스가 할당받은 자원을 이용하는 실행의 단위

<img src="https://gmlwjd9405.github.io/images/os-process-and-thread/multi-thread.png">

- 스레드는 프로세스 내에서 각각 Stack만 따로 할당받고 Code, Data, Heap 영역은 공유한다.
- 프로세스 내의 주소공간이나 자원들을 같은 프로세스 내에 스레드끼리 공유하면서 실행된다.
- 같은 프로세스안에 있는 여러 스레드들은 같은 힙 공간을 공유한다.
- 각각의 스레드는 별도의 레지스터와 스택을 갖고있지만, 힙 메모리는 서로 읽고 쓸 수 있다.
- 한 스레드가 프로세스 자원을 변경하면, 다른 이웃 스레드(sibling thread)도 그 변경 결과를 즉시 볼 수 있다.

## 스레드의 출현 배경
1. 프로세스간 Context Switch Overhead
2. 프로세스 사이의 통신의 어려움
프로세스들은 독립적인 주소공간을 가지고 있기 때문에 단순한 방법으로 서로의 메모리 공간에 접근할 수 없다. 공유 메모리, 소켓 등을 이용해서 접근해야한다.

## 스레드의 장점
- 빠른 Context Switch
    프로세스 내의 스레드들을 Context Switch 할 때는 TCB만 바꾸면 된다.

## 스택을 스레드마다 독립적으로 할당 하는 이유
스택은 함수 호출시 전달되는 인자, 되돌아갈 주소값 및 함수 내에서 선언하는 변수 등을 저장하기 위해 사용되는 메모리 공간이다. 스택 메모리 공간이 독립적이라는 것은 독립적인 함수 호출이 가능하다는 것이다. 이는 독립적인 실행흐름이 추가되는 것이다. 따라서 스레드의 정의에 따라 독립적인 실행흐름을 추가하기 위한 최소 조건으로 독립된 스택을 할당한다.

## PC Register를 스레드마다 독립적으로 할당하는 이유
PC값은 스레드가 명령어의 어디까지 수행하였는 지를 나타낸다. 스레드는 CPU를 할당 받았다가 스케줄러에 의해 다시 선점당한다. 그렇기 때문에 명령어가 연속적으로 수행되지 못하고 어느 부분까지 수행하였는지 기억할 필요가 있다. 따라서 PC 레지스터를 독립적으로 할당한다.
