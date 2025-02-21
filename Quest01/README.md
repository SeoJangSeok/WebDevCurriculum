# Quest 01. HTML과 웹의 기초

## Introduction

- HTML은 HyperText Markup Language의 약자로, 웹 브라우저에 내용을 표시하기 위한 가장 기본적인 언어입니다. 이번 퀘스트를 통해 HTML에 관한 기초적인 사항들을 알아볼 예정입니다.

## Topics

- HTML의 역사
  - HTML 4.01, XHTML 1.0, XHTML 1.1
  - XHTML 2.0과 HTML5의 대립
  - HTML5와 현재
- 브라우저의 역사
  - Mosaic와 Netscape
  - Internet Explorer의 독점시대
  - Firefox와 Chrome의 등장
  - iOS Safari와 모바일 환경의 브라우저
  - Edge와 Whale 등의 최근의 Chromium 계열 브라우저
- HTML 문서의 구조
  - `<html>`, `<head>`와 `<body>` 등의 HTML 문서의 기본 구조
  - 시맨틱 엘리먼트
  - 블록 엘리먼트와 인라인 엘리먼트의 차이

## Resources

- [MDN - HTML](https://developer.mozilla.org/ko/docs/Web/HTML)
- [HTML For Beginners](https://html.com/)
- [History of the web browser](https://en.wikipedia.org/wiki/History_of_the_web_browser)
- [History of HTML](https://en.wikipedia.org/wiki/HTML)
- [StatCounter](https://gs.statcounter.com/)

## Checklist

- HTML 표준의 역사는 어떻게 될까요?

  > HTML 1.0-HTML의 등장(1991) -> W3C(World Wide Web Consortium)-웹 표준을 정의(1994) -> HTML2.0 ~ HTML 3.2-표준화를 위한 노력(1995~1997) -> HTML 4.01-HTML의 안정기(1999) -> XHTML 1.0-W3C의 새로운 표준(2000) -> WHATWG 등장 -> HTML5-완전한 표준의 정착(2007)

  - HTML 표준을 지키는 것은 왜 중요할까요?
    > 정보의 접근에 있어서 표준을 알면 누구나 접근할 수 있는, 즉 차별없는 접근이 가능하게 된다. 예로 산업에 있어서 규격화된 기준이 있다면 보다 원활하게 제작물을 만들어 내는 경제적인 효과도 뛰어나다.
  - XHTML 2.0은 왜 세상에 나오지 못하게 되었을까요?

    > XHTML : XML과 HTML을 합성하여 더 확장된 태그와 엄격한 문법을 가짐.

    > 하지만, XML은 버전과 버전사이의 하위 호환성을 지원하지 않아서 이전의 태그들로 작성된 것들이 사용되지 않을 수 있다는 문제점이 있었고, 문법이 엄격하여 습득에 어려움을 겪어 점차 사용자에게 외면받게 되었다.

  - HTML5 표준은 어떤 과정을 통해 정해질까요?

    > W3C의 정기적인 컨소시엄을 통해 W3C 권고안을 발표한다.

    > 또한, 웹에 관하여 토론할 수 있는 열린 포럼, 심포지엄을 통해 사용자의 불편을 이해하고 차기 표준안에 반영한다.

- 브라우저의 역사는 어떻게 될까요?

  - Internet Explorer가 브라우저 시장을 독점하면서 어떤 문제가 일어났고, 이 문제는 어떻게 해결되었을까요?

    > 독점 시장에서 기술 발전은 이루어지지 않는다.

    > 개선이 거의 이루어지지 않아 느리고, 웹표준을 어기고, 기능 확장을 'Active X' 프로그램을 통해서 해야하기 때문에, 호환성이 떨어지는 등의 문제가 발생했다.

    > 크롬, 파이어폭스 등 새로운 브라우저가 부상하면서 독점은 해소되고 있다.

  - 현재 시점에 브라우저별 점유율은 어떻게 될까요? 이 브라우저별 점유율을 알아보는 것은 왜 중요할까요?

    > 2023년 3월 기준 Chrome 64.8%, Safari 19.5%, Edge 4.63%, Firefox 2.93%, 나머지 시장 점유율은 삼성, 오페라, UC 브라우저 및 기타 브라우저가 나눠 가졌다.

    > 사용자 환경을 파악하고 크로스 브라우징에 대응하기 위해서 개발자는 항상 점검하고 호환성과 폴리필을 진행해야한다.

  - 브라우저 엔진(렌더링 엔진)이란 무엇일까요? 어떤 브라우저들이 어떤 엔진을 쓸까요?

    > 렌더링 엔진의 역할 : 요청된 컨텐츠들을 브라우저 화면에 표시한다.

    > 게코(Gecko) - 파이어폭스, 모질라 선더버드, 시몽키 등이 사용.
    > 블링크(Blink) - 크롬, 오페랑 등이 사용.
    > 트라이던트(Trident) - 인터넷 익스플로러, 아웃룩 익스프레스, 마이크로소프트 아웃룩 등이 사용.
    > 웹키트(Webkit) - 사파리 등이 사용.
    > 태즈먼(Tasman) - 맥용 인터넷 익스플로러가 사용.

  - 모바일 시대 이후, 최근에 출시된 브라우저들은 어떤 특징을 가지고 있을까요?
    > 웨 브라우저를 소형화하면서 빠른 속도와 적은 데이터 용량을 기반으로 디바이스별로 반응형 뷰를 제공한다. 기기 제조사들이 직접 브라우저 구현을 하기도 하여 사용자 편의성을 고려한 애드 블록 등 확장 프로그램에 대한 고려와 모바일의 유저 인터페이스에 적합한 블루투스 컨트롤, 자이로 센서 기능들을 브라우저 내에서도 가능하도록 확장성을 넓히는데 주력하고 있다.

- HTML 문서는 어떤 구조로 이루어져 있나요?

  > HTML 문서의 시작은 <html>태그로 시작하고 </html>태그로 끝난다. HTMl 문서 내부는 <head>태그와 <body>태그로 이루어져있다.

  - `<head>`에 자주 들어가는 엘리먼트들은 어떤 것이 있고, 어떤 역할을 할까요?

  ```
    <title></title>
      title 요소는 브라우저 상단의 제목 표시줄이나 페이지 탭에 표시되는 웹페이지의 제목을 정의하기 위해서 사용한다.
    <script src=" "></script>
      script 요소는 웹페이지에서 필요한 자바스크립트 코드를 추가하기 위해서 사용한다.
      HTML 문서 외부에서 작성된 자바스크립트 코드를 불러오려면 <script> 요소의 src 속성을 통해 자바스크립트 파일 경로를 지정해줘야한다.
    <link rel= " " href=" "/>
      link 요소는 현재 HTMl 문서의 외부에 위치하고 있는 리소스를 불러올 때 사용한다.
      rel 속성에는 현재 웹페이지와 외부 리소스의 관계(relationship)을 명시하고, href 속성에는 외부 리소스의 경로(hyper text reference)를 명시한다.
      link 요소가 가장 많이 사용되는 사례는 HTML 문서 외부에서 작성된 CSS 파일을 불러오는 것이다.
      웹페이지 제목과 함께 브라우저의 제목 표시줄에 표시되는 사이트 아이콘(favicon)을 불러오기 위해서도 사용된다. <link rel="icon" href="./favicon.png" />
    <style></style>
      <link> 요소를 이용하여 외부 CSS 파일을 불러올 수도 있지만 HTML 문서 내부에 CSS 코드를 작성하려면 <style> 요소를 사용하면 된다.
      <style>
        p {
          color: red;
        }
      </style>
    <meta>
      meta 요소는 <head>의 하위 요소로 표현할 수 없는 추가 적인 메타 데이터를 명시하기 위해서 사용된다. 이러한 메타 데이터는 웹페이지가 브라우저에 어떻게 표시되는지는 아무 영향을 주진 않지만 검색 엔진 최적화(SEO) 측면에서 매우 중요하다.
      <meta charset="UTF-8" /> : charset 속성은 웹페이지가 어떤 문자 인코딩을 사용하는지 명시하기 위해 사용한다.
      <meta http-equiv="X-UA-Compatible" content="IE=edge" /> : http-equiv 속성은 HTTP 헤더를 HTMl 문서 내부에서 명시하기 위해서 사용한다.
      <meta name="viewport" content="width=device-width, initial-scale=1.0" /> : name 속성은 그 밖에 다른 메타 데이터를 명시하기 위해 사용된다. 이 코드는 모바일 환경에서 웹페이지가 어떻게 표시되야 하는지를 정의하고 있다.
  ```

  - 시맨틱 태그는 무엇일까요?
    > 인터넷의 발전으로 방대한 양의 웹문서가 생기면서, 제각기 일관적이지 않게 생성된 문서 구조는 웹문서에서 원하는 정보를 찾기가 점점 힘들어 지게 만드는 원인이었다.
    <div>태그의 기능과 마찬가지로 block element이면서 사이트의 구조(레이아웃)를 설계하기 위한 태그이다. HTML의 구조를 설계하는데 있어 태그에 의미를 부여 함으로써 사이트의 구조를 파악하기 용이할 수 있도록 도와주기 위해 만들어진 태그이다.
    - 시맨틱 엘리먼트를 사용하면 어떤 점이 좋을까요?
    ```
    1. SEO 최적화에 유리하다 : 검색 엔진이 태그의 목적에 부합하게 설계되어있는 구조의 사이트에서 더욱 빨리 효율적으로 정보를 파악할 수 있어 검색 결과의 노출에 유리할 수 있게 된다.
    2. 웹 접근성에 효율적 : 일반적인 브라우저에서는 차이가 없지만 스크린리더(시각장애인을 위한 웹 서핑 프로그램)과 같은 환경에서는 웹 접근성과 사용성을 향상시켜준다.
    3. 유지보수의 용이성 : 많은 div 사용으로 관리가 어려워지는 문제점에서 벗어나 태그의 이름만 보고도 어떤 영역인지 바로 확인이 가능하면 해당 태그 영역의 특성에 맞는 작업을 구분하여 진행하기에 용이하다.
    ```
    - `<section>`과 `<div>`, `<header>`, `<footer>`, `<article>` 엘리먼트의 차이점은 무엇인가요?
      ```
      <section> : 주제, 카테고리 별로 섹션을 구분하는 용도의 태그로 사용한다. 같은 테마를 가진 여러개의 콘텐츠를 그룹화한다. <article> 태그와는 달리 <section> 태그는 재배포할 수 없는 콘텐츠로 인식한다.
      <div> : block element로 구역을 차지하지만 의미는 가지고 있지 않다.
      <header> : 제목, 웹사이트를 나타내는 로고, 검색 폼, 작성자 이름 등의 요소를 포함할 수 있다.
      <footer> : 웹사이트 제일 아래에 나타나며 부가적인 정보나 링크를 넣을 수 있다.
      <article> : 웹 페이지 상에서의 실제 내용을 의미한다. 보통 블로그의 포스트나 웹사이트의 내용, 사용자가 등록한 코멘트, 독립적인 웹 콘텐츠 항목 등이 있으며, 한마디로 정의하자면 태그를 적용한 부분을 떼어 내 독립적으로 배포하거나 재사용하더라도 완전히 하나의 콘텐츠가 된다면 <article> 태그를 사용하면 된다. 검색엔진의 검색로봇에서는 <article> 태그가 사용된 콘텐츠를 배포할 수 있는 콘텐츠로 인식한다.
      ```
  - 블록 레벨 엘리먼트와 인라인 엘리먼트는 어떤 차이가 있을까요?

    > 블록 레벨 엘리먼트 : 태그를 사용해 요소를 삽입했을 때 혼자 한 줄을 차지한다. 너비가 100% 라는 것을 뜻한다. 따라서, 다음 요소가 양 옆으로 붙을 공간이 없어서 줄넘김이 된다.

    <!-- <p>, <h1>~<h6>, <ul>, <ol>, <div>, <blockquote>, <form>, <hr>, <table>, <fieldset>, <address> -->

    > 인라인 레벨 엘리먼트 : 줄을 차지하지 않는 요소이다. 화면에 표시되는 컨텐츠만큼 영역을 차지하고 나머지 공간에는 다른 요소가 올 수 있다. 따라서, 한 줄에 여러개의 인라인 레벨 엘리먼트를 표시할 수 있다.

    <!-- <a>, <img>, <object>, <br>, <sub>, <sup>, <span>, <input>, <textarea>, <label>, <button> -->

## Quest

- [이 화면](screen.png)의 정보를 HTML 문서로 표현해 보세요. 다만 CSS를 전혀 사용하지 않고, 문서의 구조가 어떻게 되어 있는지를 파악하여 구현해 보세요.
  - [CSS Naked Day](https://css-naked-day.github.io/)는 매년 4월 9일에 CSS 없는 웹 페이지를 공개하여 내용과 마크업에 집중한 HTML 구조의 중요성을 강조하는 행사입니다.
- 폴더에 있는 `skeleton.html` 파일을 바탕으로 작업해 보시면 됩니다.
  - 화면을 구성하는 큰 요소들을 어떻게 처리하면 좋을까요?
  - HTML 문서상에서 같은 층위에 비슷한 요소들이 반복될 때는 어떤 식으로 처리하는 것이 좋을까요?

## Advanced

- XML은 어떤 표준일까요? 어떤 식으로 발전해 왔을까요?
- YML, Markdown 등 다른 마크업 언어들은 어떤 특징을 가지고 있고, 어떤 용도로 쓰일까요?
