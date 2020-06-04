---
title: state 초기화는 어디에서 해야하는가?
date: 2020-06-05 00:06:57
category: react
---

## State 초기화는 반드시 constructor 안에서 해야하는가?

> state 초기화를 어디에서 해야하는가?에 대한 의문이 있었다. 자세히 파야하는 이슈는 아니지만 코드 별로 state 초기화를 하는 위치가 달라서 도대체 그 이유가 무엇인지를 정리해보았다.

### 1. constructor 안에서의 초기화

```typescript
class SampleComponent extends React.Component<any, any> {
  constructor(props){
    super(props);
    this.state = {
      isOpen: false,
      // ....
    }
  }
}
```

- 정석적인 방법으로써 React component의 constructor 안에서 초기화 해준다.



### 2. constructor 밖에서의 state 초기화 (component 프로퍼티로 초기화)

```typescript
class SampleComponent extends React.Component<any, any> {
   state = {
      isOpen: false,
      // ....
    }
 // ...
}
```

- `CRA(create-react-app)`를 사용하지 않고, `webpack`을 직접 구성했다면 추가적인 환경설정이 필요하다. 필요한 추가 설정은 아래와 같다.
- npm module install

```shell
  npm install --save-dev babel-plugin-transform-class-properties
```

- babel.config.js 추가 설정

```json
presets: [
  "@babel/preset-env",
  "@babel/preset-react"
],

// plugins 추가
plugins: [
  "transform-class-properties"
]
```

- 위 가지 설정을 적용했을때, 트랜스파일링 시 state 초기화 코드를 굳이 생성자 안에서 선언하지 않아도 동일한 결과를 얻을 수 있다.