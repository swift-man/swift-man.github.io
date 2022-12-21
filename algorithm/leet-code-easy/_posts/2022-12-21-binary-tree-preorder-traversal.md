---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] Binary Tree Preorder Traversal"
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
Given the `root` of a binary tree, return the preorder traversal of its nodes' values.

### Example 1:
![Image](https://assets.leetcode.com/uploads/2020/09/15/inorder_1.jpg)  
```swift
Input: root = [1,null,2,3]
Output: [1,2,3]
```

### Example 2:
```swift
Input: root = []
Output: []
```

### Example 3:
```swift
Input: root = [1]
Output: [1]
```


### Constraints:
* The number of nodes in the tree is in the range `[0, 100].`
* `-100 <= Node.val <= 100`

{% include b-link.html title="풀러가기" url="https://leetcode.com/problems/binary-tree-preorder-traversal/description/" %}

## 문제 이해


## 코드
```swift
func preorderTraversal(_ root: TreeNode?) -> [Int] {
  var result: [Int] = []
  preorderTraversal(root, &result)
  return result
}

func preorderTraversal(_ root: TreeNode?, _ arr: inout [Int]) {
  guard let root = root else { return }

  arr.append(root.val)
  preorderTraversal(root.left, &arr)
  preorderTraversal(root.right, &arr)
}
```

## 풀이
-

## 다른 분의 멋진 코드
-

## 잘 배웠습니다.
-
