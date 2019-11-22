
# Node.js 정리 프로젝트

# Index
- [Node.js 배경](#node.js-배경)
- [Node.js 란](#node.js-란)
- [Node.js 구조](#node.js-구조)
- [Node.js 특징](#node.js-특징)
- [Node.js 장단점](#node.js-장단점)
- [NPM](#node-packaged-manager)
- [참가자](#참가자)

# Node.js 배경

[목록으로](#INDEX)

# Node.js 개념

웹 브라우저위에서 동작하던 JS가 서버를 제어할 수 있도록 해주는 **JS Run time**이다.이벤트 기반, non-blocking I/O 모델을 사용하여 가볍고 효율적이며 거대한 패키지 생태계인 npm를 통해 쉽게 모듈 확장이 가능하다.

NodeJs는 이벤트 기반으로 개발이 가능하며 Non-Blocking I/O를 지원하기 때문에 **비동기식 프로그래밍**이 가능하다. 이 때문에 I/O 부하가 심한 대규모 서비스를 개발하기 적합하다고 할 수 있다. 또한 자바스크립트의 표준라이브러리 프로젝트인 CommonJS의 스펙을 따르고 있어 일반적인 범용 언어으로 타 코드를 쉽게 사용할 수 있다.

[목록으로](#INDEX)

# Node.js 구조

![node.js구조](https://t1.daumcdn.net/cfile/tistory/995D0F3B5ABE2B0405)

Node.js는 **binding API(C++ Addon)**를 활용해 **libuv**과 연결되며 I/O 작업을 **동기식**으로 libuv가 처리한 뒤 I/O 작업이 끝나면 **콜백함수**가 처리되는 것이다.

**I/O 작업**은 네트워크, 파일 시스템, 프로세스 등이 있다.
여러 Thread를 사용하기 때문에 I/O 작업이 많은 곳에서 Node.js가 활용이 좋다.

출처: [https://psyhm.tistory.com/9]

## libuv

Node.js의 또 하나의 중요한 의존성은 **libuv**이다. libuv는 **C 라이브러리로 논블로킹 I/O 작업을 지원하는 모든 플랫폼에서 일관된 인터페이스로 추상화**하는 데 사용됩니다. 

libuv는 파일 시스템, DNS, 네트워크, 자식 프로세스, 파이프, 신호 처리, 폴링, 스트리밍을 다루는 메커니즘을 제공하고 운영체제 수준에서 비동기로 처리될 수 없는 작업을 위한 스레드 풀도 포함하고 있습니다.

출처: [https://nodejs.org/ko/docs/meta/topics/dependencies/#libuv]


[목록으로](#index)

# Node.js 특징

## Single Thread

싱글 쓰레드를 가진 노드는 I/O 작업이 시작되면 I/O 작업 처리에 대한 응답을 기다리지 않고, **바로 다음 작업을 실행**해버린다. 대신 I/O 작업이 종료되면 이벤트를 발생시키고, 이 이벤트는 해당 프로세스의 이벤트 큐에 등록되게 된다. 노드로 개발된 프로세스는 이 이벤트 큐에 등록된 새로운 이벤트를 감지하여, 해당 이벤트 시 수행하여야 할 작업을 실행하는 로직을 가진다.

## V8 Engine 

V8 자바스크립트 엔진은 속도가 매우 빠르다는 장점과 더불어 구글이 해당 엔진을 개발하는 만큼 끊임없이 개선되고 발전할 것이다. 적극적인 개선과 발전으로 미래에 더 훌륭한 퍼포먼스를 가지게 될 것이라는 기대가 가능하다.

### V8이란 무엇인가?

V8은 오픈 소스이고 C++로 작성된 JavaScrpt 엔진이다. V8은 인터프리터(프로그래밍 언어의 소스 코드를 바로 실행하는 컴퓨터 프로그램 또는 환경)를 이용하는 대신 JavaScropt 코드를 좀더 효율적인 기계어 코드로 번역한다. V8은 SpiderMonkey나 Rhino 같은 많은 JavaScript 엔진처럼 JLT(Just-In-Time) 컴파일러를 적용하여 JavaScript 코드를 실행할 때 컴파일하여 기계어 코드로 만든다. V8의 가장 큰 차이는 바이트코드 또는 다른 중간 코드를 생성하지 않는 다는 것이다.

V8엔진은 다음과 같이 최적화된 코드를 생성한다.

### 인라이닝

![인라이닝](https://t1.daumcdn.net/cfile/tistory/9943DA425AA4EC1619)

첫 번째 최적화는 미리 가능한 많은 코드를 인라이닝(inlining) 하는것이다. 인라이닝은 호출 지점(함수가 호출된 곳의 코드 위치)을 호출된 함수의 내용으로 변환하는 과정이다. 

### 히든클래스 

V8은 히든클래스를 생성하여 프로퍼티 접근 시간을 줄일 수 있다.
다른 JavaScript Engine이 프로퍼티를 저장 하기 위해서 사전식 데이터 구조를 이용하지만, V8은 hidden class를 이용한다. 이 둘의 차이는 단순하게 이야기 해서 해싱과 포인터의 차이라고 할 수 있다.

V8은 객체에 프로퍼티를 추가할 때 히든 클래스를 생성하고, 히든 클래스에 프로퍼티의 정적인 위치를 저장함으로써 실제 데이터가 저장되어 있는 위치에 대한 Pointer를 제공한다. 
매번 프로퍼티를 추가할 때 마다 새로운 히든클래스를 생성하는 방식은 상당히 비효율 적이지만, 다음 번에 같은 객체를 생성할 때 이전에 생성했던 히든클래스를 재사용 함으로써 객체 생성 비용을 줄일 수 있다.


## Non-Blocking I/O

I/O 작업을 진행하는 동안 유저 프로세스의 작업을 중단시키지 않는다. non-blocking I/O의 경우 읽기/쓰기 이벤트가 발생하는 경우 데이터를 반환할 때 까지 기다리지 않고 다음 명령을 수행시킨다.  Non-blocking I/O 방식을 사용하면 외부에 I/O 작업을 하도록 요청한 후 즉시 다음 작업을 처리함으로써 시스템 자원을 더 효율적으로 사용할 수 있게된다. 그러나 I/O 작업이 완료된 이후에 처리해야하는 후속 작업이 있다면, I/O 작업이 완료될 때까지 기다려야 한다. 따라서 이 후속 작업이 프로세스를 멈추지 않도록 만들기 위해, I/O 작업이 완료된 이후 후속 작업을 이어서 진행할 수 있도록 별도의 약속([Polling](https://en.wikipedia.org/wiki/Asynchronous_I/O#Polling), [Callback function](https://en.wikipedia.org/wiki/Asynchronous_I/O#Callback_functions) 등)을 한다. 

## Event-Driven

사용자가 이벤트를 발생시켰을 때, 즉 입력장치로 데이터를 전송했을 때에만 작동한다. 발생한 이벤트에 대해서만 웹서버가 연결을 해주기 떄문에 자원을 최소화 할 수 있다.

> 대부분의 웹 서버는 이벤트가 발생할때까지 기다리면서 자원(대기시간/메모리)을 소비한다.

## Node의 모듈 시스템

[목록으로](#INDEX)

# Node.js의 장단점

## Node.js의 장점

1. 자바스크립트를 사용한다. 모든 웹 개발자는 자바스크립트를 알고 있다. 따라서 모든 웹 개발자가 쉽게 접근할 수 있다.
2. 구글이 만드는 V8 자바스크립트 엔진을 사용한다. Node.js는 구글이 무너지지 않는 한 계속 빨라질 것이다.
3. Node.js는 Non-blocking I/O와 단일 스레드 이벤트 루프를 통한 높은 Request 처리 성능을 가지고 있다. 데이터베이스로부터 대량의 데이터를 취득하여 웹페이지에 표시하는 처리의 경우, 일반적으로 데이터베이스 처리에 대기시간(blocking)이 발생하기 때문에 웹페이지 표시가 지연되는 현상이 발생한다.

Non-blocking I/O는 비동기 처리를 실시하므로 데이터베이스 처리와 웹페이지 표시를 별도 진행하여 스트레스없이 웹페이지 표시가 기능하다.

## Node.js의 단점

 NodeJs는 자바스크립트와  싱글 쓰레드 모델에서 오는 장점이 있는 반면 여기서 오는 단점 역시 만만하지 않다. 기본적으로 싱글 쓰레드 모델이기 때문에, 하나의 작업 자체가 시간이 많이 걸리면, 전체 시스템의 성능이 아주 급격하게 떨어진다. 그래서, 가벼운 작업 위주로 개발이 되어야 하고, 자바스크립트에서 오는 문제점은 자바나 다른 언어에 비해서 명시성이 떨어지기 때문에, 코드의 가독성이 자바언어에 비해서 상대적으로 낮기 때문에 유지 보수가 어려워질 수 있다 또한 이벤트 Call back 을 형태를 기준으로 하기 때문에, 이러한 call back이 중첩될 경우 (이를 callback hell이라고 한다.) 코드의 가독성이 급격하게 떨어진다.

[목록으로](#INDEX)

# Node Packaged Manager

NPM은 node.js 기반의 모듈들을 모아둔 집합으로, node.js 패키지를 관리하는 패키지 매니저이기도 하다. 즉 NPM은 Node.js에서 사용할 수 있는 모듈들을 패키지화하여 모아둔 저장소 역할과 패키지 설치 및 관리를 위한 CLI(Command line interface)를 제공한다. 

참고로 모듈은 프로젝트를 진행하면서 사용할 수 있는 자바 스크립트 라이브러리로, 패키지는 이러한 모듈들 중에서 필요로 하는 모든 파일들을 포함한 개념이다. 이러한 패키지들을 적절하게 활용하기 위해 도움을 주는 것이 NPM의 역할이라고 볼 수 있다.

npm으로 패키지를 설치하는 방법은 기본적으로  `` npm install package명 `` 이다. 여기서 전역으로 설치하려면 install 뒤에 -g 옵션을 주면 된다.  npm은 install 말고도 start, owner, update, dedupe, root 등  다양한 명령어들이 존재한다.

```
npm update  : 설치한 패키지를 업데이트하는 명령어
npm dedupe : npm으로 설치한 중복된 패키지들을 정리할 때 사용, 용량 정리에 도움
npm root : node_modules 폴더의 위치를 알 수 있는 명령어
npm outdated : 오래된 패키지를 색으로 표시해주는 명령어
npm bugs : 버그가 발생했을 시 패키지를 만든 사람에게 연락을 취할지 말지 알려주는 명령어
npm search : npm 저장소에서 패키지를 검색하는 명령어
```
하지만 이렇게 외부 모듈들을 설치해서 사용하다보면 필요한 패키지 수만큼 npm을 써야하고 관리하기도 번거로워질 수 있다. 그래서 ``npm init``으로 package.json 파일을 만들어서 추가적인 패키지 관리를 하면 좋다.

[목록으로](#INDEX)

# 참가자
1. 지현이
2. 허정민
3. 최영훈
4. 이재용
5. 이소희
6. 
7. 
8. 

[목록으로](#INDEX)

### 출처

[nodejs란](https://asfirstalways.tistory.com/43 )

[non-blocking I/O](https://tech.peoplefund.co.kr/2017/08/02/non-blocking-asynchronous-concurrency.html )

[nodejs 장단점](https://zbulletjournal.tistory.com/85)

[위키백과 NodeJs](https://ko.wikipedia.org/wiki/Node.js )

[npm 명령어](https://www.zerocho.com/category/NodeJS/post/58285e4840a6d700184ebd87)

[npm 소개](https://poiemaweb.com/nodejs-npm)

[npm 소개2](https://www.w3schools.com/nodejs/nodejs_npm.asp)

[V8엔진](https://engineering.huiseoul.com/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%9E%91%EB%8F%99%ED%95%98%EB%8A%94%EA%B0%80-v8-%EC%97%94%EC%A7%84%EC%9D%98-%EB%82%B4%EB%B6%80-%EC%B5%9C%EC%A0%81%ED%99%94%EB%90%9C-%EC%BD%94%EB%93%9C%EB%A5%BC-%EC%9E%91%EC%84%B1%EC%9D%84-%EC%9C%84%ED%95%9C-%EB%8B%A4%EC%84%AF-%EA%B0%80%EC%A7%80-%ED%8C%81-6c6f9832c1d9)


