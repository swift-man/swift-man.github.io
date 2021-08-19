---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
title: "수박수박수박수박수박수?"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : 길이가 n이고, "수박수박수박수...."와 같은 패턴을 유지하는 문자열을 리턴하는 함수, solution을 완성하세요. 예를들어 n이 4이면 "수박수박"을 리턴하고 3이라면 "수박수"를 리턴하면 됩니다.
---
[Algorithm](/algorithm/) / [Programers level1](programers-level1) / **수박수박수박수박수박수?**
{: .notice--warning}
![](https://programmers.co.kr/assets/bi-programmers-light-0d164d49b51a123bab5cca11106145d6fac5a5ac04b8646780369c2a5bc0dd79.png)

## 1. 개요
**길이가 n이고, "수박수박수박수...."와 같은 패턴을 유지하는 문자열을 리턴하는 함수, solution을 완성하세요. 예를들어 n이 4이면 "수박수박"을 리턴하고 3이라면 "수박수"를 리턴하면 됩니다.**

제한 조건
    1. n은 길이 10,000이하인 자연수입니다.
{: .notice--info}

## 2. Example
```swift
Input: 3
Output: "수박수"
```

```swift
Input: 4
Output: "수박수박"
```

## 3. 문제 이해


## 4. 코드
```swift
func solution(_ n:Int) -> String {
    return (0 ..< n).map { $0 % 2 == 0 ? "수" : "박" }.reduce("", +)
}
```

## 5. 풀이
- 

{% include utteranc.html %}
