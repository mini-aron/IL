# MVVM
> Model View, View, Model의 약자로, 비지니스 로직과 프레젠테이션 로직을 분리하는 패턴
**Model의 데이터를 가공하는 ViewModel과, 그 ViewModel을 보여주는 View로 이루어진 패턴**

## MVVM 동작방식
![image](https://github.com/mini-aron/IL/assets/105274015/19d6de55-ac45-42c5-9086-16094cf164f4)

> 1. 사용자의 액션이 view를 통해 들어온다.
> 2. view에 액션이 들어오면 ViewModel에게 전달한다.
> 3. ViewModel은 model에게 데이터를 요청한다.
> 4. Model은 ViewModel에게 요청받은 데이터를 응답한다.
> 5. ViewModel은 응답받은 데이터를 가공해 저장한다.
> 6. View는 Data Binding을 이용해 UI를 갱신한다.


## Model
다루게 될 데이터

## View
시각적 요소. 전형적으로 UIView의 서브 클래스들을 의미

## ViewModel
Model이 가지고 있는 정보를 View에 보여지는 값으로 변경
