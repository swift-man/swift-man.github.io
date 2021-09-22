---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: ComparisonResult
toc: true
toc_sticky: true
toc_label: 목차
group: "ObjCRuntime"
depth: 
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "Foundation"
    url: /ios/foundation/
    icon: "far fa-file-alt"
  - title: "ObjCRuntime"
    url: /ios/foundation/objcruntime/
    icon: "far fa-file-alt"
---
ascii 를 기준으로 정렬 되는 방식을 나타낸다.

These constants are used to indicate how items in a request are ordered, from the first one given in a method invocation or function call to the last (that is, left to right in code).

Given the function:
  NSComparisonResult f(int a, int b)

If:
   a < b   then return NSOrderedAscending. The left operand is smaller than the right operand.
   a > b   then return NSOrderedDescending. The left operand is greater than the right operand.
   a == b  then return NSOrderedSame. The operands are equal.

```swift
@frozen public enum ComparisonResult : Int {
  case orderedAscending = -1
  case orderedSame = 0
  case orderedDescending = 1
}

public typealias Comparator = (Any, Any) -> ComparisonResult
```
