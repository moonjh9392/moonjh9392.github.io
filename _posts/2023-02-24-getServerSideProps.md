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

사용하고

loading없이 API가 완료되도록 기다린 후에 모든 정보를 보여줄때에는

getServerSideProps를 이용하여

보여주면된다. loading을 보여주는게 나은것 같지만 getServerSideProps를 쓸일이 있을것 같아 보인다.

getServerSideProps가 작동하는 흐름은

\_app.tsx > props로 component에서 Home으로 이동 > getServerSideProps작동 > \_app.tsx pageProps로 들어가서 Home에 props로 작동
