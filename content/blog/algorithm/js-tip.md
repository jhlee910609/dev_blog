---
title: js tip
date: 2019-10-18 18:10:05
category: algorithm
---

> 정적 타입 언어와 다르게 형 변환 또한, 특이점이 찾아왔다.
> 그래서 한번 정리해보기로 하였다.

1. `parseInt`

```javascript
// 동적 타입 언어를 활용하여, 연산을 통해 형 변환
const strToNumber_one = str / 1
const strToNumber_two = str * 1

// 아래와 같은 방식의 형 변환은 java에서도 자주 사용.
const numToStr = num + ''
```

2. `sort(a,b)`

- 알고리즘 문제풀 때, sorting을 위해 항상 사용되는 array 기본 함수이다.
- MDN 문서에 따르면 sort 사용법은 다음과 같다.
  - `compareFunction(a, b)`이 0보다 작은 경우 a를 b보다 낮은 색인으로 정렬합니다. 즉, a가 먼저옵니다.
  - `compareFunction(a, b)`이 0을 반환하면 a와 b를 서로에 대해 변경하지 않고 모든 다른 요소에 대해 정렬합니다. 참고 : ECMAscript 표준은 이러한 동작을 보장하지 않으므로 모든 브라우저(예 : Mozilla 버전은 적어도 2003 년 이후 버전 임)가 이를 존중하지는 않습니다.
  - `compareFunction(a, b)`이 0보다 큰 경우, b를 a보다 낮은 인덱스로 소트합니다.
  - `compareFunction(a, b)`은 요소 a와 b의 특정 쌍이 두 개의 인수로 주어질 때 항상 동일한 값을 반환해야합니다. 일치하지 않는 결과가 반환되면 정렬 순서는 정의되지 않습니다.

```javascript
function compare(a, b) {
  if (a is less than b by some ordering criterion) {
    return -1;
  }
  if (a is greater than b by the ordering criterion) {
    return 1;
  }
  // a must be equal to b
  return 0;
}

```

3. `localeCompare`

- char 크기 (index) 비교

4. 소수 구하기

- [참고 링크](https://jongmin92.github.io/2017/11/05/Algorithm/Concept/prime/)
