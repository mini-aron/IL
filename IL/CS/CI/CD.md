# CI/CD (Continuous Integration/Continuous Delivery)
애플리케이션 개발 단계를 자동화하여 애플리케이션을 더욱 짧은 주기로 제공하는 방법이다.  
CI/CD의 기본개념은 지속적인 통합, 지속적인 서비스 제공, 지속적인 배포이다.  
## CI
+ 빌드/테스트 자동화 과정
+ CI/CD의 "CI"는 개발자를 위한 자동화 프로세스인 지속적인 통합(Continuius integration)을 의미한다.  
### 지속적인 통합
 애플리케이션 코드의 새로운 변경사항이 정기적으로 빌드 및 테스트를 거쳐 공유레포지토리에 병합된다.
동시협업 애플리케이션 개발중 충동문제를 해결 할 수 있다.
### CD
+ 배포 자동화 과정
+ CD는 지속적인 서비스 제공(Continuous Delivery)와 지속적인 배포(Continuius Deployment)를 의미한다.
### 지속적인 서비스 제공
개발자들이 애플리케이션에 적용한 변경사항이 리포지토리에 자동으로 업로드 되는것을 뜻하며 , 운영팀은이 레포에서 애플리케이션을 실시간 프로덕션 환경으로 배포할 수 있다.  

### 지속적인 배포
+ 빌드, 테스트 및 배포 단계를 자동화하는 DevOps 방식을 논리적 극한까지 끌어 올린다. 코드 변경이 파이프라인의 이전 단계를 모두 성공적으로 통과하면 수동 개입 없이 해당 변경 사항이 프로덕션에 자동으로 배포된다. 
+ 단한 코드 변경이 정기적으로 마스터에 커밋되고, 자동화된 빌드 및 테스트 프로세스를 거치며 다양한 사전 프로덕션 환경으로 승격되며, 문제가 발견되지 않으면 최종적으로 배포된다.

CI/CD 종류
+ Jenkins
+ CircleCI
+ TravisCI
+ Github Actions
+ etc