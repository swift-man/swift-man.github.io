---
sidebar:
  title: "Swift"
  nav: sidebar-swift
  icon: "fab fa-swift"
title: "[SwiftUI] 선언적 구문과 데이터 주도"
toc: true
toc_sticky: true
toc_label: 목차
tag: "SwiftUI"
depth:
  - title: "Swift"
    url: /swift/
    icon: "fab fa-swift"
  - title: "SwiftUI"
    url: /swift/swiftui/
    icon: "far fa-folder-open"
---
Swift의 장점은 선언적 구분과 데이터 주도 기반에서 비롯된다.
SwiftUI 는 UIKit을 구현하는 방법과 완전히 다른 선언적 구문이 도입 되었다.

> UIKit의 구현 방법<br/>
인터페이스 빌드를 사용하여 사용자 인터페이스 레이아웃을 설계하고 필요한 동작을 구현하는 방식이다.  
시간이 지남에 따라 Data State가 변한다면, User Interface를 Data State를 반영하도록 하는 코드를 작성해야 한다.

## SwiftUI의 구성 요소
### Component
SwiftUI는 Component 중심으로 설계가 가능하고, Component 중심의 화면 설계로 UI재사용에 더 좋은 방향으로 캡슐화 및 설계가 가능하다.

### Layout Manager
Layout Manager는 기본적인 컴포넌트를 선언하고 포함한다. 종류는 VStack, HStack, Form, List 등 이 있다.

### 수정자(Modifier)
Component의 attribute를 선언하는 것을 수정자라 한다. 종류는 forgraoundColor, text, tapGesture event call method 등 이 있다.

## SwiftUI의 구현 방법
### 선언적 구문(declarative syntax)
레이아웃이 실제로 구축되는 방식의 복잡함에 대해 UserInterface가 어떤 모양이어야 하는지 선언하는 방식으로 레이아웃을 생성할 수 있다.  
이는 단순하면서도 직관적인 구문을 사용하여 화면을 기술할 수 있게 해준다.  


### 데이터 주도(data driven)
App Data와 UserInterface 및 Logic 사이의 관계를 Binding 하는 방법으로 복잡도를 해결하며 이는 데이터 주도적이다.

Data Model은 구독(subscribe)할 수 있는 데이터 변수를 게시(publish)하게 된다. 이러한 방법을 통해 Data가 변경되었다는 사실을 모든 구독자에게 자동으로 알릴 수 있다. 이 방법으로 UserInterface Component와 Data Model의 Binding을 통해 추가적인 코드를 작성하지 않아도 모든 Data의 변경 사항을 UserInterface에 자동으로 반영한다.
