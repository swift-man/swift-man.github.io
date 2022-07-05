---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "[iOS] Combine, RxSwift 차이"
toc: true
toc_sticky: true
toc_label: 목차
tag: "EDD"
depth:
  - title: "Architecture"
    url: /architecture/
    icon: "fas fa-sitemap"
  - title: "EDD"
    url: /architecture/edd/
    icon: "far fa-folder-open"
---
## Deployment Target
* RxSwift
  * iOS 8.0+
* Combine
  * iOS 13.0+
  
## Platforms supported
* RxSwift
  * iOS, macOS, tvOS, watchOS, Linux
* Combine
  * iOS, macOS, tvOS, watchOS, UIKit for Mac

## Spec
* RxSwift
  * Reactive Extension(ReactiveX)
* Combine
  * Reactive Steams(+adjustments)

## Framework Consumption
* RxSwift
  * Third-party
* Combine
  * First-party(built-in)
  
## Maintained by
* RxSwift
  * Open-Source / Community
* Combine
  * Apple

## UIBindings
* RxSwift
  * RxCocoa
* Combine
  * SwiftUI
  
## Types
### Observable, Publisher
* RxSwift
```swift
// class Type
Observable<Element>
```

* Combine
```swift
//struct Type
AnyPublisher<Element, Error> 
```

### Subject
* RxSwift
```swift
PublishSubject<Element>
BehaviorSubject<Element>
Observable.just(1)
```
* Combine
```swift
PassthroughSubject<Element, Error>
CurrentValueSubject<Element, Error>
Just(1)
```

## Operator
* RxSwift
```swift
.subscribe()
.onNext()
.onComplated()
.bind(to: )
```
* Combine
```swift
.sink()
.send()
.send(completion .finished)
.subscribe()
```

## Memory
* RxSwift
```swift
Disposable 
DisposeBag()
```
* Combine
```swift
Cancellable
[Cancelable]()
```

## Thread
* RxSwift
```swift
.observe(on: )
.subscribe(on: )
```
* Combine
```swift
.receive(on: )
.subscribe(on: )
```
  
  
## 출처
[<i class="fas fa-link"></i> 상어의 개발 블로그](https://www.slideshare.net/shark-sea/combine-vs-rxswift-160610596){:target="_blank"}


