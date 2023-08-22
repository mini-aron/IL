# Chakra UI 란?



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