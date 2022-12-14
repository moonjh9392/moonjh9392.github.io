---
title: "react-confirm-alert 라이브러리"
date: "2022-10-16 00:00:00"
categories: [DevLog, MyTodoApp]
tags: [devlog, react-confirm-alert, react] # TAG는 반드시 소문자로 이루어져야함!
---

삭제 버튼은 확인창을 만들기 위해 react-confirm-alert를 사용함

1. 공용으로 쓰기위해 confirm 컴포넌트의 위치를 common에 만들어준다

![Untitled (3)](https://user-images.githubusercontent.com/45509511/207517177-96094bcf-f6b8-444e-9ce3-045b38643a1e.png)

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

<img width="827" alt="Untitled (4)" src="https://user-images.githubusercontent.com/45509511/207517223-86406c20-826a-45d0-ac1b-bb3f86f2e054.png">
