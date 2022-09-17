---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] Missing Number"
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
Given an array `nums` containing `n` distinct numbers in the range `[0, n]`, return <b>the only number in the range that is missing from the array.</b>

## Example 1:
```swift
Input: nums = [3,0,1]
Output: 2
Explanation: n = 3 since there are 3 numbers, so all numbers are in the range [0,3]. 
2 is the missing number in the range since it does not appear in nums.
```

## Example 2:
```swift
Input: nums = [0,1]
Output: 2
Explanation: n = 2 since there are 2 numbers, so all numbers are in the range [0,2]. 
2 is the missing number in the range since it does not appear in nums.
```

## Example 3:
```swift
Input: nums = [9,6,4,2,3,5,7,0,1]
Output: 8
Explanation: n = 9 since there are 9 numbers, so all numbers are in the range [0,9]. 
8 is the missing number in the range since it does not appear in nums.
```

## Constraints:

* n == nums.length
* 1 <= n <= $10^4$
* 0 <= nums[i] <= n
* All the numbers of `nums` are <b>unique</b>.

{% include b-link.html title="풀러가기" url="https://leetcode.com/problems/missing-number/" %}

## 문제 이해
* 순차 배열의 누락된 값을 찾는다.

## 코드
```swift
func missingNumber(_ nums: [Int]) -> Int {
  let totalSum = (nums.count + 1) * nums.count / 2
  return nums.reduce(totalSum, -)
}
```

## 풀이
1. 배열이 순차적 조건이므로 1부터 배열의 카운트까지의 모든 수의 합을 구한다.
2. nums 의 누락된 값을 구하기 위해 nums 의 모든 값을 더한 후 모든 수의 합을 빼준다.

## 다른 분의 멋진 코드
```swift
func missingNumber(_ nums: [Int]) -> Int {
    var target: Int = nums.count
    var i = 0
    
    while i < nums.count {
        target = target - nums[i] + i
        i += 1
    }

    return target
}
```

## 잘 배웠습니다.
> 1부터 N까지의 합 구하기
```
sum = (n + 1) * n / 2
```
