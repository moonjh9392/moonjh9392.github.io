---
title: "react stompjs"
date: "2022-11-10 00:00:00"
categories: [DevLog, Luvpli]
tags: [devlog, stompjs] # TAG는 반드시 소문자로 이루어져야함!
---

리액트와 스프링의 소켓 통신을 위한 stompjs 사용

```
import logo from './logo.svg';
import './App.css';
import React, { useEffect, useState } from 'react';
import * as StompJS from '@stomp/stompjs';
import styled from 'styled-components';

const AppStyle = styled.div`
  padding: 100px;
  display: flex;
  flex-direction: column;
  align-items: center;

  textarea {
    margin: 10px;
    width: 400px;
    height: 300px;
  }
`;

const client = new StompJS.Client({
  brokerURL: 'ws://localhost:8001',
  connectHeaders: {
    login: 'user',
    passcode: 'password',
  },
  debug: function (str) {
    console.log('debug', str);
  },
  //요청 딜레이
  //500
  reconnectDelay: 5000,
  // 핸드셰이크 후 어느 시점에서든 클라이언트 또는 서버가 상대방에게 핑(ping) 을 보낼 수 있습니다.
  // 핑이 수신되면 수신자는 가능한 한 빨리 퐁(pong) 을 보내야합니다.
  // 이게 바로 허트비트(heartbeat) 입니다. 이 도구를 사용하여 클라이언트가 계속 연결되어 있는지 확인할 수 있습니다.
  //400
  heartbeatIncoming: 4000,
  heartbeatOutgoing: 4000,
});
function App() {
  const [text, setText] = useState('');
  useEffect(() => {
    //연결
    client.onConnect = function (frame) {
      //서버 -> 클라이언트로 메세지 받는 부분
      //생성할때 client.subscribe로 받을 url 여러개 만듬
      client.subscribe('/message', function (message) {
        console.log(JSON.parse(message.body));
      });
      client.subscribe('/room', function (message) {
        console.log(JSON.parse(message.body));
      });
    };
    //에러
    client.onStompError = function (frame) {
      console.log('Broker reported error: ' + frame.headers['message']);
      console.log('Additional details: ' + frame.body);
    };
    //활성화
    client.activate();
  }, []);

  //중지
  const deactivate = () => {
    client.deactivate();
  };
  //보내기
  const send = () => {
    client.publish({
      destination: '/aaa',
      body: JSON.stringify({ message: text }),
      headers: { 'content-type': 'application/json' },
    });
  };

  return (
    <AppStyle>
      <textarea />
      <input value={text} onChange={(e) => setText(e.target.value)}></input>
      <button onClick={send}>sendMessage</button>
      <button onClick={deactivate}>연결중지</button>
    </AppStyle>
  );
}

export default App;
```

node로 테스트 해보려고했지만 node에서는 stomp 사용안됨
