# React Query Todo

- Devtools 설명 : https://velog.io/@juanito_y247/React-Query-Devtools

# App.js Mutation 정의하기

Mutation은 useMutation hook을 사용하여 정의할 수 있습니다.

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
