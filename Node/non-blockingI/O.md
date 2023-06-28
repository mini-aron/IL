# Non - blockingI/O
> 이전작업이 완료될 때까지 대기하지 않고 다음 작업을 수행하는 것을 말한다.

blocking
```
_______
작업1  
       ________
         작업2
               _______
                작업3
____________________>>
             시간 
```
non blocking
```
_______
 작업1
   ________
     작업2
         _______
          작업3
____________________>>
             시간 
```
 위의 예시를 보면 블록킹보다 논 블록킹이 같은 작업을 더 짧은 시간에 처리 할 수 있는 것을 볼 수 있다.  
 보통 노드는 I/O작업을 백그라운드로 넘겨 동시에 처리하곤 한다, 동시에 처리할 수 있는 작업이 늘어날수록 시간을 더욱 절약할 수 있다.
 ### ex)
 #### blocking
 ```js

 function longRunningTask() {
    //오랜 시간이 걸리는 작업
    console.log('작업끝');
 }

 console.log('시작');
 longTunningTask();
 console.log('다음작업');
 ```
 result
 ```
 시작
 작업끝
 다음작업
 ```

 #### non - blocking
  ```js

 function longRunningTask() {
    //오랜 시간이 걸리는 작업
    console.log('작업끝');
 }

 console.log('시작');
 setTimeout( longTunningTask, 0);
 console.log('다음작업');
 ```
 result
 ```
 시작 
 다음작업
 작업끝
 ```