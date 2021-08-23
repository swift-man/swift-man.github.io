---
sidebar:
  title: "Swift"
  nav: sidebar-swift
title: "Dictionary"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : Reference type 이다.
---
[Swift](/swift/) / [Collections](/swift/collections/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
```
@frozen public struct Dictionary<Key, Value> where Key : Hashable
```

## subscript(_:)

O(1)입니다

 

## count

O(1)입니다

 

## contains(where:)

O(N)입니다. contains(_:) method는 없습니다. (key로 바로 참조하면 알 수 있기 때문입니다.)

 

 

## index(forKey:)

평균 O(1), bridged NSDictionary으로 Wrap된 경우 O(N)입니다.


https://github.com/apple/swift/blob/main/stdlib/public/core/Dictionary.swift

## mapValues(_:)

O(N)입니다.

 

## compactMapValues(_:)

O(M+N)입니다. N은 기존 Dictionary의 크기이고, M은 결과 Dictionary의 크기입니다.

 

## remove(at:), removeValue(forKey:), removeAll(keepingCapacity:)

O(N)입니다.

 

## popFirst()

평균 O(1)입니다.

 

## rereversed()

O(N)입니다.

- [github.com/apple/swift/blob/main/stdlib/public/core/Dictionary](https://github.com/apple/swift/blob/main/stdlib/public/core/Dictionary.swift)

