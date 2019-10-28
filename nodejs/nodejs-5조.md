# Node.js 정리 프로젝트

> 이 문서를 복붙해서 시작하셔도 됩니다.

> ※ 아래 항목은 예시일 뿐입니다. 자요롭게 조원끼리 구성을 만들고 공부해서 내용을 공유하시면 됩니다!!

> 내용의 출처 링크를 꼭 남겨주세요!!

# Index
- [Node.js 배경](#NODE.JS-배경)
- [Node.js 란](#NODE.JS-란)
- [Node.js 구조](#NODE.JS-구조)
- [Node.js 특징](#NODE.JS-특징)
- [Node.js 장단점](#NODE.JS-장단점)
- [NPM](#Node-Packaged-Manager)
- (자유롭게 추가 가능)
- [참가자](#참가자)

# Node.js 배경

[목록으로](#INDEX)

# Node.js 개념

[목록으로](#INDEX)

# Node.js 구조

콜백을 담는 별도의 큐와 이것을 처리하기 위한 이벤트 루프가 자바스크립트 외부에 존재하는 등 브라우저와 비슷한 구조를 보인다. node.js 에서는 비동기 실행을 위해 libuv 라이브러리를 사용하며, libuv 가 이벤트 루프를 제공한다. 자바스크립트 엔진은 비동기 작업을 위해 node.js api 를 호출하며, 이때 넘겨받은 콜백은 libuv의 이벤트 루프를 통해 스케쥴되고, 실행된다.


<img src = "https://pbs.twimg.com/media/Bt5ywJrIEAAKJQt.jpg"> </img>

코드를 실행할 때 동기적으로 처리되는 함수들은 자바스크립트엔진 내의 호출 스택(call stack)에 쌓여 하나씩 실행되지만, 비동기로 실행되는 함수는 node api 를 통해 libuv 에 바인딩되어 libuv에 넘겨지게 되고, libuv 내의 스레드풀에서 처리되어 나온 결과는 콜백 함수에 담겨 이벤트 큐에 쌓이게 된다.


<img src = "http://4.bp.blogspot.com/-MYY3w4Y_lAg/VCHi63G4DGI/AAAAAAAAA3c/FrbGjnJbPnQ/s1600/event_loop.jpg"> </img>

이벤트 큐에 쌓인 콜백 함수들은 바로 사용되는 것이 아니라 자바스크립트엔진에 있는 호출 스택(call stack)이 비어 있을 경우에 이벤트 루프가 이벤트 큐에서 함수를 하나 가져와 호출 스택(call stack)에 쌓게되면서 실행이 된다.


libuv
node.js 의 비동기 I/O 를 지원하는 멀티스레드 플랫폼이자 라이브러리.

이벤트 루프
시스템 커널에 작업을 떠넘겨서 node.js 가 Non-Blocking 비동기 I/O 작업을 수행하도록 도와주는 객체이다. 콜백 함수가 저장되어 있는 이벤트 큐에서 콜백 함수들을 가져와 호출 스택에 넣는 작업을 한다.

(출처 : https://hyeonu1258.github.io/2018/04/05/node.js%20내부구조/)


[목록으로](#INDEX)

# Node.js 특징

## Single Thread

## Non-Blocking I/O

## Event-Driven

## Node의 모듈 시스템

[목록으로](#INDEX)

# Node.js의 장단점

## Node.js의 장점
 
1 이벤트 기반.
2 싱글 스레드 : 비동기 프로그래밍이다. 두 번째 세미나에서 배웠던 내용들 !
3 범용성 : Nodj.js의 기반인 자바스크립트를 이용하면 프론트도 다룰 수 있고 V8 엔진 덕에 다른 프로그래밍에서도 사용할 수 있다.
4 구글이 제작 : 아무래도 당분간은 강세가 지속될 듯.


## Node.js의 단점

1 싱글스레드 : 하나의 작업 자체가 오래 걸린다면 전체적인 과부하가 걸릴 수 있다, 멀티코어의 CPU 사용을 최적화할 수 없다.
2 스크립트 언어이기에 오류의 탐색이 신뢰롭지 못할 수 있다.
3 V8이 좋지만 low level 언어로 구성된 서버 어플리케이션보다는 느리다.

출처 : https://epdl-studio.tistory.com/76, https://goodgid.github.io/Node-Pros-and-Cons/

[목록으로](#INDEX)

# Node Packaged Manager

[목록으로](#INDEX)

# 참가자
1. 김해리 - node.js의 구조
2. 박승완 - node.js의 장단점
3. 
4. 
5. 
6. 
7. 
8. 

[목록으로](#INDEX)
