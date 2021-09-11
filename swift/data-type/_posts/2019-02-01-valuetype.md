---
sidebar:
  title: "Swift"
  nav: sidebar-swift
title: "Value Type"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : Int, Float, Bool, String 과 같은 기본 자료형과 struct, enum 은 Value Type 분류 한다.
---
[Swift](/swift/) / [Data Type](/swift/data-type/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
Int, Float, Bool, String 과 같은 기본 자료형과 struct, enum 은 Value Type 분류 한다.

## 2. Init
선언과 동시에 메모리 공간이 생성된다. 그래서 유효한 값으로 초기화 하지 않는 경우 할당된 메모리 공간에 있던 이전 값이 저장 될 수 있다.

    이런 값을 쓰레기 값이라고 부른다.
    쓰레기 값은 프로그램에서 논리적인 오류의 원인이 되기 쉽다. 

>Swift 컴파일러는 코드를 통해 명시적으로 초기화 하지 않은 값을 읽으면 오류를 발생시킨다.<br/>LLVM 좋구요!

## 2.1 Stack 영역에 저장
메모리의 Stack 영역에 저장된다.

```swift
let num = 10
```

| Variable     | Stack     |
|---    |---    |
| num    | 10     |

## 3. Call By Value
파라미터로 전달되거나, 리턴 값으로 사용될 때 항상 같은 값을 가진 복사본이 생성된다.
copy 된 값을 변경하여도 원본에 영향을 받지 않는다.

## 4. deinit
Stack 공간에 생성된 값이 자신이 속한 scope 의 코드 실행이 종료 되면 자동으로 해지된다.

## 5. Equal
Stack 공간에 저장된 실제 값을 비교한다.
```swift
a == b
```
