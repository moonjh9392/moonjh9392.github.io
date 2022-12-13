---
title: "react-confirm-alert 라이브러리"
date: "2022-10-16 00:00:00"
categories: [DevLog, MyTodoApp]
tags: [devlog, react-confirm-alert, react] # TAG는 반드시 소문자로 이루어져야함!
---

삭제 버튼은 확인창을 만들기 위해 react-confirm-alert를 사용함

1. 공용으로 쓰기위해 confirm 컴포넌트의 위치를 common에 만들어준다

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9755c0d1-32be-4405-b950-1bd54693c5f9/Untitled.png)

1. confirm의 내용

```jsx
import "react-confirm-alert/src/react-confirm-alert.css"; // Import css
import styled from "styled-components";

const ConfirmStyle = styled.div`
  //원하는 스타일 적용
`;
export default function Confirm({
  onClose,
  title,
  content,
  arg1,
  arg2,
  callback,
}) {
  return (
    //class='custom-ui' <<react-confirm-alert 에서 모달창 스타일을 만들어줌
    <ConfirmStyle className="custom-ui">
      <h1>{title}</h1>
      <p>{content}</p>
      <div>
        <button
          onClick={() => {
            callback(arg1, arg2);
            onClose();
          }}
        >
          Yes!
        </button>
        <button onClick={onClose}>No~</button>
      </div>
    </ConfirmStyle>
  );
}
```

1. Confirm을 호출할 위치에 아래의 내용 삽입

```jsx
import { confirmAlert } from "react-confirm-alert"; // Import

const handleDeleteClick = () => {
  //삭제 버튼
  const title = "메모 삭제하기";
  const contents = `${content.title}을(를) 끝내셨나요?`;
  confirmAlert({
    customUI: ({ onClose }) => {
      return (
        //callback에 삭제를 누르면 실행될 이벤트를 넣어주고 arg를 props로 넘겨줌
        <Confirm
          onClose={onClose}
          title={title}
          content={contents}
          arg1={url}
          arg2={id}
          callback={fetchDelete}
        />
      );
    },
  });
};
```

1. 결과

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/200015d7-cef0-442a-9d26-4abffb67b69c/Untitled.png)
