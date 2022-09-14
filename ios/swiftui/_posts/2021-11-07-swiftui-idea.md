---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "당장 적용하는 SwiftUI의 아이디어"
toc: true
toc_sticky: true
toc_label: 목차
tag: "SwiftUI"
icon: "fab fa-youtube"
depth:
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "SwiftUI"
    url: /ios/swiftui/
    icon: "far fa-folder-open"
---
절차지향적 프로그래밍은 디버깅, 데이터의 무결성에 단점을 가지고 있다.  
또한 코드가 `if else`로 분기되며 많은 코드들이 조건문으로 쌓이게 됨으로 시간이 지날수록 수정하기 어렵게 되고 유지보수에 불리하게 된다.
 
SwiftUI가 암시하는 것
- SwiftUI가 제시하는 아키텍처 - MVVM과 매우 비슷하다.
  언젠가 나아갈 방향이다.
- 지금 바로 MVVM을 적용하는 것 가능하다.(RxSwift를 이용하여)
- 미리 MVVM 아키텍처를 따라 코드를 만들고 익숙해지면, 추후 코드를 SwiftUI로 포팅하기 쉽고 머리도 SwiftUI 코드에 적응하기 쉽다.

<iframe width="640" height="360" src="https://www.youtube-nocookie.com/embed/7fanl8FrAbY" frameborder="0" allowfullscreen></iframe>

## UIViewController에서 SwiftUI의 Preview기능 사용하기
- @available(iOS 13.0, *)
- UIViewControllerRepresentable, PreviewProvider 이용
- 빌드 세팅 필요(SwiftUI Framework를 optional로 포함)

## Declarative 
### Imparative
- 수행할 작업과 타이밍을 명시적으로 기술
- 행정부 매뉴얼
- view의 위치를 계산해서 frame 값 설정(언제언제 설정해야 하는지 명시해야함)
- UIKit

### Declarative
- 만족해야 할 조건만 기술(구체적인 타이밍과 수행작업은 자동적으로 처리됨)
- 입법부가 만드는 법규
- auto layout으로 조건만 기술(설정 타이밍은 자동으로 처리됨)
- functional programming
- SwiftUI

## RxSwift와 UIKit 조합으로 SwiftUI 와 동일한 아키텍처 가능
```swift
// SwiftUI로 구현
struct MyView: View {
  @State var modelValue: Double = 0 // data
  var body: some View {
    VStack {
      Slider(value: $modelValue) // 적용되는 뷰 들
      Slider(value: $modelValue)
      Text(String(modelValue))
    }
  }
}
```

```swift
// UIKit 으로 동일하게 구현
let modelValue = BehaviorRelay<Float>(value: 0)
let slider = UISlider()
slider.rx.value
  .bind(to: modelValue)
modelValue
  .bind(to: slider.rx.value)

let label = UILabel()
modelValue
  .map { String($0 }
  .bind(to: label.rx.text)
```

## MVVM 특징
- Model
- View Model
  * logic, state 관리
  * View 코드에 대해 아무것도 모른다.
  
- View
  * view model에 종속적이다. observer pattern 사용
  * 자기만의 state 관리를 하지 않는다.
  
```swift
struct MyView: View {
  @State var modelValue: Double = 0 // View Model의 state 역할
                                    // view에 대해 모른다.
  var body: some View {             
    VStack {
      Slider(value: $modelValue)    // state에 종속적이다
      Slider(value: $modelValue)    // 일종의 observer pattern
      Text(String(modelValue))
    }
  }
}
// MVVM의 특징을 가진다.
```
```swift
class ViewModel: ObservableObject {
  @Published var modelValue: Double = 0 // state 역할. view에 대해 모른다.
}

struct MyView: View {
  @ObservedObject var viewModel: ViewModel
  
  var body: some View {
    Slider(value: $viewModel.modelValue)  // viewModel에 종속적, 일종의 observer pattern
  }
}
// MVVM의 특징을 가진다.
```
