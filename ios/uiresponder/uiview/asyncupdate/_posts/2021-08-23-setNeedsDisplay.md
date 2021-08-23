---
sidebar:
  title: "iOS"
  nav: sidebar-ios
title: "setNeedsDisplay()"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : next drawing cycle 동안 View를 업데이트해야 함을 시스템에 알린다.
---
[iOS](/ios/) / [UIResponder](/ios/uiresponder/) / [UIView](/ios/uiresponder/uiview/)  / [비동기 업데이트](/ios/uiresponder/uiview/asyncupdate/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
setNeedsDisplay()메소드 또는 setNeedsDisplay (_ :)를 사용하여 View의 내용을 다시 그려야 함을 시스템에 알릴 수 있습니다.

이 메소드는 요청을 기록하고, **즉시 리턴합**니다. View는 **다음 드로잉 사이클까지 실제로 다시 그려지지는 않습니다.** 이 시점에서 모든 무효화된 View가 업데이트됩니다.

---
Note :

>View가 CAEAGLLayer객체 뒤에 있는 경우, setNeedsDisplay()메소드는 아무 효과가 없습니다. 이 메소드는 내용을 렌더링하기 위해 native drawing technologies (예 : UIKit 및 Core Graphics)을 사용하는 View에서만 사용할 수 있습니다.<br/><br/>이 메소드를 사용하면, **View의 내용이나 모양이 변경된 경우에만 View를 다시 그립니다.** 단순히 View의 기하(geometry)를 변경하면, View는 일반적으로 다시 그려지지 않습니다. 대신 기존 내용은 View의 contentMode 속성 값을 기반으로 조정됩니다. 기존 내용을 다시 표시하면, 변경되지 않은 내용을 다시 그리지 않아도 되므로 성능이 향상됩니다.

---

## 2. 자동 호출
- **View 의 Property 가 변경되면 내부적으로 setNeedsDisplay() 가 자동 호출** 된다.
- 이후 영향을 받는 영역이 다시 그려진다.

>자동 호출 케이스
1. View를 부분적으로 가리고 있던 다른 View이동 또는 제거
2. hidden 프로퍼티를 No로 설정하여, 이전에 숨겨진 View를 다시 볼 수 있게 만들기
3. View를 화면밖으로 스크롤한다음, 화면으로 다시 이동하기

## 3. 명시적 호출
- **나 자신만의 View를 만들고**, 자체 draw메소드를 구현하고, 무언가가 변경되면 **“명시적으로” 업데이트**할때


출처: [ZeddiOS](https://zeddios.tistory.com/359)
