---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] Remove Nth Node From End of List"
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
Given the `head` of a linked list, remove the n$^t$$^h$ node from the end of the list and return its head.



## Example 1:
![Image](https://assets.leetcode.com/uploads/2020/10/03/remove_ex1.jpg)  
```swift
Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]
```

## Example 2:
```swift
Input: head = [1], n = 1
Output: []
```

## Example 3:
```swift
Input: head = [1,2], n = 1
Output: [1]
```

## Constraints:
* The number of nodes in the list is `sz.`
* `1 <= sz <= 30`
* `0 <= Node.val <= 100`
* `1 <= n <= sz`

[<i class="fas fa-link"></i> 풀러가기](https://leetcode.com/problems/remove-nth-node-from-end-of-list/){:target="_blank"}

## 문제 이해
LinkedList 의 마지막에서 n 번째 해당하는 노드를 제거

## 코드
```swift
func removeNthFromEnd(_ head: ListNode?, _ n: Int) -> ListNode? {
  var head: ListNode? = head
  
  var node: ListNode? = head
  var count = 0
  while let current = node {
    node = current.next
    count += 1
  }
  
  count -= n
  if count <= 0 {
    return head?.next
  }
  
  var i = 0
  node = head
  while let current = node, i != count - 1 {
    node = current.next
    i += 1
  }
  
  node?.next = node?.next?.next
  
  return head
}
```

## 풀이
-

## 다른 분의 멋진 코드


## 잘 배웠습니다.
-
