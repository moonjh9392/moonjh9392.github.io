---
title: "middleware"
date: "2023-01-10 00:00:00"
categories: [FE, React]
tags: [react, middleware, redux] # TAG는 반드시 소문자로 이루어져야함!
---

## 📌 미들웨어

### 미들웨어란?

상태관리 라이브러리에서 비동기 작업을 다룰 때 손쉽게 상태관리 할 수 있도록 도와줌

미들웨어는, 액션이 디스패치되어서 리듀서에 이를 처리하기전에 사전에 지정된 작업들을 설정한다.

미들웨어를 액션과 리듀서 사이의 중간자라고 이해하면됨.

### 미들웨어 만들기

src/lib/loggerMiddleware.js

```javascript
const loggerMiddleware = store => next => action =>{
  ...
}
```

next : store.dispatch와 비슷한 역할

next(action) 했을때 리듀서로 넘기거나 미들웨어가 더있다면 미들웨어가 처리되도록 진행

```javascript
const loggerMiddleware = (store) => (next) => (action) => {
  // 현재 스토어 상태값 기록
  console.log("현재 상태", store.getState());
  // 액션 기록
  console.log("액션", action);

  // 액션을 다음 미들웨어, 혹은 리듀서로 넘김
  const result = next(action);

  // 액션 처리 후의 스토어 상태 기록
  console.log("다음 상태", store.getState());
  console.log("\n"); // 기록 구분을 위한 비어있는 줄 프린트

  return result; // 여기서 반환하는 값은 store.dispatch(ACTION_TYPE) 했을때의 결과로 설정됩니다
};

export default loggerMiddleware; // 불러와서 사용 할 수 있도록 내보내줍니다.
```

store.js

```javascript
import { createStore, applyMiddleware } from "redux";
import modules from "./modules";
import loggerMiddleware from "./lib/loggerMiddleware";

// 미들웨어가 여러개인경우에는 파라미터로 여러개를 전달해주면 됩니다. 예: applyMiddleware(a,b,c)
// 미들웨어의 순서는 여기서 전달한 파라미터의 순서대로 지정됩니다.
const store = createStore(modules, applyMiddleware(loggerMiddleware));

export default store;
```
