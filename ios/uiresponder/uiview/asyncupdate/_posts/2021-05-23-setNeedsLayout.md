---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "setNeedsLayout()"
toc: true
toc_sticky: true
toc_label: 목차
group: "UIResponder"
depth: 
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "UIResponder"
    url: /ios/uiresponder/
    icon: "far fa-folder-open"
  - title: "UIView"
    url: /ios/uiresponder/uiview/
    icon: "far fa-folder-open"
  - title: "비동기 업데이트"
    url: /ios/uiresponder/uiview/asyncupdate/
    icon: "far fa-folder-open"
---
업데이트 주기에 해당 View와 모든 하위 View를 레이아웃 및 draw 하도록 시스템에 알려주는 역할을 한다.

## 2. layoutSubViews()
* **setNeedsLayout() 을 호출하면 내부적으로 layoutSubViews() 을 호출**해서 업데이트 주기에 레이아웃을 알아서 업데이트 해준다.

출처: [ZeddiOS](https://zeddios.tistory.com/359)
