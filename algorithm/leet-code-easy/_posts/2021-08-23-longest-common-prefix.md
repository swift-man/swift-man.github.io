---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] Longest Common Prefix"
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
Write a function to find the longest common prefix string amongst an array of strings.  

If there is no common prefix, return an empty string "".


## Example
```swift
Input: strs = ["flower","flow","flight"]
Output: "fl"
```

```swift
Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

```swift
1 <= strs.length <= 200
0 <= strs[i].length <= 200
strs[i] consists of only lower-case English letters.
```

{% include b-link.html title="풀러가기" url="https://leetcode.com/problems/longest-common-prefix/" %}

## 문제 이해


## 코드
```swift
class Solution {
    func longestCommonPrefix(_ strs: [String]) -> String {
        if strs.isEmpty {
            return ""
        }
        var minStr = ""
        var minStrCount = 201
        for i in 0 ..< strs.count {
            let str = strs[i]
            if minStrCount > str.count {
                minStrCount = str.count
                minStr = str
            }
        }
        if minStr.isEmpty {
            return ""
        }

        let filteredArray = strs.filter { $0 != minStr }.map { Array($0) }

        if filteredArray.isEmpty {
            return minStr
        }

        var prefix = ""
        var check = false
        for (i, c) in minStr.enumerated() {
            for str in filteredArray {
                if str[i] == c {
                    check = true
                } else {
                    check = false
                    break
                }
            }

            if check {
                prefix.append(c)
            } else {
                return prefix
            }
        }

        return prefix
    }
}
```

## 풀이
-

## 다른 분의 멋진 코드
```swift
func longestCommonPrefix(_ strs: [String]) -> String {
    guard var `prefix` = strs.min() else { return "" }
    while `prefix`.isEmpty == false {
        if strs.allSatisfy({ $0.hasPrefix(`prefix`) }) { break }
        `prefix`.removeLast()
    }
    return `prefix`
}
```
- FlightyNEO

## 잘 배웠습니다.
-
