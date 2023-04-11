# React Query Todo

- https://tanstack.com/query/latest/docs/react/devtools

# 1. Devtools 설치

-

```
npm i @tanstack/react-query-devtools
```

# 2. index.js

- QueryClientProvider는 React Query를 사용할 때 필요한 Provider입니다. QueryClientProvider를 사용하면 React Query의 설정과 상태를 애플리케이션 전체에서 공유할 수 있습니다.

- QueryClientProvider를 사용하여 queryClient를 전달합니다. 이렇게 하면 QueryClientProvider가 애플리케이션 전체에서 queryClient를 사용할 수 있게 됩니다.

- queryClient는 React Query의 기능을 구현하는 데 필요한 구성 요소입니다. 예를 들어, 쿼리 데이터 캐싱, 캐시를 만료하는 데 사용되는 캐시 구성 및 전역 쿼리 구성을 구현할 수 있습니다. queryClient를 구성하는 방법에는 다양한 옵션이 있으며, 필요한 옵션에 따라 queryClient를 구성할 수 있습니다.

- QueryClientProvider를 사용하면, App 컴포넌트와 그 하위 컴포넌트들이 QueryClientProvider의 자식 컴포넌트가 되므로, App 컴포넌트에서 useQuery나 useMutation 같은 React Query 훅을 사용할 수 있게 됩니다.

```js
import React from "react";
import ReactDOM from "react-dom/client";
import "./index.css";
import App from "./App";
import { QueryClient, QueryClientProvider } from "react-query";

// QueryClient 인스턴스를 생성합니다.
const queryClient = new QueryClient();

// ReactDOM.createRoot 메소드를 사용하여 루트 노드를 생성합니다.
const root = ReactDOM.createRoot(document.getElementById("root"));

// QueryClientProvider 컴포넌트를 사용하여 QueryClient를 전역으로 사용할 수 있도록 설정합니다.
// App 컴포넌트를 QueryClientProvider 내부에 렌더링합니다.
root.render(
  <QueryClientProvider client={queryClient}>
    <App />
  </QueryClientProvider>
);
```

# 3. App.js

이 코드는 React Query를 사용하여 "https://jsonplaceholder.typicode.com/todos"에서 Todo 리스트를 가져오고, 가져온 데이터를 화면에 보여주는 간단한 Todo 애플리케이션 예제입니다.

```js
import { useQuery } from "react-query";

function App() {
  // useQuery 훅을 사용하여 'todos' 쿼리를 정의하고, 데이터를 가져오는 fetch 함수를 지정합니다.
  const { data, isLoading, isError } = useQuery("todos", () =>
    fetch("https://jsonplaceholder.typicode.com/todos").then((res) =>
      res.json()
    )
  );

  // 데이터가 로딩 중일 때 "Loading..."을 출력합니다.
  if (isLoading) return "Loading...";

  // 데이터를 가져오는 데 에러가 발생하면 "Error"를 출력합니다.
  if (isError) return "Error";

  // 가져온 데이터를 화면에 보여줍니다.
  return (
    <div>
      {data.map((todo) => (
        <div key={todo.id}>{todo.title}</div>
      ))}
    </div>
  );
}

export default App;
```
