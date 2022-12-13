---
title: "cloudfront https 통신"
date: "2022-11-05 00:00:00"
categories: [DevLog, StackOverFlow-Clone]
tags: [devlog, aws, cloudfront] # TAG는 반드시 소문자로 이루어져야함!
---

S3 배포후 서버에서 res.setCookie 했는데 브라우저로 쿠키가 안들어옴

원인 쿠키를 sameSite none 으로 사용하려고 했는데 적용하려고 secure 쿠키를 사용해야되서

https 적용시켜야됨

S3 → cloudFront 로 https 적용 하고

서버로 통신했지만 Ec2 서버가 http 라서 통신이 안됨

도메인 구매후 로드밸런서로 서버 https 등록
