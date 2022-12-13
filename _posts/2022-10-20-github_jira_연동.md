---
title: "github jira 연동"
date: "2022-10-20 00:00:00"
categories: [DevLog, StackOverFlow-Clone]
tags: [devlog] # TAG는 반드시 소문자로 이루어져야함!
---

1. github에서 새로운 조직을 만든다

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dcc2d07d-4a6b-49f1-af34-5bc2f4dadb3c/Untitled.png)

1. 새로만든 조직으로 들어가 레포지토리 생성

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ea30c8ea-cad0-4181-802c-d0b42a235686/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a74384bf-388d-4ef6-9a31-2493154370f9/Untitled.png)

- owner로 새 조직을 선택해준다.

1. jira에서 새 프로젝트를 생성하고 앱 필드에서 github for jira 설치

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bf256190-e84f-4eb5-86a7-15b12f5f6b59/Untitled.png)

1. get it now 를 누르고 프로젝트 선택

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/75ff683c-b36d-4764-a69a-eb3e7776422c/Untitled.png)

- 순차적으로 진행하다보면

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d067cf9f-c682-4ebd-a7a5-6206f96c4f5d/Untitled.png)

이런 화면이 뜨는데 연결할 조직이 보인다면 선택하고 보이지 않는다면 맨 아래의

[`Install GitHub for Jira on a new organization`](https://github.com/apps/jira/installations/new) 선택하여

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bcd77cb9-d738-4098-9111-d26493e77eed/Untitled.png)

사용할 조직을 직접 선택해준다

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fc734eca-15dd-4676-a662-bd35c941da86/Untitled.png)

이후 나오는 화면에서 connect 한다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3320400b-a82c-49fd-9788-aca4d93bbdc4/Untitled.png)

status 가 FINISHED 라고 나오면 완료

1. 프로젝트에서 이슈 생성시

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f80f33af-149a-4a54-a0f7-67a71f8d7c16/Untitled.png)

개발탭에 브랜치와 커밋이 생기고 가이드 생성됨

github과 연동하려 했지만 codestates의 조직안에 repo가 있는 관계로 관리자가 권한을 부여하지않아 사용할 수 없음
