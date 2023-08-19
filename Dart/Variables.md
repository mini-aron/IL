# Variable

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
### Final
var대신 final로 변수를 만들게 되면 이 변수는 수정할 수 없게 된다. 
(딱 한 번만 할당될 수 있음)
자바스크립트의 const랑 비슷하다.
```dart
final name = "aron";
name = "lee"; //수정불가

final String name = "aron";
name = "lee"; //수정불가
```

### late
일반 final 변수는 선언과 동시에 초기화를 해야하지만, late final 변수는 초기화를 나중에 할 수 있도록 해준다.
여기서 주목할 점은 late final 변수는 선언과 초기화를 분리할 수 있다는 점이다. 즉, 선언과 초기화를 다른 시점에 할 수 있기 때문에 이를 지연 초기화라고 한다.
```dart
late final String API;
API = "12121212";
```
### Const 
dart에서의 const는 javascript에서의 const와는 많이 다르다.
dart에서 const는 compile-time constant를 만들어준다.
dart에서 coconst는 컴파일할 때 알고 있는 값을 사용해야 한다.
만약 어떤 값인지 모르고, 그 값이 API로부터 오거나 사용자가 화면에서 입력해야 하는 값이라면 그건 const가 아닌 final이나 var가 되어야 한다.
```dart

void main() {
    const name = "aron"; // 컴파일 시점에 바뀌지 않는 값
    final username=fetchAPI(); // 컴파일 시점에 바뀌는 값
}

```

### 명시적 타입
보통 class에서 변수나 property를 선언할 때 타입을 지정하기위해 사용한다.