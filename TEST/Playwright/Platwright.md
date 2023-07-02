# Playwright

## 지원 브라우저
+ webkit 기반 브라우저
    - 크롬
    - 파이어폭스
    - 사파리
+ 모바일 브라우저

## 테스트 속도 
동시에 수행할 수 있는 테스트는 병렬로 실행한다. 
따라서 테스트(spec 파일)의 갯수가 많아져도 Cypress보다 훨씬 빠르게 진행된다.

## 문법

실행 명령어
```bash
// 1. 모든 테스트 파일 실행
$ npx playwright test

// 2. 단일 테스트 실행
$ npx playwright test tests/todo-page.spec.ts

// 3. 폴더 단위 테스트 실행
$ npx playwright test tests/todo-page/ tests/landing-page/

// 4. 특정 키워드가 파일명에 포함된 테스트 실행
$ npx playwright test my-spec my-spec-2

// 5. 특정 파일의 특정 라인 실행
$ npx playwright test my-spec.ts:42

// 6. 제목과 함께 테스트 실행
// -- 스크립트로 테스트 실행을 자동화해둘 때 제목을 지정해두면 나중에 로그 보기가 더 편할 것 같다. 
$ npx playwright test -g "add a todo item"

// 7. 특정 브라우저에서 테스트 실행
$ npx playwright test --browser=<all/firefox/등 지원 브라우저>
```
테스트 코드 예시
```js
import { test, expect } from '@playwright/test';

const url = '테스트를 수행할 페이지 URL';

test.beforeEach(async ({ page }) => {
  await page.goto(url);
});

test('입력창에 값을 입력한 뒤 엔터를 누르면 할일이 추가된다.', async ({ page }) => {
  await page.click('.header input');
  await page.keyboard.type('todo 1');
  await page.keyboard.press('Enter');
  await page.keyboard.type('todo 2');
  await page.keyboard.press('Enter');

  // https://playwright.dev/docs/locators#locate-by-css-or-xpath
  const list = page.locator('css=.todo-list li');
  await expect(list).toHaveCount(2);
  await expect(list.first()).toHaveText('todo 1');
});

```
playwright에서 제공하는 test라는 메소드의 첫번째 인자로 테스트할 제목을 전달한다. 이때 테스트하는 단위를 기능 명세서의 기능 하나로 생각하면 좋을 것 같다. 
playwright는 async, await로 비동기 동작을 지원해서 javascript 문법에 익숙한 사람들에게는 조금 더 편리한 문법이다. 
test 함수 내에서 실행되어야 하는 동작들을 정의하고 expect 함수로 동작의 결과를 예측하는 방식인가보다. 