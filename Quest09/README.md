# Quest 09. 서버와 클라이언트의 대화

## Introduction

- 이번 퀘스트에서는 서버와 클라이언트의 연동, 그리고 웹 API의 설계 방법론 중 하나인 REST에 대해 알아보겠습니다.

## Topics

- expressJS, fastify
- AJAX, `XMLHttpRequest`, `fetch()`
- REST, CRUD
- CORS

## Resources

- [Express Framework](http://expressjs.com/)
- [Fastify Framework](https://www.fastify.io/)
- [MDN - Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [MDN - XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest)
- [REST API Tutorial](https://restfulapi.net/)
- [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete)
- [MDN - CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)

## Checklist

- 비동기 프로그래밍이란 무엇인가요?

  ```
  비동기란 앞에서 행하여진 사상(事象)이나 연산이 완료되었다는 신호를 받고 비로소 특정한 사상이나 연산이 시작되는 방식.
  비동기 프로그래밍 : 특정 코드의 처리가 완료되기 전, 처리하는 도중에도 아래로 계속 내려가며 수행을 하는 것이다.
  ```

  - 콜백을 통해 비동기적 작업을 할 때의 불편한 점은 무엇인가요? 콜백지옥이란 무엇인가요?

    ```
    프로그래밍에서 콜백(callback) 또는 콜백 함수(callback function)는 다른 코드의 인수로서 넘겨주는 실행 가능한 코드를 말한다.

    콜백 방식이란 비동기 작업이 '완료되면' 콜백함수를 호출하는 방법이다. 즉, 콜백함수란 순차적으로 실행하고 싶을 때 사용하는 것 이다.

    콜백 지옥은 JavaScript를 이용한 비동기 프로그래밍시 발생하는 문제로서, 함수의 매개 변수로 넘겨지는 콜백 함수가 반복되어 코드의 들여쓰기 수준이 감당하기 힘들 정도로 깊어지는 현상을 말한다.
    ```

  - 자바스크립트의 Promise는 어떤 객체이고 어떤 일을 하나요?

    ```
    Promise는 비동기 처리에 사용되는 객체이다.
    Promise를 사용하면 비동기 프로그래밍을 할 때 코드를 순차적으로 작성이 가능하여 컨트롤이 쉬워지고 코드 가독성이 좋아진다.

    Promise는 객체이기 때문에 생성자 함수를 호출하여 인스턴스화할 수 있다.

    Promise의 생성자 함수는 resolve와 reject함수를 인자로 전달받는 콜백함수를 인자로 전달받는다.

    Promise는 인자로 전달받은 콜백 함수를 내부에서 비동기 처리한다.
    ```

  - 자바스크립트의 `async`와 `await` 키워드는 어떤 역할을 하며 그 정체는 무엇일까요?
    ```
    async/await는 ES2017에 도입된 문법으로서, Promise 로직을 더 쉽고 간결하게 사용할 수 있게 해준다.
    async 키워드는 await를 사용하기 위한 선언문이다. function 앞에 async을 붙여줌으로써, 함수내에서 await 키워드를 사용할 수 있게 된다.
    await 키워드는 promise.then() 보다 좀 더 세련되게 비동기 처리의 결과값을 얻을 수 있도록 해주는 문법이다. await 키워드를 사용하면 then 핸들러를 복잡하게 처리할 필요 없이, 심플하게 비동기 함수 왼쪽에 await 만 명시해주고 결과값을 변수에 받도록 코드를 정의하면 끝이다. then과 콜백 함수를 남발하여 코드가 들여쓰기로 깊어지는 것을 방지하고, 한 줄 레벨에서 코드를 나열하여 가독성을 높일 수 있다. Promise 비동기 처리가 완료될때 까지 코드 실행을 일시 중지하고 wait 한다
    ```

- 브라우저 내 스크립트에서 외부 리소스를 가져오려면 어떻게 해야 할까요?
  ```
  http 프로토콜에서 req 인자에 외부 resource, data를 전달할 수 있다.
  ```
  - 브라우저의 `XMLHttpRequest` 객체는 무엇이고 어떻게 동작하나요?
    ```
    서버와 상호작용을 할 수 있는 객체이다.
    데이터를 받아올 수 있는 객체이며, 해당 사이트 혹은 get/post method를 통해 전달받는 resource들을 XMLHttpRequest를 통해 얻을 수 있다.
    HTTP와 함께 FTP같은 다른 프로토콜에서도 동작이 가능하며, 별도의 상태코드가 존재한다.
    ```
  - `fetch` API는 무엇이고 어떻게 동작하나요?
    ```
    Fetch API는 HTTP 파이프라인을 구성하는 요청과 응답 등의 요소를 JavaScript에서 접근하고 조작할 수 있는 인터페이스를 제공한다. Fetch API가 제공하는 전역 fetch() 메서드로 네트워크의 리소스를 쉽게 비동기적으로 가져올 수도 있다.
    fetch api는 promise를 기반으로 동작한다. fetch 함수는 필수 항목인 input과 옵션인 init을 파라미터로 가지며 Response 타입을 갖는 Promise를 반환한다.
    ```
- REST는 무엇인가요?

  ```
  REST(Representational State Transfer) : 자원을 이름(자원의 표현)으로 구분하여 해당 자원의 상태(정보)를 주고 받는 모든 것을 의미한다.월드 와이드 웹(www)과 같은 분산 하이퍼미디어 시스템을 위한 소프트웨어 개발 아키텍처의 한 형식으로 REST는 기본적으로 웹의 기존 기술과 HTTP 프로토콜을 그대로 활용하기 때문에 웹의 장점을 최대한 활용할 수 있는 아키텍처 스타일이다.
  ```

  - REST API는 어떤 목적을 달성하기 위해 나왔고 어떤 장점을 가지고 있나요?

    ```
    * 균일한 인터페이스(멱등성) : 요청에 상관없이 동일한 resource에 대한 모든 API 요청은 동일하게 보여져야 하며, client가 필요로 하는 모든 정보를 포함해야 한다.

    * client/server decoupling : client와 server는 서로 완전히 독립적이어야 하고, resource의 URI를 제외하고 어떠한 방식으로도 서로 상호작용은 할 수 없다.

    * Stateless : server는 client 요청과 관련한 데이터를 저장할 수 없으며, 이에 따라 client request에서 처리가 필요한 모든 정보가 담겨져 있어야 한다.

    * caching : resource는 client/server에서 caching할 수 있어야 하며, server 응답에는 caching 허용 여부에 대한 정보가 포함되어 있어야 한다.
    → resource caching이 가능하다면 client/server의 구성 요소 확장성이 증가한다.

    * 계층 구조 아키텍쳐 : REST API에서의 request, response는 다른 계층에서 전달된다.
    → 통신 루프 상에서 서로 다른 중개자가 있을 수 있음을 유념해야 하고, client/server는 이러한 통신과정을 알 수 없도록 설계해야 한다.

    * on demand : 특정 경우에는 응답에 실행코드를 포함하여, 정적 리소스에 대한 정적 응답과 더불어 동적 실행이 가능하다.
    ```

  - RESTful한 API 설계의 단점은 무엇인가요?
    ```
    use strict 모드에서만 설계할 수 있을 만큼 method가 제한적이고, 모든 조건을 만족하는 API 설계가 쉽지 않다.
    ```

- CORS란 무엇인가요? 이러한 기능이 왜 필요할까요? CORS는 어떻게 구현될까요?

  ```
  CORS(Cross-Origin Resource Sharing) : 추가 HTTP헤더를 사용하여, 한 출처에서 실행 중인 웹 애플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는 권한을부여하도록 브라우저에 알려주는 체제이다.

  CORS가 없이 모든 곳에서 데이터를 요청할 수 있게 된다면, 다른 사이트에서 원래 사이트를 흉내낼 수 있게 된다. 만약 기존 사이트와 완전히 동일하게 동작하도록 하여 사용자가 로그인을 하도록 하고, 로그인했던 세션 또는 토큰을 탈취하여 악의적으로 정보를 꺼내오거나 다른 사용자의 정보를 입력하는 등 헤킹을 할 수 있다. 하지만 이런 공격을 할 수 없도록 브라우저에서 보호하고, 필요한 경우에만 서버와 협의하여 요청할 수 있도록 하기 위해서 필요한 것이다.

  클라이언트 측 : 별도의 오리진으로의 요청은 'Origin' 이라는 필드를 추가하면 된다. Origin: https://xxx.co.kr
  Fetch API에서는 'cors mode'을 설정할 필요가 있다
  서버 측 :
  Access-Control-Allow-Origin: https://xxx.co.kr  // 특정 사이트를 허가
  Access-Control-Allow-Origin: *   // 모든 사이트를 허가
  Access-Control-Allow-Headers "X-Requested-With, Origin, X-Csrftoken, Content-Type, Accept"  // 여기는 사용하는 프레임워크에 따라 달라진다.
  ```

## Quest

- 이번 퀘스트는 Midterm에 해당하는 과제입니다. 분량이 제법 많으니 한 번 기능별로 세부 일정을 정해 보고, 과제 완수 후에 그 일정이 얼마나 지켜졌는지 스스로 한 번 돌아보세요.
  - 이번 퀘스트부터는 skeleton을 제공하지 않습니다!
- Quest 05에서 만든 메모장 시스템을 서버와 연동하는 어플리케이션으로 만들어 보겠습니다.
  - 클라이언트는 `fetch` API를 통해 서버와 통신합니다.
  - 서버는 8000번 포트에 REST API를 엔드포인트로 제공하여, 클라이언트의 요청에 응답합니다.
  - 클라이언트로부터 온 새 파일 저장, 삭제, 다른 이름으로 저장 등의 요청을 받아 서버의 로컬 파일시스템을 통해 저장되어야 합니다.
    - 서버에 어떤 식으로 저장하는 것이 좋을까요?
  - API 서버 외에, 클라이언트를 띄우기 위한 서버가 3000번 포트로 따로 떠서 API 서버와 서로 통신할 수 있어야 합니다.
  - Express나 Fastify 등의 프레임워크를 사용해도 무방합니다.
- 클라이언트 프로젝트와 서버 프로젝트 모두 `npm i`만으로 디펜던시를 설치하고 바로 실행될 수 있게 제출되어야 합니다.
- 이번 퀘스트부터는 앞의 퀘스트의 결과물에 의존적인 경우가 많습니다. 제출 폴더를 직접 만들어 제출해 보세요!

## Advanced

- `fetch` API는 구현할 수 없지만 `XMLHttpRequest`로는 구현할 수 있는 기능이 있을까요?
- REST 이전에는 HTTP API에 어떤 패러다임들이 있었을까요? REST의 대안으로는 어떤 것들이 제시되고 있을까요?
