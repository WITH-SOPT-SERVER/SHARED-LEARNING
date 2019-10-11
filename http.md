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

HTTP 는 Connectionless하고 Stateless한 protocol이다. 이는 HTTP 프로토콜을 따르는 서버에서는 `request`와 다음 `request`사이에 요청이 서로 관련이 없다는 것을 의미한다.

>Connectionless - 클라이언트가 서버에 요청을 하고 서버가 클라이언트에게 응답을 보내면 접속을 끊음</br>
>Stateless - 통신이 끝나면 상태 정보를 유지하지 않음</br>

하지만 서비스를 개발하다보면 stateful하게 개발해야하는 경우(로그인이 필요한 서비스의 경우 등)가 더러 있다. 이런 경우에는 stateless한 HTTP를 stateful하게 작동하도록 하기 위해 `쿠키`/`세션`/`토큰` 방식 등을 상황에 맞게 적절히 (따로 or 조합하여) 사용한다.

### 세션 유지 방법
1. 쿠키
> 쿠키란 클라이언트에 저장되어있는 키와 값이 들어있는 작은 데이터 파일을 말한다. 이름, 값, 만료 날짜, 경로 정보 등이 들어있다. 일정 시간동안 데이터를 저장 할 수 있어 로그인 상태를 유지하거나 사용자 정보를 일정 시간 동안 유지해야 하는 경우에 사용된다.
- 첫번 째 접속에서 Response Header의 Set-Cookie속성을 이용하여 클라이언트에 속성을 만든다.
- 쿠키가 생성이 되면, 클라이언트는 이후부터 Request Header에 자동적으로 쿠키 정보를 넣어서 보내게 된다.
- 사용자 정보가 클라이언트 컴퓨터에 파일로 남고, 클라이언트 컴퓨터에 접근할 수 있는 사람이면 누구든지 열어 확인 할 수 있다는 보안상의 문제가 있다. 

2. 세션ID
> 세션이란 서버 메모리에 저장되는 정보를 말한다. 서버에 저장되므로, 쿠키와는 다르게 사용자 정보가 노출되지 않는다.
- 서버에서 사용자가 보낸 id/pw를 확인하고, 존재하는 사용자면 서버 메모리에 세션ID를 생성하고, 사용자 id와의 매핑정보를 저장한다.
- 클라이언트에 세션ID를 쿠키로 저장한다.
- 요청시 마다, 서버는 Request header의 쿠키정보를 확인하고 쿠키 정보 안에 있는 세션ID와 매핑되는 id의 사용자로 인식한다.
- 세션은 서버 메모리에 저장되지만, 세션도 클라이언트에 쿠키에 저장된다.

3. 토큰
> JWT는 Json Web Token의 약자로, 인증에 필요한 정보들을 암호화 시킨 토큰을 말한다. 토큰을 만들기 위해서는 정보를 암호화할 방식(alg), 타입(type) 등이 들어가 있는 Header, 서버에서 보낼 데이터(유저의 고유 ID값, 유효기간)이 들어가 있는 Payload, Base64 방식으로 인코딩한 Header, payload 그리고 SECRET KEY를 더한 후 서명되는 Verify Signature가 필요하다.
- 서버에서 사용자가 보낸 id/pw를 확인한 후, 사용자의 고유한 ID값을 부여한 후, 기타 정보와 함께 payload에 넣는다.
- JWT토큰의 유효기간을 설정한다.
- 암호화 할 secret key를 이용해, access token(JWT)을 발급한다.
- 사용자는 JWT를 받아 저장 한 후, 인증이 필요한 요청마다 헤더에 실어 보낸다.
- 서버는 토큰의 Vertify Signatarue를 Secret key로 복호화 한 후, 조작여부와 유효기간을 확인하고 검증이 완료되면 payload를 디코딩하여 데이터를 가져온다.

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
- **CONNECT**
  - 목적 리소스로 식별되는 서버로의 터널을 맺는다
- **OPTIONS**
  - 목적 리소스의 통신을 설정하는 데 쓰인다
- **TRACE**
  - 목적 리소스의 경로를 따라 메시지 loop-back 테스트
- **PATCH**
  - 리소스의 부분만을 수정할 때 쓰인다

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
