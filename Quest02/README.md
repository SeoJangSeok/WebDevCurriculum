# Quest 02. CSS의 기초와 응용

## Introduction

- CSS는 Cascading StyleSheet의 약자입니다. 웹브라우저에 표시되는 HTML 문서의 스타일을 지정하는 (거의) 유일하지만 다루기 쉽지 않은 언어입니다. 이번 퀘스트를 통해 CSS의 기초적인 레이아웃 작성법을 알아볼 예정입니다.

## Topics

- CSS의 기초 문법과 적용 방법
  - Inline, `<style>`, `<link rel="stylesheet" href="...">`
- CSS 규칙의 우선순위
- 박스 모델과 레이아웃 요소
  - 박스 모델: `width`, `height`, `margin`, `padding`, `border`, `box-sizing`
  - `position`, `left`, `top`, `display`
  - CSS Flexbox와 Grid
- CSS 표준의 역사
- 브라우저별 Developer tools

## Resources

- [MDN - CSS](https://developer.mozilla.org/ko/docs/Web/CSS)
- [Centering in CSS: A Complete Guide](https://css-tricks.com/centering-css-complete-guide/)
- [A complete guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [그리드 레이아웃과 다른 레이아웃 방법과의 관계](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Grid_Layout/%EA%B7%B8%EB%A6%AC%EB%93%9C_%EB%A0%88%EC%9D%B4%EC%95%84%EC%9B%83%EA%B3%BC_%EB%8B%A4%EB%A5%B8_%EB%A0%88%EC%9D%B4%EC%95%84%EC%9B%83_%EB%B0%A9%EB%B2%95%EA%B3%BC%EC%9D%98_%EA%B4%80%EA%B3%84)

## Checklist

- CSS를 HTML에 적용하는 세 가지 방법은 무엇일까요?

  ```
  1. HTML 요소 내에 style 속성 사용.
    <h1 style="color: red;">Red Title</h1>
    <p style="font-size: 10px;">10px Text</p>
  2. head 영역에 style 요소 사용.
    <head>
      <style>
        h1 {color: blue;}
        p {color: yellow;}
      </style>
    </head>
  3. <link>요소를 사용하여 외부 CSS파일을 연결.
    <head>
      <link rel="stylesheet" href="styles.css" type="text/css">
    </head>
  ```

  - 세 가지 방법 각각의 장단점은 무엇일까요?

    > 외부 스타일 시트 연결은 가장 일반적이고 효율적인 방법이다. 하나의 CSS 파일을 다수의 웹페이지에 연결할 수 있고, 이를 통해 동일한 CSS를 적용하고 이를 효율적으로 관리할 수 있다.

    > head 영역에 style 요소 사용은 외부 CSS 파일을 수정할 수 없는 환경에서 활용될 수 있다. 페이지 수가 늘어나면 점차 비효율적이게 된다. 하나의 속성을 수정하려면 여러 웹페이지의 <head>에서 속성을 변경해야 하는 번거로움이 있다.

    > HTML 요소 내에 style 속성 사용 방법은 CSS 유지 관리에 가장 비효율적인 방법이며, 문서에 CSS 속성들이 부여 되어 있을 경우 코드를 읽기 어렵다.

- CSS 규칙의 우선순위는 어떻게 결정될까요?

  ```
  1. 속성 값 뒤에 !important 를 붙인 속성
  2. HTML에서 style을 직접 지정한 속성
  3. #id 로 지정한 속성
  4. .클래스, :추상클래스 로 지정한 속성
  5. 태그이름 으로 지정한 속성
  6. 상위 객체에 의해 상속된 속성

  +) 같은 우선순위에 있는 경우, 부모-자식 관계가 많은 경우가 우선되며, 모든 설정이 같은 경우 나중에 선언한 것이 우선되어 적용된다.
  ```

- CSS의 박스모델은 무엇일까요? 박스가 화면에서 차지하는 크기는 어떻게 결정될까요?

  ```
  문서의 레이아웃을 계산할 때, 브라우저의 렌더링 엔진은 표준 CSS 기본 박스 모델에 따라 각각의 요소를 사각형 박스로 표현한다.
  CSS는 박스의 크기, 위치, 속성(색, 배경, 테두리 모양 등)을 결정한다.

  하나의 박스는 네 부분(영역)으로 이루어진다.
  각 영역을 콘텐츠 영역, 안쪽 여백(패딩) 영역, 테두리 영역, 그리고 바깥 여백(마진) 영역이라고 부른다.
  - 콘텐츠 영역
    콘텐츠 경계(content edge)가 감싼 영역으로, 글이나 이미지, 비디오 등 요소의 실제 내용을 포함한다.
    콘텐츠 영역의 크기는 콘텐츠 너비(콘텐츠 박스 너비)와 콘텐츠 높이(콘텐츠 박스 높이)이다. 배경색과 배경 이미지를 가지고 있기도 한다.
  - 안쪽 여백 영역(패딩 영역, padding area)
    안쪽 여백 경계(padding edge)가 감싼 영역으로, 콘텐츠 영역을 요소의 안쪽 여백까지 포함하는 크기로 확장한다.
    영역의 크기는 안쪽 여백 박스 너비와 안쪽 여백 박스 높이이다.
  - 테두리 영역(border area)
    테두리 경계(border edge)가 감싼 영역으로, 안쪽 여백 영역을 요소의 테두리까지 포함하는 크기로 확장한다.
    영역의 크기는 테두리 박스 너비와 테두리 박스 높이이다.
  - 바깥 여백 영역(margin area)
    바깥 여백 경계(margin edge)가 감싼 영역으로, 테두리 요소를 확장해 요소와 인근 요소 사이의 빈 공간까지 포함하도록 만든다.
    영역의 크기는 바깥 여백 박스 너비와 바깥 여백 박스 높이이다.
  ```

- `float` 속성은 왜 좋지 않을까요?
  ```
  `float` 속성 : 요소의 배치를 제어할 때 사용하는 속성.
  `float` 속성의 문제점 : 모든 자식 요소에 float 속성을 적용하면, 부모 요소는 해당 자식 요소가 존재하지 않는 것으로 판단하여, (부모가) 높이를 인식하지 못하는 문제가 발생한다.
  ```
- Flexbox(Flexible box)와 CSS Grid의 차이와 장단점은 무엇일까요?
  ```
  둘의 차이는 Flex는 1차원으로 수평, 수직 영역 중 하나의 방향으로만 레이아웃을 나눌 수 있다. Grid는 2차원으로 수평, 수직을 동시에 영역을 나눌 수 있다.
  ```
- CSS의 비슷한 요소들을 어떤 식으로 정리할 수 있을까요?
  > , 를 이용해서 그룹화 하고 일괄 적용할 수 있다.

## Quest

- Quest 01에서 만들었던 HTML을 바탕으로, [이 그림](screen.png)의 레이아웃과 CSS를 최대한 비슷하게 흉내내 보세요. 꼭 완벽히 정확할 필요는 없으나 align 등의 속성은 일치해야 합니다.
- **주의사항: 되도록이면 원래 페이지의 CSS를 참고하지 말고 아무것도 없는 백지에서 시작해 보도록 노력해 보세요!**

## Advanced

- 왜 CSS는 어려울까요?
- CSS의 어려움을 극복하기 위해 어떤 방법들이 제시되고 나왔을까요?
- CSS가 브라우저에 의해 해석되고 적용되기까지 내부적으로 어떤 과정을 거칠까요?
- 웹 폰트의 경우에는 브라우저 엔진 별로 어떤 과정을 통해 렌더링 될까요?
