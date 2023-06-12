# jest
> `페이스북`에서 만들어서 많은 자바스크립트 개발자로부터 좋은 반응을 얻고있는 테스팅라이브러리
설치만 하면 Test Runner와 Test mathcher 그리고 Test Mock 프레임워크까지 제공하기 때문에 아주좋다.

## install
```npm
>npm i -D jest
```
## jest기본문법
+ test파일 생성
    - test 파일은 `테스트할함수파일명.test.js`로 한다.
```js
describe('계산 테스트', () => {
   const a = 1, b = 2;

   test('a + b는 3이다.', () => {
      expect(a + b).toEqual(3);
   });
});

/*
describe('그룹 테스트 설명 문자열', () => {
   const a = 1, b = 2; // 테스트에 사용할 일회용 가짜 변수 선언

   test('개별 테스트 설명 문자열', () => {
      expect(검증대상).toXxx(기대결과);
   });
});
*/
```
