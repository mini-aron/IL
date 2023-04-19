## Redux(리덕스)
> javascript 상태관리 라이브러리

### Redux의 기본개념:3가지 원칙
1. Single source of truth
> 애플리케이션의 모든 상태는 하나의 저장소 안에 하나의 객체트리 구조로 저장된다.
2. State is read-only
> 상태는 불변하며, 오직 Action만이 상태교체를 요청할 수 있다.
3. Changes are made with pure functions
> 변화는 순수함수 (Reducer)로 작성되어야 한다.
