## Reflow
Reflow는 렌더링 엔진에서 요소를 배치하는 과정을 의미한다.
렌더트리 구축 단계에서 DOM트리와 CSSOM트리를 합쳐 render트리를 만들고 reflow를 통해 각각의 요소를 레이아웃을 위치시킨다.

여기서 render 트리는 DOM요소를 기반으로 만들었지만 똑같지는 않다.
DOM은 구조를 나타낸다면 render 트리는 시각적 구조를 나타낸다. 
예를 들어 스타일에 display: none;가 있다면 DOM에는 존재하지만 render 트리에는 할당되지 않는다.

relow가 발생하는 경우는 다음과 같다. 
+ DOM 노드의 추가, 제거
+ DOM 노드의 위치 변경
+ DOM 노드의 크기 변경(margin, padding, border, width, height 등)
+ CSS3 애니메이션과 트랜지션
+ 폰트변경, 텍스트 내용
+ offset, scrollTop같이 계산된 스타일 요청
+ 페이지 초기 렌더링
+ 윈도우 리사이징

## Repaint 
Repaint는 render 트리가 탐색되고 paint 메서드가 호출된 후 UI기반의 구성요소를 사용해 그리는 과정이다.
repaint가 이뤄지기 위해선 render 트리가 있어야하고 Reflow작업 이후 repaint작업이 이뤄진다.
결과적으로 화면의 구조가 변경될 때는 reflow와 repaint가 모두 방생한다.

하지만 레이아웃에 영향을 주지 않는 엘리먼트 개열의 변화같은 경우는 repaint만 발생한다.
(color, background-color, visibility같은 속성등)
