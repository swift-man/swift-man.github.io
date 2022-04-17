---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] (String)Super Reduced String"
toc: true
toc_sticky: true
toc_label: 목차
tag: "HackerRank Easy"
depth:
  - title: "Algorithm"
    url: /algorithm/
    icon: "fas fa-calculator"
  - title: "HackerRank Easy"
    url: /algorithm/hacker-rank-easy/
    icon: "far fa-folder-open"
use_math: true
---
Reduce a string of lowercase characters in range `ascii[‘a’..’z’]`by doing a series of operations. In each operation, select a pair of adjacent letters that match, and delete them.

Delete as many characters as possible using this method and return the resulting string. If the final string is empty, return `Empty String`

## Example
```swift
Input: 
s = "aab"
// aab shortens to b in one operation: remove the adjacent a characters.
s = "abba"
// Remove the two 'b' characters leaving 'aa'. 
// Remove the two 'a' characters to leave ''. Return 'Empty String'.
```

```swift
Input: "aaabccddd"
Output: "abd" // aaabccddd → abccddd → abddd → abd
Input: "aa"
Output: "Empty String" // aa → Empty String
Input: "baab"
Output: "Empty String" // baab → bb → Empty String
```


## Function Description
Complete the superReducedString function in the editor below.

superReducedString has the following parameter(s):

* string s: a string to reduce

## Returns
* string: the reduced string or Empty String

## Input Format
A single string, `s`.

## Constraints
* 1 <= length of s <= 100

## 문제 이해

## 코드
```swift
func reducedString(_ s: String) -> String {
  var isRemoved = false
  var index = 0
  var s = Array(s)
  while index < s.count - 1 {
    if s[index] == s[index + 1] {
      s.remove(at: index)
      s.remove(at: index)
      
      isRemoved = true
    }
    
    index += 1
  }
  
  if isRemoved {
    return reducedString(String(s))
  }
  
  return String(s)
 }

func superReducedString(s: String) -> String {
    // Write your code here
  
  let ret = reducedString(s)
  
  if ret.isEmpty {
    return "Empty String"
  }
  
  return ret
}
```

## 풀이
-

## 다른 분의 멋진 코드


## 잘 배웠습니다.
-
