---
sidebar:
  title: "Architecture"
  nav: sidebar-architecture
  icon: "fas fa-sitemap"
title: "[TDD] iOS"
toc: true
toc_sticky: true
toc_label: 목차
tag: "XCUITest"
depth:
  - title: "Architecture"
    url: /architecture/
    icon: "fas fa-sitemap"
  - title: "TDD"
    url: /architecture/tdd/
    icon: "far fa-folder-open"
---
## TDD
* Test Driven Development
* 테스트코드를 먼저 짜고 구현을 나중에 하는 개발 방식
* Extreme Programming의 실천법 중 하나
> Extrame Programming<br/>
좋은것은 먼저 해보자라는 극단적인 프로그래밍 방식





## 왜
### 시안만 봤을 땐 어떤 스펙이든 단순해보인다.
* 간단해 보이는 프로그램도 잘 숙달한 프로그래머는 20~30개 정도의 테스트 케이스가 생긴다.  

### 테스트케이스 작성 = 숨은 복잡도 발굴  
* 테스트케이스가 만들어저야 일정산정이 가능하다.  
* 개발을 하면서 테스트케이스를 추가하면, 소통비용이 많이 든다.  
  * 급하게 구현을 하면 잘 만들어지기 어렵다.
* 테스트케이스 작성을 위해 새로운 코딩기법을 배울 필요는 없다.
  * 종이와 펜만 있어도 시작 할 수 있다.
  * 좋은 TC작성에는 꾸준한 훈련, 상상력, 경험이 필요하다.
  * QA 엔지니어들이 어떤 도구를 쓰고 어떤 고민과 훈련을 하는지 살펴보자.

### 하는 김에 자동화까지!
* 어차피 테스트케이스를 작성했다면
* 테스트에 필요한 데이터까지 준비 되었다면
* 그 테스트를 자동으로 실행시킬 순 없을까?

## 어떻게
### 빌드시간 줄이기
* 테스트는 즉시 실행될 수 있어야 함  
> iOS 앱은 조금만 복잡해도 빌드시간이 오래 걸림<br/>
그래서 iOS에서 TDD가 실천하는 경우가 적음

* 빌드시간을 최대 30초 이내로 줄여야 TDD는 현실적
  * 방안 1: 모듈화
    * 기능별, 레이어 별 책임을 나누면 병렬 빌드가 가능
    * 해당 모듈의 테스트만 실행 할 수 있음
  * 방안 2: 의존성 미리 빌드
  * 방안 3: Library Test 활용
  
## 종이에 시작하기
* 요구사항을 입력과 출력으로 쪼개는 연습을 하자.
> 기획서를 입력과 출력으로 보는 훈련을 해야한다.

* 자동화된 테스트에 활용되지 못하더라도,
  * 수동 테스트를 할때,
  * 커밋메시지를 쓸 때,
  * PR을 날릴 때 활용 될 수 있다.



## 무엇을
### 100%의 함정에 빠지지 않기
* 100%가 아니면 의미 없다는 착각에 빠지기 쉽다.
* 100% SwiftUI, MVVM, Swift 등등..
* 그것이 무엇이든, 한 번에 적용하려면 부작용이 일기 마련
* 내가 할 수 있는 것부터, 손에 닿는 것 부터 차근차근 실천해 나가자.

### 이벤트 로깅
* Firebase 등 자주 들어가는 버튼이나 화면을 기록하는 기능
* 입력과 출력이 명확함
* 회사의 명운을 좌우할 수도 있음
* 해당 스펙에 대한 개괄적 이해가 가능함
* 평소에 눈에 보이지 않기에 누락 될 가능성

```swift
func test버튼_누르면_로깅() {
  given {
    viewModel = SampleViewModel(data: "Hello")
  }
  
  when {
    createEvents([.next(0, Void())], to: viewModel.buttonClicked)
  }
  
  then {
    XCTAssert(resultEventsNames == [.next(0, "clicked__Hello")])
  }
}
```
### 접근성 경험
* 입력과 출력이 명확함
* 해당 화면에 대한 개괄적 이해가 가능함
* 평소에 눈에 보이지 않기에 누락 될 가능성

```swift
func testMyViewController() anyc throws {
  let viewController = MyViewController()
  await viewController.doSomeBusinessLogic()
  
  XCTAssert(
    viewController.axSnapshot() == """
    ------------------------------------------------------------
    Final Result
    button, header
    Double Tap to see detail result
    Actions: Retry
    ------------------------------------------------------------
    The question is, The answer to the Life, the Universe, and Everything
    button
    ------------------------------------------------------------
    The answer is, 42
    button
    ------------------------------------------------------------
    """
  )
}
```

## 결론
* 테스트가능성도 기능입니다.
* 테스트코드는 돈을 벌어줍니다.
* 테스트코드는 개발을 더 쾌적하고 즐겁게 만들어줍니다.


## 출처
[<i class="fas fa-link"></i> 
[WWDC22 함께보기] 03. 나의 TDD 경험기 (feat. 류성두)](https://www.youtube.com/watch?v=NA4ZwtIFYpA&ab_channel=%EC%8A%A4%EC%9C%84%ED%94%84%ED%8A%B8%ED%95%98%EC%9D%B4){:target="_blank"}  
[<i class="fas fa-link"></i>  AXSnapshot](https://github.com/banksalad/AXSnapshot){:target="_blank"}

