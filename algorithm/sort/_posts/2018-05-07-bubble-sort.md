---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
title: "버블 정렬"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : performace:O(n^2), space compexity:O(1)*
---
[Algorithm](/algorithm/) / [Sort](/algorithm/sort/) / **버블 정렬**
{: .notice--warning}

## 1. 개요
- Bubble Sort
- 정렬 알고리즘을 직접 구현할 일은 거의 없겠지만 각각의 차이와 장단점에 대해 알아둘 필요가 있습니다. 각 알고리즘 마다 장점과 단점이 있고, 모든 경우에 대해 최선의 결과를 내는 알고리즘은 없습니다. 



- 각각의 정렬 알고리즘을 알아가 봅시다. 저의 경우는 하나씩 공부하다 보니 왜 느리고 빠른지 이해가 되었습니다.
- 단, 버블정렬은 너무 느리기 때문에 실무에서 잘 쓰이지 않습니다.

>performace : O(n^2)<br />
space compexity : O(1)

---

## 2. 기본 
![Image](https://ww.namu.la/s/ee412a864c3bdcb6cf7077f8ef87e01d4353cf53e66d2a5f6b7def49d257d569a46c810b1b36b9924a495a697c60777bb82d25459c2cbb65e4a700c25351af9b6b0f6992d10dcc4becb2a97990c07ee70111bbfc4497c61df88947201933f10d)
1. 숫자 두개를 비교한 후 바꿀지 말지 정한다.
2. n 번 반복한다.

## 3. Code
```swift
for _ in 0 ..< arr.count - 1 {
    for j in 0 ..< arr.count - 1 {
        if arr[j] > arr[j + 1] {
            arr.swapAt(j, j + 1)
        }
    }
}
```

[바로가기](https://github.com/swift-man/swift/blob/master/Sort/BubbleSort.playground/Contents.swift)

{% include utteranc.html %}
