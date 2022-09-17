---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] 3Sum Closest"
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
use_math: true
---
Given an integer array `nums` of length `n` and an integer `target`, find three integers in `nums` such that the sum is closest to `target`.  

Return the sum of the three integers.  

You may assume that each input would have exactly one solution.  

## Example 1:
```swift
Input: nums = [0,0,0], target = 1
Output: 0
```

## Example 1:
```swift
Input: nums = [0,0,0], target = 1
Output: 0
```

## Constraints:
* 3 <= nums.length <= 1000
* -1000 <= nums[i] <= 1000
* -10$^4$ <= target <= 10$^4$

[<i class="fas fa-link"></i> 풀러가기](https://leetcode.com/problems/3sum-closest/){:target="_blank"}

## 문제 이해
[<i class="fas fa-link"></i> 3Sum](https://leetcode.com/problems/3sum/){:target="_blank"}과 매우 유사한 문제다. 필자는 3Sum을 풀어보고 한참 뒤에 3Sum Closest을 접했는데 비슷한 유형인지 모르고 예제만 보고 문제 이해를 잘못하여 헤맸다. 3Sum을 풀고 3Sum Closest을 접한다면 비슷한 방식으로 풀 수 있으나 Example만 보고 문제 자체를 이해하기가 어려웠다.  

주어지는 nums 배열은 순서와 상관없이 조합하여 가장 가까운 값을 찾는 것이 핵심이다. 

## 코드
```swift
func threeSumClosest(_ nums: [Int], _ target: Int) -> Int {
  if nums.count == 3 {
    return nums.reduce(0, +)
  }
  
  var ret: (numberOfDifference: Int, sum: Int) = (Int.max, Int.max)
  var nums = nums.sorted()
  
  for index in 0 ..< nums.count - 2 {
    var left = index + 1
    var right = nums.count - 1
    
    while left < right {
      var sum = nums[index] + nums[left] + nums[right]
      
      if sum == target {
        return sum
      }
      
      if sum < target {
        while nums[left + 1] == nums[left] && left + 1 < right {
          left += 1
        }
        
        left += 1
      } else {
        while nums[right - 1] == nums[right] && left < right - 1 {
          right -= 1
        }
        
        right -= 1
      }
      
      let numberOfDifference = target.numberOfDifference(sum)
      if abs(numberOfDifference) < ret.numberOfDifference {
        ret = (numberOfDifference, sum)
      }
    }
  }
  return ret.sum
}
  
extension Int {
  func numberOfDifference( _ number: Int) -> Int {
    if number < self {
      return self - number
    }
    return number - self
  }
}
```

## 풀이
배열을 sort 한 후 투 포인터로 sum 한 값을 비교하여 가장 가까운 수를 찾는다.  
sum 한 값과 target을 비교하여 다음 포인터를 이동시킨다.

## 다른 분의 멋진 코드
```swift
func threeSumClosest(_ nums: [Int], _ target: Int) -> Int {
  let sorted = nums.sorted()
  let length = sorted.count
  
  var diff: Int = .max
  var result = 0
  
  for i in 0..<length - 2 {
    var n = i + 1, q = length - 1
    while n < q {
      let sum = sorted[i] + sorted[n] + sorted[q]
      
      sum > target ? (q -= 1) : (n += 1)
      
      let value =  abs(sum - target)
      
      if value < diff {
        diff = value
        result = sum
      }
    }
  }
  return result
}
```

## 잘 배웠습니다.
-
