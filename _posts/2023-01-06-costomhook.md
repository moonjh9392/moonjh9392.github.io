---
title: "customhook"
date: "2023-01-06 00:00:00"
categories: [FE, React]
tags: [custom, react] # TAG는 반드시 소문자로 이루어져야함!
---

## 📌 customHook

참고 주소

<a href='https://react.vlpt.us/basic/21-custom-hook.html'>https://react.vlpt.us/basic/21-custom-hook.html</a>

### ✏️ 커스텀 훅

컴포넌트를 만들다보면, 반복되는 로직이 자주 발생기때문에 이러한 로직들을 공통으로 사용 할 수 있게 hook으로 만들어준다.

커스텀 Hooks 를 만들 때에는 보통 이렇게 use 라는 키워드로 시작하는 파일을 만들고 그 안에 함수를 작성함

커스텀 Hooks 를 만드는 방법은 그 안에서 useState, useEffect, useReducer, useCallback 등 Hooks 를 사용하여 원하는 기능을 구현해주고, 컴포넌트에서 사용하고 싶은 값들을 반환해주면 된다~

예를 들어 input을 관리하는 훅을 만들면

```javascript
import { useState, useCallback } from "react";

function useInputs(initialForm) {
  const [form, setForm] = useState(initialForm);
  // change
  const onChange = useCallback((e) => {
    const { name, value } = e.target;
    setForm((form) => ({ ...form, [name]: value }));
  }, []);
  const reset = useCallback(() => setForm(initialForm), [initialForm]);
  return [form, onChange, reset];
}

export default useInputs;
```

이렇게 만들어주고 들고가서 쓰면된다.

주의 할점은 customHook도 Hook이기 때문에 컴포넌트의 최상위 스코프에서만 사용이 가능하다. useState, useEffect, useReducer, useCallback 처럼
