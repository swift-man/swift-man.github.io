---
sidebar:
  title: "iOS"
  nav: sidebar-ios
title: "layoutIfNeeded()"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : 뷰의 크기가 변경될 때마다 이에 대응하여 하위 뷰들의 크기&위치 변경
---
[iOS](/ios/) / [UIResponder](/ios/uiresponder/) / [UIView](/ios/uiresponder/uiview/)  / [동기 업데이트](/ios/uiresponder/uiview/syncupdate/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요

이 메소드는 setNeedsLayout과 같이 수동으로 layoutSubviews를 예약하는 행위이지만 해당 예약을 바로 실행시키는 동기적으로 작동하는 메소드입니다. update cycle이 올 때까지 기다려 layoutSubviews를 호출시키는 것이 아니라 그 즉시 layoutSubviews를 발동시키는 메소드입니다.



만일 main run loop에서 하나의 View가 setNeedsLayout을 호출하고 그 다음 layoutIfNeeded를 호출한다면 layoutIfNeeded는 그 즉시 View의 값이 재계산되고 화면에 반영하기 때문에 setNeedsLayout이 예약한 layoutSubviews 메소드는 update cycle에서 반영해야할 변경된 값이 존재하지 않기 때문에 호출되지 않습니다.



이러한 동작 원리로 layoutIfNeeded는 그 즉시 값이 변경되어야 하는 애니매이션에서 많이 사용됩니다. 만일 setNeedsLayout을 사용한다면 애니매이션 블록에서 그 즉시 View의 값이 변경되는 것이 아니라 추후 update cycle에서 값이 반영되므로 값의 변경은 이루어지지만 애니매이션 효과는 볼 수 없는 것입니다.

setNeedsLayout과 layoutIfNeeded의 차이점은 동기적으로 동작하느냐 비동기적으로 동작하느냐의 차이입니다.

- 출처:  [이동건의 이유있는 코드 - [ios] setNeedsLayout vs layoutIfNeeded](https://baked-corn.tistory.com/105)
