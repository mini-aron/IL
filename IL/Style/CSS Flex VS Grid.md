## Flex and Grid
-----
### Flex
+ 1차원적인 부분만 고려한 레이아웃, 수평과 수직영역중 하나의 방향으로만 레이아웃을 나눌 수 있음

### Grid
+ 2차원적인 부분도 고려한 레이아웃, 수평 수직을 동시에 영역을 나눌 수 있음


![ex_screenshot](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fzy5q9%2Fbtq1aRImW4g%2FvwwzIFiaGBt5jgwXOssg2K%2Fimg.jpg)

### Flex 특징 및 사용방법

#### 방향을 설정하는 방법
__flex-direction__
+ row ➡️
+ row-reverse ⬅️
+ column ⬇️
+ column-reverse ⬆️

#### __정렬하는 방법__
+ 가로방향 justify-contect
+ 세로방향 align-items

#### 정렬 종류
+ flex-start(가로기본값) <br>
가로든 세로든 시작하는 부분부터 방향으로 정렬.가로방향 __왼쪽정렬__, 세로방향 __위쪽정렬__ <br>
+ flex-end <br>
가로든 세로든 마무리 부분에 끝쪽에 정렬. 가로방향 __오른쪽 정렬__, 세로방향 __아래쪽 정렬__ <br>
+ center <br>
 __중앙정렬__ 가온데로부터 양옆으로 간격이 없도록 설정. 따로 마진을 주면 띄울수 있음<br> <br>


__가로방향에서만 사용 가능한 속성__ <br><br>
+ space-beteen
+ space-around
+ space-evenly <br><br>
![ex_screenshot](https://velog.velcdn.com/images/ikkim01/post/66052e45-90da-4d71-b5a4-5283549ee3a3/image.png)
