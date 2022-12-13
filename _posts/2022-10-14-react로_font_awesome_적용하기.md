---
title: "react로_font_awesome_적용하기"
date: "2022-10-14 00:00:00"
categories: [DevLog, MyTodoApp]
tags: [devlog, react, fontawesome] # TAG는 반드시 소문자로 이루어져야함!
---

```markdown
npm i --save @fortawesome/fontawesome-svg-core
npm install --save @fortawesome/react-fontawesome
npm install --save @fortawesome/free-solid-svg-icons
```

@fortawesome/fontawesome-svg-core

- 폰트 어썸의 svg 아이콘을 들고올수 있는 core 라이브러리 설치

@fortawesome/react-fontawesome

- 리액트에서 폰트 어썸 컴포넌트를 사용하기 위해 설치

```jsx
import { FontAwesomeIcon } from "@fortawesome/react-fontawesome";

<FontAwesomeIcon
  icon={faPencil} //아이콘 이름
  size="2x" //아이콘 크기 lg,2x,3x,4x ...
  color="gray"
/>; //색상
```

@fortawesome/free-solid-svg-icons

- 폰트 어썸의 soild 아이콘 들을 들고옴

```jsx
import { faPencil } from "@fortawesome/free-solid-svg-icons";
faPencil; // 아이콘 종류
```
