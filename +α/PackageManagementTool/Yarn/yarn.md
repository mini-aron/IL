# yarn 이란?
yarn은 javascript 패키지 매니저다.
프로젝트 패키지 의좀성을 관리하는 툴이며, 다른 개발자들과 패키지를 공유할 수 있도록 도와준다. 
yarn은 npm과 마찬가지로 패키지의 저장소를 제공하며 시스템에서 의존 패키지를 설치, 업데이트 할 수 있도록 도와준다.  
`package.json`파일을 통해 해당 프로젝트가 의존하고있는 모든 패키지를 구분하고, `package.json`에 있는 `dependencies`필드를 기반으로 패키지를 설치한다.
이덕에 실제 패키지가 있는 node_modules 폴더 대신 package.json파일만 공유해 낭비를 줄일 수 있다.

## yarn과 npm의 성능차이
npm의 보안 및 성능문제를 겪고,이를 대체하기 위해 태어난 새로운 패키지 매니저가 바로 yarn이다.
yarn은 npm에 비해 성능과 보안이 향상되었다!

npm은 패키지를 순서대로 설치하는 것에 비해 yarn은 패키지를 병렬로 설치하기 때문에 설치속도가 빠르다.
특히 yarn은 캐싱을 이용하기 때문에 패키지 설치가 더 빠르다.
yarn은 설치한 패키지를 유저 디렉토리에 저장하여 캐싱한다.
```bash
$ yarn cached dir
/Library/Caches/Yarn/v6
```
첫번째 설치에는 npm과 비슷한 성능을 보이지만 두번째 install부턴 npm보다 훨씬 빠르다!
|명령어|첫번째 설치|두번째 설치|
|---|---|---|
|npm install|24.3s|5.4s|
|yarn install|22.9s|976ms|

표 출처:[Yarn 톺아보기](https://www.holaxprogramming.com/2017/12/21/node-yarn-tutorials/)  
또한, npm은 다른 패키지를 즉시 포함시킬 수 있는 코드를 자동으로 실행하므로, 보안 시스템에 여러 가지 취약성이 발생한다.  
반면에, YARN은 yarn.lock 또는 package.json 파일에 있는 패키지만 설치하므로 보안이 더 강화되었다고 볼 수 있다.

하지만 아직까진npm이 다운로드수가 훨씬많고 커뮤니티 규모도 훨씬 크기 때문에 정보를 찾는것은 npm이 더 편하다.