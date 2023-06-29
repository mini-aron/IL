# replace()
어떤 패턴에 일치하는 부분을 새로운 문자열로 반환한다.  
첫번째 파라미터에 문자열을 넣으면 첫번째 일치하는 문자열만 교체되고, 정규식을 넣게되면 모든 일치하는 문자열이 교체된다.
### 문법
```js
var newStr = str.replace(regexp|substr, newSubstr|function)
```
#### 매개변수
+ regexp : 정규식
+ substr : newSubStr로 대체 될 String. 첫 번째 일치되는 문자열만이 교체
+ newSubstr : 첫번째 파라미터를 대신할 문자열
+ function : 주어진 regexp 또는 substr에 일치하는 요소를 대체하는 데 사용될 새 하위 문자열을 생성하기 위해 호출되는 함수.