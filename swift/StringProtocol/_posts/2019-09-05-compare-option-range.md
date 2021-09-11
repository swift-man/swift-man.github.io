---
sidebar:
  title: "Swift"
  nav: sidebar-swift
title: "compare(_:options:range:locale:)"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : ComparisonResult 를 사용하여 문자열을 비교한다. 
---
[Swift](/swift/) / [StringProtocol](/swift/stringprotocol/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
[ComparisonResult](/ios/foundation/objcruntime/comparisonresult/) 를 사용하여 문자열을 비교한다.

추가로 접미어/접두어를 비교하거나 범위만 지정해서 비교한다.

## 2. 특정 Range 를 통한 비교
```swift
let ret = "문자열을 비교합니다.".compare("문자열")
print(result.rawValue)
// 1
```

```swift
let text = "문자열"
let textRange = text.startIndex ..< text.endIndex
let ret = "문자열을 비교합니다."
  .compare(text,
           options: [],
           range: textRange,
           locale: Locale(identifier: "ko_KR"))
print(ret.rawValue)
// 0

```

## 4. hasPrefix 와의 비교
```swift
let a = "Archives"

print(a.hasPrefix("Arc"))
// true
print(a.hasSuffix("Foundation"))
// false

let range = a.startIndex ..< a.index(a.startIndex, offsetBy: 5)
let ret = a.compare("archi",
                    options: [.caseInsensitive],
                    range: range,
                    locale: Locale(identifier: "ko_KR"))
print(ret.rawValue)
```
hasPrefix 는 범위 지정 없이 비교하지만, compare 는 range 를 통해 범위를 확정하여 비교가 가능하다.

## 5. Options

