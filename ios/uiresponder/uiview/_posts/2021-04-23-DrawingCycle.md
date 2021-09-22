---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "Drawing Cycle"
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
    icon: "far fa-file-alt"
  - title: "UIView"
    url: /ios/uiresponder/uiview/
    icon: "far fa-file-alt"
---
UIView클래스는 컨텐츠를 표시할 때, on-demand 드로잉 모델을 사용한다.  
View를 업데이트하려면 **다음 드로잉사이클** 때까지 기다렸다가 한꺼번에 업데이트 된다.
>비동기 요청을 기록하고 즉시 리턴합니다. 즉각적인 업데이트를 강제하지는 않지만, 다음 업데이트 주기를 기다리기 때문에 View를 업데이트하기 전에 여러 View의 레이아웃을 무효화하는데 사용할 수 있다. 
이러한 행동은 모든 레이아웃 업데이트를 하나의 업데이트 주기로 통합할 수 있으며, 일반적으로 성능향상에 도움이 된다. 

1. 시스템이 현재 View의 스냅샷(visual representation) 캡쳐(업데이트 전) 
2. 컨텐츠 변경 시 시스템에게 setNeedsDisplay() 를 호출하여 View업데이트 요청
3. 다음 런루프가 오기까지 모든 컨텐츠 변경을 지연하여 여러 처리를 한번에 하도록 기회 제공
5. 다음 드로잉 사이클이 오면, 이때 View업데이트를 요청받은 View를 전부 업데이트함
6. draw(_ rect: CGRect) 를 호출해서 view 업데이트



## 2. View업데이트를 트리거 할 수 있는 몇가지 작업
1. View를 부분적으로 가리고 있던 다른 View이동 또는 제거
2. hidden 프로퍼티를 No로 설정하여, 이전에 숨겨진 View를 다시 볼 수 있게 만들기
3. View를 화면밖으로 스크롤한다음, 화면으로 다시 이동
4. View의 setNeedsDisplay 또는 setNeedsDisplayInRect: 메소드를 명시적으로 호출


- 출처:  [ZeddiOS](https://zeddios.tistory.com/359)
