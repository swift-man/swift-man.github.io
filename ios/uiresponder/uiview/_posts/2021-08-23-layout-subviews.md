---
sidebar:
  title: "iOS"
  nav: sidebar-ios
title: "layoutSubviews()"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : 뷰의 크기가 변경될 때마다 이에 대응하여 하위 뷰들의 크기&위치 변경
---
[iOS](/ios/) / [UIResponder](/uiresponder/) / [UIView](/uiview/)  /**{{ page.title }}**
{: .notice--warning}

## 1. 개요

- 뷰의 크기가 변경될 때마다 이에 대응하여 하위 뷰들의 크기, 위치 변경
- auto layout을 사용하면 각 뷰의 autoresizingMask프로퍼티를 설정하여 상위 뷰의 크기가 변경되었을 때 어떻게 대응할 지 규칙을 정할 수 있음
- 뷰의 크기에 변경이 발생하면 우선 하위 뷰들의 autoresizing 동작을 적용하는데, 변경사항을 반영하기 위하여 layoutSubviews()메서드를 호출 (이 메서드 역시 하위 뷰들에서도 연쇄적으로 호출 됨)

- 출처:  [김종권의 iOS 앱 개발 알아가기 - [iOS - swift] layout subviews 메서드](https://ios-development.tistory.com/195)
