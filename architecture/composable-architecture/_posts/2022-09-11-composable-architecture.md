---
sidebar:
  title: "Architecture"
  nav: sidebar-architecture
  icon: "fas fa-sitemap"
title: "Composable Architecture"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Composable Architecture"
depth:
  - title: "Architecture"
    url: /architecture/
    icon: "fas fa-sitemap"
  - title: "Composable Architecture"
    url: /architecture/composable-architecture/
    icon: "far fa-folder-open"
---
오늘날 [<i class="fas fa-link"></i>Redux](https://github.com/reduxjs/redux){:target="_blank"}기반 [<i class="fas fa-link"></i>MVI 디자인패턴](https://amsterdamstandard.com/en/post/modern-android-architecture-with-mvi-design-pattern){:target="_blank"}은 매우 널리 쓰인다.  

![Image](https://images.velog.io/images/wooder2050/post/22581891-9ac2-40c9-bfba-bf9b7dfe6b67/redux.jpg)  

[<i class="fas fa-link"></i> UIKit](https://developer.apple.com/documentation/uikit){:target="_blank"}기반 Redux 오픈소스로 [<i class="fas fa-link"></i> ReactorKit](https://github.com/ReactorKit/ReactorKit){:target="_blank"}이 대표적이며, 필자는 MVVM 디자인 패턴과 함께 현업에서 자주 사용하고 있다. Redux기반 아키텍처는 개발자들이 매우 선호하는 아키텍처라 협업하기도 좋고, 코드를 이해하기 쉬워지며, 코드가 들어갈 자리들이 명확해 매우 좋은 아키텍처 중 하나이다. 

![Image](https://i0.wp.com/hanamon.kr/wp-content/uploads/2021/07/%E1%84%85%E1%85%B5%E1%84%83%E1%85%A5%E1%86%A8%E1%84%89%E1%85%B3-%E1%84%89%E1%85%A1%E1%86%BC%E1%84%90%E1%85%A2%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5-%E1%84%83%E1%85%A1%E1%86%AB%E1%84%80%E1%85%A8.png?resize=919%2C492&ssl=1)  
이번에 공부한 Redux 기반 아키텍처 [<i class="fas fa-link"></i> Composable Architecture](https://github.com/pointfreeco/swift-composable-architecture){:target="_blank"}는 줄여 TCA라고 한다. 필자의 첫 느낌은 ReactorKit보다 유연한 면이 많이 보였다. 각 구성요소를 만들고 조립에 중점을 두어 재사용에 용이하며 UIKit과 종속성이 없어 SwiftUI에서도 사용이 매우 편리한 아키텍처로 생각되었다. 일관성 면에서는 ReactorKit과 비슷한 장점을 가지고 있고, ReactorKit의 코드베이스로 좋은 코드 일관성을 가지고 프로젝트를 관리해 왔기 때문에 거부감 없이 친근하게 느껴졌다. 코드에 일관성이 있다는 것은 많은 기능들은 이해하기 쉽게 만들기 때문에 필자는 이러한 방식을 매우 선호한다.

Composability는 구성요소의 상호 관계를 다루는 시스템 설계 원칙이다. 점점 커지는 시스템은 특정 사용자 요구사항을 만족하기 위해 다양한 조합을 할 수 있는 구성 요소를 제공한다. 작은 단위로 만든 각 제품은 평가하기 쉬워 타 시스템보다 더 신뢰할 수 있다. 또한 독립적으로 구성한 모듈만 독립적으로 배포할 수 있다. 다른 구성 요소와 협력할 수 있으며 구성요소의 종속성 또한 교체 가능하다. request에 대해을 이전 request와 관련 없는 독립으로 처리하며, Managed state를 구성한다.

<!--### Modeling-->
<!--모델링은 현실에 대한 의도적인 추상화로 이해되며, 그 결과 개념화 및 기본 가정 및 제약에 대한 형식적인 사양이 생성된다. 특히 컴퓨터에서 실행 가능한 버전의 구현을 지원하는 데 사용되는 모델에 관심이 있다. 모델링은 개념화를 목표로 하지만 시뮬레이션 문제는 주로 구현에 중점을 둔다. 즉, 모델링은 추상화 수준에 있는 반면 시뮬레이션은 구현 수준에 있다.-->

## 출처
https://ko.redux.js.org/