---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] Maximum Subarray"
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
Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

A `subarray` is a `contiguous` part of an array.




### Example 1:
```swift
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

### Example 2:
```swift
Input: nums = [1]
Output: 1
```

### Example 2:
```swift
Input: nums = [5,4,-1,7,8]
Output: 23
```

### Constraints:
* 1 <= nums.length <= $10^5$
* -104 <= nums[i] <= $10^4$

{% include b-link.html title="풀러가기" url="https://leetcode.com/problems/maximum-subarray/" %}

## 문제 이해
```swift
// [-2,1,-3,4,-1,2,1,-5,4]
// nums[1] : 1
// nums[0] : -2
nums[1] = max(nums[1], nums[1] + nums[0])
// nums[1] : 1
// ret: -2
ret = max(ret, nums[1])
// ret: 1
```
```swift
// [-2,1,-3,4,-1,2,1,-5,4]
// nums[2] : -3
// nums[1] : 1
nums[2] = max(nums[2], nums[2] + nums[1])
// nums[2] : -2
// ret: 1
ret = max(ret, nums[2])
// ret: 1
```
```swift
// [-2,1,-3,4,-1,2,1,-5,4]
// nums[3] : 4
// nums[2] : -2
nums[3] = max(nums[3], nums[3] + nums[2])
// nums[3] : 4
// ret: 1
ret = max(ret, nums[3])
// ret: 4
```
```swift
// [-2,1,-3,4,-1,2,1,-5,4]
// nums[4] : -1
// nums[3] : 4
nums[4] = max(nums[4], nums[4] + nums[3])
// nums[4] : 3
// ret: 4
ret = max(ret, nums[4])
// ret: 4
```
```swift
// [-2,1,-3,4,-1,2,1,-5,4]
// nums[5] : 2
// nums[4] : 3
nums[5] = max(nums[5], nums[5] + nums[4])
// nums[5] : 5
// ret: 4
ret = max(ret, nums[5])
// ret: 5
```
```swift
// [-2,1,-3,4,-1,2,1,-5,4]
// nums[6] : 1
// nums[5] : 5
nums[6] = max(nums[6], nums[6] + nums[5])
// nums[6] : 6
// ret: 5
ret = max(ret, nums[6])
// ret: 6
```
```swift
// [-2,1,-3,4,-1,2,1,-5,4]
// nums[7] : -5
// nums[6] : 6
nums[7] = max(nums[7], nums[7] + nums[6])
// nums[7] : 1
// ret: 6
ret = max(ret, nums[i])
// ret: 6
```
```swift
// [-2,1,-3,4,-1,2,1,-5,4]
// nums[8] : 4
// nums[7] : 1
nums[8] = max(nums[8], nums[8] + nums[7])
// nums[8] : 5
// ret: 6
ret = max(ret, nums[i])
// ret: 6
```

## 코드
```swift
func maxSubArray(_ nums: [Int]) -> Int {
  var nums = nums
  var ret = nums[0]
  for i in 1 ..< nums.count {
    nums[i] = max(nums[i], nums[i] + nums[i-1])
    ret = max(ret, nums[i])
  }
  
  return ret
}
```

## 풀이
<iframe width="640" height="360" src="https://www.youtube-nocookie.com/embed/tmakGVOGV3A" frameborder="0" allowfullscreen></iframe>

## 다른 분의 멋진 코드
-

## 잘 배웠습니다.
-
