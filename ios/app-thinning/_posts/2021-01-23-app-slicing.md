---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "App Slicing"
toc: true
toc_sticky: true
toc_label: 목차
group: "App Thinning"
depth: 
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "App Thinning"
    url: /ios/app-thinning/
    icon: "far fa-file-alt"
---
슬라이싱 은 다양한 대상 장치 및 운영 체제 버전에 대한 앱 번들의 변형을 만들고 제공하는 프로세스입니다.   
변형은 대상 장치 및 운영 체제 버전에 필요한 경우에만 실행 아키텍처와 리소스가 포함되어 있습니다.   
앱의 전체 버전을 계속 개발하고 App Store Connect에 업로드합니다. App Store는 앱이 지원하는 기기 및 운영 체제 버전에 따라 다양한 변형을 만들고 제공합니다.   
App Store에서 각 변형에 적합한 이미지, GPU 리소스 및 기타 데이터를 선택할 수 있도록 자산 카탈로그를 사용하십시오.  
사용자가 앱을 설치하면 사용자의 장치 및 운영 체제 버전에 대한 변형이 다운로드되어 설치됩니다.  

Xcode는 개발 중에 슬라이싱을 시뮬레이션하므로 로컬에서 변형을 만들고 테스트할 수 있습니다. 
>Xcode는 기기나 시뮬레이터에서 앱을 빌드하고 실행할 때 앱을 슬라이싱합니다.<br/>
아카이브를 만들 때 Xcode에는 앱의 전체 버전이 포함되지만 아카이브에서 변형을 내보낼 수 있습니다.

![Image](https://help.apple.com/xcode/mac/current/en.lproj/Art/app_thinning_2x.png)
