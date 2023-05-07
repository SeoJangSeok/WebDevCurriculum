# Quest 13. 웹 API의 응용과 GraphQL

## Introduction

- 이번 퀘스트에서는 차세대 웹 API의 대세로 각광받고 있는 GraphQL에 대해 알아보겠습니다.

## Topics

- GraphQL
  - Schema
  - Resolver
  - DataLoader
- Apollo

## Resources

- [GraphQL](https://graphql.org/)
- [GraphQL.js](http://graphql.org/graphql-js/)
- [DataLoader](https://github.com/facebook/dataloader)
- [Apollo](https://www.apollographql.com/)

## Checklist

- GraphQL API는 무엇인가요? REST의 어떤 단점을 보완해 주나요?

```
GraphQL은 API를 위한 쿼리 언어이며 이미 존재하는 데이터로 쿼리를 수행하기 위한 런타임이다. GraphQL에서는 API서버에서 엄격하게 정의된 endpoint 들에 요청하는 대신, 한번의 요청으로 정확히 가져오고 싶은 데이터를 가져올 수 있게 도와주는 쿼리를 보낼수 있다.

user에 대한 몇 가지의 간단한 데이터가 필요할 때, 필요한 만큼의 user 정보를 최적화하여 가져올 수 있다. GraphQL은 Frontend와 Backend의 협업 방식에 많은 변화를 가져올 수 있다. Backend에서의 많은 로직을 Frontend로 분산할 수 있다

1) REST에서는 Resource에 대한 형태 정의와 데이터 요청 방법이 연결되어 있지만, GraphQL에서는 Resource에 대한 형태 정의와 데이터 요청이 완전히 분리되어 있다.
2) REST에서는 Resource의 크기와 형태를 서버에서 결정하지만, GraphQL에서는 Resource에 대한 정보만 정의하고, 필요한 크기와 형태는 client단에서 요청 시 결정한다.
3) REST에서는 URI가 Resource를 나타내고 Method가 작업의 유형을 나타내지만, GraphQL에서는 GraphQL Schema가 Resource를 나타내고 Query, Mutation 타입이 작업의 유형을 나타낸다.
4) REST에서는 여러 Resource에 접근하고자 할 때 여러 번의 요청이 필요하지만, GraphQL에서는 한번의 요청에서 여러 Resource에 접근할 수 있다.
5) REST에서 각 요청은 해당 엔드포인트에 정의된 핸들링 함수를 호출하여 작업을 처리하지만, GraphQL에서는 요청 받은 각 필드에 대한 resolver를 호출하여 작업을 처리한다.
```

- GraphQL 스키마는 어떤 역할을 하며 어떤 식으로 정의되나요?

  ```
  스키마(Schema)란 데이터 타입의 집합이다. 스키마를 미리 정의해 두면, 스키마 정의는 API 문서 같은 역할을 하며, 프론트 엔드 개발자와 백엔드 개발자가 많은 의사소통에 대한 비용을 줄이고 빠른 개발을 할 수 있다는 장점이 있다.

  GraphQL의 API를 설계하기 전에 항상 사용할 스키마를 먼저 정의해야한다. 어떤 필드를 선택할지 어떤 종류이 객체를 반환할지, 하위 객체에서 필요한 사용할 수 있는 필드는 무엇인지 알기 위해선 스키마의 존재가 필연적이다.
  ```

- GraphQL 리졸버는 어떤 역할을 하며 어떤 식으로 정의되나요?

```
GraphQL 리졸버 : GraphQL에서 설계한 Query를 사용하여 data를 얻기위해 실질적으로 사용하는 data 확보도구이다. 우리가 작성한 정의문(Query)을 실제로 활용하여 데이터를 얻는 과정을 의미한다.
```

- GraphQL 리졸버의 성능 향상을 위한 DataLoader는 무엇이고 어떻게 쓰나요?

```
N+1문제, 여러 데이터를 얻기 위해 과도하게 query 반복이 이루어지지 않도록 최적화된 데이터 조회/접근을 해주는 기능을 일컫는다.

DataLoader 특징
1. Batch : 여러 데이터들을 조회하기 위한 각각의 요청들을 하나로 모은 후, 단일 요청으로 보내고 해당 결과값들을 확보한다.
2. Cache : 요청항목 중 기존에 요청과 중복되는 것이 있다면, 이를 Caching하여(미리 기억에 저장하고 있다가, 중복 요청이 생기면 특정) 접근한다.

Database에서 DataLoader가 요청을 한 곳으로 모으고, 이 요청을 fetch(전달)하는 과정으로 접근이 이루어진다.
```

- 클라이언트 상에서 GraphQL 요청을 보내려면 어떻게 해야 할까요?

```
1. resolvers에 client를 통한 요청값을 담을 변수를 지정하고, 해당 변수가 client로 부터 요청받은 값임을 나타낸다(@client).
2. 이를 위해 type(Query)에도 해당 변수를 추가해준다.
3. client에서 동적으로 변화하는 데이터를 활용한다.
```

- Apollo 프레임워크(서버/클라이언트)의 장점은 무엇일까요?

```
GraphQL의 장점인 단일 endpoint를 그대로 활용하면서
GraphQL server에 직접 접속하지 않고도, visualstudio와 같은 환경에서 ApolloClient를 통해 server에 접근할 수 있다.
사용자가 정의한 Query도 그대로 활용하면서 data를 확보할 수 있다.
GraphQL과 함께 사용할 수 있는 호환성이 매우 높고, 이를 통해 효율적으로 data를 확보할 수 있다
```

- Apollo Client를 쓰지 않고 Vanilla JavaScript로 GraphQL 요청을 보내려면 어떻게 해야 할까요?

```
fetch, axios과 같은 데이터 전달 module 및 REST API(GET/POST method) 등 data를 확보할 수 있는 별도의 모듈을 사용해야 한다.
변수가 담겨진 querystring 및 req.body와 같은 요소를 활용할 수 있다.
```

- GraphQL 기반의 API를 만들 때 에러처리와 HTTP 상태코드 등은 어떻게 하는게 좋을까요?

```
server 접속 및 모든 요청처리 성공(※ status code - 200)
GraphQL server / apollo server initialization 실패처리
REST API 실패처리
resolver가 정의되어있지 않는 변수/객체를 반환하는 오류
```

## Quest

- 메모장의 서버와 클라이언트 부분을 GraphQL API로 수정해 보세요.

## Advanced

- GraphQL이 아직 제대로 수행하지 못하거나 불가능한 요구사항에는 어떤 것이 있을까요?
- GraphQL의 경쟁자에는 어떤 것이 있을까요?
