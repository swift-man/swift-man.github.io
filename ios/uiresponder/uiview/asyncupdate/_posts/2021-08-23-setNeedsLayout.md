---
sidebar:
  title: "iOS"
  nav: sidebar-ios
title: "setNeedsLayout()"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : 업데이트 주기에 해당 View와 모든 하위 View를 레이아웃하고 다시그려야한다는 것으 시스템에 알려주는 역할을 합니다.
---
[iOS](/ios/) / [UIResponder](/ios/uiresponder/) / [UIView](/ios/uiresponder/uiview/)  / [비동기 업데이트](/ios/uiresponder/uiview/asyncupdate/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
- 업데이트 주기에 해당 View와 모든 하위 View를 레이아웃하고 다시그려야한다는 것으 시스템에 알려주는 역할을 합니다.

## 2. layoutSubViews()
* **setNeedsLayout() 을 호출하면 내부적으로 layoutSubViews() 을 호출**해서 업데이트 주기에 레이아웃을 알아서 업데이트 해준다.

출처: [ZeddiOS](https://zeddios.tistory.com/359)
