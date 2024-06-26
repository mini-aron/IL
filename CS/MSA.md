# MSA
> `MicroService Architecture`의 줄일말로 MSA에 대한 정확한 정의는 없지만 MicroService는 작고 독립적으로 배포가 가능한  
> 각각의 기능을 수행하는 서비스로 구성된 프레임워크

# Monolithic Architecture의 형태
> `Monolithic Architecture`는 소프트웨어의 모든 구성요소가 한 프로젝트에 통합되어 있는 형태이다.  
> 웹 개발에서는 웹 프로그램을 개발하기 위해 모듈별로 개발을 하고,  
> 개발이 완료된 웹 애플리케이션을 하나의 결과물로 패키징하여 배포되는 형태를 말한다.  
> 이런 어플리케이션을 모놀리식 어플리케이션이라 하며 주로 소규모 프로젝트에서 사용된다.

## 단점
1. 부분 장애가 전체 서비스의 장애로 확대될 수 있다
2. 서비스의 변경이 어렵고 수정 시 장애의 영향 파악이 힘들다
3. 한 Framework와 언어에 종속적이다.

# MSA 특징
> MSA는 API를 통해서만 상호작용할 수 있다. 마이크로 서비스는 서비스의 접근점을 API 형태로 외부에 노출하고  
> 실질적인 세부 사항은 모두 추상화한다. 내부의 구현로직과 아키텍처와 프로그래밍 언어, 데이터베이스, 품질 유지체계와 같은  
기술적인 사항들은 서비스 API에 의해 철저하게 가려진다.

## 장점
1. 각각 개별의 서비스 개발을 빠르게하고 유지보수가 쉽다.
2. 팀단위로 적절한 수준에서 기술 스택을 다르게 할 수 있다.
3. 서비스별로 독립적인 배포가 가능하다.

## 단점
### 1. 모놀리식에 비해서 상대적으로 복잡하다.
서비스가 모두 분산되어 있어서 내부 시스템의 통신을 어떻게 가져가야할 지 정해야하고 통신의 장애와 서버의 부하가  
있을 경우에 어떻게 `transaction`을 유지할 지 결정하고 구현해야한다.

### 2. 트랜잭션을 유지하기 어렵다
모놀리식은 단일 `transaction`을 유지했지만 MSA는 DB를 갖고있는 서비스도 각기 다르고 서비스의 연결을 위해서는  
통신이 포함되기 때문에 `transaction`을 유지하기가 어렵다.
