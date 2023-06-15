# immer

> react에서 쉽게 불변성을 유지할 수 있는 코드 작성을 도와주는 라이브러리다.

## 불변성

> 기존의 값을 직접 수정하지 않으면서 새로운 값을 만들어 내는 것이다.

- 리엑트 컴포넌트에서 상태를 업데이트 할 때 불변성을 지키는 것은 매우 중요하다.
- 불변성이 지켜지지 않으면 객체 내부의 값이 새로워져도 바뀐 것을 감지하지 못한다.

```js
const object = {
  id: 1,
  name: " pumpkin",
};

//Bad case
const nextObjBad = object;
nextObjBad.name = "carrot";
console.log(
  `nextObjBad.name : ${nextObjGood.name} / object.name ${object.name}`
);
//Good Case
const nextObjGood = { ...object, name: "apple" };
console.log(`nextObjGood : ${nextObjGood.name} / object.name ${object.name}`);
```

```
//실행결과
nextObjBad.name : carrot / object.name : carrot
nextObjGood.name : apple / object.name : carrot
```

- 전개 연산자 (...\*)를 사용하여 객체나 배열 내부의 값을 복사할 때는 얕은 복사를 하게 된다.  
  즉, 내부의 값이 완전히 새로 복사되는 것이 아니라 가장 바깥쪽에 있는 값만 복사된다.  
  따라서 내부 값이 배열이거나 객체일 땐 내부의 값도 따로 복사해 줘야한다.

```js
const members = [
    {
        id :1,
        name:'pumpkin',
        age:25
    },
    {
        id :2,
        name:'carrot',
        age:23
    },
    {
        id :3,
        name:'apple',
        age:30
    }
]

const nextMembers = [...members]

//얕은 복사
nextMembers[0].name ='mango'
console.log(`nextMembers[0].name : ${nextMembers[0].name} / members[0].name : ${members[0].name}`)

//깊은 복사
nextMembers[0] ={
    ...nextMembers[0],
    name:"melon"
}
console.log(`nextMembers[0].name : ${nextMembers[0].name} / members[0].name : ${members[0].name}`
```

```
//실행결과
nextMembers[0].name : mango / menbers[0].name : mango
nextMembers[0].name : melon / menbers[0].name : mango
```

## immer 설치 및 사용법

### 설치

```
$ yarn add immer
```

- 이름과 아이디를 받아 멤버의 리스트를 보여주는 컴포넌트

```js
import { useCallback, useState, useRef } from "react";
import produce from "immer";

const MemberList = () => {
 ...
  const onChange = useCallback(
    (e) => {
      const { name, value } = e.target;
      setForm(
        produce(form, (draft) => {
          draft[name] = value;
        })
      );
    },
    [form]
  );

  const onSubmit = useCallback(
    (e) => {
      e.preventDefault();
      const info = {
        id: nextId.current,
        name: form.name,
        username: form.username,
      };
      setData(
        produce(data, (draft) => {
          draft.array.push(info);
        })
      );

      setForm({
        name: "",
        username: "",
      });
      nextId.current += 1;
    },
    [data, form.name, form.username]
  );

  const onRemove = useCallback(
    (id) => {
      setData(
        produce(data, (draft) => {
          draft.array.splice(
            draft.array.findIndex((info) => info.id === id),
            1
          );
          //draft.array.filter(info => info.id!==id)
        })
      );
    },
    [data]
  );
  return (
    ...
  );
};

export default MemberList;
```
### produce 함수
#### 파라미터
+ 첫번째: 수정하고싶은 상태
+ 두번째: 상태를 어떻게 수정할지 정의하는 함수

> 두번째 파라미터로 전달되는 함수 내부에서 원하는 값을 변경하면  
produce 함수가 불변성 유지를 대신 해주며 새로운 상태를 생성해준다.