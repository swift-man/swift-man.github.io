---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] LinkedList"
toc: true
toc_sticky: true
toc_label: 목차
group: "Data Structure"
depth: 
  - title: "Algorithm"
    url: /algorithm/
    icon: "far fa-folder-open"
  - title: "Data Structure"
    url: /algorithm/data-structure/
    icon: "far fa-folder-open"
---
리스트의 다음 원소에 대한 연결고리(link, 포인터 또는 레퍼런스) 가 들어있다.  
마지막 원소는 꼬리(tail) 라고 부르며, 연결고리는 비워두거나 nil 로 지정한다.  
각각의 원소들은 자기 자신 다음에 어떤 원소인지만을 기억하고 있다.  
Tree 구조의 근간이 되는 자료구조이며, 그 유용성이 드러난다.  

## 조회 - O(n)


## 삽입 - O(1)
```swift
linkedList = LinkedList()
linkedList.append(0)
let head = linkedList.head
head?.next = Node(value: 2)
```

## 삭제
- O(1)

## 원하는 위치에 삽입 / 삭제
- O(n)
- 위치에 삽입을 하고자 하면 원하는 위치를 Search 과정에 있어서 첫번째 원소부터 다 확인해봐야 한다는 것이다. 
- Array 와는 달리 논리적 저장 순서와 물리적 저장 순서가 일치하지 않기 때문이다. 이것은 일단 삽입하고 정렬하는 것과 마찬가지이다. 




## 구현
```swift
public class Node<T> {
  var value: T
  var next: Node?
  weak var previous: Node?
  
  public init(value: T) {
    self.value = value
  }
}
```

```swift
public final class LinkedList<T> {
  private(set) var head: Node<T>?
  public init() {}
  
  public init(_ value: T) {
    head = Node(value: value)
  }
}
```

```swift
@discardableResult
public func insertInFront(value: T) -> LinkedList<T> {
  let newList = LinkedList(value)
  guard let head = head else { return newList }
  newList.head?.next = head
  return newList
}

@discardableResult
public func insertInFront(value: T) -> Node<T> {
  let newList = LinkedList(value)
  guard let head = head else { return newList.head! }
  newList.head!.next = head
  return newList.head!
}
```


```swift
public func first(where predicate: (Node<T>) -> Bool) -> Node<T>? {
  var node = head
  
  while let nd = node {
    if predicate(nd) {
      return nd
    }
    
    node = nd.next
  }
  return nil
}
```
