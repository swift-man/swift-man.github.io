---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: StringTransform
toc: true
toc_sticky: true
toc_label: 목차
group: "NSString"
depth: 
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "Foundation"
    url: /ios/foundation/
    icon: "far fa-file-alt"
  - title: "NSString"
    url: /ios/foundation/nsstring/
    icon: "far fa-file-alt"
---
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

### 사용 가능 함수
```swift
func applyingTransform(_ transform: StringTransform, reverse: Bool) -> String?
```


## 2. Transliteration
## 2.1 toLatin
모든 언어 -> 라틴
```swift
"한글이다.".applyingTransform(.toLatin, reverse: false)
// Optional("hangeul-ida.")
```
## 2.2 latinToArabic
라틴 -> 아랍 문자
```swift
"latin".applyingTransform(.latinToArabic, reverse: false)
// Optional("لَتِن")
```

## 2.3 latinToCyrillic
라틴 -> 키릴 문자
```swift
"latin".applyingTransform(.latinToCyrillic, reverse: false)
// Optional("латин")
```

## 2.4 latinToGreek
라틴  -> 그리스어
```swift
"latin".applyingTransform(.latinToGreek, reverse: false)
// Optional("λατιν")
```

## 2.5 latinToHangul
라틴  -> 한글
```swift
"latin".applyingTransform(.latinToHangul, reverse: false)
// Optional("라틴")
```

## 2.6 latinToHebrew
라틴  -> 히브리어
```swift
"latin".applyingTransform(.latinToHebrew, reverse: false)
// Optional("לַטִן")
```

## 2.7 latinToHiragana
라틴  -> 히라가나
```swift
"latin".applyingTransform(.latinToHiragana, reverse: false)
// Optional("らてぃん")
```

## 2.8 latinToKatakana
라틴  -> 가타카나
```swift
"latin".applyingTransform(.latinToKatakana, reverse: false)
// Optional("ラティン")
```

## 2.9 latinToThai
라틴어  -> 태국어
```swift
"latin".applyingTransform(.latinToThai, reverse: false)
// Optional("ละติน")
```

## 2.10 hiraganaToKatakana
히라가나  -> 가타카나
```swift
"らてぃん".applyingTransform(.hiraganaToKatakana, reverse: false)
// Optional("ラティン")
```

## 2.11 mandarinToLatin
만다린어 -> 라틴어
```swift
"中華民國國語".applyingTransform(.mandarinToLatin, reverse: false)
// Optional("zhōng huá mín guó guó yǔ")
```

## 3. Diacritic and Combining Mark Removal
## 3.1 stripDiacritics
분음 부호 제거
```swift
"matreška".applyingTransform(.stripDiacritics, reverse: false)
// Optional("matreska")
```

## 3.2 stripCombiningMarks
결합 표시를 제거
```swift
"ǘɒ̈".applyingTransform(.stripCombiningMarks, reverse: false)
// Optional("uɒ")
```



## 4. Halfwidth and Fullwidth Form Conversion
## 4.1 fullwidthToHalfwidth
전각 CJK 문자 -> 반각 형식
```swift
"１２３４５６７８９＠ａｂｃｄｅｆｇ".applyingTransform(.fullwidthToHalfwidth, reverse: false) 
// Optional("123456789@abcdefg")
```

## 5. Character Representation
## 5.1 toUnicodeName
문자 -> 유니코드 이름으로 변환하는 식별자
```swift
"한글".applyingTransform(.toUnicodeName, reverse: false)
// Optional("\\N{HANGUL SYLLABLE HAN}\\N{HANGUL SYLLABLE GEUL}")
```

## 5.2 toXMLHex
문자-> XML 16진 이스케이프 코드
```swift
"한글".applyingTransform(.toXMLHex, reverse: false)
// Optional("&#xD55C;&#xAE00;")
```
