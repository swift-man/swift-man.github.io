---
sidebar:
  title: "Swift"
  nav: sidebar-swift
title: "Reference Type"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : Class, Closer 는 Reference Type 으로 분류한다.
---
[Swift](/swift/) / [Data Type](/swift/data-type/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
Class, Closer 는 Reference Type 으로 분류한다.

## 2. Init
메모리의 Stack, Heap 영역에 저장된다.

### 2.1 초기값 미할당
```swift
class A {

}
let a: A
```

| Variable     | Stack     | Heap     |
|---    |---    |---    |
| a    | 0x0     | |

* Heap 영역에 메모리 공간이 생성되지 않는다.

### 2.2 초기값 할당
```swift
class A {

}
let a = A()
```

| Variable     | Stack     | Heap     |
|---    |---    |---    |
| a    | 0x12345     | A |

* Heap 영역에 메모리 공간이 생성되고 Stack 공간에 Heap 메모리의 주소를 저장하는 공간이 생성된다.
    
## 3. Call By Reference
파라미터로 전달되거나, 리턴 값으로 사용될 때 Heap 공간에 저장된 값 대신 스택 공간에 저장되어 있는 **<u>주소</u>**가 전달된다.

>Reference Type 에 저장된 값은 대부분 두개 이상의 복합 값으로 구성된다.<br/>그래서 <u>값 형식 처럼 복사본이 생성된다면 메모리의 공간 낭비가 심해지고 프로그램 성능이 저하</u>된다. 참조형식은 이런 문제를 해결하기 위해 주소를 전달한다.

## 4. deinit
직접 제거하기 전까지 메모리 공간에서 사라지지 않는다. 
```swift
class A {

}
var a: A? = A()
a = nil
```
nil 을 할당하여 메모리 제거를 할 수 있다.
> ARC 를 프로젝트에서 사용하는 경우<br/>ARC 가 메모리 해제 작업을 자동으로 처리해준다.<br/>ARC 좋구요!

## 5. Equal
### 5.1 Heap 공간의 값 비교
```swift
a == b
```
### 5.2 Stack 의 주소 비교
```swift
a === b
```
