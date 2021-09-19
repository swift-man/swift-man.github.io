---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] Median of Two Sorted Arrays"
toc: true
toc_sticky: true
toc_label: 목차
group: "Leet Code Hard"
depth: 
  - title: "Algorithm"
    url: /algorithm/
    icon: "fas fa-calculator"
  - title: "Leet Code Hard"
    url: /algorithm/leet-code-hard/
    icon: "far fa-folder-open"
---
Given two sorted arrays **nums1** and **nums2** of size **m** and **n** respectively, return **the median** of the two sorted arrays.

The overall run time complexity should be O(log (m+n)).
```swift
Constraints:
  1. nums1.length == m
  2. nums2.length == n
  3. 0 <= m <= 1000
  4. 0 <= n <= 1000
  5. 1 <= m + n <= 2000
  6. -106 <= nums1[i], nums2[i] <= 106
```
## Example
```swift
Input: nums1 = [1,3], nums2 = [2]
Output: 2.00000
Explanation: merged array = [1,2,3] and median is 2.
```

```swift
Input: nums1 = [1,2], nums2 = [3,4]
Output: 2.50000
Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.
```

```swift
Input: nums1 = [0,0], nums2 = [0,0]
Output: 0.00000
```

```swift
Input: nums1 = [], nums2 = [1]
Output: 1.00000
```

```swift
Input: nums1 = [2], nums2 = []
Output: 2.00000
```

{% include b-link.html title ="풀러가기" url = "https://leetcode.com/problems/median-of-two-sorted-arrays/" %}

## 문제 이해
-

## 코드
```swift
class Solution {
    func findMedianSortedArrays(_ nums1: [Int], _ nums2: [Int]) -> Double {
        let lhsCount = nums1.count
        let rhsCount = nums2.count
        var lhsIndex = 0
        var rhsIndex = 0
        var merge: [Int] = []
        
        while lhsIndex < lhsCount || rhsIndex < rhsCount {
            var lhsValue: Int?
            if lhsIndex < lhsCount {
                lhsValue = nums1[lhsIndex]
            }
            
            var rhsValue: Int?
            if rhsIndex < rhsCount {
                rhsValue = nums2[rhsIndex]
            }
            
            if let lv = lhsValue, let rv = rhsValue {
                let v = min(lv, rv)
                if v == lv {
                    lhsIndex += 1
                } else {
                    rhsIndex += 1
                }
                merge.append(v)
            } else if let lv = lhsValue {
                merge.append(lv)
                lhsIndex += 1
            } else if let rv = rhsValue {
                merge.append(rv)
                rhsIndex += 1
            }
        }
        if merge.count == 1 {
            return Double(merge[0])
        }
        
        if merge.count % 2 == 1 {
            return Double(merge[merge.count / 2])
        }
        
        let l = Double(merge[merge.count / 2 - 1])
        let r = Double(merge[merge.count / 2])
        return (l + r) / 2
    }
}
```

## 풀이
-

## 다른 분의 멋진 코드
```swift
class Solution {
    func findMedianSortedArrays(_ nums1: [Int], _ nums2: [Int]) -> Double {
      guard nums1.count <= nums2.count  else {
            return findMedianSortedArrays(nums2, nums1)
        }
        
        let m = nums1.count, n = nums2.count
        var start = 0, end = m
        
        while start <= end {
            let cutPos1 = (start + end)/2
            let cutPos2 = (m + n + 1)/2 - cutPos1
            
            // If cutPos1 == 0, nothing in array1 is there on the left,
            // use Int.min for maxLeft1
            // If cutPos1 == m, nothing in array1 is there on the right,
            // use Int.max for minRight1
            let maxLeft1 = cutPos1 == 0 ? Int.min : nums1[cutPos1-1]
            let minRight1 = cutPos1 == m ? Int.max : nums1[cutPos1]
            
            let maxLeft2 = cutPos2 == 0 ? Int.min : nums2[cutPos2-1]
            let minRight2 = cutPos2 == n ? Int.max : nums2[cutPos2]
            
            if maxLeft1 <= minRight2, maxLeft2 <= minRight1 {
                // We have partitioned both array at correct place
                if (m + n) % 2 == 0 {
                    return Double(max(maxLeft1, maxLeft2) + min(minRight1, minRight2))/2.0
                } else {
                    return Double(max(maxLeft1, maxLeft2))
                }
            } else if maxLeft1 > minRight2 {
                // We are too far on right side for cutPos1, go left side
                end = cutPos1 - 1
            } else {
                // We are too far on left side for cutPos1, go right side
                start = cutPos1 + 1
            }
        }
      return -1
    }
}
```
- wds8807

## 잘 배웠습니다.
-
