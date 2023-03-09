---
title: "Catch all URL"
date: "2023-03-09 00:00:00"
categories: [FE, NextJS]
tags: [next] # TAG는 반드시 소문자로 이루어져야함!
---

## 📌 Catch all URL

어떤 URL이던 catch 해내는 url 항상은 아니지만 필요한 순간이 있음

예를 들어 영화 제목을 url에 넣어 SEO에 좋음

파일명을 [...id].js 처럼 앞에 ... 을 붙여준다.

![스크린샷 2023-03-09 오후 7 55 31](https://user-images.githubusercontent.com/45509511/224004772-72df44bc-aa48-4ca3-a460-d4c2946c3cd4.png)

```javascript
const router = useRouter();

const onClick = (id: string, title: string) => {
  router.push(`/movies/${title}/${id}`);
};
```

/movies/${title}/${id}로 url을 이동시킬때 router를 들여다보면

배열의 형태로 params가 생성된것을 볼수 있다.

<img width="512" alt="스크린샷 2023-03-09 오후 7 55 50" src="https://user-images.githubusercontent.com/45509511/224004837-e43878f3-b753-4ca6-b924-fe2d47d9b72d.png">

<img width="419" alt="스크린샷 2023-03-09 오후 7 55 45" src="https://user-images.githubusercontent.com/45509511/224004851-54f01e8c-ae17-4a6e-8216-f7da73ff48a7.png">

```javascript
const router = useRouter();

console.log(router);

const [title, id] = router.query.params;
```

새로고침하면 백엔드에서 pre-render되기 때문에 router.query.params 가 없어 오류가남

```javascript
// || [] 붙어서 초기값 배정
const [title, id] = router.query.params || [];
```

마무리로 SEO 최적화를 위해 getServerSideProps를 이용

```javascript
export function getServerSideProps({ params: { params } }: any) {
  return {
    props: {
      params,
    },
  };
```
