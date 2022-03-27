---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "[Cocoapods] Running pod install with an outdated master specs repo shows error message"
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
repo 설치 중 cancel 이 되거나 오류가 발생하면 이후 pod install 을 하게 되면 아래 와 같은 오류가 발생하게 된다.

![Image](https://drive.google.com/uc?export=view&id=1tNW8Vjxh9QjeCKyFLJfGBlr5QBMTgusk)

## 해결
https://github.com/CocoaPods/CocoaPods/issues/5260

```
rm -rf ~/.cocoapods/repos/master
pod setup --verbose
pod repo update
pod install
```
