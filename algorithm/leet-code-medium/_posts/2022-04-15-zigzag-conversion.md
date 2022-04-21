---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] Zigzag Conversion"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Leet Code Medium"
depth:
  - title: "Algorithm"
    url: /algorithm/
    icon: "fas fa-calculator"
  - title: "Leet Code Medium"
    url: /algorithm/leet-code-medium/
    icon: "far fa-folder-open"
---
The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)
```
P   A   H   N
A P L S I I G
Y   I   R
```

And then read line by line: `"PAHNAPLSIIGYIR"`

Write the code that will take a string and make this conversion given a number of rows:
```
string convert(string s, int numRows);
```

## Example 1:
```swift
Input: s = "PAYPALISHIRING", numRows = 3
Output: "PAHNAPLSIIGYIR"
```

## Example 2:
```swift
Input: s = "PAYPALISHIRING", numRows = 4
Output: "PINALSIGYAHRPI"
Explanation:
P     I    N
A   L S  I G
Y A   H R
P     I
```

## Example 3:
```swift
Input: s = "A", numRows = 1
Output: "A"
```

## Constraints:
* `1 <= s.length <= 1000`
* `s` consists of English letters (lower-case and upper-case), `','` and `'.'`.
* `1 <= numRows <= 1000`

[<i class="fas fa-link"></i> 풀러가기](https://leetcode.com/problems/zigzag-conversion/){:target="_blank"}

## 문제 이해

## 코드
```swift
class Solution {
  func convert(_ s: String, _ numRows: Int) -> String {
    if numRows == 1 {
      return s
    }
    var array = [[Character]](repeating: [Character](repeating: Character("-"), count: s.count), count: numRows)
    
    var j = 0
    var i = 0
    var isDown = true
    for c in s {
      if !isDown {
        i += 1
        j -= 1
      }
      array[j][i] = c
      
      if isDown {
        j += 1
      }
      
      if numRows == 2 && j == 2 {
        j = 0
        i += 1
        continue
      }
      
      if j == numRows {
        isDown = false
        j -= 1
      } else if j == 1 && !isDown {
        j = 0
        i += 1
        isDown = true
      }
    }
    
    var ret = ""
    
    for arr in array {
      for c in arr {
        let s = String(c)
        if s != "-" {
          ret += s
        }
      }
    }
    
    return ret
  }
}
```

## 풀이
-

## 다른 분의 멋진 코드


## 잘 배웠습니다.
-
