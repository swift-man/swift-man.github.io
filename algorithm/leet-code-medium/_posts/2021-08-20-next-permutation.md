---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
title: "Next Permutation"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.
---
[Algorithm](/algorithm/) / [Leet Code Medium](/algorithm/leet-code-medium/) / **31. Next Permutation**
{: .notice--warning}
![](https://leetcode.com/static/packages/interview_landing/images/logo.svg)

## 1. 개요
**Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.**

**If such an arrangement is not possible, it must rearrange it as the lowest possible order (i.e., sorted in ascending order).**

**The replacement must be in place and use only constant extra memory.**

**Constraints:**
  1. 1 <= nums.length <= 100
  2. 0 <= nums[i] <= 100
{: .notice--info}
## 2. Example
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
* [풀러가기](https://leetcode.com/problems/next-permutation/)

## 3. 문제 이해
* 외우는 문제
```swift
Input: nums = [1,3,5,4,4]
Output: [1,4,3,4,5]
```

1. 뒤에서 부터 탐색하면서 오름차순이 깨지는 인덱스를 확인(a)
```
1 3 5 4 4(a) // X
1 3 5 4(a) 4 // X
1 3 5(a) 4 4 // X
1 3(a) 5 4 4 // O
```
2. 다시 뒤에서 부터 탐색하면서 a 보다 큰 첫번째 인덱스를 확인(b)
```
1 3(a) 5 4 4(b)
```
3. a 와 b 스왑
```
1 4(a) 5 4 3(b)
```
4. a + 1 에서부터 끝까지 오름차순 정렬
```
1 4 5(start) 4 3(end)
->
1 4 3 4 5
```

## 4. 코드
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

## 5. 풀이
-

## 6. 다른 분의 멋진 코드
-

## 7. 잘 배웠습니다.
-

{% include utteranc.html %}
