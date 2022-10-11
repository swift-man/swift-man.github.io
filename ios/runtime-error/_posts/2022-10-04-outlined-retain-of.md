---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "[Xcode Runtime Error] outlined copy of"
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
애플리케이션의 크래시는 운영에 매우 중요한 요소이다. 현재 운영 중인 프로젝트는 99.98% ~ 99.99% 의 크래시로부터 안전성을 유지하고 있다. 주로 Firebase Crashlytics와, Xcode Organizer의 Crashs로 report를 받고 있으며, 예상치 못한 이슈들을 지속적으로 처리하여 유저의 어려움 없는 환경을 위해 지속적인 모니터링과 이슈를 해결하고 있다.  

![Image](https://drive.google.com/uc?export=view&id=1oKXI-c5RG4O0oVeslUz65wZBeCWMZ-4y)  

이번에 만난 오류는 'outlined copy of {object name}'인데, 과도하게 커진 struct로 인한 Crash 였으며 class로 변경하여 해결하였다.



## 해결
`Swift`는 `class` 와 `sturct` type을 지원한다.  
`class`와 `struct` 중 항상 struct가 빠르지 않다. 가지고 데이터의 type과 종류, 상황에 맞게 `class`, `struct`를 잘 선택하여 쓰는 것이 매우 중요하며, `struct`를 사용한다면 value type 이점을 살리기 위한 설계도 필요하다.
```
struct를 class로 변경하자.
```

## 원인
struct는 value type으로 보통 reference type보다 빠르다. 하지만 항상 그런 것은 아닌데, Heap영역에 많은 데이터의 메모리를 alloc 하거나, 많은 양의 데이터를 initialize 시 메모리 할당에 비용이 많이 든다. 때문에 하드웨어의 스펙에 따라 overflow Crash가 발생할 수 있으며, CPU가 A6인 iPhone 5, 5c에서 발견되었다. 

> 이러한 오류를 미리 예방할 수 있는 방법으로 프로젝트 지원 스펙 중 가장 화면이 작은, 가장 스펙이 작은 시뮬레이터로 개발을 하는 방법이 있다.
