---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] Quick 정렬"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Sort"
depth:
  - title: "Algorithm"
    url: /algorithm/
    icon: "fas fa-calculator"
  - title: "Sort"
    url: /algorithm/sort/
    icon: "far fa-folder-open"
---

## 시간 복잡도
* 평균 : O(nlog(n))
* 최악 : O(n^2)

## Code
```swift
func quickSort(_ array: [Int]) -> [Int] {
    guard let first = array.first, array.count > 1 else { return array }
 
    let pivot = first
    let left = array.filter { $0 < pivot }
    let right = array.filter { $0 > pivot }
    
    return quickSort(left) + [pivot] + quickSort(right)
}
```

[<i class="fas fa-link"></i> swift-algorithm-club](https://github.com/kodecocodes/swift-algorithm-club/blob/master/Quicksort/Quicksort.swift){:target="_blank"}

[<i class="fas fa-link"></i> wikipedia](https://ko.wikipedia.org/wiki/%ED%80%B5_%EC%A0%95%EB%A0%AC){:target="_blank"}

