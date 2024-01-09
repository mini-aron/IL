### Function
Dart는 객체 지향 언어이므로 함수도 객체이며 타입이 Function이다.
```dart
String function sayHello(String name){
	return "Hello ${name} nice to meet you."
}

void main(){
	print(sayHello("name"))
}
```

#### Optional Positional Parameters
Dart에서 []은  optional, positional parameter를 명시할 때 사용된다.
```dart
String sayHello(String name, int age, [String? country = ""]) {  
return 'Hello ${name}, You are ${age} from the ${country}';  
}  
  
void main() {  
var result = sayHello("sugar", 10);  
print(result);  
}  
```
위 예제에서 name, age는 필수값이고 []를 통해 country를 optional값으로 지정해주고있다.

#### QQ Operator
+ ??연산자를 이용해 왼쪽 값이 null인지 체크해서 null이 아니면 왼쪽 값을 리턴하고 null이면 오른쪽 값을 return한다.
+ ??=연산자를 이용해 변수 안의 값이 null일 때 값을 할당해줄 수 있다.
```dart
void main() {  
String? name;  
name ??= "sugar";  
name = null;  
name ??= "js";  
print(name); // js  
}
```

### Typedef
자료형에 사용자가 원하는 alias를 붙일 수 있게 해준다. (자료형 이름의 별명을 만들 때 사용)
```dart
// 전  
List reverseListOfNumbers(List list) {  
var reversed = list.reversed;  
return reversed.toList();  
}

// 후  
typedef ListOfInts = List;  
  
ListOfInts reverseListOfNumbers(ListOfInts list) {  
var reversed = list.reversed;  
return reversed.toList();  
}
```

### class 
dart에서 property를 선언할 때는 타입을 사용해서 정의한다.  
```dart  
class Player {  
final String name = 'jisoung';  
final int age = 17;  
void sayName(){  
// class method안에서는 this를 쓰지 않는 것을 권장한다.  
print("Hi my name is $name")  
}  
}  
  
void main(){  
// new를 꼭 붙이지 않아도 된다.  
var player =Player();  
}  
```
#### constructor
dart에서 생성자(constructor) 함수는 클래스 이름과 같아야 한다.  
  
```dart  
class Player {  
// 이럴 때 late를 사용한다.  
late final String name;  
late final int age;  
// 클래스 이름과 같아야한다!  
Player(String name){  
this.name = name;  
}  
}

void main(){  
// Player 클래스의 인스턴스 생성!  
var player = Player("jisoung", 1500);  
```  
  
위의 생성자 함수는 다음과 같이 줄일 수 있다.  
```dart  
// 생략  
Player(this.name, this.age);  
```  
첫 번째 인자는 this.name으로 두 번째 인자는 this.age로 갈 것이다.

### Named Constructor Parameters


```dart  
class Team {  
final String name;  
int age;  
String description;  
  
Team(this.name, this.age, this.description);  
}  
  
void main(){  
// 헉 너무 많은 인자를 받아야 해서 햇갈린다.  
// 거기다 각 인자의 의미를 알 수가 없다.  
var myTeam = Team("jisoung", 17, "Happy coding is end coding");  
```
이 문제를 해결할려면 너무 간단하다.  
첫 번째는 중괄호({})를 이용하는 것이다.  
  
```dart  
class Team {  
final String name;  
int age;  
String description;  
  
Team({this.name, this.age, this.description});  
}  
  
void main(){  
// 한 눈에 볼 수 있다.  
var player = Player(  
name: "jisoung",  
age: 17,  
description: "Happy coding is end coding"  
}  
}  
```  
두 번째는 name parameter를 사용하는 것이다.  
```dart  
// 생략  
Player(name:"jisoung", age: 17, description: "Happy coding is end coding");  
```  
하지만 여기에는 큰 문제가 있다.  
변수가 null일 수도 있기 때문에 우리는 이걸 required를 이용하거나 기본 값을 줘서 처리해 줘야한다. 우리는 required를 사용할 것이다.  
  
```dart  
// 생략  
Team({  
required this.name,  
required this.age,  
required this.description,  
});,  
```  
훨씬 좋아졌다.

### Named Constructors
만약 생성자(constructor) 함수를 여러개 만들고 싶다면 어떨까
생성자.이름 을 이용해 이름 생성자를 만든다!

```dart  
// 첫 번째 case  
class Player {  
late final String name;  
Player({  
required this.name  
});  
}  
  
void main(){  
var player = Player(  
name: "jisoung",  
);  
}  
```  
```dart  
// 두 번째 case  
Player({this.name, this.age, this.description});  
```  
```dart  
// 세 번째 case  
class Player {  
final String name;  
Player.createUser({  
required this.name  
}): this.name = name;  
}  
  
void main(){  
var player = Player.createUser(  
name: "jisoung",  
);  
}  
```
### Cascade Notation
cascade poerator
```dart
class Player {
  String name;
  int xp;
  String team;
  
  Player({required this.name, required this.xp, required this.team});
  
  void sayHello(){
    print("Hi my name is $name");
  }
}

void main(){
  var nico = Player(name: "nico", xp: 1200, team: "red")
    ..name = "las"
    ..team = 'blue'
    ..xp = 1200000
    ..sayHello();
} 
```
..으로 상위에 있는 클래스를 가르켜 값을 변경하거나 함수를 호출 할 수 있다.

### Enum
 ```dart
 enum Team { red, blue }

class Player {
  String name;
  int xp;
  Team team;
  
  Player({required this.name, required this.xp, required this.team});
  
  void sayHello(){
    print("Hi my name is $name");
  }
}

void main(){
  var nico = Player(name: "nico", xp: 1200, team: Team.red)
    ..name = "las"
    ..team = Team.blue
    ..xp = 1200000;
} 
```

