---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
title: "두 정수 사이의 합"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : 두 정수 a, b가 주어졌을 때 a와 b 사이에 속한 모든 정수의 합을 리턴하는 함수, solution을 완성하세요.
---
[Algorithm](/algorithm/) / [Programers level1](/algorithm/programers-level1/) / **{{ page.title }}**
{: .notice--warning}
![](https://programmers.co.kr/assets/bi-programmers-light-0d164d49b51a123bab5cca11106145d6fac5a5ac04b8646780369c2a5bc0dd79.png)

## 1. 개요
**두 정수 a, b가 주어졌을 때 a와 b 사이에 속한 모든 정수의 합을 리턴하는 함수, solution을 완성하세요.
예를 들어 a = 3, b = 5인 경우, 3 + 4 + 5 = 12이므로 12를 리턴합니다.**

    제한 조건
    * a와 b가 같은 경우는 둘 중 아무 수나 리턴하세요.
    * a와 b는 -10,000,000 이상 10,000,000 이하인 정수입니다.
    * a와 b의 대소관계는 정해져있지 않습니다.
{: .notice--info}

## 2. Example
```swift
Input: a: 3, b: 5
Output: 12
```

```swift
Input: a: 3, b: 3
Output: 3
```

```swift
Input: a: 5, b: 3
Output: 12
```
[풀러가기](https://programmers.co.kr/learn/courses/30/lessons/12912)

## 3. 문제 이해


## 4. 코드
```swift
func solution(_ a:Int, _ b:Int) -> Int64 {
    if a == b {
        return Int64(a)
    }

    let minValue = min(a, b)
    let maxValue = max(a, b)
    return Int64((minValue ... maxValue).reduce(0, +))
}
```

## 5. 풀이
- 요구사항대로 같은 경우 리턴으로 하도록 했습니다.
- Iterator 에서 max -> min 으로 가게되면 오류가 발생하기 때문에 min, max 함수를 사용했습니다.

## 6. 다른 분의 멋진 코드
```swift
func solution(_ a:Int, _ b:Int) -> Int64 {
    return Int64(a + b) * Int64(max(a, b) - min(a, b) + 1) / Int64(2)
}
```
- TheVoid , 모모

## 7. 잘 배웠습니다.
```
(3 + 5) * (max(3, 5) - min(3, 5) + 1) / 2
-> 
(3 + 5) * (5 - 3 + 1) / 2
->
8 * (2 + 1) / 2
->
8 * 3 / 2
->
24 / 2
->
12
```
- 수학적인 사고로 풀었네요. 놀랍습니다.
- [1 부터 n 까지의 합](/algorithm/basic/numberSum/) 을 포스팅 했었는데 제가 생각을 못한게 아쉽네요.

{% include utteranc.html %}
