---
sidebar:
  title: "Swift"
  nav: sidebar-swift
title: "applyingTransform(_:, reverse: Bool)"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : Perform string transliteration.
---
[Swift](/swift/) / [StringProtocol](/swift/stringprotocol/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
문자열을 [StringTransform](/ios/foundation/nsstring/stringtransform/)에 해당하는 음역으로 변환한다.

```swift
"swift".applyingTransform(.latinToHangul, reverse: false) // Optional("슆트")
"swift-man".applyingTransform(.latinToHangul, reverse: false) // Optional("슆트만")

"스위프트".applyingTransform(.toLatin, reverse: false) // Optional("seuwipeuteu")
"오홍~".applyingTransform(.toLatin, reverse: false) // Optional("ohong~")
```
