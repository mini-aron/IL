# Chakra UI 란?
컴포넌트 스타일을 아주그냥 야무지게 만들어주는 라이브러리다.
모달 인풋등 아주 많은 컴포넌트와 훅들을 지원하기 때문에 혹시 퍼블리싱이 귀찮다면 써보자!

## 사용법
### 설치
```bash
npm i @chakra-ui/react @emotion/react @emotion/styled framer-motion
yarn add @chakra-ui/react @emotion/react @emotion/styled framer-motion
pnpm add @chakra-ui/react @emotion/react @emotion/styled framer-motion
```
### 루트 설정
```js
import * as React from 'react'

// 1. import `ChakraProvider` component
import { ChakraProvider } from '@chakra-ui/react'

function App() {
  // 2. Wrap ChakraProvider at the root of your app
  return (
    <ChakraProvider>
      <TheRestOfYourApplication />
    </ChakraProvider>
  )
}
```

```js
import { ChakraBaseProvider, extendBaseTheme } from '@chakra-ui/react'
// `@chakra-ui/theme` is a part of the base install with `@chakra-ui/react`
import chakraTheme from '@chakra-ui/theme'

const { Button } = chakraTheme.components

const theme = extendBaseTheme({
  components: {
    Button,
  },
})

function App() {
  return (
    <ChakraBaseProvider theme={theme}>
      <Component {...pageProps} />
    </ChakraBaseProvider>
  )
}
```