---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "Temp 변수를 사용하지 않고 Swap 하기"
toc: true
toc_sticky: true
toc_label: 목차
tag: "기법"
depth:
  - title: "Algorithm"
    url: /algorithm/
    icon: "fas fa-calculator"
  - title: "기법"
    url: /algorithm/techniques/
    icon: "far fa-folder-open"
---
결론 : Temp 를 쓰자.

마이크로 초보다 더 적지만 연산 시간에 차이가 있을 수 있다.
메모리 공간을 절약할 수 있다.
## Code

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

## 링크
{% include b-link.html title="https://en.wikipedia.org/wiki/XOR_swap_algorithm" url="https://en.wikipedia.org/wiki/XOR_swap_algorithm" %}
{% include b-link.html title="http://minjang.egloos.com/1241820" url="http://minjang.egloos.com/1241820" %}
