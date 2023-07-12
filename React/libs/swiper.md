# swiper.js
오픈소스 JavaScript라이브러리로, 간단한 HTML,CSS,JS로  
반응형 슬라이드소 및 스와이퍼 기능을 쉽게 구현할 수 있게 도와준다.

## 특징
+ 모바일 및 데스크탑에서 모두 호환
+ 반응형 웹사이트에 최적화
+ 터치 스와이프 이벤트를 기반으로한 슬라이드쇼 및 스와이퍼 기능을 지원
+ CSS3 기반으로 애니메이션을 지원
+ 다양한 옵션을 제공하여 사용자가 자유롭게 슬라이드쇼 및 스와이퍼를 커스터마이징 가능

## 사용법
### 설치
#### 1) CDN을 이용한 방법
```html
<!-- CSS -->
<link rel="stylesheet" href="https://unpkg.com/swiper/swiper-bundle.min.css" />

<!-- JS -->
<script src="https://unpkg.com/swiper/swiper-bundle.min.js"></script>
```
#### 2) 로컬 설치
swiper.js의 소스코드를 다운로드 후, 경로지정으로 로드
```html
<!-- CSS -->
<link rel="stylesheet" href="path/to/swiper-bundle.min.css" />

<!-- JS -->
<script src="path/to/swiper-bundle.min.js"></script>
```
#### 3) npm이용 
```
npm install swiper
```

### 옵션 설정
1. direction  
  슬라이드의 방향을 설정 
  + horizontal:수평방향
  + vertical: 수직방향
  ```js
   const mySwiper = new Swiper('.swiper-container', {
  direction: 'horizontal'
  });
  ```
2. loop  
  슬라이드 루프 설정 여부를 결정  
  + true: 무한루프(기본)
  + false: 루프없음
3. autoplay  
  자동 재생 여부를 설정
  + false: 자동 재생 끔(기본)
  + true: 자동 재생 켬
  + delay: 자동 재생 딜레이 시간 (ms)
4. speed  
  슬라이드 애니메이션 속도를 성정(ms)  
  + 기본값 300  
5. slidesPerView  
  한번에 보여지는 슬라이드 수를 설정  
  + 1: 한개씩 보이기(기본)
  + 2: 두개씩 보이기
  + 3: 세개씩 보이기
  + auto: 슬라이드의 넓이나 높이에 따라 자동으로 계산  
6. pagination  
  페이징 설정 여부를 결정  
  + false: 페이징 끔(기본)
  + true: 페이징 켬
  + type: 페이징 종류(bullets, fraction, progressbar, custom)  

7. navigation  
  이전/다음버튼 설정 여부  
  + false: 버튼 끔(기본)
  + true: 버튼 켬
  + nextEI: 다음 버튼 선택자
  + prevEI: 이전 버튼 선택자  
8. scrollbar  
  스크롤바 설정 여부를 결정  
  + false: 스크롤바 끔(기본)
  + true: 스크롤바 켬
  + hide: 스크롤바 숨김  
9. effect  
  슬라이드 애니메이션 효과 설정  
  + slide: 기본 슬라이드 효과(기본)
  + fade: 페이드 효과
  + cube: 큐브 효과
  + flip: 플립 효과

  ## 장점
  + 사용 방법이 간편
  + 다양한 옵션과 효과 제공
  + 반응형 웹 디자인 지원 (모바일 환경 이용가능)
  + 마크업 코드와 스타일 코드를 분리작성가능(유지보수 용이)
  + 유연한 커마가능
