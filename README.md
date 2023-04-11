# React Query Todo

- https://github.com/gopinav/React-Query-Tutorials

# 1. json-server 설치

- https://www.npmjs.com/package/json-server

```
npm install -g json-server
```

/db.json 생성

```js
{
  "posts": [
    {
      "posts": [
        {
          "id": 1,
          "text": "내용 1",
          "isComplete": false
        },
        {
          "id": 2,
          "text": "내용 2",
          "isComplete": false
        },
        {
          "id": 3,
          "text": "내용 3",
          "isComplete": false
        }
      ]
    }
  ]
}


```

```js
json-server --watch ./db.json --port 4000
```
