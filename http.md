# HTTP

## index

- [HTTP](#http)
  - [index](#index)
  - [HTTP란](#http%eb%9e%80)
  - [HTTP의 특징](#http%ec%9d%98-%ed%8a%b9%ec%a7%95)
  - [HTTP Message의 구조](#http-message%ec%9d%98-%ea%b5%ac%ec%a1%b0)
  - [HTTP Method의 종류](#http-method%ec%9d%98-%ec%a2%85%eb%a5%98)
  - [인자 전달 방식](#%ec%9d%b8%ec%9e%90-%ec%a0%84%eb%8b%ac-%eb%b0%a9%ec%8b%9d)
  - [더 알아보자](#%eb%8d%94-%ec%95%8c%ec%95%84%eb%b3%b4%ec%9e%90)

## HTTP란

Hyper Text Transfer Protocol 이라는 뜻으로, 인터넷에서 데이터를 주고 받을 수 있게 해주는 프로토콜이다. 클라이언트(웹의 경우에서는 웹 브라우저)가 서버에게 `request`를 보내면 서버는 클라이언트(브라우저)에게 `response`한다. 이때 지키는 대표적인 통신규약이 `HTTP`이다. 크롬 개발자 도구를 통해 요청 헤더와 응답 헤더를 볼 수 있으며, 서버는 정보를 제공하면서 응답한 정보를 헤더를 통해 알려준다.

클라이언트란 HTTP request를 보내는 쪽이다. 웹 관점을 예시로 들자면 웹 브라우저가 클라이언트가 된다. 서버란 요청을 받는 쪽을 의미하며 일반적으로 데이터를 보내주는 원격지의 컴퓨터를 의미한다.

클라이언트와 서버는 바꿔진 각각의 메시지(주로 stream of data라고 표현됨)로 통신을 한다. 이 메시지들 중 클라이언트가 보낸 메시지를 request라고 부르고, 서버가 보낸 메시지를 response라고 한다.

- [참고자료 - MDN HTTP page](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)
- [참고자료 - H](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)

[목차로 돌어가기](#index)

## HTTP의 특징

OS7 계층 중에서 Application-layer의 프로토콜이다.HTTP는 고전적인 클라이언트-서버 모델을 따르고 있다.(클라이언트가 `request`를 보내기 위해 연결하고, `response`를 받을 때 까지 기다리는 형태이다.)

HTTP는 stateless protocol이다. 이는 HTTP 프로토콜을 따르는 서버에서는 `request`와 다음 `request`사이에 요청이 서로 관련이 없다는 것을 의미한다.

하지만 서비스를 개발하다보면 stateful하게 개발해야하는 경우(로그인이 필요한 서비스의 경우 등)가 더러 있다. 이런 경우에는 stateless한 HTTP를 stateful하게 작동하도록 하기 위해 `쿠키`/`세션`/`토큰` 방식 등을 상황에 맞게 적절히 (따로 or 조합하여) 사용한다.

[목차로 돌어가기](#index)

## HTTP Message의 구조

![HTTP Message 구조](https://mdn.mozillademos.org/files/13827/HTTPMsgStructure2.png)

HTTP 요청과 응답의 구조는 서로 닮았으며, 그 구조는 다음과 같다.

- `start-line`에는 각각 다음과 같은 정보가 들어있습니다. 이 줄은 항상 한 줄로 끝난다.
  - Request: HTTP Method / HTTP version
  - Response: HTTP version / status-code / status-message
- `HTTP Headers`에는 여러 Header Field가 key-value 형식으로 들어간다.(요청에 대한 설명 혹은 메시지 본문에 대한 설명이 들어간다)
- 요청에 대한 모든 메타 정보가 전송되었음을 알리는 `empty-line`이 삽입된다.
- `body`(본문)에는 추가적으로 전송할 데이터가 들어간다.
  - Payload라고도 하며, Message body라고도 한다.

HTTP 메시지의 시작 줄과 HTTP 헤더를 묶어서 요청 헤드(head)라고 부르며, 이와 반대로 HTTP 메시지의 페이로드는 본문(body)이라고 한다.

- [참고자료 - MDN::HTTP 메시지](https://developer.mozilla.org/ko/docs/Web/HTTP/Messages)

[목차로 돌어가기](#index)

## HTTP Method의 종류

- **GET**
  - 타겟 리소스의 현재 상태(representation) 조회를 요청
- **HEAD**
  - GET과 같지만 status line과 header섹션만 전송 요청
- **POST**
  - 함께 전송되는 요청 페이로드(body)의 내용을 토대로 리소스 생성 요청
- **PUT**
  - 타겟 리소스의 상태를 함께 전송되는 요청 페이로드(body)로 수정하도록 요청 (타겟 리소스가 존재하지 않다면 새로 생성 가능)
- **DELETE**
  - 타켓 리소스의 현재 상태(representation) 삭제를 요청
- CONNECT
- OPTIONS
- TRACE
- ....

[목차로 돌어가기](#index)

## 인자 전달 방식

- **Query string**
  - `?key1=value1&key2=value2....`
  - `https://www.google.com/search?q=sopt&oq=sopt&aqs=chrome..69i57j0j69i60l4.2747j0j7&sourceid=chrome&ie=UTF-8`
    - q: sopt
    - oq: sopt
    - aqs: chrome..69i57j0j69i60l4.2747j0j7
    - sourceid: chrome
    - ie: UTF-8
- **Path variable**
  - `..../{userId}/book/{bookId}`
  - ...../13109346/book/623414
    - userId: 13109346
    - bookId: 623414
- **Message Body**
  - HTTP Request의 구성요소 중 Message Body를 통해 전송하는 방식
  - 여러 `Content-Type`으로 전송할 수 있음. `Content-Type`은 HTTP 메시지 `Header`의 `Content-Type`에 명시
    - `multipart/form-data`
    - `application/json`
    - `application/x-www-urlencoded`
    - ....
  - ex)

```txt
{
    "book_name": "윤희성의 Node.js + Express",
    "author": "윤희성"
}
```

[목차로 돌어가기](#index)

## 더 알아보자

- (언젠가 시간이 날 때) [RFC7230 스펙 문서](https://tools.ietf.org/html/rfc7230)를 꼭 읽어볼 것을 적극적으로 추천한다.

[목차로 돌어가기](#index)
