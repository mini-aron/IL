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

### List
dark에서 lists를 선언하는 것은 두 가지 방법이 있다.
```dart
int case1 = [1,2,3,4,5];
List case2 = [1,2,3,4,5];
```
### collection if
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
    print(case1); // output: [1, 2, 3, 4, 5, 6]
    // 아래와 같은 기능이다.
    if(giveMeSix){
    case1.add(6);
    }
}
```
### collection for
```dart
void main() {
var oldFriends = ["minsu", "jun"];
var newFriends = [
"tom",
"jon",
for (var friend in oldFriends) "❤️ $friend"
];

print(newFriends); // [tom, jon, ❤️ minsu, ❤️ jun]
}
```

## Maps

일반적으로 맵은 key와 value를 연결하는 객체입니다. 키와 값 모두 모든 유형의 객체가 될 수 있다.
각 키는 한 번만 발생하지만 동일한 값을 여러 번 사용할 수 있다.
```dart
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
## Sets
Set에 속한 모든 아이템들이 유니크해야될 때 사용한다.
유니크할 필요가 없다면 List를 사용하면 된다.

```dart
var numbers1 = {1, 2, 3};
Set numbers2 = {1, 2, 3};
numbers1.add(1);
print(numbers1); //output: {1, 2, 3};
```
list는 대괄호를 쓰며 set은 중괄호를 쓴다는 것과 set의 요소들은 유니크하다는 것이다. list는 같은 요소가 여러개 반복될 수 있지만, set은 중복이 허용되지 않는다.
## Type
아래 타입을 포함한 거의 대부분의 타입들이 객체로 이루어져 있다. (함수도 객체)
이것이 Dart가 진정한 객체 지향 언어로 불리는 이유이다.
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

## String Interpolation
텍스트 안에 변수를 삽입하는 방법이다.
+ 단순 삽입은 따옴표 내부에 $변수명
+ 변수를 계산하여 삽입하는 법은 ${계산식}
+ `$` 그대로 표시는 escape문자 `\$`

```dart
void main() {
    var name = 'aron';
    var age = 10;
    var greeting = 'Hello my name is $name I\'m ${age+2} nice to meet you';
}
```
