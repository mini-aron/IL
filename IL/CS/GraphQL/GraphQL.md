# GraphQL
+ Graph + Query Language
+ facebook에서 만든 어플리케이션 레이어 쿼리 언어
## SQL과 GQL
+ GQL은 SQL(Structed Query Language)과 마찬가지로 쿼리 언어다.
### SQL과의 차이
#### 차이점
+ GraphQL은 보통 하나의 엔드포인트를 가진다.
+ GraphQL은 요청할 때 사용하는 쿼리에 따라 다른 응답을 받을 수 있다.
+ GraphQL은 원하는 데이터(response)만 받을 수 있다.
#### 목적
+ SQL :데이터베이스 시스템에 저장된 데이터를 효율적으로 가져오는 것
+ GQL : 웹 클라이언트가 데이터를 서버로부터 효율적으로 가져오는 것
> SQL의 문장(statement)은 주로 백앤드 시스템에서 작성하고 호출하는 반면, GQL의 문장은 주로 클라이언트 시스템에서 작성하고 호출한다.
## GraphQL 장단점
### 장점
#### 1. HTTP 요청 횟수를 줄일 수 있다.
  - restful의 경우 필요한 리소스 별로 요청 해야하고, 필요한 데이터들이 부분적으로 나눠서 개발되어있다면 그만큼 요청 횟수가 늘어난다. 하지만 GraphQL은 원하는 정보를 하나의 쿼리에 모두담아 요청할 수 있다.(over-fetching을 줄일수있음)
#### 2. HTTP응답 사이즈를 줄일 수 있다.
  - restful의 경우 응답의 형태가 정해져있기 때문에 필요한 정보만 부분적으로 요청하는 것이 힘들고, 자연스럽게 데이터 사이즈가 클 수밖에 없다. GraphQL을 사용함으로써 응답데이터 사이즈를 최소화하여 모바일 환경 부담을 줄일 수 있다.
#### 3. 프론트엔드와 백엔드 개발자의 부담을 덜 수 있다.
  - GraphQL은 request/response의존도가 많이 없기 때문에, 개발자들의 API개발 부담을 덜 수 있다.
### 단점
#### 1. 고정된 요청과 응답이 필요할 때에는 query로 인해 요청의 크기가 커질 수 있다.
#### 2. 캐싱이 REST보다 복잡하다.
#### 3. 파일 업로드 구현방법이 정해져있지 않아 직접 구현해야한다.

### ex)
### Operation
```
{
  allFilms {
    totalCount
    films {
      title
    }
  }
}
```
### Response
```
{
  "data": {
    "allFilms": {
      "totalCount": 6,
      "films": [
        {
          "title": "A New Hope"
        },
        {
          "title": "The Empire Strikes Back"
        },
        {
          "title": "Return of the Jedi"
        },
        {
          "title": "The Phantom Menace"
        },
        {
          "title": "Attack of the Clones"
        },
        {
          "title": "Revenge of the Sith"
        }
      ]
    }
  }
}
```
### 용어
+ over-fetching :필요이상의 data를 받는것
