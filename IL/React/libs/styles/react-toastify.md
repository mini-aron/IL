# react-toastify
> react 프로젝트에서 예쁜알람을 만들 수 있도록 해주는 Node.js 패키지

### install toastify
```
npm istall react-toastify
```
## react-toastify 사용법
```js
import  { toast, ToastContainer } from "react-toastify";

export default function App () {
  //알람
 const notify = () => toast("Toastify Alert!");
 
 return(
  <div>
   <button onClick={notify}/>
   <ToastContainer/>
  </div>
 );
}
```
