# Node.js 정리 프로젝트

# Index
- [Node.js 배경](#NODE.JS-배경)
- [Node.js 란](#NODE.JS-란)
- [Node.js 구조](#NODE.JS-구조)
- [Node.js 특징](#NODE.JS-특징)
- [Node.js 장단점](#NODE.JS-장단점)
- [NPM](#Node-Packaged-Manager)
- [참가자](#참가자)

# Node.js 배경

[목록으로](#INDEX)

# Node.js 개념
- Node.js는 크롬 V8 자바스크립트 엔진으로 빌드된 자바스크립트 런타임으로, 이벤트 기반, 논블로킹 I/O 모델을 사용해 가볍고 효율적이다.
- Node.js의 패키지 생태계인 npm은 세계에서 가장 큰 오픈 소스 라이브러리 생태계이다.

[목록으로](#INDEX)

# Node.js 구조

[목록으로](#INDEX)

# Node.js 특징

## Single Thread

- 노드는 스레드를 늘리는 대신, 프로세스 자체를 복사해 여러 작업을 동시에 처리하는 멀티 프로세싱 방식을 사용한다.

## Non-Blocking I/O

- 이전 작업이 완료될 때까지 멈추지 않고 다음 작업을 수행하는 것.
> setTimeout(콜백, 0) : 코드를 논블로킹으로 만드는 기법 중 하나. 브라우저와 노드에서는 기본적인 지연 시간이 있으므로 바로 실행 되지는 않는다. HTML5 브라우저에서는 4ms, 노드에서는 1ms의 지연시간이 있다.

- 블로킹 : 이전 작업이 끝날때까지 기다렸다가 다음 작업을 수행한다.

## Event-Driven

- 이벤트가 발행할 때 미리 지정해둔 작업을 수행하는 방식
> 이벤트로는 클릭이나 네트워크 요청 등이 있다.
> 미리 작업을 지정해두는 것을 '이벤트 리스너에 콜백 함수를 등록한다.' 고 한다.
> 이벤트 루프 : 여러 이벤트가 동시에 발생했을 때, 어떤 순서로 콜백 함수를 호출할지를 판단하는 행위
![image](https://user-images.githubusercontent.com/35549653/68538254-d7ef4400-03b4-11ea-8675-a5184d84538f.png)

- setTimeout(콜백, 밀리초);  ->  특정 밀리초(1000분의 1초) 이후에 콜백에 해당하는 코드를 실행하는 함수

## Node의 모듈 시스템

[목록으로](#INDEX)

# Node.js의 장단점

## Node.js의 장점

## Node.js의 단점

[목록으로](#INDEX)

# Node Packaged Manager
npm은 node package manager의 약자로, 앞서 설며한 모듈들에 대한 설치 및 의존성을 관리해 주는 도구이다. 마치 Linux의 rpm이나 Python의 pip 처럼 설치를 하면, repository에서 해당 모듈을 읽어다가 설치를 해주며, java의 maven처럼 package.json 이라는 파일에 (pom.xml과 비슷한 역할을 함) module간의 dependency (의존성)에 따라서 의존성이 있는 모듈을 같이 설치한다.

*주요 명령어*
여러가지 기능들이 있지만, 주요한 명령을 설명한다.

- npm list {module} {-g} : 이 명령은 현재 디렉토리 아래에 설치되어 있는 확장 모듈을 리스트 해준다. {module}을 정해주면, 해당 모듈에 대한 리스트를 출력해주고, {-g} 옵션을 추가하면 global에 설치된 모듈 리스트들을 출력해준다.

- npm install {-g} : npm 레파지토리 (maven 레파지토리 처럼 외부에 설치되어 있음)로부터, 모듈을 읽어서 로컬에 설치한다. –g 옵션을 적용할 경우 전역 모듈로 설치한다.

- npm update {module} {-g} : 설치된 모듈을 최신 버전으로 업데이트 한다.

- npm remove {module} {-g} : 설치된 모듈을 삭제한다.

- npm info {module} : 해당 모듈의 의존성, 모듈명등 상세 정보를 출력한다.

- npm init : 이 명령어를 수행하면 interactive prompt 모드를 통해서 package.json 파일을 만들기 위한 사용자로부터 받아서, package.json 파일을 생성해준다.

[목록으로](#INDEX)

# 참가자
1. 이시연
2. 
3. 
4. 
5. 
6. 
7. 
8. 


# Reference
(http://bcho.tistory.com/885)
(https://charming-jung.tistory.com/80)

[목록으로](#INDEX)
