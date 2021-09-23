---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "[UIViewController] Life Cycle"
toc: true
toc_sticky: true
toc_label: 목차
tag: "UIViewController"
depth: 
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "UIResponder"
    url: /ios/uiresponder/
    icon: "far fa-folder-open"
  - title: "UIViewController"
    url: /ios/uiresponder/uiviewcontroller/
    icon: "far fa-folder-open"
---
## loadView()
- 컨트롤러가 관리하는 뷰를 로드한다.
- 뷰컨트롤러가 생성되고 순차적으로 완성되었을때만 호출된다.


## viewDidLoad()
- 컨트롤러의 뷰가 메모리에 올라간 뒤에 호출된다.
- 뷰가 생성될때만 호출된다.

## viewWillAppear(_ animated: Bool)()
- 화면에 뷰가 표시될때마다 호출된다. 
- 이 단계는 뷰는 정의된 바운드를 가지고 있지만 화면회전은 적용되지않는다.

## viewWillLayoutSubviews()
- 뷰컨트롤러에게 그 자식뷰의 레이아웃을 조정하는 것에 대한 것을 알려주기위해 호출된다. 
- frame이 바뀔때마다 호출된다.
- viewController.view.layoutSubviews() 가 호출
- 이후 뷰 계층구조를 순회하면서 모든 하위 뷰들이 동일한 메서드를 호출

## viewDidLayoutSubviews()
- 레이아웃 정보의 변경사항을 뷰들에 반영되면 호출
- 뷰가 그 자식 뷰의 레이아웃에 영향을 준 것을 뷰컨트롤러에게 알려주기 위해 호출된다. 
- 뷰가 그 자식 View의 레이아웃을 바꾸고난 뒤에 추가적인 변경을 하고 싶을때 사용하는 이벤트 함수


## viewDidAppear(_ animated: Bool)()
- 뷰가 나타났다는 것을 컨트롤러에게 알리는 역할을 한다. 
- 호출되는 시점으로는 뷰가 화면에 나타난 직후에 실행된다.

![Image](https://miro.medium.com/max/700/1*etDLgjBamDJoiaM3_hie9A.png)

## viewWillDisappear(_ animated: Bool)()
- 뷰가 사라지기 직전에 호출되는 함수이다. 
- 뷰가 삭제 되려고하고있는 것을 ViewController에게 알린다.

## viewDidDisappear(_ animated: Bool)()
- ViewController에게 View가 제거되었음을 알린다. 

## deinit()
- 클래스 인스턴스가 할당 해지되기전에 즉각 호출된다.
- 클래스 타입에서만 가능하다.
