---
title: "redux persist 이용"
date: "2022-11-02 00:00:00"
categories: [DevLog, StackOverFlow-Clone]
tags: [devlog, redux, persist] # TAG는 반드시 소문자로 이루어져야함!
---

`redux` 상태 관리 라이브러리를 많이 사용하실 것입니다.

리덕스의 store는 페이지를 새로고침 할 경우 state가 날아가는 것을 보실 수 있습니다.

이것에 대한 대응 방안으로 localStorage 또는 session에 저장하고자 하는 reducer state를 저장하여, 새로고침 하여도 저장공간에 있는 데이터를 redux에 불러오는 형식으로 이루어집니다.

위에서 말한 이 작동을 위해 `redux-persist`를 사용합니다.

스토어에 isLogin,tags 들어감

문제1. 로컬 스토리지에 저장되서 브라우저 꺼도 로그인 안풀림

해결. presist 옵션으로 세션스토리지에 저장하고 tags 만 저장되게 바꿈
