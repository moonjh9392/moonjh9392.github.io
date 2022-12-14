---
title: "github jira 연동"
date: "2022-10-20 00:00:00"
categories: [DevLog, StackOverFlow-Clone]
tags: [devlog] # TAG는 반드시 소문자로 이루어져야함!
---

1. github에서 새로운 조직을 만든다

![Untitled](https://user-images.githubusercontent.com/45509511/207517939-ef19840f-c9a3-4c1e-88ce-cef79caf6e23.png)

1. 새로만든 조직으로 들어가 레포지토리 생성

![Untitled (1)](https://user-images.githubusercontent.com/45509511/207517957-c1089950-7eae-4570-b84e-52d345bb396b.png)

![Untitled (2)](https://user-images.githubusercontent.com/45509511/207517971-ba0a3289-109a-47d2-8a07-7fc3eb070aba.png)

- owner로 새 조직을 선택해준다.

1. jira에서 새 프로젝트를 생성하고 앱 필드에서 github for jira 설치

![Untitled (3)](https://user-images.githubusercontent.com/45509511/207517987-744911d5-6747-4376-b8a2-63376eb2e078.png)

1. get it now 를 누르고 프로젝트 선택

![Untitled (4)](https://user-images.githubusercontent.com/45509511/207518008-bc768768-505a-404e-8f2d-d5b3d2a0ad6f.png)

- 순차적으로 진행하다보면

![Untitled (5)](https://user-images.githubusercontent.com/45509511/207518028-2c8d6a52-f715-4fea-9e1d-f6ef47fb4b6b.png)

이런 화면이 뜨는데 연결할 조직이 보인다면 선택하고 보이지 않는다면 맨 아래의

[`Install GitHub for Jira on a new organization`](https://github.com/apps/jira/installations/new) 선택하여

![Untitled (6)](https://user-images.githubusercontent.com/45509511/207518046-6a47cd2b-baa4-45b8-af02-eb456905cbe5.png)

사용할 조직을 직접 선택해준다

![Untitled (7)](https://user-images.githubusercontent.com/45509511/207518066-f46f44af-a3f3-425b-9c79-2084fcd0ded1.png)

이후 나오는 화면에서 connect 한다.

![Untitled (8)](https://user-images.githubusercontent.com/45509511/207518083-0fee546a-6aa8-4f12-a16e-9ca2b96d14d5.png)

status 가 FINISHED 라고 나오면 완료

1. 프로젝트에서 이슈 생성시

![Untitled (9)](https://user-images.githubusercontent.com/45509511/207518109-644da6a6-1c25-4ffa-a2be-87f5be25fede.png)

개발탭에 브랜치와 커밋이 생기고 가이드 생성됨

github과 연동하려 했지만 codestates의 조직안에 repo가 있는 관계로 관리자가 권한을 부여하지않아 사용할 수 없음
