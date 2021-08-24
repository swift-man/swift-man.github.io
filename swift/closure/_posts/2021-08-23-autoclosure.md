---
sidebar:
  title: "Swift"
  nav: sidebar-swift
title: "@autoClosure"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : 클로저에 자동으로 래핑되는 인수를 정의할 수 있다. 
---
[Swift](/swift/) / [closure](/swift/closure/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
@autoclosure속성을 사용하면 클로저에 자동으로 **래핑**되는 인수를 정의할 수 있다. 
일반 구문을 인자값으로 넣어도 컴파일러가 알아서 클로저로 만들어서 사용한다.

이것이 Swift 표준 라이브러리에서 사용되는 한 가지 예는 assert함수다. 

assert는 디버그 빌드에서만 트리거되므로 릴리스 빌드에서 assert 되는 표현식을 평가할 필요가 없다. 

```swift
func assert(_ expression: @autoclosure () -> Bool,
            _ message: @autoclosure () -> String) {
    guard isDebug else {
        return
    }

    // Inside assert we can refer to expression as a normal closure
    if !expression() {
        assertionFailure(message())
    }  
}
```
좋은 점은 @autoclosure호출 사이트에 영향을 미치지 않는다. assert는 기본 클로저를 사용하여 구현된 경우 다음과 같이 사용해야 한다.

```swift
assert({ someCondition() }, { "Hey, it failed!" })
```
이제 비클로저 인수를 사용하는 함수처럼 호출할 수 있다.

```swift
assert(someCondition(), "Hey it failed!")
```

## 2. 인라인 할당
한 가지는 함수 호출에서 표현식을 인라인이 가능하다. 이를 통해 할당 표현식을 인수로 전달하는 것과 같은 작업을 수행할 수 있다. 유용할 수 있는 예를 살펴보자.

iOS에서는 일반적으로 다음 API를 사용하여 애니메이션을 만들 수 있다.

```swift
UIView.animate(withDuration: 0.25) {
    view.frame.origin.y = 100
}
```
를 사용 하여 다음과 같이 애니메이션 클로저를 자동으로 생성하고 실행 @autoclosure하는 animate함수를 작성할 수 있다 .

```swift
func animate(_ animation: @autoclosure @escaping () -> Void,
             duration: TimeInterval = 0.25) {
    UIView.animate(withDuration: duration, animations: animation)
}
```
이제 추가 {}구문 없이 간단한 함수 호출로 애니메이션을 수행할 수 있다 .

```swift
animate(view.frame.origin.y = 100)
```
위의 기술을 사용하면 가독성이나 표현력을 희생하지 않고도 애니메이션 코드의 장황함을 줄일 수 있다. 🎉

## 3. 표현식으로 오류 전달
다른 상황은 오류를 처리하는 유틸리티를 작성할 수 있다. 예를 들어 API를 Optional사용하여 래핑을 해제할 수 있는 확장을 추가하고 싶다고 가정해 보자. 그렇게 하면 옵셔널이 non-nil이 되도록 요구 하거나 다음과 같이 오류를 던질 수 있다.
```swift
extension Optional {
    func unwrapOrThrow(_ errorExpression: @autoclosure () -> Error) throws -> Wrapped {
        guard let value = self else {
            throw errorExpression()
        }

        return value
    }
}
```
assert구현된 방법과 유사하게 옵셔널을 언래핑하려고 할 때마다 수행하지 않고 필요할 때만 오류 표현식을 평가한다. 이제 unwrapOrThrow다음과 같이 API를 사용할 수 있다.

```swift
let name = try argument(at: 1).unwrapOrThrow(ArgumentError.missingName)
```
## 4. 기본값을 사용한 유형 추론
@autoclosure내가 찾은 마지막 사용 사례 는 Dictionary, 데이터베이스 또는 UserDefaults.

일반적으로 유형이 지정되지 않은 사전에서 값을 추출하고 기본값을 제공할 때 다음과 같이 작성해야 한다.
```swift
let coins = (dictionary["numberOfCoins"] as? Int) ?? 100
```
그것은 읽기 어려운 종류이며 캐스팅 및 ??연산자 와 관련된 구문이 많이 복잡합니다 . 를 사용 @autoclosure하여 다음과 같은 동일한 표현식을 대신 작성할 수 있는 API를 정의할 수 있습니다.
```swift
let coins = dictionary.value(forKey: "numberOfCoins", defaultValue: 100)
```
위에서 우리는 기본값이 둘 다 값이 없을 때 사용된다는 것을 알 수 있지만, 또한 유형을 지정하거나 캐스팅을 수행할 필요 없이 Swift가 값에 대한 유형 추론을 수행할 수 있도록 합니다. 깔끔하네요👍

이러한 API를 작성하는 방법을 살펴보겠습니다.
```swift
extension Dictionary where Value == Any {
    func value<T>(forKey key: Key, defaultValue: @autoclosure () -> T) -> T {
        guard let value = self[key] as? T else {
            return defaultValue()
        }

        return value
    }
}
```
>다시 말하지만, @autoclosure이 메서드가 호출될 때마다 기본값을 평가할 필요가 없도록 하기 위해 사용 한다.

## 5. 지연된 실행
'지연된 실행' 이라는 단어는 클로져의 특징과 관계가 있다. 클로져는 선언 단계에서 코딩된 내용이 바로 실행되지 않는다. 클로져가 호출되어야만 비로소 실행이 된다. 아래 예제를 보자.
```swift
var names = ["Kim", "Park", "Lee"]

let closure = {
  names.removeFirst()
}

names
// ["Kim", "Park", "Lee"]

closure()

names
// ["Park", "Lee"]
```
names 의 내용을 두 차례에 걸쳐서 확인해 봤는데, closure 자체가 호출되기 전에는 names.removeFirst() 라는 기능이 실행되지 않았음을 확인 할 수 있다. 바로 이것이 '지연된 실행(Delayed Evaluation)'이라는 말의 의미이다.

뭐 당연하다면 당연한 이야기다.

```swift
var names = ["Kim", "Park", "Lee"]

func updateNames(closure: () -> String) {
  print("Updated names array with \(closure())")
}

names
// ["Kim", "Park", "Lee"]

updateNames() {
  return names.removeFirst()
}

names
// ["Park", "Lee"]
```
updateNames() 라는 함수는 클로져를 받아서 이 클로져를 실행시키고 콘솔에 결과를 표시하는 매우 단순한 녀석이다. 앞서 본 지연된 실행이라는 이야기도 같이 들어있다.

여기서 updateNames() 를 통해 names의 첫 번째 아이템을 삭제하는 코드를 클로져를 구현하고 있다.

그런데, 만약 이 클로져 코딩 내용을 좀 더 짧게 표시하고자 하는 생떼(?)를 부릴 사람이 있을지도 모르겠다. 아래 처럼 말이다.

```swift
updateNames(names.removeFirst())
```
물론 현재 상태에서 위 코드는 에러가 발생한다. 여기서 쓰인 names.removeFirst()  코드는 지연된 실행이 아니라 즉시 실행되는 코드이다. 즉 함수 호출 전에 이미 names.removeFirst() 가 실행되어 버리고 이 결과가 updateNames() 함수에 인자로 전달되려 하고 결국 타입이 맞지 않다는 오류를 일으킨다.

이런 경우에 활용이 가능한 것이 바로 @autoclosure 속성이다.

```swift
var names = ["Kim", "Park", "Lee"]

func updateNames(@autoclosure closure: () -> String) {
  print("Updated names array with \(closure())")
}

names
// ["Kim", "Park", "Lee"]

updateNames(names.removeFirst())

names
// ["Park", "Lee"]
```
앞서 봤던 생떼가 실제로 이루어지는 기적을 볼 수 있다.

기적 같지만... 여기서 생긴 변화가 실제로는 앞서 본 클로져를 이용하는 것과 동일하게 변화한다고 생각해야 한다. @autoclosure 속성은 wrapping 이라는 걸 상기하자. 즉, @autoclosure 가 표기되어 있는 곳에 들어가는 코드는 자동으로 클로져 형식으로 한번 더 감싸져서 넘어가게 된다.
이 때문에 함수를 실행할 때에는 {} 형식의 클로저가 아닌 () 형식의 일반값을 인자 값으로 사용해야 하며, 인자 값은 코드에 작성된 시점이 아니라 해당 클로저가 실행되는 시점에 맞추어 실행된다.

## 5. 결론
- **@autoclosure 는 '구문을 클로져로 알아서 감싸달라' 라는 속성**
- '코드에 모호성을 주는 문법'은 가급적 지양하자.
- 물론 잘 쓰면 편한데, 만약 함수나 메소드의 원형에 @autoclosure 가 명시되어 있는지 미리 확인하지 않고 코드를 작성하면 문제가 발생할 여지가 있다.
- 심지어 @autoclosure 파라미터에는 일반 클로져를 넘길 수가 없다. 함수나 구문이 자동으로 클로져로 감싸지니 말이다.
- @autoclosure에 전달하는 코드가 여러줄은 불가능하다.



참고: 
- [swiftbysundell.com](https://www.swiftbysundell.com/articles/using-autoclosure-when-designing-swift-apis/)
- [seorenn.blogspot.com](http://seorenn.blogspot.com/2016/04/swift-autoclosure.html)
