# Quest 08. 웹 API의 기초

## Introduction

- 이번 퀘스트에서는 웹 API 서버의 기초를 알아보겠습니다.

## Topics

- HTTP Method
- node.js `http` module
  - `req`와 `res` 객체

## Resources

- [MDN - Content-Type Header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Type)
- [MDN - HTTP Methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)
- [MDN - MIME Type](https://developer.mozilla.org/en-US/docs/Glossary/MIME_type)
- [Postman](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop)
- [HTTP Node.js Manual & Documentation](https://nodejs.org/api/http.html)

## Checklist

- HTTP의 GET과 POST 메소드는 어떻게 다른가요?

  ```
  GET 과 POST 는 HTTP 메서드로 클라이언트에서 서버로 무언가를 요청할 때 사용한다.

  GET : GET 은 URL 파라미터에 요청하는 데이터를 담아 보내기 때문에 HTTP 메시지에 body가 없다.
  POST : POST 는 body 에 데이터를 담아 보내기 때문에 당연히 HTTP 메시지에 body가 존재한다.
  GET 요청은 멱등이며, POST는 멱등이 아니다.
  * 멱등?
    멱등의 사전적 정의는 연산을 여러 번 적용하더라도 결과가 달라지지 않는 성질을 의미한다.
    GET은 리소스를 조회한다는 점에서 여러 번 요청하더라도 응답이 똑같을 것 이다. 반대로 POST는 리소스를 새로 생성하거나 업데이트할 때 사용되기 때문에 멱등이 아니라고 볼 수 있다. (POST 요청이 발생하면 서버가 변경될 수 있다.)
  ```

  - 다른 HTTP 메소드에는 무엇이 있나요?
    ```
    -HEAD : GET과 동일하지만 서버에서 Body를 Return 하지 않는다.
    -PUT : 서버에 문서를 쓸때 사용한다. (GET과 반대)
    -TRACE : Client로 부터 Request Packet이 방화벽, Proxy Server, Gateway등을 거치면서 packet의 변조가 일어날 수 있는데, 이 때 Server에 도달 했을 때의 최종 Packet의 Request Packet을 볼수 있다.
    -OPTION : Target Server의 지원 가능한 method(ex> GET, POST …)를 알아보기 위함
    -DELETE : 요청 Resource를 삭제하도록 요청한다. (그러나 HTTP 규격에는 Client의 요청에도 서버가 무효화 시킬수 있도록 정의되어 있음)
    ```

- HTTP 서버에 GET과 POST를 통해 데이터를 보내려면 어떻게 해야 하나요?
  ```
  GET : URL 뒤에 ?를 붙인뒤 Query string을 넣는 형식 - 각 파라미터를 &로 연결을 한다.
  POST : DATA를 PARAMETER로 표기하지 않고, BODY에 넣어서 서버에 요청을 하게 된다. BODY에 넣음으로써 메시지 길이 제한이 없다. Content-type 헤더 필드를 꼭 추가기입하여 명시해야 한다
  ```
  - HTTP 요청의 `Content-Type` 헤더는 무엇인가요?
    ```
    Content-Type : Http 통신에서 전송되는 데이터의 타입을 명시하기 위해 header에 실리는 정보다. 즉, api 요청 시 request에 실어 보내는 데이터(body)의 타입 정보다.
    ```
  - Postman에서 POST 요청을 보내는 여러 가지 방법(`form-data`, `x-www-form-urlencoded`, `raw`, `binary`) 각각은 어떤 용도를 가지고 있나요?
    ```
    -Form Data(양식 데이터) : 양식을 채울때 입력 한 세부 정보와 같이 양숙 내부에 래핑하는 데이터를 보내는데 사용한다. 이러한 세부 정보는 Key가 보내는 항목의 "이름" 이고 Value는 실제 값을 입력하면 된다. 즉, Key-Value 쌍으로 작성하여 전송된다.
    -x-www-form-urlencoded : Form Data와 x-www-form-urlencoded는 매우 유사하다. URL이 x-www-form-urlencoded를 통해 전송 될 때 인코딩된다. 인코딩 된다는 뜻은 전송되는 데이터가 다른 문자로 인코딩되어 공격을 받고 있어도 인식할 수 없음을 의미한다.
    -raw : POST 메서드에서 본문을 보내는 동안 가장 많이 사용되는 부분 또는 옵션이다. Postman의 관점에서 중요하다. Raw는 본문 메시지가 요청 본문을 나타내는 비트 스트림으로 표시됨을 의미한다. 이러한 비트는 문자열 서버로 해석된다.
    -binary : 수동으로 입력할 수 없는 형식으로 데이터를 전송하도록 설계되었다. 컴퓨터의 모든 것이 바이너리로 변환되기 때문에 이미지, 파일 등과 같이 수동으로 작성할 수 없는 상황일 때 이러한 옵션을 사용한다.
    ```
- node.js의 `http` 모듈을 통해 HTTP 요청을 처리할 때,

  - `req`와 `res` 객체에는 어떤 정보가 담겨있을까요?
    ```
    `req`
    req.body : POST 정보를 가진다. 파싱을 위해서 body-parser와 같은 패키지가 필요하다.
    req.query : GET정보를 가진다. 즉 , URL로 전송된 쿼리 스트링 파라미터를 담고 있다.
    req.params : 내가 이름 붙인 라우트 파라미터 정보를 가진다.
    req.headers : HTTP의 Header 정보를 가진다
    `res`
    res.send : 다양한 유형의 응답을 전송(클라한테 보낼때 사용)
    res.redirect : 브라우저 리다이렉트.
    res.render : 설정된 템플릿 엔진을 사용해서 views에 연결한다.
    res.json : JSON 응답을 전송한다.
    res.end : 응답 프로세스를 종료한다.
    ```
  - GET과 POST에 대한 처리 형태가 달라지는 이유는 무엇인가요?

    ```
    GET은 클라이언트에서 서버로 어떠한 리소스로 부터 정보를 요청하기 위해 사용되는 메서드이다. GET 요청은 오로지 데이터를 읽을 때만 사용되고 수정할 때는 사용하지 않는다. 따라서 이런 이유로 사용하면 안전하다. 즉, 데이터의 변형의 위험없이 사용할 수 있다.

    POST는 리소스를 생성/업데이트하기 위해 서버에 데이터를 보내는 데 사용한다. GET과 달리 전송해야될 데이터를 HTTP 메세지의 Body에 담아서 전송한다.
    ```

- 만약 API 엔드포인트(URL)가 아주 많다고 한다면, HTTP POST 요청의
  `Content-Type` 헤더에 따라 다른 방식으로 동작하는 서버를 어떻게 정리하면 좋을까요?

  ```
  client로 부터 많은 요청이 오고, 이에 따른 resource update(PUT req)가 발생하면, middleWare에서 parsing하는 부분을 더 효율적으로 구상한다.

  HTML form tag로 부터의 request 등 예상치 못한 API exception이 발생한다면, content-type을 json 방식 혹은 x-www-url-encoded(url-encoded) 방식으로 제공하는 두개의 method를 구성하는 등 지원하는 data 형식을 확인한다.
  ```

  - 그 밖에 서버가 요청들에 따라 공통적으로 처리하는 일에는 무엇이 있을까요? 이를 어떻게 정리하면 좋을까요?
    ```
    기본적으로 http module을 사용한다면 res인자에 server 응답 정보가 담겨져 온다. 우리의 역할은 이 res인자를 parsing하여, client가 어떠한 가공된 정보를 받아야 하는지 결정하고 구현하는 것이다.
    ```

## Quest

- 다음의 동작을 하는 서버를 만들어 보세요.
  - 브라우저의 주소창에 `http://localhost:8080`을 치면 `Hello World!`를 응답하여 브라우저에 출력합니다.
  - 서버의 `/foo` URL에 `bar` 변수로 임의의 문자열을 GET 메소드로 보내면, `Hello, [문자열]`을 출력합니다.
  - 서버의 `/foo` URL에 `bar` 키에 임의의 문자열 값을 갖는 JSON 객체를 POST 메소드로 보내면, `Hello, [문자열]`을 출력합니다.
  - 서버의 `/pic/upload` URL에 그림 파일을 POST 하면 서버에 보안상 적절한 방법으로 파일이 업로드 됩니다.
  - 서버의 `/pic/show` URL을 GET 하면 브라우저에 위에 업로드한 그림이 뜹니다.
  - 서버의 `/pic/download` URL을 GET 하면 브라우저에 위에 업로드한 그림이 `pic.jpg`라는 이름으로 다운로드 됩니다.
- expressJS와 같은 외부 프레임워크를 사용하지 않고, node.js의 기본 모듈만을 사용해서 만들어 보세요.
- 처리하는 요청의 종류에 따라 공통적으로 나타나는 코드를 정리해 보세요.

## Advanced

- 서버가 파일 업로드를 지원할 때 보안상 주의할 점에는 무엇이 있을까요?
