---
layout: default
title: TCP Handshake
parent: Network
nav_order: 3
---
# TCP Handshake

TCP에서 연결을 위해 3-Way HandShaking, 연결 해제를 위해 4-Way HandShaking을 사용한다.

* [3-Way Handshacking란?](#3-Way-Handshacking란?)
* [3-Way HandShaking의 역할](#3-Way-HandShaking의-역할)
* [3-Way HandShaking 과정](#3-Way-HandShaking-과정)
    * [SYN](#[STEP-1]-SYN)
    * [SYN+ACK](#[STEP-2]-SYN+ACK)
    * [ACK](#[STEP-3]-ACK)
* [왜 3-Way까지 필요할까?](#왜-3-Way까지-필요할까?)
* [4-Way Handshacking란?](#4-Way-Handshacking란?)
* [4-Way HandShaking 과정](#4-Way-HandShaking-과정)
    * [FIN](#[STPE-1]-FIN)
    * [ACK](#[STEP-2]-ACK)
    * [FIN](#[STEP-3]-FIN)
    * [ACK](#[STEP-4]-ACK)
    * [TIME_WAIT](#TIME_WAIT)
* [비정상 종료 상황](#비정상-종료-상황)

<img src="https://t1.daumcdn.net/cfile/tistory/9910A8345BB0B75F2A?download">

## 3-Way HandShaking란?
TCP 통신을 이용하여 데이터를 전송하기 위해 네트워크 연결을 설정(Connection Establish)하는 과정이다.

TCP/IP 프로토콜을 이용해서 통신을 하는 응용 프로그램이 데이터를 전송하기 전에 정확한 전송을 보장하기 위해 상대방 컴퓨터와 사전에 세션을 수립하는 과정을 의미한다.

쉽게말해, 서로 통신이 가능한지를 파악하기 위한 과정이다.

## 3-Way HandShaking의 역할

실제로 데이터를 주고받기 전에 양 쪽이 모두 준비가 되었다는 것을 보장한다.(연결성립, Connection Establishment)

## 3-Way HandShaking 과정
* SYN(Synchronize Sequence Number)
* ACK(Acknowledgement)
<img width="662" alt="스크린샷 2020-09-16 오후 12 18 12" src="https://user-images.githubusercontent.com/60229909/93288386-b2259d80-f816-11ea-9c82-9e08d3f20e80.png">


#### [STEP 1] SYN
- A 클라이언트는 B서버에 접속을 요청하는 SYN 패킷을 보낸다.
- 이때 A클라이언트는 SYN 을 보내고 SYN/ACK 응답을 기다리는SYN_SENT 상태가 된다.

#### [STEP 2] SYN+ACK
- B서버는 SYN요청을 받고 A클라이언트에게 요청을 수락한다는 ACK 와 SYN flag 가 설정된 패킷을 보낸다.
- A가 다시 ACK으로 응답하기를 기다린다. 이때 B서버는 SYN_RECEIVED 상태가 된다.

#### [STEP 3] ACK
- A클라이언트는 B서버에게 ACK을 보낸다.
- 이후로부터는 연결이 이루어지고 데이터 송수신이 이루어진다.
- 이때의 B서버 상태가 ESTABLISHED 이다.

## 왜 3-Way까지 필요할까?

클라이언트가 서버에게 SYN을 보내고 난 후, 서버가 클라이언트에게 응답을 해주는 2-way로 충분하지 않을까?


이는 클라이언트는 서버에게 데이터 전송을 하고 서버는 데이터를 받았다는 것을 보장해준다.
하지만, 서버가 클라이언트에게 데이터 전송시 클라이언트가 제대로 받았는지 확인할 방법이 없다.
이는 양쪽간에 정확한 정보 전송이 이루어지고 있음을 보장할 수 없다.

TCP Connection은 양방향성(bidirectional) connection이다. 클라이언트에게 서버의 존재를 알리고 패킷을 보낼 수 있다는 것을 알리듯, 서버에게도 클라이언트의 존재를 알리고 패킷을 보낼 수 있다는 신호를 보내야 한다. 그렇기 때문에 2-way handshake로는 부족하다.

3-way방식은 아래와 같이 예를 들 수 있다.
<img width="500" src="https://t1.daumcdn.net/cfile/tistory/9970B14E5B343EF607">

이 과정은 양쪽 모두 준비가 되었다는 것을 보장하고 이제 서로 이야기를 나누기 시작한다.

## 4-Way Handshacking란?
TCP의 연결을 해제(Connection Termination)하는 과정이다.

## 4-Way HandShaking 과정

* FIN(finish) : 세션 연결을 종료시킬 때 사용되며, 더이상 전송할 데이터가 없음을 의미한다.

<img width="538" alt="스크린샷 2020-09-16 오후 12 18 35" src="https://user-images.githubusercontent.com/60229909/93288423-bfdb2300-f816-11ea-9184-e9b491df0d0d.png">

#### [STPE 1] FIN
- A가 연결을 종료하겠다는 FIN 플래그를 전송
- B가 FIN 플래그로 응답하기 전까지 연결을 계속 유지

#### [STEP 2] ACK
- B서버는 클라이언트의 요청(FIN)을 받고 확인 메시지로 ACK을 보낸다.
- 남아있는 자신의 데이터를 모두 보낼 때까지 잠깐 TIME_WAIT상태가 된다.

#### [STEP 3] FIN
- B서버는 데이터를 모두 보내고 통신이 끝났으면 연결이 종료도었다고 A클라이언트에게 FIN flag를 전송한다.

#### [STEP 4] ACK
- A클라이언트는 FIN 메시지를 확인했다는 ACK을 보낸다.
- B서버는 소켓 연결을 close한다.

###  * TIME_WAIT
B서버에서 FIN을 전송하기 전에 전송한 패킷이 Routing 지연이나 패킷 유실로 인한 재정송 등으로 인해 FIN패킷 보다 늦게 도착하는 상황이 발생한다면?

Client에서 세션을 종료 시킨 후 뒤늦게 도착하는 패킷이 있다면 이 패킷은 Drop되고 데이터는 유실될 것이다. 이러한 상황을 대비하여 Client는 Server로 부터 FIN을 수신하더라도 일정시간동안 세션을 남겨놓고 잉여 패킷을 기다리는 과정을 거친다.(이러한 과정을 TIME_WAIT라고 한다.)

## 비정상 종료 상황


#### Reference
-  https://mindnet.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-22%ED%8E%B8-TCP-3-WayHandshake-4-WayHandshake
- https://gmlwjd9405.github.io/2018/09/19/tcp-connection.html
- https://asfirstalways.tistory.com/356
- https://www.crocus.co.kr/1362
