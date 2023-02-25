---
title: "getServerSideProps"
date: "2023-02-25 00:00:00"
categories: [FE, NextJS]
tags: [next] # TAG는 반드시 소문자로 이루어져야함!
---

## 📌 getServerSideProps

### getServerSideProps

데이터가 없을때 loading을 보여줄것인지 loading없이 API가 완료되도록 기다린 후에 모든 정보를 보여줄거인지 선택하게된다

먼저 loading을 보여줄때는

react에서 사용하던것처럼

![스크린샷 2023-02-25 오후 10 40 48](https://user-images.githubusercontent.com/45509511/221361071-46f0d955-b961-451f-992e-9a541ad97726.png)

사용하고

loading없이 API가 완료되도록 기다린 후에 모든 정보를 보여줄때에는

getServerSideProps를 이용하여

![스크린샷 2023-02-25 오후 10 58 08](https://user-images.githubusercontent.com/45509511/221361081-4517075b-4b90-47ff-a345-43eefc93e97f.png)

보여주면된다. 주의할점 getServerSideProps에서 fetch를 사용할때는 http://localhost가 붙는다는 점

loading을 보여주는게 나은것 같지만 getServerSideProps를 쓸일이 있을것 같아 보인다.

getServerSideProps가 작동하는 흐름은

![스크린샷 2023-02-25 오후 10 59 47](https://user-images.githubusercontent.com/45509511/221361089-c869fd30-1a1c-4777-865b-46f961539716.png)

\_app.tsx > props로 component에서 Home으로 이동 > getServerSideProps작동 > \_app.tsx pageProps로 들어가서 Home에 props로 작동
