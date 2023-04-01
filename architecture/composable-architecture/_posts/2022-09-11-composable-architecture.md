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

>
SwiftUI, UIKit, and more, and on any Apple platform (iOS, macOS, tvOS, and watchOS).


Composability는 구성요소의 상호 관계를 다루는 시스템 설계 원칙이다. 점점 커지는 시스템은 특정 사용자 요구사항을 만족하기 위해 다양한 조합을 할 수 있는 구성 요소를 제공한다. 작은 단위로 만든 각 제품은 평가하기 쉬워 타 시스템보다 더 신뢰할 수 있다. 또한 독립적으로 구성한 모듈만 독립적으로 배포할 수 있다. 다른 구성 요소와 협력할 수 있으며 구성요소의 종속성 또한 교체 가능하다. 각 모듈은 존재여부를 모를 수 있으나 Protocol로 조합할 수 있으며, request에 대해을 이전 request와 관련 없는 독립으로 처리하며, Managed state를 구성한다.

> [<i class="fas fa-link"></i> Composable Architecture는 한국어 README 도 지원한다.](https://gist.github.com/pilgwon/ea05e2207ab68bdd1f49dff97b293b17){:target="_blank"}

# 앱 로직의 분류
![Image](https://markvillar.com/content/images/2023/01/tca-diagram-swift-and-tips.png)  
## Outside dependency(Effect - Enviroment, Middleware)
### Data save
* Memory Cache
* Binary
* Database
* File

## Business Logic
### Service
* Network
* Bluetooth
* Core Location Service 

### Navigation (Router)
* 화면의 이동
  * Present, Dismiss, Push, Pop

### Coordination(Reducer, Action)
* 각종 layer를 조합해 앱이 사용자를 위해 하는 일

## UI
### 뷰(View)
* UIView
* UIViewController
* SwiftUI

### Presentation
* UI 모델 변환
  * 이미지
  * 색상
  * 폰트



## Managed state
Redux의 state 관리와 동일하게 상태를 읽을 수 있으나 직접 수정 할 수 없다. 극단적인 방법인데, action을 사용해서만 state 를 변경한다.

## SideEffect
비동기 방식의 프로그래밍을 가능한 테스트 가능하게 하고 이해하기 쉬운 방식으로 처리한다. TCA는 SideEffect를 제외하고 모든 처리는 `main thread` 에서 실행 된다. SideEffect는 TCA 내부에서 처리되며, 완료에 대한 피드백을 받으며,  TCA내부에서 `main thread`에서 처리할 수 있도록 업데이트하게 된다.

<!--### Modeling-->
<!--모델링은 현실에 대한 의도적인 추상화로 이해되며, 그 결과 개념화 및 기본 가정 및 제약에 대한 형식적인 사양이 생성된다. 특히 컴퓨터에서 실행 가능한 버전의 구현을 지원하는 데 사용되는 모델에 관심이 있다. 모델링은 개념화를 목표로 하지만 시뮬레이션 문제는 주로 구현에 중점을 둔다. 즉, 모델링은 추상화 수준에 있는 반면 시뮬레이션은 구현 수준에 있다.-->

## Types and Values
### State
모든 객체에는 고유한 상태가 있다. 
* UILabel에 표시하는 중
* 데이터를 처리하기 위한 로딩 중
* Lock 상태 
* UI에 표시되지 않을 수 있는 데이터 등등..


### Action
이벤트에 대한 작업을 시작한다. 데이터의 흐름은 단방향으로 흐르게 되며 Action에서 State를 바로 수정할 수 없다.
* 로그인 작업 수행
* 로그아웃 작업 수행 등등

### (Optional) Enviorment
외부 API와 연결해 환경을 구성한다. 모든 구성요소는 Enviorment가 필요하지 않을 수 있으므로 Optional하다. Dependencies를 구성하고 API를 보유한다.
* LoggedIn Server API
* Google Analytics

### Reducer
값을 반환하여 수행할 수 있는 API 요청과 같이 실행해야 하는 로직과 Effect를 리턴하는 역할도 합니다.
### Store
기능을 실제로 Runtime에 구동합니다. Store가 Reducer와 Effect를 실행할 수 있도록 모든 사용자 Action을 Store로 보내고, UI를 업데이트할 수 있도록 Store의 State 변화를 관찰할 수 있습니다.

## What is State?
data.. and data.. and data..
* Requied Data
* View Data
* Extra Data
* Children Data

```swift
struct State: Equatable {
  // ...
}
```

## What is an Action?
Cases
* User actions
* Actions reponses
* Children actions

```swift
enum Action: Equatable {
  // ...
}
```

## What is an Environment?
Dependencies and Effects
* Main Scheduler Queue
* Mockable dependencies / closures
* Effect is something that deals with the "outside world"

```swift
struct Environment {
  // ...
}
```

## What is a Reducer?
* Defines the evolution of state for any given action
* Uses State, Action, and Environment
* Testable business logic

```swift
Reducer<State, Action, Environment>
```


## 출처
https://ko.redux.js.org/
https://github.com/pointfreeco/swift-composable-architecture
