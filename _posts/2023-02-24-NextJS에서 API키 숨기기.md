---
title: "NextJS에서 API키 숨기기"
date: "2023-02-20 00:00:00"
categories: [FE, NextJS]
tags: [next] # TAG는 반드시 소문자로 이루어져야함!
---

## 📌 NextJS에서 API키 숨기기

### api 키 보는법

(사진)

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
