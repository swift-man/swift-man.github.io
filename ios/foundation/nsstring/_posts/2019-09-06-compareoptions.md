---
sidebar:
  title: "iOS"
  nav: sidebar-ios
title: CompareOptions
toc: true
toc_sticky: true
toc_label: 목차
excerpt : 문자열 처리에 여러가지 옵션을 지정하여 처리할 수 있다.
---
[iOS](/ios/) / [Foundation](/ios/foundation/) / [NSString](/ios/foundation/nsstring/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
문자열 처리에 여러가지 옵션을 지정하여 처리할 수 있다.
```swift
extension NSString {
  public struct CompareOptions : OptionSet {
    public init(rawValue: UInt)
    public static var caseInsensitive: NSString.CompareOptions { get }
    public static var literal: NSString.CompareOptions { get }
    public static var backwards: NSString.CompareOptions { get }
    public static var anchored: NSString.CompareOptions { get }
    public static var numeric: NSString.CompareOptions { get }

    @available(macOS 10.5, *)
    public static var diacriticInsensitive: NSString.CompareOptions { get }

    @available(macOS 10.5, *)
    public static var widthInsensitive: NSString.CompareOptions { get }

    @available(macOS 10.5, *)
    public static var forcedOrdering: NSString.CompareOptions { get }

    @available(macOS 10.7, *)
    public static var regularExpression: NSString.CompareOptions { get }
    }
}
```

## 1.1 사용 가능 함수
```swift
func replacingOccurrences(of target: String, 
                     with replacement: String, 
                  options: NSString.CompareOptions = [],
                    range searchRange: NSRange) -> String
func range(of searchString: String) -> NSRange
func compare<T>(_ aString: T,
                options mask: String.CompareOptions = [],
                range: Range<Self.Index>? = nil,
                locale: Locale? = nil) -> ComparisonResult where T : StringProtocol
```

OptionSet 이기 때문에 여러개의 옵션을 전달할 수 있다.

## 2. caseInsensitive
대소문자를 구분하지 않는다.

## 3. literal
유니코드의 동등성을 구분한다.
```swift
let encode1 = stringToUnicode("한글")
let encode2 = stringToUnicode("ㅎㅏㄴㄱㅡㄹ")

print(encode1) // "\u{D55C}\u{AE00}"
print(encode2) // "\u{1112}\u{1161}\u{11AB}\u{1100}\u{1173}\u{11AF}"
```
```swift
if "한글" == "\u{D55C}\u{AE00}" {
  print("true")
} else {
  print("false")
}
// true
```
```swift
if "한글".compare("\u{D55C}\u{AE00}") == .orderedSame {
  print("true")
} else {
  print("false")
}
// true
```
```swift
if "한글".compare("\u{D55C}\u{AE00}", options: .literal) == .orderedSame {
  print("true")
} else {
  print("false")
}
// true
```
```swift
if "\u{D55C}\u{AE00}" == "\u{1112}\u{1161}\u{11AB}\u{1100}\u{1173}\u{11AF}" {
  print("true")
} else {
  print("false")
}
// true
```
```swift
if "\u{D55C}\u{AE00}".compare("\u{1112}\u{1161}\u{11AB}\u{1100}\u{1173}\u{11AF}") == .orderedSame {
  print("true")
} else {
  print("false")
}
// true
```
```swift
if "한글".compare("\u{1112}\u{1161}\u{11AB}\u{1100}\u{1173}\u{11AF}") == .orderedSame {
  print("true")
} else {
  print("false")
}
// true
```
```swift
if "\u{D55C}\u{AE00}".compare("\u{1112}\u{1161}\u{11AB}\u{1100}\u{1173}\u{11AF}",
                              options: .literal) == .orderedSame {
  print("true")
} else {
  print("false")
}
// false
```

## 4. backwards
소스 문자열의 끝에서 검색하여 가장 먼저 검색되는 결과를 리턴 한다.
```swift
let str = "첫번째문자열 두번째문자열 마지막문자열"
if let result = str.range(of: "마지막문자열", options: [.backwards]) {
  print(str.distance(from: str.startIndex, to: result.lowerBound))
}
// 14

if let result = str.range(of: "두번째문자열", options: [.backwards]) {
  print(str.distance(from: str.startIndex, to: result.lowerBound))
}
// 7
```

## 5. anchored
소스 문자열의 첫번째에서 검색하여 가장 먼저 검색되는 결과를 리턴 한다.
검색은 소스 문자열의 시작(또는 NSBackwardsSearch인 경우 끝)으로 제한됩니다.
```swift
let str = "첫번째문자열 두번째문자열 마지막문자열"
if let result = str.range(of: "첫번째문자열", options: [.anchored]) {
  print(str.distance(from: str.startIndex, to: result.lowerBound))
}
// 0
if let result = str.range(of: "두번째문자열", options: [.anchored, .backwards]) {
  print(str.distance(from: str.startIndex, to: result.lowerBound))
}
// nil

if let result = str.range(of: "마지막문자열", options: [.anchored]) {
  print(str.distance(from: str.startIndex, to: result.lowerBound))
}
// nil

if let result = str.range(of: "마지막문자열", options: [.anchored, .backwards]) {
  print(str.distance(from: str.startIndex, to: result.lowerBound))
}
// 14
```

## 6. numeric
문자열 내의 숫자는 숫자 값을 사용하여 비교됩니다. 즉, Name2.txt < Name7.txt < Name25.txt입니다.
파일이름을 정렬할때 유용하다.

## 7. diacriticInsensitive
알파벳의 발음 부호로 문자열을 비교한다.
```swift
print("é".compare("e", options: .diacriticInsensitive).rawValue) // 0
```
## 8. widthInsensitive
검색은 동아시아 문자 집합의 전각문자와 반각 문자 형식을 가진 문자의 너비 차이를 무시합니다.
전각 문자 : 영문자 기준으로 2 배의 너비를 가지는 문자
반각 문자 : 전각문자의 절반의 너비를 가지는 문자

## 9. forcedOrdering
문자열이 동일하지만 엄격하게 동일하지 않은 경우 비교는 NSOrderedAscending 또는 NSOrderedDescending을 반환하도록 강제 실행됩니다.
## 10. regularExpression
검색 문자열은 ICU 호환 정규식으로 처리됩니다. 설정하면 대소문자 구분 및 고정을 제외한 다른 옵션을 적용할 수 없습니다. 

```swift
// 이 옵션은 이 함수에서만 사용할 수 있다.
func range(of searchString: String) -> NSRange <br/>
func replacingOccurrences(of target: String, 
                     with replacement: String, 
                  options: NSString.CompareOptions = [],
                    range searchRange: NSRange) -> String
```

```swift
let emailPattern = "([0-9a-zA-Z_-]+)@([0-9a-zA-Z_-]+)(\\.[0-9a-zA-Z_-]+){1,2}"
let emailAddress = "jiniopening@naver.com"

print(emailAddress.range(of: emailPattern, options: [.regularExpression]))
//Optional(Range(Swift.String.Index(_rawBits: 1)..<Swift.String.Index(_rawBits: 1376256)))
```
