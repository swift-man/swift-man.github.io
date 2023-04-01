---
sidebar:
  title: "Swift"
  nav: sidebar-swift
  icon: "fab fa-swift"
title: Swift Package Manager 생성해보기
toc: true
toc_sticky: true
toc_label: 목차
tag: "Swift Package Manager"
depth:
  - title: "Swift"
    url: /swift/
    icon: "fab fa-swift"
  - title: "Swift Package Manager"
    url: /swift/swift-package-manager/
    icon: "far fa-folder-open"
---
## 요약 - 터미널 명령어
```
swift package init --type library
swift build
swift test
swift package generate-xcodeproj
```

## Package 생성
```
swift package init
```
or
```
swift package init --type library
```
![Image](https://drive.google.com/uc?export=view&id=1jEXoA_yfEEblmwWpiBf046kJA6fBx2f8)


## 빌드
```
swift build
```
![Image](https://drive.google.com/uc?export=view&id=1L547lEfSC06Zg4w7B-zyl1Qg4ui2edq4)
## 테스트
```
swift test
```
![Image](https://drive.google.com/uc?export=view&id=1zDwslUPvlMGFN5Q5mG_kKzdvMrXzT2E-)
## 프로젝트 생성
```
swift package generate-xcodeproj
```

### 프로젝트 열어보기
```
xed . // 현재 폴더의 프로젝트 열기 명령어
```
![Image](https://drive.google.com/uc?export=view&id=10fcwtgS1D4TETgSQ-0VJ1OHxHTlK963B)

- 열었을때 Xcode 의 오류가 없으면 성공

## 출처
* [<i class="fas fa-link"></i> docs.swift.org/package-manage](https://docs.swift.org/package-manager/PackageDescription/PackageDescription.html#package-dependency){:target="_blank"}
* [<i class="fas fa-link"></i> developer.apple](https://developer.apple.com/documentation/xcode/creating-a-standalone-swift-package-with-xcode){:target="_blank"}

