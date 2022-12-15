---
title: "JS[Scope, Closure]"
date: "2022-12-08 00:00:00"
categories: [FE, JS]
tags: [JS, javaSciprt] # TAG는 반드시 소문자로 이루어져야함!
---

> Scope

변수의 유효범위

- let,const

```javascript
let username = "moon";
if (username) {
  let message = `hello ${username}`;
  const message2 = `hello ${username}`;
  console.log(message);
}
console.log(message); //ReferenceError: message is not defined
console.log(message2); //ReferenceError: message2 is not defined
```

let,const는 블록 내에서만 사용가능

- var

```javascript
let username = "moon";
if (username) {
  var message = `hello ${username}`;
  console.log(message);
}
console.log(message); //hello moon
```

var는 블록 스코프를 무시
(모든 블록 스코프를 무시하는건 아님, 화살표 함수의 블록 스코프는 무시하지 않는다.)

블록 단위로 스코프를 구분했을 때, 훨씬 예측 가능한 코드를 작성할 수 있으므로 _**let**_,_**const**_ 키워드 사용이 권장됨

|           |               let               |             const              |     var     |
| --------- | :-----------------------------: | :----------------------------: | :---------: |
| 유효범위  | 블록 스코프 및<br/> 함수 스코프 | 블록 스코프 및<br/>함수 스코프 | 함수 스코프 |
| 값 재할당 |              가능               |             불가능             |    가능     |
| 재선언    |             불가능              |             불가능             |    가능     |

> Closure

외부 함수의 변수에 접근할 수 있는 내부 함수

```javascript
const adder = (x) => (y) => x + y;
/*const adder = function (x) {
	return function(y){
    	return x+y
    }
}*/
adder(5)(7); // 12

typeof adder(5); // function

adder(5); // y => x + y
```

클로저는 리턴하는 함수에 의해 스코프가 구분된다.
클로저의 핵심은 스코프를 이용해, 변수의 접근 범위를 닫는데 있다.

클로저는 `정보의 접근 제한(캡슐화)`에 유용하게 사용된다
