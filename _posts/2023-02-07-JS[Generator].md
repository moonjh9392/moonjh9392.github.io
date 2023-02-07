---
title: "JS[Generator]"
date: "2023-02-07 00:00:00"
categories: [FE, JS]
tags: [generator] # TAG는 반드시 소문자로 이루어져야함!
---

## 📌 Generator

ES6에서 도입된 제너레이터(Generator) 함수는 이터러블을 생성하는 함수이다. 제너레이터 함수를 사용하면 이터레이션 프로토콜을

준수해 이터러블을 생성하는 방식보다 간편하게 이터러블을 구현할 수 있다. 또한 제너레이터 함수는 비동기 처리에 유용하게 사용된다.

제너레이터 함수는 일반 함수와는 다른 독특한 동작을 한다. 제너레이터 함수는 일반 함수와 같이 함수의 코드 블록을 한 번에

실행하지 않고 함수 코드 블록의 실행을 일시 중지했다가 필요한 시점에 재시작할 수 있는 특수한 함수이다.

일반 함수를 호출하면 return 문으로 반환값을 리턴하지만 제너레이터 함수를 호출하면 제너레이터를 반환한다.

```javascript
function* generateSequence() {
  yield 1;
  yield 2;
  return 3;
}

// '제너레이터 함수'는 '제너레이터 객체'를 생성합니다.
let generator = generateSequence();
alert(generator); // [object Generator]
```

next() 로 제네레이터 실행 가능

```javascript
let one = generator.next();

alert(JSON.stringify(one)); // {value: 1, done: false}

let two = generator.next();

alert(JSON.stringify(two)); // {value: 2, done: false}

let three = generator.next();

alert(JSON.stringify(three)); // {value: 3, done: true}
```

제너레이터는 이터러블(iterable)이면서 동시에 이터레이터(iterator)인 객체이다.

iterator 메소드를 소유한 이터러블이다. 그리고 제너레이터는 next 메소드를 소유하며 next 메소드를 호출하면 value, done

프로퍼티를 갖는 이터레이터 객체를 반환하는 이터레이터이다.

for 로도 실행됨

```javascript
function* generateSequence() {
  yield 1;
  yield 2;
  return 3;
}

let generator = generateSequence();

for (let value of generator) {
  alert(value); // 1, 2가 출력됨
}
```

주의할 점은 위 예시를 실행하면 1과 2만 출력되고 3은 출력되지 않음

이유는 for..of 이터레이션이 done: true일 때 마지막 value를 무시하기 때문이다.

제너레이터는 이터러블 객체이므로 제너레이터에도 전개 문법(...) 같은 관련 기능을 사용할 수 있다.

```javascript
function* generateSequence() {
  yield 1;
  yield 2;
  yield 3;
}

let sequence = [0, ...generateSequence()];

alert(sequence); // 0, 1, 2, 3
```
