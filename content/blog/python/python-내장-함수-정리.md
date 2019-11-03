---

title: python 내장 함수 정리 - 문자열 메소드
date: 2019-11-01 14:11:63
category: python

---

> 알고리즘을 풀거나, 혹은 실무를 할 때 문자열 다루는 것은 필수입니다.
> 파이썬 내장 함수 중 유용한 문자열 메소드를 정리해봅니다.

### 1. list 복사

- list를 deep copy하여 새로운 list를 반환하는 함수입니다.

```python
origin = [1,2,3,4,5]
newOrigin = origin[:]
newOrigin2 = list(origin)
```

### 2. set 복사

- 자료구조 set을 deep copy하여 새로운 set을 반환합니다.

```python
animal = {'dog', 'cat', 'bird' ,'lion' }
animalSet = animal.copy()
```

### 3. slicing 연산자

- 배열을 원하는 인덱스까지 자르고, 새로운 배열을 반환합니다.
- 사용법은 아래와 같습니다.

```python
origin = [1, 2, 3, 4, 5, 6, 7]

copyOne = origin[:3]
# index (0~2) 슬라이싱

copyTwo = origin[3:]
# index (3~끝까지) 슬라이싱

copyThree = origin[::2]
# index 2n 슬라이싱

print("origin", origin)
# origin [1, 2, 3, 4, 5, 6, 7]

print("one", copyOne)
# one [1, 2, 3]

print("two", copyTwo)
# two [4, 5, 6, 7]

print("three", copyThree)
# three [1, 3, 5, 7]

```
