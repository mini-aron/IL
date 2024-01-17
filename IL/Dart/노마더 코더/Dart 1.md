
## main function
main함수는 모든 Dart 프로그램의 Entry point이다.
main함수에서 쓴코드가 호출된다.(main이 없으면 실행안됨)
dart는 자동 세미콜론이 없어 직접 붙여야 한다.(일부러 안쓸때가 있음)

```dart
void main(){
	print("hello world");
}
```

## 변수
```dart
void main(){
	var name = "pizza"; 
	String name = "chicken";
	name = "chicken";
}
```

### 정의 타입
#### var
+ 동적 타입으로 자동으로 타입을 추론한다.
+  함수나 메소드 내부에 지역변수를 선언할 때 사용한다.
+ Class에서 변수나 property를 사용할 때는 타입을 명시적으로 지정한다.
#### Dynamic
+ 여러 타입을 가질 수 있는 타입이다.
+ 변수를 선언할 때 아무런 값을 지정하지 않거나 타입을 선언하지 않으면 자동으로 dynamic 타입으로 바뀐다.

#### Var 와 Dynamic의 차이
var는 한번 추론된 타입대로 유지되지만, dynamic타입은 처음 선언된 타입이 아닌 다른타입의 값을 넣어도 오류가 나지 않는다.

#### Final
변수를 정의한 이후 수정이 불가능하다.
```dart
void main(){
	final name = "pizza";
	name = "ham"; // 수정불가
}
```

#### late 변수
+ 초기 데이터 없이 변수를 먼저 생성후 추후에 데이터를 넣을때 사용
+ class 내의 인스턴스 변수가 final이면 만들면서 바로 할당해야하지만 late final이면 만들고 난 후 할당해도 된다.
+ Nullable 타입이 아닌 타입들은 null이 될 수 없는데 late를 통해 사용하기전에 할당한다고 알려줄 수 있다. (null-safety)

#### const
+ const는 컴파일 시 알고 있는 값을 사용해야한다.
+ 만약 어떤 값인지 모르고 api에게 오거나 사용자에게 입력받는 값이라면 final이나 var를 사용해야한다.
```dart
void main() {  
const name = "tom"; // 컴파일 시점에 바뀌지 않는 값  
final username=fetchAPI(); // 컴파일 시점에 바뀌는 값  
}  
```

#### 원시타입
```dart
void main() {  
	String name = "tom";  
	bool isPlay = true;  
	int age = 10;  
	double money = 52.55;  
	num x = 12;  
	num y = 1.2;  
}  
```
### Null Safety
개발자가 null을 참조할 수 없게 하는 기능

```dart
void main(){
	String? name = "hello";
	name = null;
}
```
위 코드에선 String뒤에 ?를 붙임으로서 String,null이 될 수 있다고 명시해준 것이다.
기본적으로 모든 변수는 null이 될 수 없다.(non-nullable)

#### List
+ dart의 list는  `collection if`와 `collection for`를 지원한다.
+ 이를 통해 존재가능성이 있는 요소를 가져올수있다.
```dart  
void main(){  
	var giveMeSix = true;  
	int case1 = [  
		1,  
		2,  
		3,  
		4,  
		5,  
		if(giveMeSix) 6,  
	];  
	// 아래와 같은 기능이다.  
	if(giveMeSix){  
		case1.add(6);  
	}  
}  
```

##### Collection For
```dart
void main() {  
	var oldFriends = ["nico", "lynn"];  
	var newFriends = [  
		"tom",  
		"jon",  
		for (var friend in oldFriends) "❤️ $friend"  
	];  
  
	print(newFriends); // [tom, jon, ❤️ nico, ❤️ lynn]  
}  
```
### String Interpolation
> 변수 사용법

+ $달러 기호를 붙이고 사용할 변수를 적어주면 된다.  
+ 만약 무언가를 계산하고 싶다면 ${ } 형태로 적어주면 된다.
```dart
void main(){  
	var name = "tom";  
	var age = 10;  
	var greeting = "hello $name, I'm ${age + 5}";  
}  
```

#### Maps
key와 value를 연결하는 객체, 
```  dart
var gifts = {  
// Key: Value  
	'first': 'partridge',  
	'second': 'turtledoves',  
	'fifth': 'golden rings'  
};  
  
// Map 생성자를 사용하여 동일한 객체를 만들 수 있다.  
var gifts2 = Map();  
	gifts2['first'] = 'partridge';  
	gifts2['second'] = 'turtledoves';  
	gifts2['fifth'] = 'golden rings';  
```

#### Sets
Set에 속한 모든 아이템들이 유니크해야될 때 사용한다.  
유니크할 필요가 없다면 List를 사용하면 된다.
```  dart
var halogens = {'fluorine', 'chlorine', 'bromine', 'iodine', 'astatine'};  
```
