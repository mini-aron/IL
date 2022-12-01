## IntersectionOdserver
> IntersectionOdserver는 기본적으로 브라우저 뷰포트(viewport)와 설정한 요소(Element)의 교차점을 관찰하며, 요소가 뷰포트에 포함되는지, 더 쉽게는 사용자 화면에 지금 보이는 요소인지 아닌지를 구별하는 기능을 제공함

>이 기능은 기동적으로 실행되기 때문에, scroll 같은 이벤트 기반의 요소 관찰에서 발생하는 렌더링 성능이나 이벤트 연속 호출같은 문제 없이 사용할 수 있습니다.



### IntersectionOdserver
>  ```new IntersectionObserver()``` 를 통해 생성한 인스턴스 (``` io ```)로 관찰자(Observer)를 초기화 하고 관찰할 대상(Element)을 지정합니다. 생성자는 2개의 인수(```callback```,``` options```)를 가집니다.

```
const io = new IntersectionObserver(callback, options)

io.observe(element)
```

### callback

>관찰할 대상(Target)이 등록되거나 가시성(Visibility, 보이는지 보이지 않는지)에 변화가 생기면 관찰자는 콜백(Callback)을 실행합니다 콜백은 2개의 인수(``` entries```, ```observer ```)를 가집니다.

```
const io = new IntersectionObserver((entries, observer) => {}, options)
io.observe(element)
```



