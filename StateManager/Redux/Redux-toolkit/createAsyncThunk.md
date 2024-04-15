# createAsyncThunk
Redux 액션은 일반적으로 동기적인 작업을 수행한다. 하지만 비동기 작업인 API 요청, 데이터 가져오기, 파일 업로드 등을 처리해야 하는 경우 Redux Toolkit은 createAsyncThunk를 사용하여 비동기 작업을 처리하는 액션을 손쉽게 생성할 수 있도록 도와준다.

## 속성
```ts
createAsyncThunk(typePrefix: string, payloadCreator: AsyncThunkPayloadCreator,
options?: AsyncThunkOptions): AsyncThunk
```

## 매개변수
1. typePrefix : 액션 타입 생성
2. payloadCreator : promise 기반으로 결과를 반환하는 action을 작성