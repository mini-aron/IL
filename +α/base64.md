# base64
+ 그대로 직역하면 64진법
+ `8비트 이진데이터`를 문자 코드에 영향을 받지 않는 `공통 ASCII 영역의 문자`들로만 이루어진 문자열로 바꾸는 `인코딩 방식`을 가르키는 개념

![image](https://github.com/mini-aron/IL/assets/105274015/3d8fce78-d2af-451c-91bc-4ac9393586ee)
+ base64는 2의 6제곱 (2^6=64) 64로 ASCII문자들로 표시할 수 있는 가장 큰 진법이다.

```
"ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/="
```
+ ASCII문자코드중 제어문자가 상당해 위의 기본적인 문자로 Base64인코딩이 진행된다.
+ "="는 부족한 bit수를 =으로 채워 나타내는 padding문자이다.  
  (인코딩된 문자열이 "~~~=="또는"~~~~="인경우 base64라고 유추해 볼 수 있다.)
## Base64 변환과정
+ 위의 문자64개로 모든 문자열을 표형하려하면 (0~63:총 64개=2^6)6비트가 필요하다.
+ 일반적으로 컴퓨터 데이터에 쓰이는 ASCII문자는 모두8비트로 구성되어 있다.
+ base64인코딩을 위해 `문자열 2진 데이터`를 6비트씩 묶어야 하는데 6과8의 최소공배수 = 24비트씩 끊어서 묶도록 한것이다.
+ 그럼 원래3바이트(3*8=24 bytes)였던 문자열이 6비트 단위4개로 바뀐다.(4*6=24 bytes)(같은수인데 몇개의 바이트를 하나로 묶는지가 다를 뿐이다,)
#### 문자열 "men" 변환과정
![image](https://blog.kakaocdn.net/dn/CpFVj/btrJLR56U4T/9PFunYcChkBjrlCehNPKok/img.jpg)
```
문자열 -> Ascii binary -> 6 bit cut -> base64 encod 
```
+ 만약 글자가 2개이거나 1개일 경우는   "="padding 기호를 사용한다.
#### 문자열 "ma" 변환과정
![image](https://blog.kakaocdn.net/dn/z8EhG/btrJE2z3eR0/a2h9gmQhDvT1NkkjkxhBG0/img.jpg)
#### 문자열 "M" 변환과정
![image](https://blog.kakaocdn.net/dn/d7WHPu/btrJHe74OrG/T8eQXm8lP5EmerMBmd4v31/img.jpg)

### 문제
> 위와같은 변환과정을 거치고나면 base64로 인코딩한 파일의 사이즈가 우너본보다 더 커진다는 것

### 굳이 base64를 사용하는 이유
> ascii는 7bits 인코더인데 나머지 1bit를 처리하는 방식이 시스템 별로 다르고 일부 제어문자의 경우도 시스템별로 다른 코드값을 가진다.  
> 이러한 문제로 직접 시스템간 전달하기에 문제가 생길 수 있어 base64를 사용하게 되었다.  
> 이렇게 되면 문자코드에도 영향받지않고 시스템 간에 전달도 문제없이 가능하기 때문이다.
