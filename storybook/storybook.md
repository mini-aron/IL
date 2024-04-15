# storybook이란?

storybook은 컴포넌트 단위의 UI개발 환경을 지원하는 도구다!
storybook을 사용하면 컴포넌트 단위의 UI 개발 진행이 가능하다.
이외에도 컴포넌트 문서화를 할때도 문서화 도구로써 사용이 가능하다.
다양한 웹 프레임 워크를 지원하고있다.

## cra를 이용한 react프로젝트에 적용
웹팩 환경을 구성하지 않고 적용해보자!

```bash
npx create-react-app storybook-app --template typescript
```
자 스토리북을 설치해보자
```bash
npx -p @storybook/cli sb init
```
### 실행
제대로 설치가 되었다면 stories 폴더에 샘플 코드가 생기고
package.json 에 스토리북 실행을 위한 스크립트가 추가된다
```js
"scripts": {
    "storybook": "start-storybook -p 6006 -s public",
    "build-storybook": "build-storybook -s public"
  },
```
```bash
npm run storybook
```
