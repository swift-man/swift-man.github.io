---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] Merge Intervals"
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
Given an array of <u>intervals</u> where <u>intervals[i] = [start$_i$, end$_i$]</u>, merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

## Example 1:
```swift
Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].
```

## Example 1:
```swift
Input: intervals = [[1,4],[4,5]]
Output: [[1,5]]
Explanation: Intervals [1,4] and [4,5] are considered overlapping.
```

## Constraints:
* 1 <= intervals.length <= 10$^4$
* intervals[i].length == 2
* 0 <= starti <= endi <= 10$^4$

[<i class="fas fa-link"></i> 풀러가기](https://leetcode.com/problems/merge-intervals/){:target="_blank"}

## 문제 이해

## 코드
```swift
class Solution {
  func merge(_ intervals: [[Int]]) -> [[Int]] {
    if intervals.count < 2 {
      return intervals
    }
    
    var intervals = intervals.sorted { $0.first! < $1.first! }
    
    var ret: [[Int]] = []
    
    for i in 1 ..< intervals.count {
      let left = intervals[i - 1]
      var right = intervals[i]
      if left.last! >= right.first! && right.last! >= left.first! {
        right[0] = min(left[0], right[0])
        right[1] = max(left[1], right[1])
        intervals[i] = right
      } else {
        ret.append(left)
      }
    }
    ret.append(intervals.last!)
    
    return ret
  }
}
```

## 풀이
-

## 다른 분의 멋진 코드


## 잘 배웠습니다.
-
