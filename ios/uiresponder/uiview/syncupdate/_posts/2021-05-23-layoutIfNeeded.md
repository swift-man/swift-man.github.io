---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "layoutIfNeeded()"
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
  - title: "동기 업데이트"
    url: /ios/uiresponder/uiview/syncupdate/
    icon: "far fa-folder-open"
---
뷰의 크기가 변경될 때마다 이에 대응하여 하위 뷰들의 크기&위치 변경한다.  
이 메소드는 setNeedsLayout과 같이 수동으로 layoutSubviews를 예약하는 행위이지만 해당 예약을 바로 실행시킨다.

```swift
// view 변경 코드
view.setNeedsLayout() // main run loop 에 예약
view.layoutIfNeeded() // View의 값이 재계산되고 화면에 반영

/*
setNeedsLayout이 예약한 layoutSubviews() 메소드는 
update cycle에서 반영해야할 변경된 값이 존재하지 않기 때문에 호출되지 않음
*/
```

## 2. 애니메이션에서 사용
```swift
// 애니메이션 전에 뷰를 즉시 반영시키면 애니메이션이 잘 동작한다.
view.layoutIfNeeded() 
UIView.animate(....)
```

```swift
// View의 값이 변경되는 것이 아니라 추후 update cycle에서 값이 반영되므로 
// 값의 변경은 이루어지지만 애니매이션 효과는 볼 수 없다.
view.setNeedsLayout() 
UIView.animate(....)
```

## 3. setNeedsLayout과 layoutIfNeeded의 차이
- setNeedsLayout : 비동기
- layoutIfNeeded : 동기

- 출처:  [이동건의 이유있는 코드 - [ios] setNeedsLayout vs layoutIfNeeded](https://baked-corn.tistory.com/105)
