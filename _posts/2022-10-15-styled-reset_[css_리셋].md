---
title: "styled-reset [css 리셋]"
date: "2022-10-15 00:00:00"
categories: [DevLog, MyTodoApp]
tags: [devlog, reset, css] # TAG는 반드시 소문자로 이루어져야함!
---

```jsx
npm install styled-reset
npm install styled-component
```

css 리셋을 따로 설정할 필요없이 styled 라이브러리의 reset을 이용

reset 컴포넌트를 하나 만들어주고

```jsx
import { createGlobalStyle } from "styled-components";
import reset from "styled-reset";

const Reset = createGlobalStyle`
    ${reset};`;

export default function ResetStyle(params) {
  return <Reset />;
}
```

최상위 컴포넌트 바로 아래에 reset 컴포넌트를 불러오면 된다

```jsx
import ResetStyle from "../styles/Reset";

const AppRouter = () => {
  return (
    <BrowserRouter>
      <ResetStyle /> //여기 추가
      <Routes>
        <Route path="/" element={<Landing />} />
        <Route path="/main" element={<Main />} />
      </Routes>
    </BrowserRouter>
  );
};
```
