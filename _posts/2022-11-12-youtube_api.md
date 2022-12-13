---
title: "youtube api"
date: "2022-11-12 00:00:00"
categories: [DevLog, Luvpli]
tags: [devlog, youtube, api] # TAG는 반드시 소문자로 이루어져야함!
---

npm i react-youtube 설치

```jsx
<YouTube
  videoId="qEVUtrk8_B4"
  opts={opts}
  onReady={onReady}
  onStateChange={onPlayerStateChange}
/>
```

YouTube 컴포넌트 사용

onReady = 시작시 이벤트

onStateChange = 시간이나 다른 이벤트 발생시 발생하는 이벤트

```jsx
const [player, setPlayer] = useState();

const onReady = (event) => {
  setPlayer(event.target); // 처음에 유튜브 컴포넌트의 event.target을 state 로 변환
};
```

e.target.getCurrentTime() = 현재시간 뽑기

e.target.playVideo() = 비디오 플레이 시키기

e.target.seekTo(data.time, true) = 지정한 시간으로 이동 ture = 현재 이동한 시간에서 플레이, false = 원래 보던 시간대에서 플레이

player.getPlaylist():Array
이 함수는 현재 순서에 따라 재생목록에 있는 동영상 ID의 배열을 반환합니다. 기본적으로 이 함수는 재생목록 소유자가 지정한 순서로 동영상 ID를 반환합니다. 그러나 setShuffle 함수를 호출하여 재생목록 순서에 셔플을 사용한 경우에는 getPlaylist() 함수의 반환 값이 셔플을 사용한 순서를 반영합니다.

player.getPlaylistIndex():Number
이 함수는 현재 재생 중인 재생목록 동영상의 색인을 반환합니다.
재생목록에 셔플을 사용하지 않은 경우 반환 값은 재생목록 제작자가 동영상을 배치한 위치를 식별합니다. 반환 값은 0부터 시작하는 색인을 사용하므로 0의 값은 재생목록에서 첫 번째 동영상을 식별합니다.
재생목록에 셔플을 사용한 경우 반환 값은 셔플을 사용한 재생목록 내의 동영상 순서를 식별합니다.
