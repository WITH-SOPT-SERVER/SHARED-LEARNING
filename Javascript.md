# Javascript

## index

-   [Javascript](#자바스크립트란) ★
-   [변수](#변수) ★
-   [데이터타입](#데이터타입) ★
-   [동적언어와 정적언어](#동적언어와-정적언어)
-   [객체지향 언어의 2줄기](#객체지향-언어의-2줄기)
-   [객체 지향과 객체 기반](#객체지향과-객체-기반)
-   [자바스크립트의 오브젝트](#자바스크립트-오브젝트) ★
-   [리터럴](#리터럴) ★
-   [스코프](#스코프) ★
-   [호이스팅](#호이스팅) ★
-   [Closure](#클로저)★
-   [ECMA 스크립트](#에크마스크립트)
-   [고차원함수](#고차원함수)
-   [apply, bind, call](#함수호출)
-   [순수성, 불변성](#)
-   [흐름기반](#)
-   [Underscore](#언더스코어)

## 자바스크립트란

> 객체 기반의 언어

프로토타입 기반의 객체지향 언어입니다.
즉 상속과 클래스라는 개념이 없습니다.

> 인터프리터 언어

실행하는 시점에서 실행되는 동적언어입니다.

[목차로 돌아가기](#index)

## 변수

자바스크립트에서 변수는 `var`를 사용합니다.
자바스크립트의 변수는 실행되는 시점에서 메모리에 할당됩니다.

[목차로 돌아가기](#index)

## 데이터타입

### 원시 데이터 타입

원시 데이터 타입인 number, string, boolean이 있습니다.

```
var number = 24
var string = "String"
var bool = true
```

### null, undefined

null, undefined의 추가적인 데이터 타입이 있습니다.

```
console.log(data)	//undefined
var data;
console.log(data)	//null
```

※ 자바스크립트는 인터프리터 언어로 실행되는 시점에 메모리에 할당됩니다. 따라서 메모리에 할당되기 전은 undefined, 할당된 이후는 null으로 분류됩니다.

### 배열

배열은 `[]`를 이용해서 배열을 구현합니다.
배열안에 변수는 여러 데이터타입이 들어 갈 수 있습니다.

```
var arr = [1, 2, "안녕하세요"]
```

### 객체

객체는 `{}`를 이용해서 객체를 구현합니다.

```
var obj = { id: 25, name: "윤희성"}
```

### 함수

자바스크립트는 1급시민 함수를 지원하여서 함수를 변수에 저장할 수 있습니다.

```
var addFunc = function (a, b) {
  return a + b;
};
```

[목차로 돌아가기](#index)

## 동적언어와 정적언어

프로그랭 언어는 크게 정적언어(컴파일 언어)와 동적언어(인터프리터)로 구분됩니다.
프로그램 언어는 크게 정적언어(컴파일 언어)와 동적언어(인터프리터)로 구분됩니다.

### 정적언어/타입 (컴파일)

C언어, JAVA등이 대표적인 정적언어입니다.
정적 언어는 컴파일을 통해서 프로그램 실행파일이 만들어집니다.
정적 타입은 컴파일 하는 시점에 자료형을 결정합니다.

#### 장점

-   미리 컴파일을 하기 때문에 런타임 속도 ↑
-   컴파일 시점에 에러 체크할 수 있음

#### 단점

-   코드를 수정하면 전체를 다시 컴파일 해야 한다.
-   운영체제가 달라지면 다시 컴파일을 해야 한다

### 동적언어/타입 (인터프리터)

javascript, python등이 대표적인 동적언어입니다.
동적 언어는 컴파일이라는 과정없이 바로 실행됩니다.
동적 타입은 실행하는 시점에서 자료형을 결정합니다

#### 장점

-   코드 수정시 바꾼 부분만 번역, 실행하여 빠르게 수정 가능하다.
-   타입을 지정하지 않아도 되기 때문에 빠르게 개발이 가능하다.

#### 단점

-   런타임 속도 ↓
-   실행하기 전까지 프로그램 에러를 확인할 수 없다.

> **동적언어를 쓰는 이유**
> 프로그램 성능상으로는 정적언어가 우수합니다. 하지만 최근 컴퓨터, 서버, 하드웨어의 비용이 저렴해지면서 실행속도 자체보다 개발속도가 더 중요하게 되었다. 이러한 이유로 동적언어가 많이 쓰이고 있습니다.

[목차로 돌아가기](#index)

## 객체지향 언어의 2줄기

객체지향 언어에는 클래스 기반과 프로토타입 기반 2가지가 존재합니다.
자바스크립트는 이중에서 프로토타입을 기반의 **객체기반** 언어입니다.

### 클래스 기반 언어(C++, Java, C#, Ruby, Python 등)

클래스 기반 언어에서는, 객체의 형식이 정의된 클래스라는 개념이 있습니다.
클래스 기반 언어에서만 **상속**이라는 개념을 갖습니다.

### 프로토타입 기반 언어

프로토타입 기반 언어에서는 **클래스라는 개념이 존재하지 않습니다**.

대신 여러 종류의 Built-in 객체들이 시스템 상에 존재하게 됩니다.
또한 객체 원형의 위임 과정을 통해 상속 과정이 구현됩니다.

[자세히 보기](http://mohwa.github.io/blog/javascript/2015/10/16/prototype/)

[목차로 돌아가기](#index)

#### 프로토타입의 유래와 기반 개념

프로토타입이라는 개념은 디자인 패턴(Design Pattern)에서 나왔습니다.
디자인 패턴은 건축학 및 컴퓨터 과학에서 사용되는 용어로, 설계 문제에 대한 해답을 문서화 하기 위해 고안되었습니다.
그 중 프로토타입 패턴은 생성할 객체들의 타입이 프로토타입인 인스턴스로부터 결정되도록 하며, 인스턴스는 새 객체를 만들기 위해 자신을 복제(clone)하게 되는 패턴을 말합니다.

프로토타입을 사용하면서 얻는 이점은 다음과 같다고 합니다.

-   프로토타입 패턴은, 추상 팩토리 패턴과는 반대로, 클라이언트 응용 프로그램 코드 내에서 객체 창조자(creator)를 서브클래스(subclass)하는 것을 피할 수 있게 해줍니다.
-   프로토타입 패턴은 새로운 객체는 일반적인 방법(예를 들어, new를 사용해서라든지)으로 객체를 생성(create)하는 고유의 비용이 주어진 응용 프로그램 상황에 있어서 불가피하게 매우 클 때, 이 비용을 감내하지 않을 수 있게 해줍니다.
    [디자인 패턴 자세히 보기](https://gmlwjd9405.github.io/2018/07/06/design-pattern.html)
    [목차로 돌아가기](#index)

## 자바스크립트 오브젝트

자바스크립트는 객체 기반의 스크립트 언어이며 자바스크립트를 이루고 있는 모든 것들이 객체로 존재합니다.

객체는 **프로퍼티(Property)** 와 **메소드(Method)** 로 이루어집니다.

### 프로퍼티

프로퍼티는 **객체의 속성**을 나타내는 접근 가능한 이름과 활용 가능한 값을 가지는 특별한 형태입니다.

```
var foo = {}
foo.id = 25	// .연산자를 이용하여 id라는 이름의 프로퍼티를 생성+할당
console.log(foo.id) // .연산자를 이용하여 foo 객체의 id 프로퍼티 접근
```

여기서 주의해야하는 점 한가지가 프로퍼티의 삭제는 반드시 delete라는 키워드를 사용해야 합니다. 즉 undefined나 null을 할당한다고 삭제되지 않습니다.

#### 프로퍼티의 2가지 종류

- instance property

   특정 object 인스턴스의 특정 데이터를 갖고 있다. 

- static property

   모든 object 인스턴스들에게 공유된 데이터를 갖고 잇다. 

### 메소드

**메소드는 객체가 가지고있는 동작**입니다.
동작이라는 의미에서 함수와 메소드는 같지만 이 둘은 다른 개념입니다.
메소드는 **객체를 통해서 해당 메소드를 수행한다**. 즉 객체를 생성한 이후에 동작을 지시할 수 있으며 이때 주체는 객체입니다.
이와 다르게 함수는 함수자체가 **함수객체**이기 때문에 자기 자신을 수행하는 것입니다.

자바스크립트에서 메소드는 각각 개별 객체로 존재합니다. 즉 객체에 속한 메타데이터를 사용하는 것이 아니라 그 **객체로 부터 파생되어 확장된 새로운 객체를 사용하는 것**입니다.

### 객체의 구성

#### 1. Built-in Object

Built-in Object는 자바스크립트 내장객체입니다.
여기에는 Global, Object, String, Number, Boolean, Date, Array, Math, RegExp, Error이 있습니다.

#### 2. Native Object

Native Object는 브라우져 내장객체입니다.
자바스크립트가 구동되는 시점에서 바로 사용할 수 있지만 이들은 **자바스크립트 엔진을 구동하는 녀석들에서 빌드되는 객체**입니다.
BOM(브라우저 객체 모델), DOM(문서 객체 모델)등이 이에 속합니다.

#### 3. Host Object

개발자가 생성한 객체들을 Host Object라고 한다.

### Object

자바스크립트의 Object객체는 Top-Level-Object이며 자바스크립트의 모든 객체는 이 Object 객체에서 파생되어 나온 확장형태입니다.
이 Object객체에는 constructor, prototype이라는 프로퍼티와 hasOwnProperty, toString, isPrototypeOf의 메소드를 가지고 있습니다.

[자세히보기(object)](http://insanehong.kr/post/javascript-object/)

[자세히보기(프로터타입)](http://tcpschool.com/javascript/js_object_prototype)

[목차로 돌아가기](#index)

## 리터럴 표기법

리터럴은 사전적 의미로 **"있는 그대로의 의미"** 라고 합니다.

보통 객체를 생성할때는 new를 이용해서 생성합니다.

```
var no = new Number();
var str = new String();
var obj = new Object();
```

하지만 자바스크립트는 아래와 같이 리터럴 표기법을 지원합니다.

```
var no = 25;
var str = "sopt";
var obj = {name: "sopt", age: 25};
```

객체를 생성한 후에 값을 담는 것이 아니라 코드 자체가 값을 의미합니다.
리터럴 표기법의 장점은 **코드가 짧아지면** , 인터프리터가 **해석해야 하는 양이 줄어**든다는 장점이 있습니다.

[자세히보기](https://enarastudent.tistory.com/entry/자바스크립트-객체-생성과-리터럴-표기법)
[참고1](https://webclub.tistory.com/390)
[목차로 돌아가기](#index)

## 스코프

어떤 변수에 접근할 수 있는지를 정의하는 것을 스코프라 하며 여기에는 전역 스코프(global scope)와 지역 스코프(local scope)가 있습니다.

### 전역 스코프(global scope)

함수 안에 포함되지 않는 곳에서 정의된 것이며 코드 어디서든 참조할 수 있습니다.

### 지역 스코프(local scope)

함수 내에 정의 된 것으로 함수 내에서만 참조할 수 있습니다.

일반적인 언어는 Block-level scope를 사용하며 코드 블록 단위로 유효하다. 하지만 Javascript는 Function-level scope로 동작하여서 함수 블록 내에서 선언된 변수는 함수 블록 내에서만 유효합니다.

※여기서 변수는 `var`만을 의미합니다.

### 정적 스코프(Lexical scope)

```
var test = 'global'
funtion foo(){
	console.log(text);
}
function bar(){
	var text = 'bar';
	foo();
}
bar();
```

위 코드를 실행하면 `global`이 출력된다.

이는 어디서 호출하는지가 아니라 **어떤 스코프에 선언하였는지**에 따라 결정되기 때문이다.

[자세히 보기](https://edu.goorm.io/1.0/learn/lecture/557/바로-실행해보면서-배우는-node-js/lesson/226443/스코프와-호이스팅)

[목차로 돌아가기](#index)

## 호이스팅

```
function foo() {
	console.log(data);
	var data = 25;
	console.log(data);
}
```

위 코드를 실행하면 아래의 결과가 나옵니다.

```
undefined
25
```

var는 function scope이기 때문에 실제 코드는 아래와 같습니다.

```
function foo() {
	var data;
	console.log(data);
	var data = 25;
	console.log(data);
}
```

이렇게 함수안에 변수를 함수의 시작위치로 끌어 올리는 것을 호이스팅이라고 합니다.

[자세히 보기](https://edu.goorm.io/1.0/learn/lecture/557/바로-실행해보면서-배우는-node-js/lesson/226443/스코프와-호이스팅)

[목차로 돌아가기](#index)

## 클로저

클로저는 외부함수의 변수에 접근할 수 있는 내부함수를 말합니다.

```
function outerFunc(){
	const outer = "out var";
	function innerFunction(){
		console.log(outer);
	}
	return innerFunction;
}
outerFunction()();
```

이는 아래와 같이도 표현 가능합니다.

```
function outerFunc(){
	const outer = "out var";
	return function innerFunction(){
		console.log(outer);
	}
}
outerFunction()();
```

### 클로저 규칙과 부수효과

```
function celebrityName(firstName){
	var nameIntro = "Thie is celevrity is ";
	return function lastName(theLastName){
		return nameIntro + firstName + " " + theTalsName;
	}
}
var mjName = celebrityName("Michael");
mjName("Jackson");
```

```
This celebrity is Michael Jackson
```

클로저는 함수가 실행 되었을 때, 함수는 자신이 생성되었을 때와 동일한 스코프 체인을 사용합니다. 그러므로 내부 함수를 나중에 호출 할 수 있습니다.

```
function celebrityID() {
    var celebrityID = 999;
    return {
        getID: function() {
            return celebrityID;
        },
        setID: function(theNewID) {
            celebrityID = theNewID;
        }
    }
}
var mjID = celebrityID();
mjID.getID();
mjID.setID(567);
mjID.getID();
```

```
999
567
```

클로저는 값이 참조로 변수를 접근합니다. 따라서 첫번째 getID에서는 999를 출력하지만 setID(567) 이후에는 567이 출력되는 것을 확인할 수 있습니다.

[자세히 보기1](https://medium.com/@khwsc1/%EB%B2%88%EC%97%AD-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%8A%A4%EC%BD%94%ED%94%84%EC%99%80-%ED%81%B4%EB%A1%9C%EC%A0%80-javascript-scope-and-closures-8d402c976d19)
[자세히 보기2](http://chanlee.github.io/2013/12/10/understand-javascript-closure/)

[목차로 돌아가기](#index)

## 에크마스크립트

ECMAScript는 자바스크립트를 이루는 코어 스크립트입니다.

자바스크립트에 표준 규격이 필요해졌는데 이를 ECMA 국제기구에서 표준 규격을 만들어서 자바스크립트는 ECMAScript와 BOM, DOM이라는 1개의 코어와 2개의 모델로 이루어져있습니다.

ECMAScript를 줄여서 ES라고 부르는데 ES5는 2009년, ES6는 2015년에 만들어져 널리 사용중이다.
[자세히보기](https://takeuu.tistory.com/93)
[목차로 돌아가기](#index)

## 고차원함수

고차원 함수에 앞어서 1급 시민(first class citizen)에 대해서 알아야 합니다.

### 1급 시민 함수

-   변수(variable)에 담을 수 있다.
-   인자(parameter)로 전달할 수 있다.
-   반환값(return value)으로 전당할 수 있다.

위 조건을 만족하면 1급 시민의 조건을 충족합니다,

-   런타임 생성이 가능하다
-   익명으로 생성이 가능하다
    즉 위 조건까지 만족하는 함수를 1급 함수라고 할 수 있습니다.

### 고차원함수

하나 이상의 함수를 인수로 받거나 함수를 결과로 반환하는 함수를 고차원 함수라고 부릅니다.

[목차로 돌아가기](#index)

## 함수호출

함수를 호출하는 방법에는 2가지가 있습니다.

1. func();
2. func.call/apply/bind(...);

함수를 실행하면 주체가 존재하는데 this는 이를 가리킵니다.
이 this를 외부에서 지정하는 방법이 **call/apply/bind**입니다.

> **모든 함수에서 사용 가능**
> call, apply, bind는 Function.Prototype에서 물려받은 메소드(프로퍼티)이다. 즉 모든 함수에서 호출할 수 있다.

### 함수의 실행영역을 지정

call, apply, bind 첫번째 인자는 그 함수의 this가 됩니다. 즉 함수 자신의 실행 환경을 외부 this로 설정 할 수 있습니다.

### call 메소드

**call 구문**

```
fun.call(thisArg[, arg1[, arg2[, ...]]])
```

**thisArg**
fun 호출에 제공되는 this의 값입니다.
만약 이 값이 null 또는 undefined인 경우 전역 객체로 대체되고 원시값은 객체로 반환됩니다.
**arg1, arg2, ...**
객체를 위한 인수입니다.

#### 예시) 객체의 생성자 연결에 call 사용

```
function Product(name, price) {
	this.name = name;
	this.price = price;
	if(price < 0) {
		throw RangeError(`Cannot create product ${this.name} with a negative price`);
	}
}
function Food(name, price) {
	Product.call(this, name, price);
	this.category = 'food';
}
function Toy(name, price) {
	Product.call(this, name, price);
	this.category = 'toy';
}
var cheesze = new Food('feta', 5);
var fun = new Toy('robot', 40);
```

Food, Toy 함수는 각각의 this를 call 메소드를 통해서 Product로 전달하여 name과 price 속성을 지정하고 각각의 함수에서 category를 정의합니다.

[자세히보기](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/call)

### apply 메소드

> **call와 apply()의 차이**
> call()과 apply()는 유사하지만 call는 인수 목록을, apply는 인수 배열 하나를 받는 다는 점이 다릅니다.

**apply 구문**

```
fun.apply(thisArg, [argsArray])
```

**thisArg**
fun 호출에 제공되는 this의 값입니다.

**argsArray**
fun이 호출해야 하는 인수들을 지정하는 배열객체입니다..

#### 예제 1 배열을 붙이기 위해서 apply 사용

```
var array = ['a','b'];
var fisrt = ['a','b'];
var second = [0,1,2];
array.push(second);		// ['a','b',Array(3)];
first.push.apply(first, second);
console.log(first);		//['a','b',0,1,2];
```

array의 경우 일반 push를 하는 경우 배열 내부에 배열이 만들어 집니다.
이 결과가 원하는 동작이 아니라면 first와 같이 apply를 이용해서 구현할 수 있습니다.
push 함수의 주체를 first로 지정하고 함수가 호출해야 하는 인수를 second로 지정하여서 배열 붙이는 기능을 구현했습니다.

#### 예제 2 내장함수와 apply

```
var numbers = [5,6,2,3,7];
var max = Math.max.apply(null, numbers);
var min = Math.min.apply(null, numbers);
```

기존의 max를 구하기 위해서는 반복문을 이용해서 max값을 구해야 했다. 하지만 내장함수 Math에 apply를 적용한다면 위와 같이 간단하게 구현할 수 있다.

> **주의할점**
> 위와 같은 방법을 사용하면 Javascript 엔진의 인수 길이제한을 초과하는 위험성이 발생 할 수 있습니다. (JavascriptCore의 경우 인수의 개수 제한이 65536입니다.) 만약 엔진이 srguments의 상한을 4개로 했다고 가정하면 위 코드는 5, 6, 2,3만 apply에 전달되어 온것처럼 작동합니다.

[자세히보기](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/apply)

### bind 메소드

bind()함수는 새로운 바인딩한 함수를 만듭니다. 바인딩한 함수는 원본 함수 객체를 감싸는 함수로 특이 함수 객체(exotic function object)입니다.

```
var module = {
  x: 25,
  getX: function() {
    return this.x;
  }
}

var unboundGetX = module.getX;
console.log(unboundGetX()); // The function gets invoked at the global scope

var boundGetX = unboundGetX.bind(module);
console.log(boundGetX());
```

```
undefined
25
```

**bind 구문**
`func.bind(thisArg[, arg1[, arg2[, ...]]])`

**thisArg**
바인딩 함수가 대상 함수의 `this`에 전달하는 값입니다.

**arg1, arg2 ...**
대상 함수의 인수 앞에 사용될 인수입니다.

**반환값**
지정한 `this` 값 및 초기 인수를 사용하여 변경한 원본 함수의 복제본

**내부 속성**
바인딩한 함수는 다음과 같은 내부 속성을 가지고 있습니다.
BoundTargetFunction: 바인딩으로 감싼 원본 함수 객체
BoundThis: 감싸진 함수를 호출했을 때 항상 전달되는 값
BoundArguments: 감싸진 함수가 호출될 때 첫번째 인수로 사용되는 값들의 목록
Call: 이 객체와 관련된 코드 실행

바인딩된 함수가 호출되면 BoudTargetFunction의 내부메소드를 call(boundThis, args)를 호출합니다. 이때 boundThis는 BoundThis이고 args는 BoundArguments입니다.

#### 예제 1 바인딩된 함수 생성

```
this.x = 9;
var module = {
	x: 81,
	getX: function() { return this.x; }
};
module.getX();	// 81

var retrieveX = module.getX;
retrieveX(); 	// 9
```

위 예제와 같이 retrieveX를 호출하면 this는 원본객체(module)를 가르키지 않습니다. 따라서 실행결과는 81이 아닌 9가 나오게 됩니다.
이러한 경우 원본 객체를 가리키고 싶다면 bind를 활용해서 구현할 수 있습니다.

```
var boundGetX = retrieceX.bind(module);
boundGetX();	// 81
```

#### 예제 2 부분 적용 함수

bind를 활용하면 미리 지정된 초기인수가 있는 함수를 만들 수 있습니다.

```
function list() {
  return Array.prototype.slice.call(arguments);
}

var list1 = list(1, 2, 3); 						// [1, 2, 3]

// 선행될 인수를 설정하여 함수를 생성합니다.
var leadingThirtysevenList = list.bind(null, 37);
var list2 = leadingThirtysevenList();  			// [37]
var list3 = leadingThirtysevenList(1, 2, 3);  	// [37, 1, 2, 3]

function addArguments(arg1, arg2) {
    return arg1 + arg2
}

var result1 = addArguments(1, 2); 			// 3

var addThirtySeven = addArguments.bind(null, 37);
var result2 = addThirtySeven(5); 			// 37 + 5 = 42
var result3 = addThirtySeven(5, 10); 		// 37 + 5 = 42
```

위 예제와 같이 bind를 사용하여 37이라는 값이 이미 인자로 갖는 함수를 만들 수 있다.

#### 예제3 setTimeout과 함께 사용

setTimeout함수의 `this`는 `window` 또는 `global`객체가 된다. 이를 바꾸고 싶다면 아래의 예제와 같이 bind를 이용해서 가능하다.

```
function LateBloomer() {
  this.petalCount = Math.ceil(Math.random() * 12) + 1;
}

LateBloomer.prototype.bloom = function() {
  window.setTimeout(this.declare.bind(this), 1000);
};

LateBloomer.prototype.declare = function() {
  console.log('I am a beautiful flower with ' +
    this.petalCount + ' petals!');
};

var flower = new LateBloomer();
flower.bloom();
```

#### 예제4 바로가기 생성

```
var slice = Array.prototype.slice;
slice.apply(arguments);
```

위의 예제에서 bind를 적용한다면 아래와 같이 적용할 수 있습니다.

```
var unboundSlice = Array.prototype.slice;
var slice = Function.prototype.apply.bind(unboundSlice);

slice(arguments);
```

slice는 Function.prototype의 apply() 함수에 바인딩된 함수입니다, this 값을 Array.prototype의 slice() 함수로 설정한 채 사용하기 때문에 apply를 생략할 수 있습니다.

### 활용 예시(응용)

아래는 call과 apply를 이용해서 함수 f와 g를 합성하는 compose함수입니다.

```
function compose(f, g){
	return function(){
		return f.call(this, g.apply(this,arguments));
	}
}
```

[자세히보기](https://velog.io/@rohkorea86/this-%EC%99%80-callapplybind-%ED%95%A8%EC%88%98-mfjpvb9yap)

[목차로 돌아가기](#index)


## 순수성, 불변성

순수성 : 
- 오직 인자를 이용해서 결과값이 만들어집니다
- 상태 변이가 자유롭다면 조립과정에 문제가 생깁니다
- 순수 함수를 사용하여 다른 함수로 쉽게 교체가 가능하고 결과값을 예측합니다
- Date.now, console.log, this 일부 전역 변수 등은 자바스크립트에서 비순수성을 야기하는 메서드와 함수입니다.
- 자바 스크립트는 객체 레퍼런스를 전달하므로 객체나 배열을 인자로 받는 함수는 잠재적으로 비순수성을 일으킬 수 있습니다.

```
function generateRandomCharacter() { //비순수
	return rand(26).toString(36);
}

function generateString(charGen, len){ //순수
	return repeatedly(len, charGen).join('');
}

```

불변성(Immutability):

객체가 생성된 이후 그 상태를 변경할 수 없는 디자인 패턴입니다. Immutability은 함수형 프로그래밍의 핵심 원리이다.

객체는 참조(reference) 형태로 전달하고 전달 받습니다. 객체가 참조를 통해 공유되어 있다면 그 상태가 언제든지 변경될 수 있기 때문에 문제가 될 가능성도 커지게 됩니다. 이는 객체의 참조를 가지고 있는 어떤 장소에서 객체를 변경하면 참조를 공유하는 모든 장소에서 그 영향을 받기 때문인데 이것이 의도한 동작이 아니라면 참조를 가지고 있는 다른 장소에 변경 사실을 통지하고 대처하는 추가 대응이 필요합니다.

```
var statement = 'I am an immutable value'; // string은 immutable value

var otherStr = statement.slice(8, 17);

console.log(otherStr);   // 'immutable'
console.log(statement);  // 'I am an immutable value'
```

2행에서 Stirng 객체의 slice() 메소드는 statement 변수에 저장된 문자열을 변경하는 것이 아니라 사실은 새로운 문자열을 생성하여 반환하고 있습니다. 그 이유는 문자열은 변경할 수 없는 immutable value이기 때문입니다.

```
var arr = [];
console.log(arr.length); // 0

var v2 = arr.push(2);    // arr.push()는 메소드 실행 후 arr의 length를 반환
console.log(arr.length); // 1
```

상기 예제에서 v2의 값은 무엇인가? 문자열의 예와 같이 배열이 동작한다면 v2는 새로운 배열(하나의 요소를 가지고 그 값은 2인)을 가지게 될 것입니다. 그러나 객체인 arr은 push 메소드에 의해 update되고 v2에는 배열의 새로운 length 값이 반환됩니다.

[자세히보기](https://poiemaweb.com/js-immutability)

[목차로 돌아가기](#index)

## 흐름기반
체이닝 패턴 :
객체에 연쇄적으로 메서드를 호출할 수 있도록 하는 패턴입니다
```
var Test = function() { //메서드 체이닝을 위한 this호출
    this.x = 0;
    this.y = 0;
    this.z = 0;
};
 
Test.prototype.setX = function(x) {
    this.x = x;
    return this;
};
 
Test.prototype.setY = function(y) {
    this.y = y;
    return this;
};
 
Test.prototype.setZ = function(z) {
    this.z = z;
    return this;
};
 
// 메소드 체이닝 패턴을 이용한 set 호출
var element = new Test();
element.setX(1).setY(2).setZ(3);
 
// Test {x : 1, y : 2, z : 3}
console.log(element);

```

[목차로 돌아가기](#index)

## 언더스코어

UNDERSCORE.JS(이하 언더스코어)는 자바스크립트 유틸리티(여러가지 편의를 도와주는) 라이브러리 입니다. 언더스코어라는 이름이 의미하는 바와 같이 언더스코어는 모든 함수들을 '_' 를 사용합니다. jQuery가 $를 사용하는 것과 같습니다. 자바스크립트에서 함수형 페러다임을 잘 보여줍니다.

```
var list = [1, 2, 3, 4, 5, 6];
_.reject(list, function(num) { return num % 2 == 0; });
// [1, 3, 5]
console.log(list);
// [1, 2, 3, 4, 5, 6]

_.contains([1, 2, 3], 3);
// true

_.isArray([1, 2, 3]);
// true
```

_.reject는 list를 받아 predicate를 실행하여 true이면 제외합니다. 그리고 남아 있는 값들만 담긴 새로운 list를 리턴합니다('새로운'이 중요).

_.contains는 첫 번째 인자인 배열에 두 번째 인자와 동일한 값이 포함되어 있는지를 true/false로 리턴 

_.isArray는 객체의 type이 Array가 맞는지를 검사한다. IE9 미만에서는 Array.isArray가 없어서 _.isArray가 필요합니다.


```
var users = [
  { id: 1, name: "ID", age: 32 },
  { id: 2, name: "HA", age: 25 },
  { id: 3, name: "BJ", age: 32 },
  { id: 4, name: "PJ", age: 28 },
  { id: 5, name: "JE", age: 27 },
  { id: 6, name: "JM", age: 32 },
  { id: 7, name: "HI", age: 24 }
];
_.pluck(users, 'name');
// ["ID", "HA", "BJ", "PJ", "JE", "JM", "HI"]

_.first([5, 4, 3, 2, 1]);
// 5
_.first([5, 4, 3, 2, 1], 1);
// [5]
_.first([5, 4, 3, 2, 1], 2);
// [5, 4]

_.last([5, 4, 3, 2, 1]);
// 1
_.last([5, 4, 3, 2, 1], 1);
// [1]
_.last([5, 4, 3, 2, 1], 2);
// [2, 1]

_.rest([5, 4, 3, 2, 1]);
// [4, 3, 2, 1]
_.rest([5, 4, 3, 2, 1], 2);
// [3, 2, 1]

_.initial([5, 4, 3, 2, 1]);
// [5, 4, 3, 2]
_.initial([5, 4, 3, 2, 1], 2);
// [5, 4, 3]

_.lastIndexOf([1, 2, 3, 1, 2, 3], 2);
// 4
_.lastIndexOf([1, 2, 3, 1, 2, 3], 3);
// 5
_.lastIndexOf([1, 2, 3, 1, 3], 2);
// 1

_.flatten([[1, 2, 3], [4, 5], 6]);
// [1, 2, 3, 4, 5, 6]
```
_.pluck는 users처럼 배열 내부의 값들이 key/value 쌍으로 구성된 객체일 때 사용합니다. 두 번째 인자로 넘긴 key에 해당하는 value를 모아서 리턴합니다. 안쪽에 있는 값들을 짧은 코드로 뽑아 낼 수 있어 유용합니다. 역시 기존의 users의 내용을 바꾸는 것이 아닌 새로운 list를 만들어 값을 담습니다.

_.first(list)는 list[0]와 같고 _.last(list)는 list[list.length-1]와 같습니다. list[0]과 같이 key로 접근하면 되는 일을 굳이 함수로 만들 필요가 있을까 싶을 수 있지만, 사소한 것도 함수로 만들어 두면 조합성이 생기고 실행 시점을 다룰 수 있는 등의 이점이 있습니다. _.first와 _.last의 두 번째 인자는 앞이나 뒤에서부터 몇 개를 남길 것인지에 대한 옵션입니다.

_.rest는 앞쪽의 값을 제외한 새로운 리스트를 리턴합니다. 두 번째 인자는 몇 개의 값을 제외할 것인지에 대한 옵션입니다. _.initial은 _.rest의 반대 방향으로 동작합니다.

_.lastIndexOf는 뒤에서부터 동일한 값을 찾아 index를 리턴한다. 뒤에서부터 세는 것이 아니라 뒤에서부터 찾습니다.

_.flatten은 깊이를 가진 배열을 펴주는 함수입니다.

[자세히보기](https://github.com/indongyoo/functional-javascript/wiki/3.1-Underscore.js-%EC%86%8C%EA%B0%9C)

[목차로 돌아가기](#index)