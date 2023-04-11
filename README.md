# React Query Todo

- https://tanstack.com/query/latest/docs/react/devtools

# 1. Devtools 설치

-

```
npm i @tanstack/react-query-devtools
```

# 2. index.js

QueryClientProvider를 사용하여 queryClient를 전달합니다. 이렇게 하면 QueryClientProvider가 애플리케이션 전체에서 queryClient를 사용할 수 있게 됩니다.

queryClient는 React Query의 기능을 구현하는 데 필요한 구성 요소입니다. 예를 들어, 쿼리 데이터 캐싱, 캐시를 만료하는 데 사용되는 캐시 구성 및 전역 쿼리 구성을 구현할 수 있습니다. queryClient를 구성하는 방법에는 다양한 옵션이 있으며, 필요한 옵션에 따라 queryClient를 구성할 수 있습니다.

QueryClientProvider를 사용하면, App 컴포넌트와 그 하위 컴포넌트들이 QueryClientProvider의 자식 컴포넌트가 되므로, App 컴포넌트에서 useQuery나 useMutation 같은 React Query 훅을 사용할 수 있게 됩니다.

```js
import React from "react";
import ReactDOM from "react-dom/client";
import "./index.css";
import App from "./App";
import { QueryClient, QueryClientProvider } from "react-query";
const queryClient = new QueryClient();

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <QueryClientProvider client={queryClient}>
    <App />
  </QueryClientProvider>
);
```
