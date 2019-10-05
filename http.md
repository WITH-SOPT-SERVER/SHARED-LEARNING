# Javascript

## index

-   [HTTP란](#HTTP-란)
-   [HTTP의 종류](#HTTP의-종류)
-   [GET Method](#GET-METHOD)
-   [POST Method](#POST-METHOD)
-   [PUT Method](#PUT-METHOD)
-   [DELETE Method](#DELETE-METHOD)
-   [query string 방식](#QUERY-STRING-방식)
-   [query parameter 방식](#QUERY-PARAMETER-방식)
-   [multipart/form-data](#)

# HTTP 란

Hyper Text Transfer Protocol 이라는 뜻으로, 인터넷에서 데이터를 주고 받을 수 있게 해주는 프로토콜이다. 클라이언트(웹의 경우에서는 웹 브라우저)가 서버에게 `request`를 보내면 서버는 클라이언트(브라우저)에게 `response`한다. 이때 지키는 대표적인 통신규약이 `HTTP`이다. 크롬 개발자 도구를 통해 요청 헤더와 응답 헤더를 볼 수 있으며, 서버는 정보를 제공하면서 응답한 정보를 헤더를 통해 알려준다.

클라이언트란 HTTP request를 보내는 쪽이다. 웹 관점을 예시로 들자면 웹 브라우저가 클라이언트가 된다. 서버란 요청을 받는 쪽을 의미하며 일반적으로 데이터를 보내주는 원격지의 컴퓨터를 의미한다.

클라이언트와 서버는 바꿔진 각각의 메시지(주로 stream of data라고 표현됨)로 통신을 한다. 이 메시지들 중 클라이언트가 보낸 메시지를 requests라고 부르고, 서버가 보낸 메시지를 responses라고 한다.

-	[참고자료 - MDN HTTP page] (https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)

# HTTP의 특징
OS7 계층 중에서 application-layer의 프로토콜이다.HTTP는 고전적인 클라이언트-서버 모델을 따르고 있다.(클라이언트가 `request`를 보내기 위해 연결하고, `response`를 받을 때 까지 기다리는 형태이다.)

HTTP는 stateless protocol이다. 이는 HTTP 프로토콜을 따르는 서버에서는 `request`와 다음 `request`사이에 요청이 서로 관련이 없다는 것을 의미한다.

# HTTP의 종류

# GET METHOD

# POST METHOD

# PUT METHOD

# DELETE METHOD

# query string 방식

# query parameter 방식


