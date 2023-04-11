---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: 재귀와 꼬리재귀(2) (Feat. ARC)
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
## Stack frame
어떤 함수든 호출되는 순간 스택에 그 함수를 위한 영역(스택 프레임 stack frame)이 할당된다.
함수가 호출될 때마다 스택에 값들이 쌓이고, 계산이 끝나면 다시 하나씩 빼면서 출력값이 가장 밑에 있던 리턴 공간으로 돌아오는 것이다.   

## 재귀
함수가 함수를 호출하거나 자기 자신을 호출하는 것도 스택에 기반을 두고 있다.  
재귀가 연산속도에서 불리한 점이 발생한다.
재귀 알고리즘을 사용할 때는 반드시 재귀 알고리즘이 필요한지 설계를 먼저 정확히 하는 것이 중요하다.  

## Tail recursion
Tail recursion은 컴퓨터 프로그래밍에서 재귀 알고리즘을 작성하는 특별한 기법이다. 일반적인 재귀 호출이 여러 개의 함수 호출을 스택에 쌓아 두는 반면, 꼬리 재귀(tail recursion)는 함수 호출을 끝낼 때마다 스택에 쌓이지 않게 하는 최적화 기법이다. 이러한 최적화를 통해 꼬리 재귀는 스택 오버플로우 문제를 방지하고, 반복문과 같은 성능을 얻을 수 있다.

꼬리 재귀가 일어나는 경우는 함수의 마지막 작업이 재귀 호출일 때이다. 이 경우 컴파일러는 재귀 호출을 처리하기 위해 새로운 스택 프레임을 만들지 않고, 현재의 스택 프레임을 재사용한다. 따라서 꼬리 재귀는 함수 호출에 따른 추가적인 메모리 사용이 없으므로 스택 오버플로우 위험이 적다.

### Example
```swift
func factorialTailRecursive(_ n: Int, accumulator: Int = 1) -> Int {
  if n == 0 {
      return accumulator
  }
  return factorialTailRecursive(n - 1, accumulator: accumulator * n)
}

let result = factorialTailRecursive(5) // 결과: 120
```
이 예제에서 `factorialTailRecursive(:,accumulator:)` 함수는 꼬리 재귀를 사용한다. `accumulator`라는 추가 인수를 사용하여 이전 계산 결과를 전달한다. 함수의 마지막 작업은 재귀 호출이므로, 꼬리 재귀로 최적화될 수 있습니다. 이 경우 컴파일러는 함수 호출을 처리하기 위해 새로운 스택 프레임을 만들지 않고, 현재의 스택 프레임을 재사용하여 메모리 사용량을 줄인다.

### Tail recursion은 함수 호출을 최적화 한다.
꼬리 재귀(`tail recursion`)는 함수 호출의 최적화로, 재귀 함수의 호출이 연속적으로 발생할 때 스택 프레임이 누적되지 않도록 최적화하는 것이다. 꼬리 재귀 최적화는 컴파일러에 의해 수행되며, 재귀 함수의 스택 프레임을 재사용하여 메모리 사용량을 줄인다. 이 최적화로 인해 스택 오버플로우 위험이 감소하고, 재귀 함수의 성능이 향상된다.

## Objective-C는 Tail recursion을 지원하는가? 
Objective-C 언어 자체는 `tail recursion`을 직접 지원하지 않지만, 컴파일러 최적화를 통해 `tail recursion`을 사용할 수 있다. Objective-C는 C 기반의 언어로, 일반적으로 `LLVM`의 `Clang` 컴파일러를 사용하여 코드를 컴파일한다. `Clang` 컴파일러는 `tail call` 최적화를 지원하므로, 최적화 옵션을 사용하면 Objective-C 코드에서 `tail recursion`을 사용할 수 있다.

## Swift는 Tail recursion을 지원하는가?
Swift 컴파일러는 일반적으로 tail call 최적화를 지원하므로, 최적화된 빌드에서는 tail recursion이 작동할 가능성이 높다. 이 최적화를 통해 재귀 호출이 더 효율적인 루프로 변환되어 스택 오버플로우를 방지할 수 있다. 

그러나 디버그 빌드에서는 tail call 최적화가 적용되지 않을 수 있으므로, 실제 작동 여부는 사용하는 컴파일러 설정과 최적화 수준에 따라 다를 수 있다. 따라서 Swift에서 `tail recursion`을 사용할 때는 컴파일러 설정과 최적화 수준을 고려해야 한다.

이는 Swift 컴파일러가 재귀 호출을 더 효율적인 루프로 변환하여 스택 오버플로우를 방지할 수 있다는 것을 의미한다. 

## ARC는 컴파일러에 의해 코드가 작성 된다.
ARC (Automatic Reference Counting)는 Objective-C와 Swift에서 메모리 관리를 단순화하는 방법이다. ARC는 객체의 참조 횟수를 추적하고, 더 이상 필요하지 않은 객체를 자동으로 해제한다.

ARC (Automatic Reference Counting)는 Objective-C와 Swift에서 컴파일러에 의해 수행되는 메모리 관리 기법이다. 컴파일 시점에, 컴파일러는 객체의 참조 횟수를 추적하고, 더 이상 필요하지 않은 객체를 자동으로 해제하는 코드를 삽입한다.
>  ARC는 프로그래머가 수동으로 retain, release, autorelease와 같은 메모리 관리 코드를 작성할 필요 없이 메모리를 관리할 수 있게 해 준다. 컴파일러는 ARC를 사용하여 프로그램의 전반적인 성능과 메모리 사용량을 최적화한다.

### ARC에 의해 자동으로 `release()` 코드가 들어가면 컴파일러의 꼬리 재귀 최적화는 안 되는 것 아닌가?
![Image](https://drive.google.com/uc?export=view&id=1_UP9mSzcInwuIizN39iN_Y13CJP3P6E9)  
 > ARC에 의해 자동으로 `release()` 코드가 들어가면 컴파일러의 꼬리 재귀 최적화는 안 되는 것 아닌가?<br/>- 개발자





![Image](https://drive.google.com/uc?export=view&id=1mOkNTLqdPNVGqrjNXLzBGxP_hG3VCegK)  
> ARC는 꼬리 재귀(tail recursion)와 직접적인 관련이 없다.<br/>- 컴파일러

ARC와 꼬리 재귀(tail recursion) 최적화는 둘 다 컴파일러에 의해 수행되지만, 각각 메모리 관리와 함수 호출 최적화에 초점을 맞추는 독립적인 기법이다.

실제로 컴파일러가 최적화를 수행하는 과정에서 상호 작용할 수 있다. ARC가 메모리 해제 코드를 삽입하는 것이 꼬리 재귀 최적화에 영향을 미칠 수 있지만, 이러한 상황은 일반적으로 컴파일러가 처리하도록 설계되어 있다.

컴파일러는 코드를 분석하고 최적화하는 과정에서 다양한 최적화 기법을 함께 적용하며, ARC를 사용하면서도 꼬리 재귀 최적화가 제대로 적용되도록 컴파일러가 최적화 순서를 조정할 수 있다.

하지만 특정 경우에 ARC와 꼬리 재귀 최적화 간의 상호 작용으로 인해 꼬리 재귀 최적화가 적용되지 않을 수도 있다. 이 경우, 해당 상황에 따라 프로그램 구조를 조정하거나 컴파일러 설정을 변경하여 꼬리 재귀 최적화를 적용할 수 있다. 대부분의 경우 컴파일러는 최적화 과정에서 이러한 상황을 자동으로 처리하도록 설계되어 있다.

![Image](https://drive.google.com/uc?export=view&id=19BVE3AgbxFtFWJcoElU5KsVDWjAyKz5x)  

ARC와 꼬리 재귀는 서로 독립적인 최적화 기법으로, ARC는 메모리 관리에 초점을 맞추고, 꼬리 재귀는 함수 호출의 최적화에 초점을 맞춘다. 따라서 ARC가 메모리 해지 코드를 삽입하는 것은 꼬리 재귀 최적화에 직접적인 영향을 미치지 않는다.
