## hoisting
>변수와 함수 선언이 스코프(SCOPE)의 최상단으로 올려져 실행되는 것

### 변수 생성 단계
+ 선언 단계(Declaration Phase): 변수 객체를 실행 컨텍스트에 등록한다. 
+ 초기화 단계(Initialization Phase): 등록된 변수의 메모리를 확보한다. (변수는 ```undefined```로 초기화된다.) 
+ 할당 단계(Assignment Phase): 초기화된 변수에 실제 값을 할당한다.


### 스코프(scope)
> ```javascript```에서 ```scope```는 변수에 접근할 수 있는 범위이다.

#### javascript scope의 특징
+ 블록레벨 스코프
+ 함수레벨 스코프
+ 렉시컬 스코프
+ 동적 스코프

#### 블록레벨 스코프
>코드블록 내에서만 참조(접근) 가능한 범위를 말한다.
```
//c언어 기반
int main(void) {
  if(1) {
    int x = 11;
    print("x = %d\n",x);
  }
  print("x = %d\n",x);  //ERROR
}
```
#### 함수 레벨 스코프
>함수 코드 블록 내에서만 참조(접근) 가능한 범위를 말한다.
```
var x = 0;
{
  var x = 1;
  console.log(x); //1
}
console.log(x);   //1

let y = 0;
{
  let y = 1;
  console.log(y); //1
}
console.log(y);   //0
```
#### 상위스코프
>scope의 또다른 특징으로, 상위스코프를 결정하는 방법을 들 수 있다.
>상위스코프를 결정하는 방법은 2가지가 있다.
+ 동적스코프
   - Dynamic Scope
   - 함수를 어디서 호출 하였는지에 따라 상위 스코프를 결정 
+ 렉시컬 스코프
  - Lexical scope/static scope
  - 함수를 어디서 선언 하였는지에 따라 상위 스코프를 결정
  - javascript 및 대부분의 프로그래밍 언어에서 사용하는 
