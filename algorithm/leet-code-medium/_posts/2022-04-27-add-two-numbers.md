---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] Add Two Numbers"
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
You are given two `non-empty` linked lists representing two non-negative integers. The digits are stored in `reverse order`, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.



## Example 1:
![Image](https://assets.leetcode.com/uploads/2020/10/02/addtwonumber1.jpg)  
```swift
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.
```

## Example 2:
```swift
Input: l1 = [0], l2 = [0]
Output: [0]
```

## Example 3:
```swift
Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]
```

## Constraints:
* The number of nodes in each linked list is in the range [1, 100].
* 0 <= Node.val <= 9
* It is guaranteed that the list represents a number that does not have leading zeros.

[<i class="fas fa-link"></i> 풀러가기](https://leetcode.com/problems/add-two-numbers/){:target="_blank"}

## 문제 이해

## 코드
```swift
func addTwoNumbers(_ l1: ListNode?, _ l2: ListNode?) -> ListNode? {
  var l1 = l1
  var l2 = l2
  
  var carry = 0
  var prev = ListNode()
  let ret = prev
  while l1 != nil || l2 != nil || carry != 0 {
    var sum = 0
    if l1 != nil {
      sum += l1!.val
      l1 = l1!.next
    }
    
    if l2 != nil {
      sum += l2!.val
      l2 = l2!.next
    }
    sum += carry
    
    carry = sum / 10
    
    let cur = ListNode(sum % 10)
    prev.next = cur
    prev = cur
  }
  
  return ret.next
}
```

## 풀이
-

## 다른 분의 멋진 코드


## 잘 배웠습니다.
-
