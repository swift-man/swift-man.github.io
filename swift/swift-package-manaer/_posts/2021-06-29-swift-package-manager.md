---
sidebar:
  title: "Swift"
  nav: sidebar-swift
title: 생성하기
toc: true
toc_sticky: true
toc_label: 목차
excerpt : Swift Package Manager 생성
---
[Swift](/swift/) / [Swift Package Manager ](/swift/swift-package-manager/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
Swift Package Manager 생성해보기

터미널 명령어
```
swift package init --type library
swift build
swift test
swift package generate-xcodeproj
```

## 2. Package 생성
```
swift package init
```
or
```
swift package init --type library
```
![Image](https://drive.google.com/uc?export=view&id=1jEXoA_yfEEblmwWpiBf046kJA6fBx2f8)


## 3. 빌드
```
swift build
```
![Image](https://drive.google.com/uc?export=view&id=1L547lEfSC06Zg4w7B-zyl1Qg4ui2edq4)
## 4. 테스트
```
swift test
```
![Image](https://drive.google.com/uc?export=view&id=1zDwslUPvlMGFN5Q5mG_kKzdvMrXzT2E-)
## 5. 프로젝트 생성
```
swift package generate-xcodeproj
```

## 5.1 프로젝트 열어보기
```
xed . // 현재 폴더의 프로젝트 열기 명령어
```
![Image](https://drive.google.com/uc?export=view&id=10fcwtgS1D4TETgSQ-0VJ1OHxHTlK963B)

- 열었을때 Xcode 의 오류가 없으면 성공

## 6. dependencies 생성
- 추후 작성하기
