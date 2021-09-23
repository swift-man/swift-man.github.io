---
sidebar:
  title: "Swift"
  nav: sidebar-swift
  icon: "fab fa-swift"
title: "init(format:_:)"
toc: true
toc_sticky: true
toc_label: 목차
tag: "String"
depth:
  - title: "Swift"
    url: /swift/
    icon: "fab fa-swift"
  - title: "String"
    url: /swift/string/
    icon: "far fa-folder-open"
---
변수나 리터럴, 표현식 등 조합으로 새로운 문자열을 구성하는 것을 String Interpolation 이라 한다.  
문자열 형식 지정 방법 및 함수에서 지원하는 형식 지정자를 요약한다.

```swift
init(format: String, _ arguments: CVarArg...)
```
> %@ 은 'description: String property' 가 리턴하는 값을 출력한다.

## 포맷 지정자

[<i class="fas fa-link"></i> String Format Specifiers](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Strings/Articles/formatSpecifiers.html){:target="_blank"}

| 포맷 지정자   |  값 |
|---  |---  |
| %@   |  Objective-C Object  |
| %% | character |
| %%   |  정수  |
| %d, %D   |  Unsigned 32bit integer  정수  |
| %u, %U   |  Unsigned 32bit integer  16진수로 출력  |
| %x, %X   |  Unsigned 32bit integer 8진수로 출력  |
| %o, %O   |  Unsigned 32-bit integer (unsigned int), printed in octal. 실수  |
| %f   |  64-bit floating-point number (double).  |
| %c   |  유니코드 문자  |
| %s   |  C 문자열  |

## 길이 수식어
두 문자 사이에 표현할 값의 크기를 지정할 수 있는 길이 수식어(Length Modifiers) 를 추가할 수 있다.

Length modifiers supported by the NSString formatting methods and CFString formatting functions

| 길이 수식어   |  값 |
|---  |---  |
| l   |  long  |
| L   |  long double  |
| z   |  size_t  |

## 소수점 자리수 제어
```swift
String(format: "%.1f", 1.243)
// 1.2
```
