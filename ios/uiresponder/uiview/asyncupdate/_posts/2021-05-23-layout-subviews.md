---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "layoutSubviews()"
toc: true
toc_sticky: true
toc_label: 목차
tag: "UIView Drawing Cycle"
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
뷰의 크기가 변경될 때마다 이에 대응하여 하위 뷰들의 크기, 위치 변경한다.  
- auto layout을 사용하면 각 뷰의 autoresizingMask프로퍼티를 설정하여 상위 뷰의 크기가 변경되었을 때 어떻게 대응할 지 규칙을 정할 수 있다.
- 뷰의 크기에 변경이 발생하면 우선 하위 뷰들의 autoresizing 동작을 적용하는데, 변경사항을 반영하기 위하여 layoutSubviews()메서드를 호출 한다.(이 메서드 역시 하위 뷰들에서도 연쇄적으로 호출 됨)
- 업데이트 주기에 해당 View와 모든 하위 View를 레이아웃하고 다시그려야한다는 것을 시스템에 알려주는 역할을 한다. 

## 2. 비동기 액티비티
- 메소드가 완료되어 즉시 반환된다.
- 하지만 메인 런 루프 이벤트에 대기된 상태로 지연된다.
- 따라서 레이아웃과 다시 그리는 작업이 실제로 발생하기 까지는 아직 이른 상태이며, 업데이트 주기가 언제일지도 모르는 상태다.

## 3. 주의
- **직접 이 메소드를 호출하면 안된다.**
- 대신 [setNeedsLayout()](/ios/uiresponder/uiview/asyncupdate/setNeedsLayout/) 로 호출하자


출처:  [김종권의 iOS 앱 개발 알아가기 - [iOS - swift] layout subviews 메서드](https://ios-development.tistory.com/195)
