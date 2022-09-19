---
sidebar:
  title: "Architecture"
  nav: sidebar-architecture
  icon: "fas fa-sitemap"
title: "[iOS] 앱 모듈화의 필요성"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Module"
depth:
  - title: "Architecture"
    url: /architecture/
    icon: "fas fa-sitemap"
  - title: "Module"
    url: /architecture/module/
    icon: "far fa-folder-open"
---
IT 소프트웨어 산업은 계속 성장하고 있다. 아마도 많은 서비스들은 점점 더 커질 것을 예상하고 기대할 것이다. Backend에서는 [<i class="fas fa-link"></i> 마이크로서비스 아키텍처](https://cloud.google.com/learn/what-is-microservices-architecture?hl=ko){:target="_blank"}로 대규모 애플리케이션을 작은 단위로 분리해 독립적인 구성요소로 구분해 개발하는 방법이 있다.  

## 모바일 애플리케이션도 이러한 모듈화가 필요한가?
의문이 들 수 있다. '점점 커지는 기능과 코드들을 어떻게 하면 효율적으로 관리할 수 있을까'에 대한 고민을 하는 순간이 온다.  클린 아키텍처나 Redux 아키텍처 등 이런 고민에서 시작한 아키텍처이고, 모듈화 또한 유지보수를 더 용이하고 효율적으로 할 수 있는 방법 중 하나이다. 앱 내부도 기능 단위, 화면 단위로 작게 나눌 수 있는 포인트가 있으며 하나의 기능에 집중하여 개발한다면 유지보수에 큰 도움이 된다. 

모듈을 작은 단위로 만들면 더욱 여러 가지 이점이 있다. 이것을 살펴보자.

## Composition 
책임단위를 명확하게 나눠 모듈단위로 분리하고, 이것을 조립해 제품을 만든다. 하나의 Target(애플리케이션 모듈)만 있는 앱을 생각해보자. 이 앱은 논리적으로 역할이 나뉘어 있을지 몰라도 물리적으로 나눠져 있지 않아 스파게티처럼 코드가 꼬일 가능성이 매우 높다. 개발자는 코딩하면서 애플리케이션의 모든 구조를 예상할 수 없기 때문이다.  

서비스의 성장 또는 시간이 지남에 따라 기능은 점점 많아지고, 요구사항은 점점 복잡해진다. 이를 해결하기 위해 책임을 나누고 역할을 분리한다. 그리고 조립해 사용하도록 코드를 만들면 더 좋은 품질의 프로젝트로 거듭 날 수 있다.

## 최적화와 빌드 속도 향상
### Xcode New Build System
Xcode9부터 `Xcode New Build System`이 도입되었다. 빌드 시스템 전체 빌드 시간을 줄이는 것이 목표인 시스템이며 Xcode10부터 기본 선택이다.  

![Image](https://drive.google.com/uc?export=view&id=1_Rt-Bpvg8QKsdziwCTScvFpCccc-hX7U)  

XCBuild로 부르며 확인 New Build System 적용 여부는 Xcode 아래의 메뉴에서 확인 가능하다.  
```
File - Workspace Setting... - New Build System
```

### Parallelizing Build
Xcode 10부터 Parallelizing Build로 모듈 별 병렬로 빌드를 진행한다. 이로 인해 모듈화를 하면 빌드 속도에 이점이 있다.

Xcodes Targets and Dependencies
* iOS App
* Framework
* Unit Tests

아래 그림과 같이 모듈별 가장 의존성이 적은 순서대로 트리구조를 형성 및 먼저 빌드하며 프로젝트 최적화로 인해 상황에 따라 빌드 성능이 3배까지 향상 가능하다.
![Image](https://drive.google.com/uc?export=view&id=1KY5Fsk24w5U9ToKb0EU6ciszypCsW8eX)  

따라 개발자는 이 효율성을 사용하기 위해 의존성을 최소화하며 프로젝트를 구성하는 것이 매우 좋다. 코드 베이스 분리 또는 모듈화하고 프로젝트의 모든 대상을 실행 순서대로 분리하여 빌드 프로세스의 내부적 의존성을 재배치하는 시간을 절약하는데 도움이 된다.

![Image](https://drive.google.com/uc?export=view&id=1GF7yFiTCzf-18dCG5Gy9CRW57nwarp82)  

의존성은 컴파일러가 가능한 최선의 방법으로 빌드를 할 수 있는 중요한 역할을 한다.

### Link Frameworks Automacticallty
`Link Frameworks Automacticallty`를 통해 프로젝트의 추가된 모든 프레임워크가 빌드 중 컴파일러에 의해 자동으로 링크가 된다. 

![Image](https://drive.google.com/uc?export=view&id=14m5ISaHMCJF4hiE9pzSXrpBVTVgaTZ2X)  

Default 설정은 YES이다.  

Application Target에서 import를 누락하더라도 알아서 Link 하여 빌드해주어 이 설정은 매우 유용하다. 다만 Auto Link는 빌드 속도에 영향을 미친다. 오히려 모듈화를 통해 Framework를 생성한다면 더 엄격하게 import를 검사하기 때문에 더 빠르게 빌드되는 프로젝트를 구축을 할 수 있다.

![Image](https://drive.google.com/uc?export=view&id=1unI26fBXgTaOkdMXWQabcbFDZBez0PAD)  
자동으로 잘 되더라도 Link Frameworks Automatically에 의존하지 않고 수동으로 연결해주는 것이 가장 좋다.


## 접근제한자


## 작은 책임 단위
모듈화를 시작하게 되면 프로젝트를 모듈화하고 파고들수록 분해 가능한 것들을 계속 찾게 된다. 분해요소는 기능, 모듈, class 단위에서 어떻게 책임을 가져갈 것인가에 대한 고민을 하게 되고 "단일 책임의 원칙"을 기반하여 설계한다. 이는 매우 프로젝트에 대한 몰입도를 제공하며 프로젝트를 점점 더 유연하고 조립 가능하도록 설계할 수 있다. 결국 지속적인 분해와 조립은 이해하기 쉬운 작은 요소들로 구성되기 때문에 유지보수가 매우 쉬워지고, 원하는 코드를 찾기 쉬워진다. 프로그램은 점점 진화한다. 많은 비즈니스, 많은 화면, 많은 기능들로 인한 비대함은 복잡해져 가는 프로그램을 단순화할 수 있는 좋은 방법이다.
![Image](https://drive.google.com/uc?export=view&id=1xDRFh6L0xLnJMODMAHK9FMSiO70hRSSt)  

## 모듈 별 테스트
