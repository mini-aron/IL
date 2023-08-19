# Blob

Binary Large Object의 약자로 바이너리 데이터의 집합을 의미한다.

이름에서 알 수 있듯이 Blob은 용량이 큰 데이터를 의미한다.  

주로 이미지, 오디오 같은 미디어 객체를 저장하는 데 사용된다.

## Blob 생성

```jsx
const newBlob = new Blob(array, options);
```

- #### array  
 [ArrayBuffer](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer), [ArrayBufferView](https://developer.mozilla.org/en-US/docs/Web/API/ArrayBufferView), Blob([File](https://developer.mozilla.org/ko/docs/Web/API/File)), [DOMString](https://developer.mozilla.org/ko/docs/Web/API/DOMString) 객체 또는 이런 객체가 혼합된 Array를 사용할 수 있다.

```jsx
new Blob([new ArrayBuffer(data)], { type: 'video/mp4' });
new Blob(new Uint8Array(data), { type: 'image/png' });  
new Blob(['<div>Hello Blob!</div>'], {
  type: 'text/html',
  endings: 'native'
});
```

- #### options  
+ `type`: 데이터의 MINE 타입을 설정하며, 기본값은 `""`이다
+ `endings`: `\n`을 포함하는 문자열 처리를 `"transparent"`(사용중인 OS에 맞춰 줄바꿈 문자를 사용)와`"native"`(사용하던 줄바꿈 문자를 그대로 사용)로 지정할 수 있으며, 기본값은 `"transparent"`이다.

