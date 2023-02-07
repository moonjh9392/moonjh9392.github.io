---
title: "JS[iterable, iterator]"
date: "2023-02-07 00:00:00"
categories: [FE, JS]
tags: [iterable, iterator] # TAG는 반드시 소문자로 이루어져야함!
---

## 📌 iterable, iterator

이터러블을 [for...of], [전개 연산자], [비구조화] ..등, 이터러블이나 이터레이터 프로토콜을 따르는 연산자들과 함께 동작하도록 하는 약속된 규약을 의미한다.

이터러블은 이터러블 규약을 따르는 객체

### ✏️ iterable

이터레이터를 리턴하는 [Symbol.iterator]() 메서드를 가진 객체

배열의 경우 Array.prototype 의 Symbol.iterator 를 상속받기 때문에 이터러블임

### ✏️ iterator

{value : 값 , done : true/false} 형태의 이터레이터 객체를 리턴하는 next() 메서드를 가진 객체.

next 메서드로 순환 할 수 있는 객체다. [Symbol.iterator]() 안에 정의 되어있다.

next() 는

```javascript
function* gen() {
  yield 1;
  yield 2;
  yield 3;
}

//{ value : 값 , done : 값이 없으면 true}

const g = gen(); // "Generator { }"
g.next(); // "Object { value: 1, done: false }"
g.next(); // "Object { value: 2, done: false }"
g.next(); // "Object { value: 3, done: false }"
g.next(); // "Object { value: undefined, done: true }"
```

형태로 이루어짐

iterable => [Symbol.iterator]() => iterator가 => next()로 순환가능

한마디로 iterable은 반복가능한 객체이고 iterator는 그안의 반복을 수행하는 메서드라고 생각하면 될거같다.
