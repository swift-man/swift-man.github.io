---
sidebar:
  title: "iOS"
  nav: sidebar-ios
title: StringTransform
toc: true
toc_sticky: true
toc_label: 목차
excerpt : 문자열 음역(Transliteration) 변환을 제공한다.
---
[iOS](/ios/) / [Foundation](/ios/foundation/) / [NSString](/ios/foundation/nsstring/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
문자열 음역(Transliteration) 변환을 제공한다.
```swift
public struct StringTransform : Hashable, Equatable, RawRepresentable {
  public init(_ rawValue: String)
  public init(rawValue: String)
}
extension StringTransform {
  @available(macOS 10.11, *)
  public static let latinToKatakana: StringTransform

  @available(macOS 10.11, *)
  public static let latinToHiragana: StringTransform

  @available(macOS 10.11, *)
  public static let latinToHangul: StringTransform

  @available(macOS 10.11, *)
  public static let latinToArabic: StringTransform

  @available(macOS 10.11, *)
  public static let latinToHebrew: StringTransform

  @available(macOS 10.11, *)
  public static let latinToThai: StringTransform

  @available(macOS 10.11, *)
  public static let latinToCyrillic: StringTransform

  @available(macOS 10.11, *)
  public static let latinToGreek: StringTransform

  @available(macOS 10.11, *)
  public static let toLatin: StringTransform

  @available(macOS 10.11, *)
  public static let mandarinToLatin: StringTransform

  @available(macOS 10.11, *)
  public static let hiraganaToKatakana: StringTransform

  @available(macOS 10.11, *)
  public static let fullwidthToHalfwidth: StringTransform

  @available(macOS 10.11, *)
  public static let toXMLHex: StringTransform

  @available(macOS 10.11, *)
  public static let toUnicodeName: StringTransform

  @available(macOS 10.11, *)
  public static let stripCombiningMarks: StringTransform

  @available(macOS 10.11, *)
  public static let stripDiacritics: StringTransform
}
```

## 1.1 사용 가능 함수
```swift
func applyingTransform(_ transform: StringTransform, reverse: Bool) -> String?
```
