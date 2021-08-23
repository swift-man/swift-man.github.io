---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
title: "Temp 변수를 사용하지 않고 Swap 하기"
toc: true
toc_sticky: true
toc_label: 목차
---
[Algorithm](/algorithm/) / [기법](/algorithm/techniques/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요

결론 : Temp 를 쓰자.

마이크로 초보다 더 적지만 연산 시간에 차이가 있을 수 있다.
메모리 공간을 절약할 수 있다.
## 2. Code

```swift
func swap(a: Int, b: Int) {
  var temp = a
  a = b
  b = temp
}
```

```swift
/*
a = 10
b = 5
*/
func swap(a: Int, b: Int) {
  a = a + b // a = 10 + 5 = 15
  b = a - b // b = 15 - 5 = 10
  a = a - b // a = 15 - 10 = 5
}
```

재밌는 것은
XOR Swap 은 별로라고 한다.

링크
>https://en.wikipedia.org/wiki/XOR_swap_algorithm

>http://minjang.egloos.com/1241820
