### useNavigate
> Link같이 페이지를 이동시킬 때 사용된다. 보통 단순이동이 아닌 특정 이벤트가 실행될때 동작하도록 하거나 추가적인 로직이 필요할 때 많이 사용한다.

#### basic

```
navigate("../success",{replace:true});
```
>첫번째 인자는 주소,두번째 인자는{replace,state}사용
+ replace(true or false): true사용시 뒤로가기를 하더라도 방금전 체이지로 돌아오지 않고 메인페이지인```("/")```으로 감. fase는 뒤로가기가 가능하며 기본값임
+ 
```
import { useNavigate } from 'react-router-dom';
function Func() {
  const navigate = useNavigate();
  const onClicking = () => {
    navigate('/원하는 주소');
  };
  
  return (
    <button onClick={onCliking}> button </button>
  );
}

```
```
import { Navigate } from 'react-router-dom';

function Func() {
  const onClicking = () =>{
    return <Navigate to="/1" />
  }
  return(
    <button onClick={onCliking}>go to 1page</button>
  );
}
```
