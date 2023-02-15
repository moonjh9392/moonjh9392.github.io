---
title: "react-query"
date: "2023-02-15 00:00:00"
categories: [FE, REACT]
tags: [react, query] # TAG는 반드시 소문자로 이루어져야함!
---

## 📌 react-query

react-query는 서버의 값을 클라이언트에 가져오거나, 캐싱, 값 업데이트, 에러핸들링 등 비동기 과정을 더욱 편하게 하는데 사용됩니다.

### 사용 이유

서버로 부터 값을 가져오거나 업데이트 하는 로직을 store 내부에 개발하는 경우가 많습니다. 그렇다보니 store는 클라이언트 state를 유지해야하는데 어느 순간부터 store에 클라이언트 데이터와 서버 데이터가 공존 하게 됩니다.

그래서 react-query를 사용함으로 서버, 클라이언트 데이터를 분리합니다.

### react-query 장점

- 캐싱
- get을 한 데이터에 대해 update를 하면 자동으로 get을 다시 수행한다. (예를 들면 게시판의 글을 가져왔을 때 게시판의 글을 생성하면 게시판 글을 get하는 api를 자동으로 실행 )
- 데이터가 오래 되었다고 판단되면 다시 get (invalidateQueries)
- 동일 데이터 여러번 요청하면 한번만 요청한다. (옵션에 따라 중복 호출 허용 시간 조절 가능)
- 무한 스크롤 (Infinite Queries (opens new window))
- 비동기 과정을 선언적으로 관리할 수 있다.
- react hook과 사용하는 구조가 비슷하다.
