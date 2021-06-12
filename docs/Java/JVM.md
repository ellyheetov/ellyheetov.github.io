---
layout: default
title: JVM
parent: Java
nav_order: 1
---

# JVM

## 자바 가상머신, JVM(Java Virtual Machine)이란?
JAVA Virtual Machine, 자바 가상 머신의 약자를 따서 줄여 부르는 용어이다.

## JVM의 역할
- 애플리케이션을 클래스 로더를 통해 읽어 들여 자바 API와 함께 실행하는 것
- JAVA와 OS사이에서 중개자
- 메모리 관리(Garbage Collection을 수행)
- 스택기반

<img width="831" alt="스크린샷 2020-09-22 오후 3 50 59" src="https://user-images.githubusercontent.com/60229909/93851614-6a59b700-fceb-11ea-97f4-d7e95abd77a1.png">

## JVM의 구성

<img width="1201" alt="스크린샷 2020-09-22 오후 3 59 52" src="https://user-images.githubusercontent.com/60229909/93852249-a8a3a600-fcec-11ea-80e4-29e53bda41f5.png">

### Class Loader(클래스 로더)
- JVM내로 클래스(.class파일)를 로드하고, 링크를 통해 배치하는 작업을 수행하는 모듈
- Runtime시에 동적으로 클래스를 로드
    - 즉, 클래스를 처음 참조할 때, 해당 클래스를 로드하고 링크한다는 것이다.

### Execution Engine(실행 엔진)
- Interpreter(인터프리터)
    - Byte code를 명령어 단위로 읽어서 실행
- JIT(Jist-In-Time)
    - Interpreter방식으로 실행하다가 적절한 시점에 Byte code 전체를 compile하여 native code로 변경, 이후에는 더이상 인터프리팅 하지 않고, native code로 직접 실행하는 방식
    - navtive code는 캐시에 보관하기 때문에 한번 컴파일된 코드는 빠르게 수행된다.
    - 컴파일 과정이 Byte code를 인터프리팅 하는 것보다 오래걸림
    - 여러번 실행되는 코드일 경우 유리
- Garbage collector
    - GC를 수행하느 모듈(Thread)


#### * Complile VS Interpreter
소스코트를 변환시키고 실해시키는 방식을 말한다.
- Compile : 소스코드가 runtime되기 전에 기계어로 한번에 변환 및 해석되는 방식이다.
    - 소스코드에 문제가 있다면 실행되지 않고 오류를 알린다.
    - 기존 코드 : 원시코드 , 변환된 코드 : object code
    - compile 언어 : C/C++, JAVA
- Interptret : 소스코드가 runtime 된 후에 코드 한 줄씩 변환 및 해석되는 방식이다.
    - 소스코드에 문제가 있더라도 그 코드 전까지는 실행된 후, 오류를 알린다.
    - 가상머신 위에서 컴파일 되기에 소스 코드의 이동이 자유롭다.
    - interpret 언어 ; python



### Runtime Data Area

#### Method Area(=Class area,Static area)
- Field Information
- Type information
- Method information
- JVM에서 읽어들인 클래스와 인터페이스에 대한 런타임 constant pool, 멤버 변수(필드), 클래스 변수(static 변수), 생성자와 메소드를 저장하는 공간

#### Heap
- new 연산자로 생성된 객체 또는 객체(인스턴스)와 배열을 저장
- 런타임 시 동적으로 할당하여 사용하는 영역
- 힙 영역에 생성된 객체와 배열은 스택 영역의 변수나 다른 객체의 필드에서 참조한다.
- 참조하는 변수나 필드가 없다면 의미없는 객체가 되어 GC의 대상이 된다.
- 힙 영역의 사용기간 및 스레드 공유범위
    - 객체가 더이상 사용되지 않거나 명시적으로 null선언 시
    - GC(Garbage Collection) 대상
    - 모든 스레드에서 공유한다.

#### PC Register
- Thread가 생성될때 생성
    - 즉, Thread 하나당 하나의 PC Register
    - 현재 수행중인 JVM 명령의 주소
- 현재 수행 중인 JVM 명령 주소를 가짐

#### Stack 영역
- 각 스레드마다 하나씩 존재하며, 스레드가 시작될 때 할당
- 각종 형태의 변수나 임시데이터, 스레드나 메소드의 정보를 저장
- 메소드 호출시마다 각각의 스택 프레임(Frame)(해당 매소드 만을 위한 공간)이 생성(push)
- 메서드 수행이 끝나면 프레임 별로 삭제(pop)
- 메소드 안에서 사용되는 값들(local variable)을 저장
- 호출 된 메소드의 매개변수, 지역변수, 리턴 값 및 연산 시 일어나는 값들을 임시로 저장
- 기본(원시)타입 변수는 스택영역에 직접 값을 가진다.
- 참조타입 변수는 힙 영영이나 메소드 영역의 객체 주소를 가진다.

#### Native method stack
- 자바 프로그램이 컴파일 되어 생성되는 Byte code가 아닌, 실제 실행할 수 있는 기계어로 작성된 프로그램을 실행시키는 영역
- Java가 아닌 다른 언어로 작성된 코드를 위한 공간
- Java Native Interface를 통해 바이트 코드로 전환하여 저장하게 된다.
- 독자적으로 프로그램을 실행시키는 영역
- 이 부분을 통해 C code를 실행시켜 Kernel에 접근 할 수 있다.


## Reference

https://hoonmaro.tistory.com/19
