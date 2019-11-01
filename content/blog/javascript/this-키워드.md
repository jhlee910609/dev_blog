---
title: this 키워드와 call, bind, apply 함수
date: 2019-10-29 13:10:57
category: javascript
---

# this 키워드와 call, bind, apply 함수

> call, bind, apply에 대한 설명 전에 함수 바디에 사용할 수 있는 `this` 키워드에 대해 알아봅니다. 객체지향 언어를 사용해보신 분이라면 익숙한 용어일 것이며, 이해 또한 쉬우시리라 생각합니다. 이 부분을 이해하셔야 call, bind, apply에 대한 이해를 하실 수 있습니다.

## 1. 객체지향 언어에서의 `this`

- 객체지향 언어에서의 `this`는 해당 메소드가 속한 인스턴스를 지칭합니다. 설명을 위한 예제코드는 아래와 같습니다.

```javascript
// javascript도 es6부터 class 개념이 도입되었습니다.
class Person {

  constructor(name, age){
    this._name = name;
    this._age = age;
  }

  function introduce(){
    // 현재 Person 인스턴스에 할당된 필드 값들(_name, _age)이 출력됩니다.
    console.log(`name: ${this._name}, age: ${this._age}`);
  }
}

```

## 2. call, apply, bind 함수

> class가 아닌 함수에서만 사용하게 될 때, 해당 함수의 this를 지정할 수 있습니다. 이를 위해 apply, call, bind와 같은 함수를 통해 this를 해당 함수에 전달해줘야 합니다. 각각의 방법과 그 차이를 함께 알아봅시다.

### 2.1. call

- `call` 함수는 기존 함수에 this를 바인딩 시켜줍니다.
- 따라서 바인딩된 `this`의 프로퍼티에 접근 가능합니다.

```javascript
const john = { name: 'john', age: 17 }
const mary = { name: 'mary' }

function sayHello() {
  console.log(`${this.name}, ${this.age}`)
}
sayHello()
// undefined, undefined
sayHello.call(john)
// john, 17
sayHello.call(mary)
// mary, undefined
```

### 2.2. apply

- `apply`는 `call`과 동작은 같습니다. 다만 매개변수를 처리하는 방법이 약간 다릅니다.
- `apply`는 매개변수를 각각의 파라미터로 받았지만, `call`은 배열로 받습니다.

```javascript
function update(name, age) {
  this.name = name
  this.age = age
}

const john = { name: 'john', age: 17 }
update.apply(john, ['JOHN', 20])
console.log(john)
// { name: 'JOHN', age: 20 }
```

### 2.3. bind

- `bind`는 `call`, `apply`과 동작 방식이 매우 다릅니다.
- `bind` 함수를 사용할 경우, 해당 함수의 `this`는 영구적으로 바뀌게 됩니다.

```javascript
function updateName(name) {
  this.name = name
}

const john = { name: 'john' }
const mary = { name: 'mary' }

const updateJohn = updateName.bind(john, 'JOHN')
updateJohn()
console.log(john)
// { name: 'JOHN' }
updateJohn.call(mary, 'MARY')
console.log(john)
// { name: 'JOHN' }
console.log(mary)
// 이미 updateName 함수가 가르키는 this는 john입니다.
// 따라서 mary의 name은 call 함수를 사용하더라도 바뀌지 않습니다.
// { name: 'mary' }
```
