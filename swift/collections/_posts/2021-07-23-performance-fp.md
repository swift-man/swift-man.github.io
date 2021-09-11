---
sidebar:
  title: "Swift"
  nav: sidebar-swift
title: "Performance, functional programming and collections in Swift"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : Collections 의 함수 사용 시 성능 고려하기
---
[Swift](/swift/) / [Collections](/swift/collections/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
- Collections 의 함수 사용 시 성능 고려하기

## 2. Prefer contains over first(where:) != nil
### 2.1 Best practice
```swift
let numbers = [0, 1, 2, 3]
numbers.contains(1)
```

### 2.2 Bad practice
```swift
let numbers = [0, 1, 2, 3]
numbers.filter { number in number == 1 }.isEmpty == false
numbers.first(where: { number in number == 1 }) != nil
```
- contains 를 사용하자


## 3. Prefer checking isEmpty over comparing count to zero.
### 3.1 Best practice
```swift
let numbers = []
numbers.isEmpty

myString.isEmpty
```

### 3.2 Bad practice
```swift
let numbers = []
numbers.count == 0

myString == ""
myString.count == 0
```
- isEmpty 를 사용하자

## 4. Get the first object matching a condition
### 4.1 Best practice
```swift
let numbers = [3, 7, 4, -2, 9, -6, 10, 1]
let firstNegative = numbers.first(where: { $0 < 0 })
```

### 4.2 Bad practice
```swift
let numbers = [3, 7, 4, -2, 9, -6, 10, 1]
let firstNegative = numbers.filter { $0 < 0 }.first
```
- **first(where _:)** 은 조건 중촉 시 즉시 중단 됨 

## 5. Getting the minimum or maximum element in a collection
### 5.1 Best practice
```swift
let numbers = [0, 4, 2, 8]
let minNumber = numbers.min()
let maxNumber = numbers.max()
```

### 5.2 Bad practice
```swift
let numbers = [0, 4, 2, 8]
let minNumber = numbers.sorted().first
let maxNumber = numbers.sorted().last
```

## 6. Making sure all objects match a condition
### 6.1 Best practice
```swift
let numbers = [0, 2, 4, 6]
let allEven = numbers.allSatisfy { $0 % 2 == 0 }
```

### 6.2 Bad practice
```swift
let numbers = [0, 2, 4, 6]
let allEven = numbers.filter { $0 % 2 != 0 }.isEmpty
```
- Swift 4.2 버전에 소개된 **allSatisfy(_:)** 컬렉션의 모든 요소가 특정 조건과 일치하는 지 알 수 있음

대부분의 이런 사례는 [SwiftLint](https://github.com/realm/SwiftLint) 로 알 수 있음.


출처: [avanderlee.com](https://www.avanderlee.com/swift/performance-collections/)
