---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "isProtectedDataAvailable"
toc: true
toc_sticky: true
toc_label: 목차
tag: "UIResponder"
depth:
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "UIResponder"
    url: /ios/uiresponder/
    icon: "far fa-file-alt"
  - title: "UIApplicationMain"
    url: /ios/uiresponder/uiapplicationmain/
    icon: "far fa-file-alt"
---
보호된 파일(키 체인, UserDefaults 등)을 엑세스 가능한지 확인하는 변수이다.

이 속성의 값이 false인 경우 보호된 파일을 읽을 거나 쓸 수 없으며 사용자가 device 를 unlock 해야한다.

> iOS 15 부터 키체인이 예측하지 못한 간헐적 오 동작이 발생한다고 한다. 이때 `isProtectedDataAvailable`로 체크를 하는 것이 좋다. 원인은 [<i class="fas fa-link"></i> iOS 15부터 사용자의 패턴을 분석하여 앱 라이프사이클을 미리 로드](https://developer.apple.com/documentation/uikit/app_and_environment/responding_to_the_launch_of_your_app/about_the_app_launch_sequence?language=objc){:target="_blank"}하는 기능이 생겼다고.. 

## 출처
[<i class="fas fa-link"></i> developer.apple.com](https://developer.apple.com/documentation/uikit/uiapplication/1622925-isprotecteddataavailable){:target="_blank"}
