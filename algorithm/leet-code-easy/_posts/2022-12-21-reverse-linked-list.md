---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] Reverse Linked List"
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
Given the `head` of a singly linked list, reverse the list, and return the reversed list.

### Example 1:
![Image](https://assets.leetcode.com/uploads/2021/02/19/rev1ex1.jpg)  
```swift
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
```

### Example 2:
![Image](https://assets.leetcode.com/uploads/2021/02/19/rev1ex2.jpg)  
```swift
Input: head = [1,2]
Output: [2,1]
```

### Example 3:
```swift
Input: head = []
Output: []
```


### Constraints:
* The number of nodes in the list is the range `[0, 5000].`
* `-5000 <= Node.val <= 5000`

{% include b-link.html title="풀러가기" url="https://leetcode.com/problems/reverse-linked-list/description/" %}

## 문제 이해


## 코드
```swift
func reverseList(_ head: ListNode?) -> ListNode? {
  var current = head
  var previous: ListNode?
  var following = head

  while current != nil { 
   following = following?.next
   current?.next = previous
   previous = current
   current = following
  }

  return previous
}
```

## 풀이
-

## 다른 분의 멋진 코드
-

## 잘 배웠습니다.
-
