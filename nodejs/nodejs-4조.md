# Node.js 정리 프로젝트

# Index
- [Node.js 배경](#NODE.JS-배경)
- [Node.js 란](#NODE.JS-란)
- [Node.js 구조](# Node.js 구조)
- [Node.js 특징](#NODE.JS-특징)
- [Node.js 장단점](#NODE.JS-장단점)
- [NPM](#Node-Packaged-Manager)
- [참가자](#참가자)

# Node.js 배경

[목록으로](#INDEX)

# Node.js 개념

웹 브라우저위에서 동작하던 JS가 서버를 제어할 수 있도록 해주는 **JS Run time**이다.이벤트 기반, non-blocking I/O 모델을 사용하여 가볍고 효율적이며 거대한 패키지 생태계인 npm를 통해 쉽게 모듈 확장이 가능하다.

NodeJs는 이벤트 기반으로 개발이 가능하며 Non-Blocking I/O를 지원하기 때문에 **비동기식 프로그래밍**이 가능하다. 이 때문에 I/O 부하가 심한 대규모 서비스를 개발하기 적합하다고 할 수 있다. 또한 자바스크립트의 표준라이브러리 프로젝트인 CommonJS의 스펙을 따르고 있어 일반적인 범용 언어으로 타 코드를 쉽게 사용할 수 있다.

[목록으로](#INDEX)

# Node.js 구조

[목록으로](#INDEX)

# Node.js 특징

## Single Thread

싱글 쓰레드를 가진 노드는 I/O 작업이 시작되면 I/O 작업 처리에 대한 응답을 기다리지 않고, **바로 다음 작업을 실행**해버린다. 대신 I/O 작업이 종료되면 이벤트를 발생시키고, 이 이벤트는 해당 프로세스의 이벤트 큐에 등록되게 된다. 노드로 개발된 프로세스는 이 이벤트 큐에 등록된 새로운 이벤트를 감지하여, 해당 이벤트 시 수행하여야 할 작업을 실행하는 로직을 가진다.

## V8 Engine 

V8 자바스크립트 엔진은 속도가 매우 빠르다는 장점과 더불어 구글이 해당 엔진을 개발하는 만큼 끊임없이 개선되고 발전할 것이다. 적극적인 개선과 발전으로 미래에 더 훌륭한 퍼포먼스를 가지게 될 것이라는 기대가 가능하다.

## Non-Blocking I/O

I/O 작업을 진행하는 동안 유저 프로세스의 작업을 중단시키지 않는다. non-blocking I/O의 경우 읽기/쓰기 이벤트가 발생하는 경우 데이터를 반환할 때 까지 기다리지 않고 다음 명령을 수행시킨다.  Non-blocking I/O 방식을 사용하면 외부에 I/O 작업을 하도록 요청한 후 즉시 다음 작업을 처리함으로써 시스템 자원을 더 효율적으로 사용할 수 있게된다. 그러나 I/O 작업이 완료된 이후에 처리해야하는 후속 작업이 있다면, I/O 작업이 완료될 때까지 기다려야 한다. 따라서 이 후속 작업이 프로세스를 멈추지 않도록 만들기 위해, I/O 작업이 완료된 이후 후속 작업을 이어서 진행할 수 있도록 별도의 약속([Polling](https://en.wikipedia.org/wiki/Asynchronous_I/O#Polling), [Callback function](https://en.wikipedia.org/wiki/Asynchronous_I/O#Callback_functions) 등)을 한다. 

## Event-Driven

사용자가 이벤트를 발생시켰을 때, 즉 입력장치로 데이터를 전송했을 때에만 작동한다. 발생한 이벤트에 대해서만 웹서버가 연결을 해주기 떄문에 자원을 최소화 할 수 있다.

> 대부분의 웹 서버는 이벤트가 발생할때까지 기다리면서 자원(대기시간/메모리)을 소비한다.

## Node의 모듈 시스템

[목록으로](#INDEX)

# Node.js의 장단점

## Node.js의 장점

## Node.js의 단점

 NodeJs는 자바스크립트와  싱글 쓰레드 모델에서 오는 장점이 있는 반면 여기서 오는 단점 역시 만만하지 않다. 기본적으로 싱글 쓰레드 모델이기 때문에, 하나의 작업 자체가 시간이 많이 걸리면, 전체 시스템의 성능이 아주 급격하게 떨어진다. 그래서, 가벼운 작업 위주로 개발이 되어야 하고, 자바스크립트에서 오는 문제점은 자바나 다른 언어에 비해서 명시성이 떨어지기 때문에, 코드의 가독성이 자바언어에 비해서 상대적으로 낮기 때문에 유지 보수가 어려워질 수 있다 또한 이벤트 Call back 을 형태를 기준으로 하기 때문에, 이러한 call back이 중첩될 경우 (이를 callback hell이라고 한다.) 코드의 가독성이 급격하게 떨어진다.

[목록으로](#INDEX)

# Node Packaged Manager

[목록으로](#INDEX)

# 참가자
1. 지현이
2. 
3. 
4. 
5. 
6. 
7. 
8. 

[목록으로](#INDEX)

### 출처

[nodejs란](https://asfirstalways.tistory.com/43 )

[non-blocking I/O](https://tech.peoplefund.co.kr/2017/08/02/non-blocking-asynchronous-concurrency.html )

[위키백과 NodeJs]( https://ko.wikipedia.org/wiki/Node.js )
