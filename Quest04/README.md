# Quest 04. OOP의 기본

## Introduction

- 이번 퀘스트에서는 바닐라 자바스크립트의 객체지향 프로그래밍에 대해 알아볼 예정입니다.

## Topics

- 객체지향 프로그래밍
  - 프로토타입 기반 객체지향 프로그래밍
  - 자바스크립트 클래스
    - 생성자
    - 멤버 함수
    - 멤버 변수
  - 정보의 은폐
  - 다형성
- 코드의 재사용

## Resources

- [MDN - Classes](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Classes)
- [MDN - Inheritance and the prototype chain](https://developer.mozilla.org/ko/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
- [MDN - Inheritance](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Inheritance)
- [Polymorphism](https://medium.com/@viktor.kukurba/object-oriented-programming-in-javascript-3-polymorphism-fb564c9f1ce8)
- [Class Composition](https://alligator.io/js/class-composition/)
- [Inheritance vs Composition](https://woowacourse.github.io/javable/post/2020-05-18-inheritance-vs-composition/)

## Checklist

- 객체지향 프로그래밍은 무엇일까요?
  ```
  객체 지향 프로그래밍은 프로그램 구현에 필요한 객체를 파악하고 각각의 객체들의 역할이 무엇인지를 정의하여 객체들 간의 상호작용을 통해 프로그램을 만드는 것을 말한다.
  ```
  - `#`로 시작하는 프라이빗 필드는 왜 필요한 것일까요? 정보를 은폐
    (encapsulation)하면 어떤 장점이 있을까요?
    ```
    자바스크립트의 프라이빗 필드는 외부에서 클래스로 접근이 불가능하고 인스턴스로도 접근이 불가능하다. 해당하는 클래스 안에서만 접근할 수 있다.
    데이터의 무결성을 보장할 수 있다.
    ```
  - 다형성이란 무엇인가요? 다형성은 어떻게 코드 구조의 정리를 도와주나요?
    ```
    다형성(polymorphism)은 특정 기능을 선언(설계)부분과 구현(동작)부분으로 분리한 후 구현부분을 다양한 방법으로 만들어 선택해서 사용할 수 있게 하는 기능이다. 선언부분은 인터페이스라고도 한다.
    ```
  - 상속이란 무엇인가요? 상속을 할 때의 장점과 단점은 무엇인가요?
    ```
    상속 : 객체지향 프로그래밍의 핵심 개념으로 어떤 객체의 프로퍼티 또는 메서드를 다른 객체가 상속받아 그대로 사용할 수 있는 것을 말한다.
    장점 : 상속을 통해 클래스를 구현하다 보면 적은 양의 코드로 새로운 클래스를 작성할 수 있고 코드를 공통적으로 관리할 수 있어서 코드 추가나 변경이 편하다. 이런 특징은 코드의 재사용성을 높이고, 중복을 제거해서 프로그래밍 생산성과 유지보수에 크게 기여한다.
    단점 : 상속구조가 복잡해지면 상위클래스의 변화가 하위 클래스에 주는 영향을 예측하기 힘들다. 적절하지 못한 상속을 사용하면 의도했던 것과 다르게 동작한다.
    ```
  - OOP의 합성(Composition)이란 무엇인가요? 합성이 상속에 비해 가지는 장점은 무엇일까요?
    ```
    합성은 중복되는 로직들을 갖는 객체를 구현하고, 이 객체를 주입받아 중복 로직을 호출함으로써 퍼블릭 인터페이스를 재사용하는 방법이다.
    장점 : 합성을 이용하면 객체의 내부는 공개되지 않고 인터페이스를 통해 코드를 재사용하기 때문에 구현에 대한 의존성을 인터페이스에 대한 의존성으로 변경하여 결합도를 낮출 수 있다.
    ```
- 자바스크립트의 클래스는 어떻게 정의할까요?
  ```
  class 선언을 이용한다.
  예) $ class 클래스이름 {}
  ```
  - 프로토타입 기반의 객체지향 프로그래밍은 무엇일까요?
    ```
    class가 없고 객체를 원형(prototype)으로 하여 복제의 과정을 통해 객체의 동작 방식을 다시 사용할 수 있다.
    ```
  - 자바스크립트의 클래스는 이전의 프로토타입 기반의 객체지향 구현과 어떤 관계를 가지고 있나요?
    ```
    class가 없던 Javascript는 객체를 생성할 때 별도의 내부 생성자없이 바로 객체를 생성하였고, 이에 따른 속성이나 행동 값들을 부여해주었다.
    ES6이후 생긴 class에서는 constructor 생성자를 통해 정의해줄 수 있고, 외부 생성자인 new를 통해 class를 생성하거나 상속받을 수 있다.
    ```

## Quest

- 웹 상에서 동작하는 간단한 바탕화면 시스템을 만들 예정입니다.
- 요구사항은 다음과 같습니다:
  - 아이콘은 폴더와 일반 아이콘, 두 가지의 종류가 있습니다.
  - 아이콘들을 드래그를 통해 움직일 수 있어야 합니다.
  - 폴더 아이콘은 더블클릭하면 해당 폴더가 창으로 열리며, 열린 폴더의 창 역시 드래그를 통해 움직일 수 있어야 합니다.
  - 바탕화면의 생성자를 통해 처음에 생겨날 아이콘과 폴더의 개수를 받을 수 있습니다.
  - 여러 개의 바탕화면을 각각 다른 DOM 엘리먼트에서 동시에 운영할 수 있습니다.
  - Drag & Drop API를 사용하지 말고, 실제 마우스 이벤트(mouseover, mousedown, mouseout 등)를 사용하여 구현해 보세요!

## Advanced

- 객체지향의 역사는 어떻게 될까요?
- Smalltalk, Java, Go, Kotlin 등의 언어들로 넘어오면서 객체지향 패러다임 측면에서 어떤 발전이 있었을까요?
