---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] Valid Palindrome"
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
---
A phrase is a <b>palindrome</b> if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.  

Given a string `s`, return `true` if it is a <b>palindrome</b>, or `false` otherwise.  

### Example 1:
```swift
Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
```

### Example 2:
```swift
Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.
```

### Example 3:
```swift
Input: s = " "
Output: true
Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.
```

### Constraints:
* 1 <= s.length <= 2 * $10^5$
* `s` consists only of printable ASCII characters.

{% include b-link.html title="풀러가기" url="https://leetcode.com/problems/valid-palindrome/" %}

## 문제 이해


## 코드
```swift
func isPalindrome(_ s: String) -> Bool {
  var arr = Array(s)
  var left = 0
  var right = s.count - 1
  
  while left < right {
    var first = arr[left]
    var last = arr[right]
    
    if !first.isLetter && !first.isNumber {
      left += 1
    } else if !last.isLetter && !last.isNumber {
      right -= 1
    } else if first.lowercased() == last.lowercased() {
      left += 1
      right -= 1
    } else {
      return false
    }
  }
  
  return true
}
```

## 풀이
-

## 다른 분의 멋진 코드
-

## 잘 배웠습니다.
-
