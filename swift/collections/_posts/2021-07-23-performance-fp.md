---
sidebar:
  title: "Swift"
  nav: sidebar-swift
  icon: "fab fa-swift"
title: "Performance, functional programming and collections in Swift"
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
Collections 의 함수 사용 시 성능 고려하기

## Prefer contains over first(where:) != nil
### Best practice
```swift
let numbers = [0, 1, 2, 3]
numbers.contains(1)
```

### Bad practice
```swift
let numbers = [0, 1, 2, 3]
numbers.filter { number in number == 1 }.isEmpty == false
numbers.first(where: { number in number == 1 }) != nil
```
- contains 를 사용하자


## Prefer checking isEmpty over comparing count to zero.
### Best practice
```swift
let numbers = []
numbers.isEmpty

myString.isEmpty
```

### Bad practice
```swift
let numbers = []
numbers.count == 0

myString == ""
myString.count == 0
```
- isEmpty 를 사용하자

## Get the first object matching a condition
### Best practice
```swift
let numbers = [3, 7, 4, -2, 9, -6, 10, 1]
let firstNegative = numbers.first(where: { $0 < 0 })
```

### Bad practice
```swift
let numbers = [3, 7, 4, -2, 9, -6, 10, 1]
let firstNegative = numbers.filter { $0 < 0 }.first
```
- **first(where _:)** 은 조건 중촉 시 즉시 중단 됨

## Getting the minimum or maximum element in a collection
### Best practice
```swift
let numbers = [0, 4, 2, 8]
let minNumber = numbers.min()
let maxNumber = numbers.max()
```

### Bad practice
```swift
let numbers = [0, 4, 2, 8]
let minNumber = numbers.sorted().first
let maxNumber = numbers.sorted().last
```

## Making sure all objects match a condition
### Best practice
```swift
let numbers = [0, 2, 4, 6]
let allEven = numbers.allSatisfy { $0 % 2 == 0 }
```

### Bad practice
```swift
let numbers = [0, 2, 4, 6]
let allEven = numbers.filter { $0 % 2 != 0 }.isEmpty
```
- Swift 4.2 버전에 소개된 **allSatisfy(_:)** 컬렉션의 모든 요소가 특정 조건과 일치하는 지 알 수 있음

대부분의 이런 사례는 [<i class="fas fa-link"></i> SwiftLint](https://github.com/realm/SwiftLint){:target="_blank"} 로 알 수 있음.


## 출처
[<i class="fas fa-link"></i> avanderlee.com](https://www.avanderlee.com/swift/performance-collections/){:target="_blank"}
