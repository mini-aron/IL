
## JS의 dataType
javascript의 데이터 타입은 7가지가 있다
+ undefined
+ null
+ boolean
+ String
+ Symbol
+ Numeric(Number 과 BigInt)
+ Object
## 정적 타입과 동적타입
타입을 결정하는 시점에 따라 타입을 정적타입과 동적타입으로 분류할 수 있다.

+ #### 정적타입
> 정적 타입은 모든 변수의 타입이 컴파일타임에 결정된다. 
> 코드수준에서 개발자가 타입을 명시해주어야하는 C, Java, Typescript 가 여기에 속한다.
+ #### 동적타입
> 동적 타입은 변수타입이 런타임에서 결정된다.
> 프로그램이 실행될 때 타입에러가 발견되기 때문에 코드작성시 에러 없이 작성이 가능하다.


### TypeOf
값으로 사용된 typeOf는 자바스크립트 런타임의 typeof가 된다.
```typescript
const v1 = typeof person; // 값은 'object' const
v2 = typeof email //값은 'function'
```

타입에서 사용된 typeof는 값을 읽고 ts type을 반환한다.
```typescript
type T1 = typeof person; //타입은 Person
type T2 = typeof email; //타입은 (options: { person: Person; subject: string; body: string; });
```