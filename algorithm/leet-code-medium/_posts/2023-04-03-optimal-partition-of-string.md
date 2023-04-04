---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] Optimal Partition of String"
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
Given a string `s`, partition the string into one or more <b>substrings</b> such that the characters in each substring are <b>unique</b>. That is, no letter appears in a single substring more than <b>once</b>.

Return the `minimum` number of substrings in such a partition.

Note that each character should belong to exactly one substring in a partition.



## Example 1:
```swift
Input: s = "abacaba"
Output: 4
Explanation:
Two possible partitions are ("a","ba","cab","a") and ("ab","a","ca","ba").
It can be shown that 4 is the minimum number of substrings needed.
```

## Example 2:
```swift
Input: s = "ssssss"
Output: 6
Explanation:
The only valid partition is ("s","s","s","s","s","s").
```

## Constraints:
* 1 <= s.length <= $10^5$
* `s` consists of only English lowercase letters.

[<i class="fas fa-link"></i> 풀러가기](https://leetcode.com/problems/optimal-partition-of-string/description/){:target="_blank"}

## 문제 이해

## 코드
```swift
func partitionString(_ s: String) -> Int {
  var result: [String] = [""]
  var index = 0
  for c in s {
    var current = result[index]
    if current.contains(c) {
      result.append("\(c)")
      index += 1
    } else {
      result[index] = current + "\(c)"
    }
  }
  return result.count
}
```

## 풀이
-

## 다른 분의 멋진 코드
* Time complexity: O(n)
* Space complexity: O(1)

```swift
func partitionString(_ s: String) -> Int {
  var map = Array(repeating: false, count: 26)
  var ans = 1
  for c in s
  {
    if map[Int(c.asciiValue! - 97)]
    {
      ans += 1
      map = Array(repeating: false, count: 26)
    }
    map[Int(c.asciiValue! - 97)] = true
  }
  return ans
}
```
[<i class="fas fa-link"></i> Link](https://leetcode.com/problems/optimal-partition-of-string/solutions/3376621/swift-solution-with-explanations/?q=swift&orderBy=hot){:target="_blank"}

## 잘 배웠습니다.
-
