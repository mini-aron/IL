## util function

- react의 유틸함수는 일반적으로 react에서 자주사용되는 기능을 모듈화해 재사용할 수 있도록 도와주는 함수들이다.
- 프로젝트에서 자주 사용되는 함수들을 모아서 별도의 파일로 관리하는 것이 일반적이다.
- 배열안의 특정 아이템을 찾거나, 문자열에서 특정 문자를 대체하는 등의 기능을 유틸 함수로 구현할 수 있다.

### 장점

- 코드위 중복을 줄인다.
- 유지보수성을 높일 수 있다.
#### ex) 날짜문자열을 특정형식으로 지정하는 유틸함수

```js
function formatData(dateString, format) {
  const date = new Date(dateString);
  return date.toLocaleDateString(format);
}
```

