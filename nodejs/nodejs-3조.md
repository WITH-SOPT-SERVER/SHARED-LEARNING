# Node.js 정리 프로젝트

> 이 문서를 복붙해서 시작하셔도 됩니다.

> ※ 아래 항목은 예시일 뿐입니다. 자요롭게 조원끼리 구성을 만들고 공부해서 내용을 공유하시면 됩니다!!

> 내용의 출처 링크를 꼭 남겨주세요!!

# Index
- [Node.js 배경](#nodejs-배경)
- [Node.js 란](#nodejs-개념)
- [Node.js 구조](#nodejs-구조)
- [Node.js 특징](#nodejs-특징)
- [Node.js 장단점](#nodejs-장단점)
- [NPM](#Node-Packaged-Manager)
- (자유롭게 추가 가능)
- [참가자](#참가자)

# Node.js 배경

[목록으로](#INDEX)

# Node.js 개념
Node js란?
: 자바스크립트를 이용해서 서버를 만들 수 있는 개발도구이다.
(노드제이에스라고 불러도 되며 노드라도 불러도 된다.)

크롬 V8 자바스크립트 엔진으로 빌드된 자바스크립트 런타임이다. 
Node.js는 이벤트 기반, 논블로킹 I/O 모델을 사용해 가볍고 효율적이다. 
Node.js의 패키지 생태계인 npm은 세계에서 가장 큰 오픈 소스 라이브러리 생태계이기도 한다.

왜 노드를 사용해야할까?
- 웹 서버에 파일을 업로드할 때, 업로드가 완료되기 전까지 웹 서버에서 데이터를 조회한다거나 하는 등의 다른 작업을 할 수 없었다. 이 문제를 해결하기 위해 새로운 방식의 서버 개발 도구를 만들기 시작했는데 그것이 바로 "노드"다.

[출처]https://nodejs.org/ko/
Do it! Node.js 프로그래밍 책

[목록으로](#INDEX)

# Node.js 구조

### Node.js 시스템 구조 / 내부구조 

![node js 시스템 구조에 대한 이미지 검색결과](https://wckhg89.github.io/images/20160929_node_arch.jpg)

[출처]  https://wckhg89.github.io/images/20160929_node_arch.jpg



#### 가장 아래 빨간 부분 

> node.js는 구글 V8 자바스크립으 엔진을 기본으로 한다. 이를 기반으로 Single-thread 기반의 Event Loop (libev)가 돌면서 요청을 처리한다. 그림을 보면 Thread Pool (libeio)를 볼 수 있다. 이는 시스템적으로 non-blocking IO를 지원하지 않는 IO 호출이 있는 경우, 이를 비동기 처리 하기 위해 내부의 Thread Pool을 별도 이용하여 차리하도록 되어 있다.



#### 중간 파란 부분 

> 이 영역은 네트워크 프로토콜 (http …)을 처리하는 socket, http 바인딩 모듈등이 있다.



#### 맨위 오렌지 부분 

>  노드 JS의 기본 라이브러리를 말합니다. 노드에서 기본적으로 제공하는 라이브러리(모듈)에는 HTTP, TCP, FS, OS, EVENT 모듈 등이 있다. 노드 기본 라이브러리는 require를 할때에 별도의 경로 지정없이 사용할 수 있다. 



### Event Loop 구조 


이벤트 루프는 가능하다면 언제나 **시스템 커널에 작업을 넘겨서** Node.js가 **none-blocking I/O 작업을 수행**하도록 해준다.



대부분의 현대 커널은 **멀티 스레드**이므로 백그라운드에서 다수의 작업을 실행할 수 있습니다. 이러한 작업 중 하나가 완료되면 **커널이 Node.js에게 알려주어 콜백 함수를 poll 큐에 추가**할 수 있게 하여 동시성 있게 처리하도록 합니다. 



![img](https://t1.daumcdn.net/cfile/tistory/998056375ABE334D19)

[출처] https://psyhm.tistory.com/9



#### 이벤트 루프의 작업순서

- **Timers**: 이 단계는 setTimeout()과 setInterval()로 스케줄링한 콜백 실행

- **I/O callbacks**: 클로즈 콜백, 타이버로 스케줄링된 콜백, setImmediate()를 제외한 거의 모든 콜백을 실행

- **Idle, prepare**: 내부용으로만 사용

- **Poll**: 새로운 I/O 이벤트를 가져오며 node는 이곳에서 적절한 시기에 block 한다. 

- **Check**: setImmediate() 콜백은 여기서 호출됩니다.

- **Close callbacks**

  

>  이벤트 루프는 이 모든 큐 들에 존재하는 작업들을 순차적으로 처리함으로써 비즈니스 로직을 수행한다.

[목록으로](#INDEX)

# Node.js 특징

## Single Thread

>nodejs 요청들이 모두 같은 스레드에서 실행된다.
>
>실제로는 내부적으로 여러 스레드가 동작하나 
>
>개발자가 제어하는 것을 싱글스레드이다.

## Non-Blocking I/O

>___논 -블로킹___: 이전 작업이 완료될 때 까지, 기다리면서 멈추지 않고, 다음작업이 지연되지 않게 동작하는 패러다임이다.
>
>오래걸리는 작업은 백그라운드에서 진행하며 완료 후 , 이벤트 루프를 통해 태스크 큐를 거쳐 호출 스택에 올라오길 기다리는 방식으로 
>
>시간이 많이 걸리는 다른 컴퓨팅 자원에 접근하는 I/O 는 논 블로킽 방식으로 채택..
>
>---> 비동기 개념으로 쉽게 이해 가능

## Event-Driven

>+ 이벤트가 발생하였을 때, 저장해둔 작업을 수행하는 방식
>+ 이벤트 리스너에 미리 콜백함수를 저장해 놓고 , 입려된 이벤트에 따라 해당되는 작업을 수행
>+ 발생한 이벤트는 순차적으로 처리하며, 발생한 이벤트가 없다면, 대기한다.
>+ 이벤트 루프가 이벤트 처리 순서를 관리해 준다.

[출처]<https://namjackson.tistory.com/30>

[출처] <https://seungwoohong.tistory.com/7>

## Node의 모듈 시스템

>___모듈___: 독립적인 하나의 소프트웨어
>
>Node .js는 파일 하나하나가 모듈로 기능.
>
>~~~javascript
>module.exports
>~~~
>
>=> 대표적인 모듈 생성 방법

<예시>

~~~javascript
//calc.js
function add(a, b) {
  return a + b;
}
function multiply(a, b) {
  return a * b;
}


module.exports = {
  add: add,
  multiply: multiply,
};
~~~

 ~~~javascript
//main.js
const add = require('./calsc.js').add;
const multiply = require('./calc.js').multiply;

console.log(multiply(add(1,2),add(3,2)));
 ~~~

[출처] <https://www.zerocho.com/category/NodeJS/post/5835b500373b5b0018a81a10>

또 다른 모듈 예시를 참고해보고 싶다면

[여기로] <https://andole87.github.io/til/node-module/#>



------------------

궁금해서 찾아본 v8

> 자바스크립트 엔진이다.
>
> 자바스크립트 엔진은 자바스크립트 코드를 실행하는 프로그램 혹은 인터프리터를 말한다.
>
> 자바스크립트 엔진은 표준적인 인터프리터로 구현될 수도 있고 혹은 자바스크립트 코드를 바이트코드로 컴파일하는 
>
> 저스트인타임(just-in-time) 컴파일로서 구현할 수도 있다.

v8은 자바스크립트 엔진을 구현하는 유명한 프로젝트들 중 하나로 오픈 소스이며

구글에서 개발 그리고 c++로 작성된 자바스크립트 엔진이다.



그럼 v8엔진과 다른 엔진들과의 차이점은 무엇일까?

--> 노드 js 의 런타임으로도 사용된다는 점

(웹 브라우저 내부에서 자바스크립트 수행 속도의 개선을 목표로 처음 고안)

[출처] <https://engineering.huiseoul.com/자바스크립트는-어떻게-작동하는가-v8-엔진의-내부-최적화된-코드를-작성을-위한-다섯-가지-팁-6c6f9832c1d9>

[목록으로](#INDEX)

# Node.js 장단점

## Node.js의 장점
1. Node.js는 비동기 I/O 처리를 한다.
따라서 CPU로부터 I/O 응답을 기다리는 시간이 필요 없다. 또한 대부분의 CPU가 연산 작업에 사용되기 때문에 높은 효용성을 갖는다.

2. Node.js는 Single Thread 기반이다.
따라서 clock문제를 처리하는데 매우 최적화 되어 있다. 또한 multi Thread에서의 Thread간 동기화 처리 등의 복잡한 과정이 필요가 없다. 즉, 프로그래밍을 단순하게 만들어 준다.

3. 백엔드 영역 개발에 대한 진입 장벽을 낮춰주었다.
Node.js를 통해서 자바스크립트 기술을 가지고 백엔드 영역을 개발할 수 있게 되었다. 또한 Node.js로 인하여 프론트엔드와 백엔드 기술을 통합하여 생산성을 높이기 수월해졌다.

## Node.js의 단점
1. Node. js는 Single Thread 기반이다.
따라서 하나의 작업에 시간이 많이 걸리면 전체 시스템의 성능이 매우 급격하게 떨어진다. 따라서 가벼운 작업위주의 개발에 적절하다.

2. 자바스크립트의 가독성이 낮다.
자바 등 다른 언어에 비하여 코드의 가독성이 좋지 않아 유지 보수가 어렵다. JS의 가독성이 낮은 코드 예로는 call back이 여러 개 중첩돼있는 callback hell이 있다.

3. 자바스크립트는 해당 코드가 수행이 되어야 에러를 확인할 수 있다.
이러한 특징은 script언어의 특징으로 해당 코드가 수행 되어야만 에러를 확인할 수 있고 에러가 나면 프로세스가 다운되기 때문에 프로세스가 잘 죽는다는 단점이 있다.
또한 개발 과정에서 코드 테스트에 비중이 많이 들어간다.
-> watch dog, domain API 등으로 상당 부분 해결 가능하다.

**즉, node.js는 개발 과정이 빠르고 쉽다는 장점이 있지만 운영 시 테스트, 장애 대응, 디버깅 등에 대해서 신경 쓸 부분이 많다는 단점이 있다.**

(참고블로그 : https://bcho.tistory.com/876) 

[목록으로](#INDEX)

# Node Packaged Manager

영상 - NPM 개념
[![IMAGE ALT TEXT HERE](https://user-images.githubusercontent.com/35513039/67358130-5e74ea80-f59a-11e9-8a60-c1a95d6c6d3f.png
)](https://www.youtube.com/watch?time_continue=2&v=x03fjb2VlGY)

```
만약 자바스크립트로 개발하고 있다면 NPM을 들어봤을 거예요
npm은 자바스크립트 개발자들에게 코드를 쉽게 공유하기 위해서 만들어 졌어요
또한 작은 문제들을 해결해주고 다른 개발자들의 애플리케이션을 재사용 할 수 있지요
다른 NPM 개발자의 코드를 사용하고 있다면 그 코드가 업데이트 된 것을 쉽게 확인 할 수 있고
다운로드를 할 수 있어요
재사용 할 수 있는 코드들을 packages 라고 부르거나 modules라고 불러요
package는 하나 또는 그 이상의 파일로 이루어진 폴더(directory) 예요
package의 형식은 json으로 되어있으며 metadata들이 포함되어 있어요.
웹 사이트와 같은 전형적인 애플리케이션들은 수백개의 package로 이루어져 있어요.
이러한 package들은 작아요.

일반적으로 작은 블록(package)이 하나의 문제를 해결해 나가요
이것들은 큰 문제점들을 해결하게 만들어요
공유된 빌딩 블록(package)들을 통해서 큰 문제들을 해결할 수 있게 해줍니다.
packages는 사용자의 팀이 다른 팀의 package를 가져와 특정한 문제를 해결하는데 많은 도움을 줍니다.
다른 팀의 코드를 재사용하지 않는다면 기본적인 모듈을 이용하여 다른 프로젝트에 재사용 할 수 있습니다.
그러면 팀의 일이 더 좋아질 거예요 

NPM 웹사이트에서 packages를 찾을 수 있어요. 
웹사이트에 들어가면 다른 종류들의 packages들을 볼 수 있어요

많은 node module들은 node package manager로써 시작해요
그래서 많은 모듈들은 서버 기반으로 사용되죠.
많은 package들은 CLI를 통해 사용할 수 있어요. 
그리고 브라우저에서 package의 이용자 수를 찾을 수 있는데 
이것을 통해 어떤 NPM을 사용할지 상의 할 수 있어요

사람들이 NPM에 대하여 이야기를 할 때 세가지 중 하나에 대해 이야기 하죠
하나는 웹사이트에서 본 것,
또 하나는 사람들이 공유한 많은 데이터로 이루어진 package registry에 대해 이야기 할 수 있어요
세 번째는 그들이 NPM Client로서 code를 공유할 때를 이야기 해요
코드를 공유하기 위해 컴퓨터에 설치된 NPM Client를 사용하여 registry에 올립니다.
그리고 registry에 있는 package 덕분에 다른 개발자들이 NPM Client를 사용하여 설치할 수 있어요.
registry에 있는 package 객체들은 업데이트된 package가 있는 웹사이트를 기반으로 해요. 

결국 NPM은 다른 개발자로 부터 코드를 재사용 할 수 있고 본인의 코드를 공유할 수 있는 수단이예요.
그리고 서로 다른 버전들을 가진 코드를 관리하기  편하게 해줘요.

기본적인 개념들을 다루어 보았어요  우리의 다른 영상들은 어떻게 NPM을 시작할 수 있을지 도움을 줄거예요 
```

# Node Packaged Manager #2

<h4>npm이란?</h4>

먼저, Node는 Node.js를 의미한다. Packaged라는 것은 package로 만들어진 것들을 의미한다. 

이 때, package는 모듈이라고도 불리는데, 패키지나 모듈은 프로그램보다는 조금 작은 단위의 기능들을 의미한다.

Manager는 관리자를 의미한다.

즉, npm은 Node.js로 만들어진 package(module)을 관리해주는 툴이다.



<h4>어떻게 npm을 사용하는가?</h4>

우선 npm을 설치해야 하는데, 지금은 node.js를 설치하면 내장되어있다.

npm을 사용한다는 것은 곧 모듈을 활용한다는 뜻이므로, 가장 먼저 해야 할 일은 사용할 모듈을 다운로드 하는 것이다.

아래 코드를 사용하여 모듈을 다운로드 해준다.

```javascript
npm install '모듈 이름'
```



이렇게 하나하나 설치할 수도 있지만 모듈의 의존성을 한꺼번에 관리하는 방법도 있다. 

json 파일을 만들어 그 안에 기록을 통해 관리한다. 우선 json 파일을 생성한다.

```javascript
npm init
```

위 명령어를 terminal 창 등에 입력하면 name을 시작으로 여러 가지를 입력 요청받는다.

이름 규약같은 것을 위반하지 않았으면 엔터를 치면 default로 등록 된다. 

그 단계에서 바로 설정을 해도 되고 나중에 수정할 수도 있다.

package.json 파일이 생성될 것이다.



package.json 파일이 정리되면 배포를 해야할 때 파일만 같이 배포를 한다면 해당 프로그램 개발에 사용되었던 모듈을 그대로 install 할 수 있게 된다. install은 위의 모듈 다운로드 처럼

```javascript
npm install '모듈 이름'
```

명령어를 사용하여 사용하면 된다.

(참고 블로그 : https://m.blog.naver.com/magnking/220961896609)


[목록으로](#INDEX)

# 참가자
1. 김강희 - NPM 개념
2. 김채린 - Node.js 구조
3. 김민준 - Node.js 장점 및 단점 
4. 이소연 - Node.js 특징
5. 유희수 - Node.js 개념
6. 조수민 - NPM 개념
7. 
8. 

[목록으로](#INDEX)

