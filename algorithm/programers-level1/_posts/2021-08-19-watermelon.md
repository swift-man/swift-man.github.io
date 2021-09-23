---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] 수박수박수박수박수박수?"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Programers level1"
depth:
  - title: "Algorithm"
    url: /algorithm/
    icon: "fas fa-calculator"
  - title: "Programers level1"
    url: /algorithm/programers-level1/
    icon: "far fa-folder-open"
---
길이가 n이고, "수박수박수박수...."와 같은 패턴을 유지하는 문자열을 리턴하는 함수, solution을 완성하세요. 예를들어 n이 4이면 "수박수박"을 리턴하고 3이라면 "수박수"를 리턴하면 됩니다.

    제한 조건
    n은 길이 10,000이하인 자연수입니다.
{: .notice--info}

## Example
```swift
Input: 3
Output: "수박수"
```

```swift
Input: 4
Output: "수박수박"
```
[<i class="fas fa-link"></i> 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/12922)


## 코드
```swift
func solution(_ n:Int) -> String {
    return (0 ..< n).map { $0 % 2 == 0 ? "수" : "박" }.reduce("", +)
}
```
