---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] Next Permutation"
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
Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.

If such an arrangement is not possible, it must rearrange it as the lowest possible order (i.e., sorted in ascending order).

The replacement must be in place and use only constant extra memory.
```
Constraints:
  1. 1 <= nums.length <= 100
  2. 0 <= nums[i] <= 100
```
## Example
```swift
Input: nums = [1,2,3]
Output: [1,3,2]
```

```swift
Input: nums = [3,2,1]
Output: [1,2,3]
```

```swift
Input: nums = [1,1,5]
Output: [1,5,1]
```

```swift
Input: nums = [1]
Output: [1]
```
{% include b-link.html title ="풀러가기" url = "https://leetcode.com/problems/next-permutation/" %}

## 문제 이해
외우는 문제
```swift
Input: nums = [1,3,5,4,4]
Output: [1,4,3,4,5]
```


```swift
// 뒤에서 부터 탐색하면서 오름차순이 깨지는 인덱스를 확인(a)
1 3 5 4 4(a) // X
1 3 5 4(a) 4 // X
1 3 5(a) 4 4 // X
1 3(a) 5 4 4 // O
```

```swift
// 다시 뒤에서 부터 탐색하면서 a 보다 큰 첫번째 인덱스를 확인(b)
1 3(a) 5 4 4(b)
```

```swift
// a 와 b 스왑
1 4(a) 5 4 3(b)
```

```swift
// a + 1 에서부터 끝까지 오름차순 정렬
1 4 5(start) 4 3(end)
->
1 4 3 4 5
```

## 코드
```swift
class Solution {
    func nextPermutation(_ nums: inout [Int]) {
        // 뒤에서 부터 탐색하면서 오름차순이 깨지는 인덱스를 확인(a)
        var a = nums.count - 2
        while a >= 0 && nums[a] >= nums[a + 1] {
            a -= 1
        }

        if a != -1 {
            // 다시 뒤에서 부터 탐색하면서 a 보다 큰 첫번째 인덱스를 확인(b)
            var b = nums.count - 1
            while nums[a] >= nums[b] {
                b -= 1
            }

            // a 와 b 스왑
            nums.swapAt(a, b)
        }

        // a + 1 에서부터 끝까지 오름차순 정렬
        var start = a + 1
        var end = nums.count - 1
        while start < end {
            nums.swapAt(start, end)
            start += 1
            end -= 1
        }
    }
}
```

## 풀이
-

## 다른 분의 멋진 코드
-

## 잘 배웠습니다.
-
