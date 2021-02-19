---
layout: default
title: HTTP
parent: Network
nav_order: 1
---

# HTTP

* [HTTP(Hyper Text Transfer Protocol)란?](#HTTP(Hyper-Text-Transfer-Protocol)란?)
* [Request 구조](#요청-구조)
* [Response 구조](#응답-구조)
* [요약](#요약)

## HTTP(Hyper Text Transfer Protocol)란?

**인터넷에서 서버와 클라이언트 간에 데이터를 주고받기 위한 약속**이다. 

HTML, CSS, Javascript와 같은 contents를 주고받기 위해서는 client와 server간에 공통 약속인 메시지가 필요하다. 이러한 메시지를 HTTP라고 하는 것이다.

HTTP의 메시지 타입에는 2가지가 있다.
- request(요청) : 클라이언트 -> 서버
- response : 서버 -> 클라이언트 (요청에 대한 답변)


## 요청 구조

<img src="https://media.vlpt.us/post-images/rosewwross/6cafb380-4b37-11ea-b8a3-d182d6d1a356/image.png">

* start line(request line)
    * HTTP Method
    * Request target (request가 전송되는 url)
    * HTTP version
* headers : request에 대한 meta정보를 담고 있으며, key:value 값으로 되어있다.
    * Host : 요청이 전송되는 target의 host url: 예를 들어, google.com
    * User-Agent : 요청을 보내는 클라이언트의 대한 정보: 예를 들어, 웹브라우저에 대한 정보.
    * Accept : 해당 요청이 받을 수 있는 응답(response) 타입
        (조건부 요청을 허용: (accept-, If-), 모든 요청 허용:(/))
    * Connection : 해당 요청이 끝난후에 클라이언트와 서버가 계속해서 네트워크 컨넥션을 유지 할것인지 아니면 끊을것인지에 대해 지시하는 부분. (Keep-alive or cancel)
    * Content-Type : 해당 요청이 보내는 메세지 body의 타입. 예를 들어, JSON을 보내면 application/json.
    * Content-Length :메세지 body의 길이.
* empty line: 요청에 대한 meta 정보가 전송되었음을 알린다.

* body: 해당 request의 실제 메세지/내용이 들어있다.
    * XML 이나 JSON 데이터가 들어갈 수 있다.
    * GET은 body가 대부분 없다.

### Request Method
- ```GET```(select, fetch) : Web Server로 부터 데이터를 가져옴
- ```POST```(add,insert): Web Server로 데이터를 보냄
- ```PUT(update)``` : 서버에 이미 존재하는 데이터를 수정
- ```DELETE``` : 서버에 데이터를 삭제 

## 응답 구조

<img src="https://media.vlpt.us/post-images/rosewwross/6fc65770-4b39-11ea-abce-67c155f8f58a/image.png">


* status line : response의 상태를 간략하게 나타내며, 3부분으로 구성되어 있다.
    *  HTTP 버젼
    * status code : 응답 상태를 나타내는 코드
    * status text : 응답 상태의 설명 (ex: Not Found)
* headers : response의 header와 동일하다
response에서만 사용되는 header 값이 있다 (예: User-Agent가 없고, Server가 있음).
* empty line
* body : 실제 응답하는 데이터를 나타낸다. 

### Status Code
- 1xx : informational response
- 2xx : success
- 3xx : redirection
- 4xx : client error
- 5xx : Server error


## 예시

#### 웹 브라우저가 웹 서버에 요청한 메시지

<img width="764" alt="request" src="https://user-images.githubusercontent.com/60229909/93063036-a1f3ae00-f6b0-11ea-8f5a-3863f9190996.png">


#### 웹 서버가 웹 브라우저에게 응답한 메시지

<img width="372" alt="response" src="https://user-images.githubusercontent.com/60229909/93063122-c18ad680-f6b0-11ea-9b63-b69d2ac1c475.png">

웹 브라우저가 하는 역할은 이렇게 응답받은 메시지를 화면에 뿌려주는 것이다.

## 요약
- HTTP란 Server와 Client간에 통신을 위한 약속이다. 
- client는 request header에 method와 url, http version등을 넣어서 보낸다.
- server는 client로 부터 받은 메시지의 header를 보고 
    - response body에 실제 응답 데이터를 넣어 clinet에게 응답하게 된다. 
    - 이때, response의 header에는 response status와 http version이 함께 전달 된다.


#### reference
> https://velog.io/@rosewwross/Http-and-Request-and-Response-hok6exbnfb
