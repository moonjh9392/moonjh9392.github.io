---
title: "useCallback"
date: "2022-12-28 00:00:00"
categories: [FE, React]
tags: [callback, react] # TAG는 반드시 소문자로 이루어져야함!
---

## 📌 useCallback

### ✏️ 함수 재사용

이 함수들은 컴포넌트가 리렌더링 될 때 마다 새로 만들어진다. 함수를 선언하는 것 자체는 사실 메모리도, CPU 도 리소스를 많이 차지 하는 작업은 아니기 때문에 함수를 새로 선언한다고 해서 그 자체 만으로 큰 부하가 생길일은 없지만, 한번 만든 함수를 필요할때만 새로 만들고 재사용하는 것은 여전히 중요함

이전에 useMemo에서 사용했던 예제를 들고와서 일부분만 바꿔주려고함

<a href='https://moonjh9392.github.io/posts/useMemo/'>https://moonjh9392.github.io/posts/useMemo/</a>

onToggle function을 바꿀 예정

```javascript
const onToggle = useCallback(
  (id) => {
    setUsers(
      users.map((user) =>
        user.id === id ? { ...user, active: !user.active } : user
      )
    );
  },
  [users]
);
```

주의 할 점은, 함수 안에서 사용하는 상태 혹은 props 가 있다면 꼭, deps 배열안에 포함시켜야 된다는 것 입니다. 만약에 deps 배열 안에 함수에서 사용하는 값을 넣지 않게 된다면, 함수 내에서 해당 값들을 참조할때 가장 최신 값을 참조 할 것이라고 보장 할 수 없음. props 로 받아온 함수가 있다면, 이 또한 deps 에 넣어주어야 함

useCallback 을 사용 함으로써, 바로 이뤄낼수 있는 눈에 띄는 최적화는 없음...

그래서 어떨때 사용해야될지 감지 잘 오지않는다..
