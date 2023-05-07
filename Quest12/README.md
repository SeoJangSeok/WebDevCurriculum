# Quest 12. 보안의 기초

## Introduction

- 이번 퀘스트에서는 가장 기초적인 웹 서비스 보안에 대해 알아보겠습니다.

## Topics

- XSS, CSRF, SQL Injection
- HTTPS, TLS

## Resources

- [The Basics of Web Application Security](https://martinfowler.com/articles/web-security-basics.html)
- [Website Security 101](https://spyrestudios.com/web-security-101/)
- [Web Security Fundamentals](https://www.shopify.com.ng/partners/blog/web-security-2018)
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)
- [Wikipedia - TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security)

## Checklist

- 입력 데이터의 Validation을 웹 프론트엔드에서 했더라도 서버에서 또 해야 할까요? 그 이유는 무엇일까요?
  ```
  validation이라는 개념은 데이터의 유효성/ 신뢰도/ 위변조 여부 등 매우 넓은 범위를 포괄하며, 이는 경중에 따라 client - server side에서 처리하도록 분할할 수 있다. client level에서 전달되는 data들은 데이터 위변조가 쉽고 그만큼 보안적으로 취약하다. 사용자, 혹은 이에 준하는 중요한 데이터들이 server에 안전하게 보관되기 위해선 client level의 validation보다 더 안전하고 신뢰할 수 있는 validation이 진행되어야 한다.
  ```
  - 서버로부터 받은 HTML 내용을 그대로 검증 없이 프론트엔드에 innerHTML 등을 통해 적용하면 어떤 문제점이 있을까요?
  ```
  server side script에서 다른 사용자의 정보를 훔쳐볼 수 있는 미들웨어가 삽입되었다면, 꼼짝없이 사용자 정보가 노출된다(=XSS).
  ```
  - XSS(Cross-site scripting)이란 어떤 공격기법일까요?
    ```
    공격자가 상대방의 브라우저에 스크립트가 실행되도록 해 사용자의 세션을 가로채거나, 웹사이트를 변조하거나, 악의적 콘텐츠를 삽입하거나, 피싱 공격을 진행하는 것을 말한다. XSS 공격은 스크립트 언어와 취약한 코드를 공격 대상으로 한다.
    ```
  - CSRF(Cross-site request forgery)이란 어떤 공격기법일까요?
    ```
    웹 어플리케이션 취약점 중 하나로 인터넷 사용자(희생자)가 자신의 의지와는 무관하게 공격자가 의도한 행위(수정, 삭제, 등록 등)를 특정 웹사이트에 요청하게 만드는 공격이다.
    ```
  - SQL Injection이란 어떤 공격기법일까요?
    ```
    악의적인 사용자가 보안상의 취약점을 이용하여, 임의의 SQL 문을 주입하고 실행되게 하여 데이터베이스가 비정상적인 동작을 하도록 조작하는 행위이다. 인젝션 공격은 OWASP Top10 중 첫 번째에 속해 있으며, 공격이 비교적 쉬운 편이고 공격에 성공할 경우 큰 피해를 입힐 수 있는 공격이다.
    ```
- 대부분의 최신 브라우저에서는 HTTP 대신 HTTPS가 권장됩니다. 이유가 무엇일까요?

  ```
  HTTP의 문제점은 서버에서부터 브라우저로 전송되는 정보가 암호화되지 않는다.
  HTTPS 프로토콜은 SSL(보안 소켓 계층)을 적용함으로써 서버와 브라우저 사이에 안전하게 암호화된 연결을 할 수 잇고 서버 브라우저가 민감한 정보를 주고받을 때 도난당하는 것을 막아준다.
  ```

  - HTTPS와 TLS는 어떤 식으로 동작하나요? HTTPS는 어떤 역사를 가지고 있나요?

    ```
    1. Client -> Server
    Client hello 라고 불린다. 다음과 같은 데이터를 서버에 전송한다.
    -클라이언트가 생성한 랜덤 데이터
    -클라이언트가 지원하는 암호화 방식
    -Session Id (이미 SSL handshake를 한번 완료했다면 기존 session 재활용)

    2. Server -> Client
    Server hello 라고 불린다. 다음과 같은 데이터를 클라이언트에 전송한다.
    -서버가 생성한 랜덤 데이터
    -서버가 선택한 암호화 방식
    -CA의 비밀키로 암호화 된 SSL 인증서

    3. Client -> Server
    -클라이언트는 먼저 인증서를 발행한 CA를 신뢰할 수 있는지 판단한다 (갖고 있는 CA 리스트와 비교).
    -진짜 그 CA가 발행한 인증서가 맞는지 확인한다.
    -기존에 갖고 있는 CA의 공개키를 사용해 인증서를 복호화 한다.
    -복호화에 성공한다면, 신뢰 할 수 있는 CA가 보증한 서버임을 확신할 수 있다.
    -공개키 방식을 거꾸로 사용해 Authentication에 활용했다고 할 수 있다.
    이후 Client hello 의 랜덤 데이터와 Server hello 의 랜덤 데이터를 조합하여 pre master key 생성한다.
    -pre master key를 암호화(인증서에 포함된 서버측 공개키 사용)하여 서버에 전송한다.

    4. Pre master key를 session key로 변환
    -서버는 자신의 비밀키로 전달받은 pre master key를 복호화한다.
    -클라이언트와 서버 모두 일련의 과정을 거쳐 세션 키를 획득한다.
    ( pre master key -> master key -> session key )
    -이후 세션 키를 대칭키로 사용해 데이터를 암호화 하여 클라이언트-서버 통신이 이루어진다.
    5. Handshake 종료

    네트워크 통신 보안을 제공하기 위하여 설계된 암호 규약인 SSL/TLS는 1995년 처음 발표되어 공개되었고, SSL 규약은 1995년 2.0버전을 시작으로 공개되었다.
    SSL 자체는 이후 1999년 국제 인터넷 표준화 기구(IETF)에서 표준 규약으로 정의하면서, TLS로 명칭이 바뀌었고 최근에는 SSL과 TLS 모두 혼용하고 있다.
    ```

  - HTTPS의 서비스 과정에서 인증서는 어떤 역할을 할까요? 인증서는 어떤 체계로 되어 있을까요?

  ```
  SSL 인증서는 클라이언트와 서버간의 통신을 제3자가 보증해주는 전자화된 문서다. 클라이언트가 서버에 접속한 직후에 서버는 클라이언트에게 이 인증서 정보를 전달한다.
  SSL과 SSL 디지털 인증서를 이용했을 때의 이점은 통신 내용이 공격자에게 노출되는 것을 막을 수 있다. 클라이언트가 접속하려는 서버가 신뢰 할 수 있는 서버인지를 판단할 수 있다. 통신 내용의 악의적인 변경을 방지할 수 있다.
  ```

## Quest

- 메모장의 서버와 클라이언트에 대해, 로컬에서 발행한 인증서를 통해 HTTPS 서비스를 해 보세요.

## Advanced

- TLS의 인증서에 쓰이는 암호화 알고리즘은 어떤 종류가 있을까요?
- HTTP/3은 기존 버전과 어떻게 다를까요? HTTP의 버전 3이 나오게 된 이유는 무엇일까요?
