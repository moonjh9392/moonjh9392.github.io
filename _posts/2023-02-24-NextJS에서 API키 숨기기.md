---
title: "NextJS에서 API키 숨기기"
date: "2023-02-20 00:00:00"
categories: [FE, NextJS]
tags: [next] # TAG는 반드시 소문자로 이루어져야함!
---

## 📌 NextJS에서 API키 숨기기

### api 키 보는법

![스크린샷 2023-02-24 오후 5 18 03](https://user-images.githubusercontent.com/45509511/221131955-637247b8-1d4d-4151-8520-b5e39f04d9c7.png)


### next의 redirects 와 rewrites 활용

```javascript
//next.config.js
/** @type {import('next').NextConfig} */

const API_KEY = "api_key";

const nextConfig = {
  reactStrictMode: true,
  async redirects() {
    return [
      {
        source: "/old-blog/:path", //변경될 path로 보낼 url
        destination: "/new-blog/:path", //source로 오면 destination으로 보냄
        permanent: false, //브라우저나 검색엔진이 이 정보를 기억하는지 여부
      },
    ];
  },
  async rewrites() {
    return [
      {
        source: "/api/movies", //유저가 보는 url
        destination: `https://api.themoviedb.org/3/movie/popular?api_key=${API_KEY}`, //실제로 보내는 url
      },
    ];
  },
};

module.exports = nextConfig;
```

### rewrites를 이용하여 api_key 숨긴 결과

![스크린샷 2023-02-24 오후 5 37 04](https://user-images.githubusercontent.com/45509511/221131990-6ba29fe5-c2b1-4c06-b1e4-abf0775e3a93.png)

![스크린샷 2023-02-24 오후 5 37 46](https://user-images.githubusercontent.com/45509511/221132029-78c5978c-818c-484f-b6f6-10e08e8fa252.png)

