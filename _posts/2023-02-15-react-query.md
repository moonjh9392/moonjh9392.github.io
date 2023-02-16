---
title: "react-query"
date: "2023-02-15 00:00:00"
categories: [FE, REACT]
tags: [react, query] # TAG는 반드시 소문자로 이루어져야함!
---

## 📌 react-query

react-query는 서버의 값을 클라이언트에 가져오거나, 캐싱, 값 업데이트, 에러핸들링 등 비동기 과정을 더욱 편하게 하는데 사용됩니다.

### 사용 이유

서버로 부터 값을 가져오거나 업데이트 하는 로직을 store 내부에 개발하는 경우가 많습니다. 그렇다보니 store는 클라이언트 state를 유지해야하는데 어느 순간부터 store에 클라이언트 데이터와 서버 데이터가 공존 하게 됩니다.

그래서 react-query를 사용함으로 서버, 클라이언트 데이터를 분리합니다.

### react-query 장점

- 캐싱
- get을 한 데이터에 대해 update를 하면 자동으로 get을 다시 수행한다. (예를 들면 게시판의 글을 가져왔을 때 게시판의 글을 생성하면 게시판 글을 get하는 api를 자동으로 실행 )
- 데이터가 오래 되었다고 판단되면 다시 get (invalidateQueries)
- 동일 데이터 여러번 요청하면 한번만 요청한다. (옵션에 따라 중복 호출 허용 시간 조절 가능)
- 무한 스크롤 (Infinite Queries (opens new window))
- 비동기 과정을 선언적으로 관리할 수 있다.
- react hook과 사용하는 구조가 비슷하다.

### setting

next 13에서 기본 layout.js

```javascript
import "./globals.css";
import { QueryClient, QueryClientProvider } from "react-query";
import { ReactQueryDevtools } from "react-query/devtools";

const queryClient = new QueryClient();

export default function RootLayout({
  children,
}: {
  children: React.ReactNode,
}) {
  return (
    <html lang="en">
      {/*
        <head /> will contain the components returned by the nearest parent
        head.tsx. Find out more at https://beta.nextjs.org/docs/api-reference/file-conventions/head
      */}
      <head />
      <body>
        <QueryClientProvider client={queryClient}>
          <ReactQueryDevtools initialIsOpen={true} />
          {children}
        </QueryClientProvider>
      </body>
    </html>
  );
}
```

### useQuery

- 데이터를 get 하기 위한 api입니다. post, update는 useMutation을 사용합니다.
- 첫번째 파라미터로 unique Key가 들어가고, 두번째 파라미터로 비동기 함수(api호출 함수)가 들어갑니다. (당연한 말이지만 두번째 파라미터는 promise가 들어가야합니다.)
- 첫번째 파라미터로 설정한 unique Key는 다른 컴포넌트에서도 해당 키를 사용하면 호출 가능합니다. unique Key는 string과 배열을 받습니다. 배열로 넘기면 0번 값은 string값으로 다른 컴포넌트에서 부를 값이 들어가고 두번째 값을 넣으면 query 함수 내부에 파라미터로 해당 값이 전달됩니다.
- return 값은 api의 성공, 실패여부, api return 값을 포함한 객체입니다.
- useQuery는 비동기로 작동합니다. 즉, 한 컴포넌트에 여러개의 useQuery가 있다면 하나가 끝나고 다음 useQuery가 실행되는 것이 아닌 두개의 useQuery가 동시에 실행됩니다. 여러개의 비동기 query가 있다면 useQuery보다는 밑에 설명해 드릴 useQueries를 권유드립니다.
- enabled를 사용하면 useQuery를 동기적으로 사용 가능합니다. 아래 예시로 추가 설명하겠습니다.

#### status

```javascript
function Todos() {
  const { status, data, error } = useQuery("todos", fetchTodoList);

  if (status === "loading") {
    return <span>Loading...</span>;
  }

  if (status === "error") {
    return <span>Error: {error.message}</span>;
  }

  return (
    <ul>
      {data.map((todo) => (
        <li key={todo.id}>{todo.title}</li>
      ))}
    </ul>
  );
}
```

status로 loading, error 한번에 처리가능

### useQuery 동기적으로 실행

```javascript
const { data: todoList, error, isFetching } = useQuery("todos", fetchTodoList);
const {
  data: nextTodo,
  error,
  isFetching,
} = useQuery("nextTodos", fetchNextTodoList, {
  enabled: !!todoList, // true가 되면 fetchNextTodoList를 실행한다
});
```

### useQueries

```javascript
const usersQuery = useQuery("users", fetchUsers);
const teamsQuery = useQuery("teams", fetchTeams);
const projectsQuery = useQuery("projects", fetchProjects);

//위의 코드를

//아래 처럼 변경 가능
const result = useQueries([
  {
    queryKey: ["getRune", riot.version],
    queryFn: () => api.getRunInfo(riot.version),
  },
  {
    queryKey: ["getSpell", riot.version],
    queryFn: () => api.getSpellInfo(riot.version),
  },
]);

useEffect(() => {
  console.log(result); // [{rune 정보, data: [], isSucces: true ...}, {spell 정보, data: [], isSucces: true ...}]
  const loadingFinishAll = result.some((result) => result.isLoading);
  console.log(loadingFinishAll); // loadingFinishAll이 false이면 최종 완료
}, [result]);
```

### useMutation

- 값을 바꿀때 사용하는 api. return 값은 useQuery와 동일

```javascript
const riot = {
  version: "12.1.1",
};

const result = useQueries([
  {
    queryKey: ["getRune", riot.version],
    queryFn: (params) => {
      console.log(params); // {queryKey: ['getRune', '12.1.1'], pageParam: undefined, meta: undefined}

      return api.getRunInfo(riot.version);
    },
  },
  {
    queryKey: ["getSpell", riot.version],
    queryFn: () => api.getSpellInfo(riot.version),
  },
]);
```

### update후에 get 다시 실행

```javascript
const mutation = useMutation(postTodo, {
  onSuccess: () => {
    // postTodo가 성공하면 todos로 맵핑된 useQuery api 함수를 실행합니다.
    queryClient.invalidateQueries("todos");
  },
});
```

- mutation에서 return된 값을 이용해서 get 함수의 파라미터를 변경해야할 경우 setQueryData를 사용

```javascript
const queryClient = useQueryClient();

const mutation = useMutation(editTodo, {
  onSuccess: (data) => {
    // data가 fetchTodoById로 들어간다
    queryClient.setQueryData(["todo", { id: 5 }], data);
  },
});

const { status, data, error } = useQuery(["todo", { id: 5 }], fetchTodoById);

mutation.mutate({
  id: 5,
  name: "nkh",
});
```
