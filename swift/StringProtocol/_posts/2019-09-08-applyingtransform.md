---
sidebar:
  title: "Swift"
  nav: sidebar-swift
  icon: "fab fa-swift"
title: "applyingTransform(_:, reverse: Bool)"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : Perform string transliteration.
tag: "StringProtocol"
depth:
  - title: "Swift"
    url: /swift/
    icon: "fab fa-swift"
  - title: "StringProtocol"
    url: /swift/stringprotocol/
    icon: "far fa-folder-open"
---
Perform string transliteration.  
문자열을 [<i class="fas fa-link"></i> StringTransform](/ios/foundation/nsstring/stringtransform/)에 해당하는 음역으로 변환한다.

```swift
"swift".applyingTransform(.latinToHangul, reverse: false) // Optional("슆트")
"swift-man".applyingTransform(.latinToHangul, reverse: false) // Optional("슆트만")

"스위프트".applyingTransform(.toLatin, reverse: false) // Optional("seuwipeuteu")
"오홍~".applyingTransform(.toLatin, reverse: false) // Optional("ohong~")
```
