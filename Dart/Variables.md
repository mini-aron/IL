# Variable

## Type
### Var
보통 함수나 메소드 내부의 지역변수를 선언할때 사용하는 타입이다.  
컴파일러가 타입을 추론한다.
```Dart
var name;
var name = "aron";
var String name = "aron";
```
### Dynamic
여러가지 타입을 가질 수 있는 변수에 사용하는 타입이다.
해당 변수의 타입을 알 수 없을 때 주로 사용한다.
선언할 때 dynamic을 쓰거나 값을 지정하지 않으면 dynamic타입을 가진다.
```Dart
var name; //type: Dynamic
dynamic name;
```

### 명시적 타입
보통 class에서 변수나 property를 선언할 때 타입을 지정하기위해 사용한다.