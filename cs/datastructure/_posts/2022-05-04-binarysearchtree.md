---
sidebar:
  title: "CS"
  nav: sidebar-cs
  icon: "fas fa-microchip"
title: "[Swiift] BinarySearchTree"
toc: true
toc_sticky: true
toc_label: 목차
tag: "DataStructure"
depth:
  - title: "CS"
    url: /cs/
    icon: "fas fa-microchip"
  - title: "DataStructure"
    url: /cs/datastructure/
    icon: "far fa-folder-open"
published: false
---

```swift
public class BinarySearchTree<T: Comparable> {
  fileprivate(set) public var value: T
  fileprivate(set) public var parent: BinarySearchTree?
  fileprivate(set) public var left: BinarySearchTree?
  fileprivate(set) public var right: BinarySearchTree?

  public init(value: T) {
    self.value = value
  }

  public convenience init(array: [T]) {
    precondition(array.count > 0)
    self.init(value: array.first!)
    for v in array.dropFirst() {
      insert(value: v)
    }
  }
}
```

## Insert
```swift
public func insert(value: T) {
  if value < self.value {
    if let left = left {
      left.insert(value: value)
    } else {
      left = BinarySearchTree(value: value)
      left?.parent = self
    }
  } else {
    if let right = right {
      right.insert(value: value)
    } else {
      right = BinarySearchTree(value: value)
      right?.parent = self
    }
  }
}
```

## Search
```swift
public func search(value: T) -> BinarySearchTree? {
  var node: BinarySearchTree? = self
  while let n = node {
    if value < n.value {
      node = n.left
    } else if value > n.value {
      node = n.right
    } else {
      return node
    }
  }
  return nil
}
```

## Delete
```swift
@discardableResult public func remove() -> BinarySearchTree? {
  let replacement: BinarySearchTree?

  // Replacement for current node can be either biggest one on the left or
  // smallest one on the right, whichever is not nil
  if let right = right {
    replacement = right.minimum()
  } else if let left = left {
    replacement = left.maximum()
  } else {
    replacement = nil
  }

  replacement?.remove()

  // Place the replacement on current node's position
  replacement?.right = right
  replacement?.left = left
  right?.parent = replacement
  left?.parent = replacement
  reconnectParentTo(node:replacement)

  // The current node is no longer part of the tree, so clean it up.
  parent = nil
  left = nil
  right = nil

  return replacement
}

public func minimum() -> BinarySearchTree {
  var node = self
  while let next = node.left {
    node = next
  }
  return node
}

/*
  Returns the rightmost descendent. O(h) time.
*/
public func maximum() -> BinarySearchTree {
  var node = self
  while let next = node.right {
    node = next
  }
  return node
}

private func reconnectParentTo(node: BinarySearchTree?) {
  if let parent = parent {
    if isLeftChild {
      parent.left = node
    } else {
      parent.right = node
    }
  }
  node?.parent = parent
}
```

## 출처
[<i class="fas fa-link"></i> raywenderlich.com](https://www.raywenderlich.com/990-swift-algorithm-club-swift-binary-search-tree-data-structure){:target="_blank"}  
[<i class="fas fa-link"></i> swift-algorithm-club/BinarySearchTree.swift
](https://github.com/raywenderlich/swift-algorithm-club/blob/master/Binary%20Search%20Tree/Solution%201/BinarySearchTree.playground/Sources/BinarySearchTree.swift){:target="_blank"}  
[<i class="fas fa-link"></i> 개발자 소들이 - Swift) 이진 탐색 트리(BST) 구현 해보기 (1/2)
](https://babbab2.tistory.com/90){:target="_blank"}  
[<i class="fas fa-link"></i> 개발자 소들이 - Swift) 이진 탐색 트리(BST) 구현 해보기 (2/2)
](https://babbab2.tistory.com/91){:target="_blank"}
