---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "[Xcode Build Error] Could not find module for target x86_64-apple-ios-simulator"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Xcode Build Error"
depth:
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "Build Error"
    url: /ios/build-error/
    icon: "far fa-folder-open"
---
Could not find module for target 'x86_64-apple-ios-simulator'; found: arm64, armv7-apple-ios, arm64-apple-ios, arm, armv7

![Image](https://drive.google.com/uc?export=view&id=1iZLJnFW-_V-TOCx4fwrFP3yQzJ_McebF)

## 해결
해당 모듈 - Build Settings - Exclueded Architectures - simulator에 arm64 로 세팅해주면 해결 된다.

![Image](https://drive.google.com/uc?export=view&id=1oGNhXAruLvcKy29j_gxOf8a98n4fFXcc)

### 적용 후 다시 빌드
![Image](https://drive.google.com/uc?export=view&id=1i-J-7IyDUT25NOu5oFdq6mzbKBEG-0_d)
성공!
