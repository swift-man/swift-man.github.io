---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
title: "LinkedList"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : 각각의 원소들은 자기 자신 다음에 어떤 원소인지만을 기억하고 있다.
---
[Algorithm](/algorithm/) / [Data Structure](/algorithm/data-structurey/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요

- 리스트의 다음 원소에 대한 연결고리(link, 포인터 또는 레퍼런스) 가 들어있다.
- 마지막 원소는 꼬리(tail) 라고 부르며, 연결고리는 비워두거나 nil 로 지정한다.
- 각각의 원소들은 자기 자신 다음에 어떤 원소인지만을 기억하고 있다.
- Tree 구조의 근간이 되는 자료구조이며, 그 유용성이 드러난다.

## 2. 조회
- O(n)

## 3. 삽입
- O(1)

## 4. 삭제
- O(1)

## 5. 원하는 위치에 삽입 / 삭제
- O(n)
- 위치에 삽입을 하고자 하면 원하는 위치를 Search 과정에 있어서 첫번째 원소부터 다 확인해봐야 한다는 것이다. 
- Array 와는 달리 논리적 저장 순서와 물리적 저장 순서가 일치하지 않기 때문이다. 이것은 일단 삽입하고 정렬하는 것과 마찬가지이다. 




## 5. 구현
```swift
public class ListElement<T> {
    private var _data: T
    private var _next: ListElement<T>?
    
    public init(value: T) {
        self._data = value
    }
    
    public var next: ListElement<T>? {
        return _next
    }
    
    public var value: T {
        return _data
    }
    
    public func setNext(_ next: ListElement<T>) {
        _next = next
    }
    
    public func setValue(_ value: T) {
        _data = value
    }
}
```
