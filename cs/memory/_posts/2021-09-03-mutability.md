---
sidebar:
  title: "CS"
  nav: sidebar-cs
title: "Mutability"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : 데이터를 변경할 수 있음을 나타낸다.
---
[CS](/cs/) / [Memory](/cs/memory/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
데이터를 변경할 수 있음을 나타낸다.
```swift
var a = 0
let s = NSMutableString("")
```

## 2. 데이터의 변경
현재의 메모리 공간을 사용하여 변경된 데이터를 저장할 수 없는 경우 공간의 크기를 자동으로 조절해준다.
변경 과정에서 메모리 공간이 부족해지면 변경된 문자열을 모두 저장할 수 있는 새로운 메모리 공간을 할당한다.
새로운 메모리 공간을 할당하고 복사하는 작업은 성능에 영향을 준다.

## 3. Exponenial growth
신규 메모리 공간을 할당할 때 현재 보다 두 배 이상 큰 공간을 할당한다. 새로운 공간이 할당되는 작업의 횟수를 최대 한 줄여 대부분의 작업을 상수 시간에 처리할 수 있게 해준다.
