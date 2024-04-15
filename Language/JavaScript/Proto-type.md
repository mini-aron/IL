# proto type
> javaScript는 클래스라는 개념이 없다.  
> 기존의 객체를 복사해 새로운 객체를 생성하는 프로토타입 기반의 언어이다.  
> 프로토타입 기반 언어는 객체원형인 프로토타입을 이용해 새로운 객체를 만들어낸다.  
> 이렇게 생긴 객체도 또다른 객체의 원형이 될 수 있다.  
> 프로토타입은 객체를 확장하고 객체지향적 프로그래밍을 할 수 있게 해준다.  
 
 
 ## 함수와 객체의 내부 구조
 JavaScript에서는 함수를 정의하고 파싱단계에 들어가면 내부적으로 수행되는 작업이 있다.  
 함수 멤버로 prototype 속성이 있다. 이속성은 다른곳에 생성된 함수이름의 프로토타입 객체를 참조한다.  
 프로토타입 객체의 멤버인 constructor 속성은 함수를 참조하는 내부구조를 가진다.
 ### ex)1
 ![image](https://github.com/mini-aron/IL/assets/105274015/f4f67ccd-15cf-4c47-8fd3-2ceba52e797a)
```js
function Person(){}
```
person이라는 함수가 정의되고, 파싱단계에 들어가면 person함수 Prototype이라는 속성은 프로토타입 객체를 참조한다.  
프로토타입 객체멤버인 constructor 속성은 Person 함수를 참조하는 구조를 지닌다.  
Proto type속성이 참조하는 프로토타입 객체는 new라는 연산자와 Person 함수를 통해 생성된 모든 객체의 원형이 되는 객체이다.
### ex)2
 ![image](https://github.com/mini-aron/IL/assets/105274015/75efaf93-e28e-40c5-9fc2-5d7efeda79aa)

```js
function Person(){ }

var joon = new Person();
var jisoo = new Person();
```
