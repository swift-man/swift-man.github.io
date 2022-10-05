---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "[Xcode Runtime Error] flock failed to lock list file"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Xcode Runtime Error"
depth:
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "Xcode Runtime"
    url: /ios/runtime-error/
    icon: "far fa-folder-open"
---
Apple Silicon 에서 MacOS App 빌드 시 간헐적으로 발생하는 오류다. 지금 실행 중인 앱과, 빌드한 앱에서 충돌이 발생하는 것이 원인이다.

## 해결
해당 앱을 종료하면 해결 된다. 명령어, Finder, 활성 상태 보기 앱을 통해 종료하자.

```
$ pkill <yourappname>
```
