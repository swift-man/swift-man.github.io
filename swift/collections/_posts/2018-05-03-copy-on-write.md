---
sidebar:
  title: "Swift"
  nav: sidebar-swift
  icon: "fab fa-swift"
title: "[Swift] copy-on-write"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Swift Collections"
depth:
  - title: "Swift"
    url: /swift/
    icon: "fab fa-swift"
  - title: "Collections"
    url: /swift/collections/
    icon: "far fa-folder-open"
---
반드시 복사되어야 하는 경우에만 새로운 복사본을 생성하도록 컴파일러가 최적화한다.

## 성능
기본적으로 collection은 value type이다. 크기가 큰 collection 을 복사하는 경우 reference type 에 비해 성능면에서 불리하다.
하지만 copy-on-write 의 최적화 방식으로 성능 저하는 크게 발생하지 않는다.

```swift
var a = [0, 5, 6]
var b = a

b.append(1) // COW!!
```

>줄여서 copy-on-write 를 COW 라고도 한다.
