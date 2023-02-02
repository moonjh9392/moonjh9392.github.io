---
title: "Footer 하단고정"
date: "2023-02-01 00:00:00"
categories: [FE, React]
tags: [redux] # TAG는 반드시 소문자로 이루어져야함!
---

## 📌 redux-thunk

### ✏️ redux-thunk

redux-thunk는 리덕스에서 비동기 작업을 처리 할 때 가장 많이 사용하는 미들웨어입니다. 이 미들웨어를 사용하면 액션 객체가 아닌 함수를 디스패치 할 수 있습니다. redux-thunk는 리덕스의 창시자인 Dan Abramov가 만들었으며, 리덕스 공식 매뉴얼에서도 비동기 작업을 처리하기 위하여 미들웨어를 사용하는 예시를 보여줍니다.

thunk의 예시

```javascript
const getComments = () => (dispatch, getState) => {
  // 이 안에서는 액션을 dispatch 할 수도 있고
  // getState를 사용하여 현재 상태도 조회 할 수 있습니다.
  const id = getState().post.activeId;

  // 요청이 시작했음을 알리는 액션
  dispatch({ type: "GET_COMMENTS" });

  // 댓글을 조회하는 프로미스를 반환하는 getComments 가 있다고 가정해봅시다.
  api
    .getComments(id) // 요청을 하고
    .then((comments) =>
      dispatch({ type: "GET_COMMENTS_SUCCESS", id, comments })
    ) // 성공시
    .catch((e) => dispatch({ type: "GET_COMMENTS_ERROR", error: e })); // 실패시
};
```
