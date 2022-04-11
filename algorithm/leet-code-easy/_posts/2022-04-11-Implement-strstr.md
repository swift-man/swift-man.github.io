---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] Implement strStr()"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Leet Code Easy"
depth:
  - title: "Algorithm"
    url: /algorithm/
    icon: "fas fa-calculator"
  - title: "Leet Code Easy"
    url: /algorithm/leet-code-easy/
    icon: "far fa-folder-open"
use_math: true
---
Implement [<i class="fas fa-link"></i> strStr](http://www.cplusplus.com/reference/cstring/strstr/){:target="_blank"}.  

Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.  

## Clarification:
What should we return when needle is an empty string? This is a great question to ask during an interview.  

For the purpose of this problem, we will return 0 when needle is an empty string. This is consistent to C's strstr() and Java's indexOf().




### Example 1:
```swift
Input: haystack = "hello", needle = "ll"
Output: 2
```

### Example 2:
```swift
Input: haystack = "aaaaa", needle = "bba"
Output: -1
```

### Constraints:
* `1 <= haystack.length, needle.length <= $10^4$`
* `haystack` and `needle` consist of only lowercase English characters.

{% include b-link.html title="풀러가기" url="https://leetcode.com/problems/implement-strstr/" %}

## 문제 이해


## 코드
```swift
class Solution {
  func strStr(_ haystack: String, _ needle: String) -> Int {
    var strIndex = 0
    var haystack = haystack
    while 0 <= haystack.count - needle.count {
      if haystack.hasPrefix(needle) {
        return strIndex
      }
      haystack.removeFirst()
      
      strIndex += 1
    }
    
    return -1
  }
}
```

## 풀이
-

## 다른 분의 멋진 코드
-

## 잘 배웠습니다.
-
