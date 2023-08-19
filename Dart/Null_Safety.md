## Null Safety
개발자가 null 값을 참조할 수 없도록 하는 것이다.
기본적으로 모든 변수는 non-nullable(null이 될 수 없음)이다.
```dart
bool isEmpty(String string) => string.length == 0;

main(){
    isEmpty(null);
}
```
위 코드를 실행시키면 `NoSuchMethodError`를 실행한다.
이런 오류를 뱉어내는 이유는 String을 보내야 하는 곳에 null을 보냈기 때문이다.
또한 null에는 length라는 속성이 없기 때문이기도 하다.

이런 에러같은경우 컴파일러에서 잡을 수 있는 에러가 아니다.
이런 상황이 발생하지 않도록 null을 삭제하기에는 null이라는 값은 유용하다.  

이런 경우에는 dart에서는 변수가 null이 될 수 있음을 명확히 표시해야한다.

```dart
void main(){
    String name = "aron";
    name = null;
}
```
위 코드는 에러가 발생한다. name이 null값을 참조할 수 있다고 명시하지 않았기 때문이다.


```dart
void main(){
    String? name = "aron";
    name = null;
}
```
하지만 위 코드는 에러가 나지 않는다.
바로 type뒤에 ?를 붙여줌으로서 name이 tpe 또는 null이 될 수 있다고 명시해준 것이다.
만약 `?`를 붙인 변수는 이 변수가 null인지 아닌지 확인해야 한다.
```dart
void main(){
    String? name = "aron";
    if(name != null){
        nico.isNotEmpty;
    }
}
```