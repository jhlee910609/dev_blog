---
title: 호이스팅(hoisting)
date: 2019-11-03 10:11:13
category: javascript
---

## 1. 함수 스코프와 호이스팅

- es6에서 `let`을 도입하기 전에는 `var`를 써서 변수를 선언했고, 이렇게 선언된 변수들을 함수 스코프라고 불리는 스코프를 가졌습니다.

```javascript
let var1
let var2 = undefined

var1 // undefined
var2 // undefined
undefinedVar // ReferenceError
```

- `var`를 사용할 경우, 변수 선언 전에 사용할 수 있습니다.
- 자바스크립트 매커니즘으로 인해 자바스크립트 함수나 전역 스코프 전체를 살펴보고 `var`로 선언한 변수를 맨 위로 끌어올립니다.
- 선언만 끌어올려지고, 할당은 끌어올려지지 않습니다.

```javascript
x // undefined
var x = 3
x // 3
```

## 2. 함수 호이스팅

- 함수 선언도 스코프 맨 위로 끌어올려집니다. 따라서 함수를 선언하기 전에 호출할 수 있습니다.

```javascript
f() // f
function f() {
  console.log('f')
}
```
