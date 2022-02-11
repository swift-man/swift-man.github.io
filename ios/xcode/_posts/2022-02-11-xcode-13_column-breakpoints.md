---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "Xcode 13 Column Breakpoints"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Xcode"
depth:
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "Xcode"
    url: /ios/xcode/
    icon: "far fa-folder-open"
---
구글 번역기로 돌린 번역입니다. 잘못된 오역이 있음을 주의하여 주세요.👀

Xcode 13은 보다 세분화된 버전의 column breakpoints처럼 작동하는 line breakpoints이 추가되었다.  
사용 방법은 다음과 같다.

## Setting Breakpoints
Xcode는 다양한 유형의 breakpoint를 지원하지만 제가 가장 많이 사용하는 것은 line **breakpoint** 이다. 
breakpoint line에서 소스 코드 편집기의 여백을 클릭하여 설정한다.

![Image](https://useyourloaf.com/blog/xcode-column-breakpoints/001@2x.png)

대부분 line breakpoint를 많이 사용하지만 **부족할 때**가 있다. debugger는 확인하려는 코드에 도달하기 전에 property initializers, getter 및 기타 메서드를 단계별로 실행하거나 실행할 수 있다.

만약 가로 열에 breakpoint를 잡으려면 어떻게 해야 할까? debugger가 breakpoint에 도달하면 `countries` 첫 번째 메서드의 인수에서 잡힌다.(밑줄이 어떻게 표시되는지 확인)

![Image](https://useyourloaf.com/blog/xcode-column-breakpoints/002@2x.png)

두 번째 방법에 도달하려면 countries속성 이니셜라이저에 들어가고 나와야 한 다음 `visited`메서드에 들어가고 나와야 한다.

## Column Breakpoints

largerThanXcode 13부터 메서드 에 직접 열 breakpoint을 설정할 수 있습니다. 기호를 Command-클릭하면 열 breakpoint을 설정할 수 있는 코드 작업 메뉴가 표시된다.

![Image](https://useyourloaf.com/blog/xcode-column-breakpoints/003@2x.png)

Xcode는 소스 코드의 열에서 breakpoint을 작은 캐럿으로 표시한다.

![Image](https://useyourloaf.com/blog/xcode-column-breakpoints/004@2x.png)

line breakpoint와 같은 방법으로 breakpoint을 변경할 수 있다. breakpoint을 클릭하여 활성화/비활성화한다. 삭제하려면 멀리 드래그하면 됨. breakpoint을 편집하고 조건 및 작업을 추가하려면 두 번 클릭한다. breakpoint을 Control-클릭하면 breakpoint 메뉴가 표시된다.. Xcode는 또한 breakpoint 탐색기에 breakpoint을 표시된다.

디버거가 열 breakpoint에 도달하면 이미 `largerThan`메서드에 있다.

![Image](https://useyourloaf.com/blog/xcode-column-breakpoints/005@2x.png)

## Working With Closures

breakpoint에 대한 [<i class="fas fa-link"></i> WWDC 2021 비디오](https://developer.apple.com/videos/play/wwdc2021/10209){:target="_blank"}에서는 복잡한 Swift 클로저 세트로 작동하는 열 breakpoint의 예를 보여줍니다. Xcode가 breakpoint에 도달하면 클로저( $0)의 익명 매개변수를 검사할 수 있다.

나는 그것을 작동시키는 혼합 결과를 얻었다. 여기 예가 있습니다. `$0`마지막 클로저에서 열 breakpoint을 설정했다.

![Image](https://useyourloaf.com/blog/xcode-column-breakpoints/006@2x.png)

불행히도 디버거는 해당 위치에서 중단되지 않는다. 피드백(FB9190264)을 제출했고 Apple 엔지니어로부터 유용한 설명을 받았다.

>compiler 익명 ​​매개변수에 대해 생성하는 항목에 따라 다르다. 때때로 $0은 레지스터에서 오는 것처럼 간단하므로 컴파일러는 이에 대한 코드를 생성할 필요가 없다. 이러한 상황에서는 설정할 수 있는 breakpoint 위치가 없다.

Xcode가 해결되지 않은 breakpoint 아이콘 을 표시할 때 내 예제를 실행할 때:

![Image](https://useyourloaf.com/blog/xcode-column-breakpoints/008@2x.png)

Xcode는 breakpoint navigator에 해결되지 않은 breakpoint 아이콘도 표시한다.

![Image](https://useyourloaf.com/blog/xcode-column-breakpoints/009@2x.png)

아이콘 위로 마우스를 가져가면 해결되지 않은 breakpoint에 대한 설명이 표시된다.

![Image](https://useyourloaf.com/blog/xcode-column-breakpoints/010@2x.png)

Xcode는 해결되지 않았기 때문에 이 breakpoint으로 일시 중지되지 않는다. 이 문제를 해결하려면 다음이 필요하다.

* 컴파일러는 열 breakpoint의 식에 대한 위치를 생성한다. 그러한 위치가 없는 것은 유효하다.
* breakpoint의 줄이 컴파일된다.
* 컴파일러는 제거되지 않은 디버그 정보를 생성한다(빌드 설정 확인).
* breakpoint에 대한 라이브러리가 로드 됨.

## Further Details
[<i class="fas fa-link"></i> WWDC 2021 Discover breakpoint improvements](https://developer.apple.com/videos/play/wwdc2021/10209){:target="_blank"} 

## 출처
[<i class="fas fa-link"></i> Xcode Column Breakpoints](https://useyourloaf.com/blog/xcode-column-breakpoints/){:target="_blank"}  
