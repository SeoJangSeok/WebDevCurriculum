# Quest 17-B. 배포 파이프라인

## Introduction

- 이번 퀘스트에서는 CI/CD 파이프라인이 왜 필요한지, 어떻게 구축할 수 있는지 등에 대해 다룹니다.

## Topics

- Continuous Integration
- Continuous Delivery
- AWS Codebuild

## Resources

- [AWS: Continuous Integration](https://aws.amazon.com/ko/devops/continuous-integration/)
- [AWS: Continuous Delivery](https://aws.amazon.com/ko/devops/continuous-delivery/)
- [AWS Codebuild](https://aws.amazon.com/ko/codebuild/getting-started/)

## Checklist

- CI/CD는 무엇일까요? CI/CD 시스템을 구축하면 어떤 장점이 있을까요?

```
CI/CD는 애플리케이션 개발 단계부터 배포 때까지의 모든 단계를 자동화를 통해서 좀 더 효율적이고 빠르게 사용자에게 빈번히 배포할 수 있는 것을 말한다.

CI : 지속적 통합이라는 뜻으로 개발을 진행하면서도 품질을 관리할 수 있도록 하는 것으로 여러 명이 하나의 코드에 대해서 수정을 진행해도 지속적으로 통합하면서 관리할 수 있음을 의미한다.

CD : 지속적 배포로 소프트웨어가 항상 신뢰 가능한 수준에서 배포될 수 있도록 관리하자는 개념으로 지속적 제공(Continuous Delivery)로 사용되기도 한다.
```

> 장점

```
-코드에서 발생하는 버그 발견, 코드 테스트가 자동화되므로 배포 간격이 짧아짐
-각 개인이 코드를 병합할 때마다 자동으로 테스트를 거치므로, 버그 발생 가능성이 낮아짐
-코드 배포 및 체크가 자동화되므로, 최종 코드 확인에 필요한 시간이 단축됨
-매 작업마다 테스트가 진행되므로 버그를 초기에 발견할 수 있으며 이는 버그의 빠른 해결에 도움이 됨
```

- CI 시스템인 Travis CI, Jenkins, Circle CI, Github Actions, AWS Codebuild 의 차이점과 장단점은 무엇일까요?
  > Travis CI

```
Travis CI는 github에서 제공하는 무료 CI 서비스이다. Jenkins의 경우 설치하여 사용해야 하지만 Travis CI는 오픈소스 웹 서비스이기 때문에 오픈 소스인 경우 무료로 사용이 가능하다.
```

> Jenkins

```
CI system에서 가장 많이 활용하는 open source - CI server이다.

코드의 build, test, deploy를 지원해주는 tool이다.
```

> Circle CI

```
CI/CD 플랫폼을 제공하는 소프트웨어이다.

소프트웨어를 활용하여 CI/CD 과정을 자동화할 수 있도록 지원한다.
```

> Github Actions

```
GitHub Actions는 빌드, 테스트 및 배포 파이프라인을 자동화할 수 있는 CI/CD 플랫폼이다.
repository에 대한 모든 pull request를 빌드 및 테스트하는 workflow를 생성하거나 병합된 pull request를 프로덕션에 배포할 수 있다.
```

> AWS Codebuild

```
AWS에서 제공하는 툴, 완전히 managed된 build service를 제공한다.

컴파일, 실행, 프로덕션까지 수행해주기 때문에 AWS Codebuild를 채택하면 별도의 build server를 관리하고 모니터링할 필요가 없다.
```

## Quest

- AWS Codebuild를 이용하여, 특정 브랜치에 푸시를 하면 린트와 테스트를 거쳐 서버 이미지를 빌드한 뒤, 직전 퀘스트의 EC2 인스턴스에 배포되는 시스템을 만들어 보세요.

## Advanced

- 빅테크 회사들이 코드를 빌드하고 배포하는 시스템은 어떻게 설계되고 운영되고 있을까요?
