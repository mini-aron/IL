# flux패턴
MVC의 복잡성의 해결방안으로 나온 단방향 데이터 흐름으로 애플리케이션을 만드는 아키텍쳐다.
![image](https://github.com/mini-aron/IL/assets/105274015/5895f572-0daf-40ea-bba8-0791aee7d43e)

## flux 패턴의 작동

> 사용자 입력을 기반으로 action생성  
> action을 dispatcher에 전달하여 store의 데이터를 변경  
> store의 변경점을 view에 반영

![image](https://github.com/mini-aron/IL/assets/105274015/b3654ecb-e9ce-4d8a-aca2-9755107be440)

## 각 요소들

### Action
데이터를 변경하는 행위로 dispatcher에 전달되는 객체를 이야기한다.  
action creator 메서드는 새로 발생한 action의 타입  (type)과 새로운 데이터(payload)를 묶어 Dispatcher에게 전달한다.
```
{
  type: 'SET_PROFILE',
  data: {
    'name': 'Harry',
    'age': 458
  }
}
```
### Dispatcher
dispatcher는 모든 데이터의 흐름을 관리하는 중앙 허브다.   
dispatcher에는 store들이 등록해놓은 각각의 action 타입마다 콜백 함수들이 존재한다.  
action을 감지하게 되면 store들이 각 타입에 맞는 store의 콜백함수를 실행한다.  
store의 데이터를 조작하는건 오직 dispatcher를 통해서만 가능하다.

### store
mvc의 model과 같은 역할로 상태 저장소의 역할로써 상태와 상태를 변경할 수 있는 메서드를 가지고있다.  
어떤 타입의 action이 발생했는지에 따라 맞는 콜백함수를 dispatcher에 등록한다.  
dispatcher를 통해 상태가 변경되게되면 view에게 데이터가 변경되었음을 알린다.

### View
view는 사용자에게 보여지는 ui적 요소로 store에서 상태가 변경되었음을 알려주면 최상위 view는 하위view로 전차 데이터를 내려보낸다.  
새로운 데이터를 받은 view는 화면을 업데이트 시킨다.  
또한 사용자가 view를 통해 조작을 하게되면 그에 해당하는 action을 생성한다.

