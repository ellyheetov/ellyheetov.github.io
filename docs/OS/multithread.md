---
layout: default
title: Multi-Thread
parent: Operating System
nav_order: 4
---

# Multi-Thread

## 멀티 스레딩(multi-threading)
- 하나의 프로세스를 다수의 실행단위로 구분하여 자원을 공유하고, 자원의 생성과 관리의 중복성을 최소화 하여 수행 능력을 향상시키는 것을 멀티 스레딩이라고 한다.
- 하나의 응용프로그램을 여러 개의 스레드로 구성하고 각 스레드로 하여금 하나의 작업을 처리하도록 하는 것이다.


## 멀티 쓰레드를 사용하는 이유
<img src="https://gmlwjd9405.github.io/images/os-process-and-thread/multi-thread.png">


- 자원의 효율성 증대
    - 멀티 프로세스로 실행되는 작업을 멀티 스레드로 실행할 경우, 프로세스를 생성하여 자원을 할당하는 시스템 콜이 줄어들어 자원을 효율적으로 관리할 수 있다.
        - 프로세스 간의 Context Switching시 단순히 CPU 레지스터 교체 뿐만 아니라 RAM과 CPU 사이의 캐쉬 메모리에 대한 데이터까지 초기화되므로 오버헤드가 크기 때문
    - 스레드는 프로세스 내의 메모리를 공유하기 때문에 독립적인 프로세스와 달리 스레드 간 데이터를 주고 받는 것이 간단해지고 시스템 자원 소모가 줄어들게 된다.
- 처리비용 감소 및 응답시간 단축
    - 프로세스 간의 통신(IPC)보다 스레드 간의 통신의 비용이 적으므로 작업들 간의 통신의 부담이 줄어든다.
        - 스레드는 Stack 영역을 제외한 모든 메모리를 공유하기 때문
    - 프로세스 간의 전환 속도보다 스레드 간의 전환 속도가 빠르다.
        - Context Switching시 스레드는 Stack 영역만 처리하기 때문

## 장점
- 시스템 자원 소모 감소(=자원의 효율성 증대)
    - 프로세스를 생성하여 자원을 할당하는 시스템 콜이 줄어들어 자원을 효율적으로 관리할 수 있다.
- 시스템 처리량 증가(=처리 비용 감소)
    - 스레드 간 데이터를 주고 받는 것이 간단해지고 시스템 자원 소모가 줄어들게 된다.
    - 스레드 사이의 작업량이 작아 Context Switching이 빠르다.
- 간단한 통신 방법으로 인한 프로그램 응답 시간 단축
    - 스레드는 프로세스 내의 Stack 영역을 제외한 모든 메모리를 공유하기 때문에 통신의 부담이 적다


## 단점
- 주의 깊은 설계가 필요하다.
- 멀티 스레드의 경우 자원 공유의 문제가 발생한다. (동기화 문제)
    - 쓰레드간 공유하는 자원이 있기 떄문에 동일한 자원에 동시에 접근하는 경우를 신경써야한다.
    - 동기화를 통해 작업 처리 순서를 컨트롤 하고 공유 자원에 대한 접근을 컨트롤 한다.
- 하나의 스레드에 문제가 발생하면 전체 프로세스가 영향을 받는다.
- 병목현상이 발생하여 성능이 저하될 우려가 있다.
- 공유자원이 아닌 부분은 동기화 처리를 할 필요가 없다.
- 불필요한 부분까지 동기화를 처리 할 경우 현재 스레드는 락(lock)을 획득한 쓰레드가 종료하기 전까지 대기해야한다.


#### Reference
https://goodgid.github.io/What-is-Multi-Thread/
https://gmlwjd9405.github.io/2018/09/14/process-vs-thread.html
