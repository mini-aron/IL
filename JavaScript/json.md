## JSON
+ JSON(JavaScript Odject Notation)
+ 사람이 읽을 수 있는 텍스트 기반 데이터 교환 표준
+ XML의 대안으로서 좀 더 쉽게 데이터를 교환하고 저장하기 위하여 고안
+ JSON은 텍스트 기반이므로 어떠한 프로그래밍 언어에서도 읽고 사용 가능

### JSON api
>#### parse
```parse(text: string, reviver?: (this: any, key: string, value: any) => any): any;```
+ ```text```<br>
A valid JSON string.<br>
+ ```reviver```<br>
A function than transforms the results.



>#### stringify
```stringify(value: any, replacer?: (this: any, key: string, value: any) => any, space?:```
 + ```value```<br>
 A JavaScript value to a JavaScript Object Notation (JSON) string.
 + ```replacer```<br>
 A function than transforms the results.
 + ```space```<br>
 Adds indentation, while space, and line break characters to the return-value JSON text to make it easier to read.

