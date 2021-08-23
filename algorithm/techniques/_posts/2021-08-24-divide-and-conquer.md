---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
title: "Divide and conquer"
toc: true
toc_sticky: true
toc_label: 목차
---
[Algorithm](/algorithm/) / [기법](/algorithm/techniques/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요

분할 정복 알고리즘(Divide and conquer algorithm)은 그대로 해결할 수 없는 문제를 작은 문제로 분할하여 문제를 해결하는 방법이나 알고리즘이다.

빠른 정렬이나 합병 정렬로 대표되는 정렬 알고리즘 문제와 고속 푸리에 변환(FFT) 문제가 대표적이다.

## 2. 분할 정복 알고리즘
```
function F(x):
  if F(x)의 문제가 간단 then:
    return F(x)을 직접 계산한 값
  else:
    x 를 y1, y2로 분할
    F(y1)과 F(y2)를 호출
    return F(y1), F(y2)로부터 F(x)를 구한 값
```

또한 여기서 작은 부문제로 분할할 경우에 부문제를 푸는 알고리즘은 임의로 선택할 수 있다. 이러한 재귀호출을 사용한 함수는 함수 호출 오버헤드 때문에 실행 속도가 늦어진다.

빠른 실행이나 부문제 해결 순서 선택을 위해, 재귀호출을 사용하지 않고 스택, 큐(queue) 등의 자료구조를 이용하여 분할 정복법을 구현하는 것도 가능하다.

ex)
```swift
func f(_ array: [Int]) -> Int {
    if array.count == 1 {
        return array.first!
    }
    let center = array.count / 2
    let max1 = f(array[0 ..< center])
    let max2 = f(array[center ..< array.count])
    return max(max1, max2)
}
```
