---
title: "JS[for of, for in]"
date: "2022-12-08 00:00:00"
categories: [JS, Study]
tags: [JS, javaSciprt] # TAG는 반드시 소문자로 이루어져야함!
---

js 에서 for of 와 for in의 사용법

> for of

배열

```javascript
let a = ["가", "나", "다"];

for (val of a) {
  console.log(val);
}
// 가
// 나
// 다

//배열의 값을 리턴해줌
```

Object

```javascript
let b = { name: "moon", age: 27 };

for (val of b) {
  console.log(val);
}

//TypeError: b is not iterable
//반복할수 없어 에러가 난다
```

> for in

배열

```javascript
let a = ["가", "나", "다"];

for (val in a) {
  console.log(val);
}
// 0
// 1
// 2

//배열의 index를 리턴해줌
```

Object

```javascript
let b = { name: "moon", age: 27 };

for (val in b) {
  console.log(val);
}

//moon
//27
//Object의 값을 순서대로 리턴
```
