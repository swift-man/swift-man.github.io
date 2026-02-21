---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "Fastlane 명령어로 앱 버전 올리기"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Fastlane"
depth:
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "Fastlane"
    url: /ios/fastlane/
    icon: "far fa-folder-open"
---
Fastlane 은 iOS개발을 도와주는 좋은 도구이다.    
배포 자동화를 도와주는 툴이며, 많은 iOS개발자들이 사용할 수 있다.
대표적인 장점은 수동으로 배포를 하다 보면 실수를 할 수 있는데, 이를 방지할 수 있는 장점이 있다.   

## 기본 설정
터미널을 열고 해당 프로젝트 경로로 가자.
```
fastlane init
```

## 명령어로 앱 버전 올리기
버전 업데이트 명령어에 타입이 존재하는데, 다음 3가지다.  
>major, minor, patch    

### Major update 
4.0.1 -> 5.0.1
```
fastlane increaseVersion type:major 
```

### Minor update
4.0.1 -> 4.1.1
```
fastlane increaseVersion type:minor 
```

### Patch update
4.0.1 -> 4.0.2
```
fastlane increaseVersion type:patch 
```
