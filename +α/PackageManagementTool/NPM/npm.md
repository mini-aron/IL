# npm 이란?
npm은 Node packaged manager의 약자다.
이름처럼 Node.js로 만들어진 모듈을 웹에서 받아 설치하고 관리해주는 프로그램이다.
전세계의 개발자들이 만든 다양한 기능(패키지,모듈)등을 npm에서 관리하고있다.

### 사용법 
기본적으로 npm을 사용할려면 package.json 파일이 존재해야한다.
package.json을 생성하기 위해 다음 명령어를 터미널에 입력한다.
```bash
$ npm init
```

package.json의 파일 내부로 가서 구성을 보면 다음과 같다.
```json
{
  "name": "js",
  "version": "1.0.0",
  "description": "",
  "main": "2_13.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}

```
| 옵션 | 설명 |
|---|---|
|  name | 프로젝트 이름  |
|  version | 프로젝트의 버전  |
|  description | 프로젝트에 대한 간단한 설명  |
|  main | 프로그램의 시작점이 되는 모듈의 ID  |
|  scripts | 현재 프로젝트 내부에서 사용할 수 있는 스크립트 명령들  (명령이름:"명령~-> 터미널 $ npm run 명령이름)  |
|  author | 소유주  |
|  license | 다른사용자들이 이 패키지를 사용할 때 필요한 권한  |


