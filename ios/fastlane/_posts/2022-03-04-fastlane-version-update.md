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
배포 자동화를 도와주는 좋은 툴이며, 실수를 방지할 수 있는 장점이 있다.   
익숙해지기 까지의 과정을 더 쉽게 하기위해 메모한다.

## 설치
### Fastlane 설치
터미널을 열자.
```
brew install fastlane
```

### Bundler 설치
```
gem install bundler
```

## Fastlane 업데이트
```
bundle update
```

## 기본 설정
터미널을 열고 해당 프로젝트 경로로 가자.
```
fastlane init
```

## 버전 올리기
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


## 참고
[<i class="fas fa-link"></i> iOS — 배포 자동화, Fastlane 시작부터 적용까지](https://medium.com/hcleedev/ios-%EB%B0%B0%ED%8F%AC-%EC%9E%90%EB%8F%99%ED%99%94-fastlane-%EC%8B%9C%EC%9E%91%EB%B6%80%ED%84%B0-%EC%A0%81%EC%9A%A9%EA%B9%8C%EC%A7%80-3d9107cdc3b4){:target="_blank"}
