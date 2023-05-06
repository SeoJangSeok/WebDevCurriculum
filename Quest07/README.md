# Quest 07. node.js의 기초

## Introduction

- 이번 퀘스트에서는 node.js의 기본적인 구조와 개념에 대해 알아 보겠습니다.

## Topics

- node.js
- npm
- CommonJS와 ES Modules

## Resources

- [About node.js](https://nodejs.org/ko/about/)
- [Node.js의 아키텍쳐](https://edu.goorm.io/learn/lecture/557/%ED%95%9C-%EB%88%88%EC%97%90-%EB%81%9D%EB%82%B4%EB%8A%94-node-js/lesson/174356/node-js%EC%9D%98-%EC%95%84%ED%82%A4%ED%85%8D%EC%B3%90)
- [npm](https://docs.npmjs.com/about-npm)
- [npm CLI commands](https://docs.npmjs.com/cli/v7/commands)
- [npm - package.json](https://docs.npmjs.com/cli/v7/configuring-npm/package-json)
- [How NodeJS Require works!](https://www.thirdrocktechkno.com/blog/how-nodejs-require-works)
- [MDN - JavaScript Modules](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Modules)
- [ES modules: A cartoon deep-dive](https://hacks.mozilla.org/2018/03/es-modules-a-cartoon-deep-dive/)
- [require vs import](https://www.geeksforgeeks.org/difference-between-node-js-require-and-es6-import-and-export/)

## Checklist

- node.js는 무엇인가요? node.js의 내부는 어떻게 구성되어 있을까요?

  ```
  Node.js는 Chrome V8 JavaScript 엔진으로 빌드 된 JavaScript 런타임입니다.
  => 노드를 통해 다양한 자바스크립트 애플리케이션을 실행할 수 있으며, 서버를 실행하는데 제일 많이 사용된다.
  * Node.js는 JavaScript를 서버에서도 사용할 수 있도록 만든 프로그램이다.
  * Node.js는 V8이라는 JavaScript 엔진 위에서 동작하는 자바스크립트 런타임(환경)이다.
  * Node.js는 서버사이트 스크립트 언어가 아니다. 프로그램(환경)이다.
  * Node.js는 웹서버와 같이 확장성 있는 네트워크 프로그램을 제작하기 위해 만들어졌다.

  사용되는 언어로는 자바스크립트(Javascript)를 활용하며, Non-blocking I/O와 단일 스레드 이벤트 루프를 통한 높은 처리 성능을 가지고 있는 것이 특징이다.

  내장 HTTP 서버 라이브러리를 포함하고 있어 웹 서버에서 아파치 등의 별도 소프트웨어 없이 동작하는 것이 가능하며, 이를 통한 웹 서버의 동작에 있어 더 많은 통제에서 벗어나 여러 가지 기능을 가능하게 한다.
  ```

- npm이 무엇인가요? `package.json` 파일은 어떤 필드들로 구성되어 있나요?

  ```
  npm(Node Package Manager) : JavaScript 및 세계 최대의 소프트웨어 레지스트리 패키지 관리자로 Node.js를 설치하면 같이 설치되어 사용할 수 있다.

  npm에는 Node.js에서 사용되는 각종 코드 패키지들이 모여있고, 우리는 그 패키지를 다운로드 받아 사용할 수 있다.

  package.json은 개발자가 배포한 패키지에 대해, 다른 사람들이 관리하고 설치하기 쉽게 하기 위한 문서이다.
  $ npm init -y 로 기본 설정 값으로 package.json을 생성하면,
  {
  "name": "PROJECT_DIRECTORY",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
  }
  와 같이 field가 생성된다.

  * "name" : 이 패키지의 이름을 나타낸다.
  * "version" : [major].[minor].[patch]의 형태로 작성해야한다.
  * "description" : 문자열로 기술한 패키지에 대한 설명. npm에서 검색되었을 때 리스트에 표시되어 사람들이 패키지를 찾아내고 이해할 수 있는데 도움을 준다.
  * "main" : 패키지의 진입점(entry point)이 되는 모듈의 ID.
  * "scripts" : 패키지의 생명주기에서 다양한 타이밍에 자주 사용할 command를 alias(별칭)를 통해 지정해 둘 수 있는 dictionary이다.
  * “keywords” : 키워드를 문자열 배열로 설명. description과 마찬가지로 npm에서 검색되었을 때 리스트에 표시되어 사람들이 패키지를 찾아내고 이해할 수 있는데 도움을 준다.
  * “author” : 배포자 한 사람을 위한 field로, 다수의 사람을 표시하기 위해서는 “contributors” field로 작성해야 한다.
  * “license” : 배포한 패키지에 대해 패키지 사용자가 패키지를 사용하는데 어떤 권한과 제한 사항이 있는지 알기 위해 license를 명시해야 한다.
  ```

- npx는 어떤 명령인가요? npm 패키지를 `-g` 옵션을 통해 글로벌로 저장하는 것과 그렇지 않은 것은 어떻게 다른가요?

  ```
  npx는 자바스크립트 패키지 관리 모듈인 npm(Node Package Module)의 5.2.0 버전부터 새로 추가된 도구이다. =>  npm을 좀 더 편하게 사용하기 위해서 npm에서 제공해주는 하나의 도구이다.

  $ npm install (패키지명) : 프로젝트 폴더에 패키지 설치.
  $ npm install -g (패키지명) : 시스템 폴더에 패키지 설치.(Win10 기준, (사용자명)\AppData\Roaming\npm\node_modules)
  ```

- 자바스크립트 코드에서 다른 파일의 코드를 부르는 시도들은 지금까지 어떤 것이 있었을까요? CommonJS 대신 ES Modules가 등장한 이유는 무엇일까요?

  ```
  <commonJS>
  - commonJS는 Node.js의 디폴트 모듈 시스템이다.
  - require(), module.exports 문법을 사용한다.
  - commonJS 문법은 런타임에 파싱되므로 require 는 코드 어디에서나 사용할 수 있다. if 문 안에서도, loop 안에서도 사용할 수 있다.
  - commonJS는 sync하게 하나씩 순차적으로 모듈을 로드하기 때문에 큰 어플리케이션에서는 퍼포먼스 이슈가 있을 수 있다.

  <ES module (ESM)>
  - ES module은 자바스크립트 공식 모듈 시스템이고 거의 모든 모던 웹 브라우저가 ES module을 지원한다.
  - 다만 Node.js에서는 commonJS가 디폴트였고, ESM은 실험적으로만 제공하다가 v13.2.0 에서부터 ESM을 stable로 제공하기 시작했다.
  - ESM은 import, export 문법을 사용하여 commonJS보다 readable 하다.
  - ESM의 import문은 항상 파일의 최상단에 위치해야한다.
  - ESM은 모듈을 async하게 로드한다.
  - ESM을 프로젝트에 적용하려면 js파일을 mjs확장자로 바꾸어 사용하거나, package.json에 "type": "module" 을 선언해주는 방법이 있다.
  - React나 Vue는 ESM을 사용하는 대신 하위호환을 맞추기 위해 Babel 트랜스파일러를 사용하여 commonJS로 컴파일한다.
  ```

- ES Modules는 기존의 `require()`와 동작상에 어떤 차이가 있을까요? CommonJS는 할 수 있으나 ES Modules가 할 수 없는 일에는 어떤 것이 있을까요?
  ```
  require()는 CommonJS를 사용하는 node.js문이지만 import()는 ES6에서만 사용
  require()는 파일에 들어있는 곳에 남아 있으며 import()는 항상 맨 위로 이동
  require()는 프로그램의 어느 지점에서나 호출 할 수 있지만 import()는 파일의 시작 부분에서만 실행할 수 있다. (그렇지만 import 전용 비동기 문법으로 파일 중간에 모듈 불러오기를 할 수 있다.)
  ```
- node.js에서 ES Modules를 사용하려면 어떻게 해야 할까요? ES Modules 기반의 코드에서 CommonJS 기반의 패키지를 불러오려면 어떻게 해야 할까요? 그 반대는 어떻게 될까요?

  ```
  1. Node.js에서 ES 모듈을 사용하는 첫번째 방법은 파일의 확장자를 js 대신에 mjs를 사용하는 것이다. (프로젝트에서 부분적으로 ES 모듈을 사용할 때 가장 쉽고 빠르게 적용할 수 있는 방법)
  2. Node.js에서 ES 모듈을 사용하는 두번째 방법은 package.json 파일 설정을 통해 전체 파일에 적용하는 것이다. (모든 파일의 확장자를 일일이 바꾸지 않고, 프로젝트 전체에 ES 모듈을 적용하고 싶을 때 적합한 방법)

   default import로 가능. CJS.method1()과 같이 .을 찍어서 이용가능하다.
  ```

## Quest

- 스켈레톤 코드에는 다음과 같은 네 개의 패키지가 있으며, 용도는 다음과 같습니다:
  - `cjs-package`: CommonJS 기반의 패키지입니다. 다른 코드가 이 패키지의 함수와 내용을 참조하게 됩니다.
  - `esm-package`: ES Modules 기반의 패키지입니다. 다른 코드가 이 패키지의 함수와 내용을 참조하게 됩니다.
  - `cjs-my-project`: `cjs-package`와 `esm-package`에 모두 의존하는, CommonJS 기반의 프로젝트입니다.
  - `esm-my-project`: `cjs-package`와 `esm-package`에 모두 의존하는, ES Modules 기반의 프로젝트입니다.
- 각각의 패키지의 `package.json`과 `index.js` 또는 `index.mjs` 파일을 수정하여, 각각의 `*-my-project`들이 `*-package`에 노출된 함수와 클래스를 활용할 수 있도록 만들어 보세요.

## Advanced

- node.js 외의 자바스크립트 런타임에는 어떤 것이 있을까요?
