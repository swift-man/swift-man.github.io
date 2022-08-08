---
sidebar:
  title: "IT"
  nav: sidebar-it
  icon: "fas fa-mobile-alt"
title: "[WWDC22] What's new in Swift 5.7"
toc: true
toc_sticky: true
toc_label: 목차
tag: "IT Conference"
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: https://drive.google.com/uc?export=view&id=1Ql6FXg4a-GmRAzvwnJIcn7ONjyMbfEs0
excerpt: "Community update, Swift on Server, Swift packages..."
---
# What's new in Swift


## New Features in Swift 5.7
Swift의 목표는 개발자의 삶은 더 쉽게 만들기 위함이라고 함!

## Community update
### Swift Website(new)
![Image](https://drive.google.com/uc?export=view&id=1Ql6FXg4a-GmRAzvwnJIcn7ONjyMbfEs0)  

* docC와 Swift를 통해 커뮤니티에서 더 활성화되고 있음
* [<i class="fas fa-link"></i> swift.org](https://www.swift.org/){:target="_blank"}는 opensource이며 많은 개발자가 참여 중
> Open Source를 적극적으로 관리할 때 Swift와 제품은 가장 잘 작동
  
## Swift on Server
### C++ Interoperability
* Swift on Server, Swift의 다양한 작업 그룹 모델을 사용 중인데,
  * 이것을 이제 두 개의 새로운 작업 그룹으로 시작함
    * Swift Website, community resouce
    * C++, Swift 간의 모델 디자인을 형성하기 위한 운용
    
### Diversity in Swift
* Swift를 쉽게 사용할 수 있도록 Linux 플랫폼 배포 간소화(RPM 지원)
  * Amazon Linux 2
  * CentOS 7
    * 하지만 매우 실험적이기 때문에 피드백을 원함

> Swift는 서버에 더 잘 지원하기 위해 노력하고 있음

## Swift packages
![Image](https://drive.google.com/uc?export=view&id=1UaC9SNh3WCp5mQ2izjbqcvXuUuRCngPT)  
### 새로운 보안 프로토콜인 TOFU(Trust On First Use)를 도입
  * package를 첫 다운로드 시 지문의 유효성을 검사하도록 변경
  * 보안과 신뢰 위해서라고 함

### [<i class="fas fa-link"></i> Command plug-ins](https://theswiftdev.com/beginners-guide-to-swift-package-manager-command-plugins/){:target="_blank"}
  * Swift Developer의 workflow를 개선하는 좋은 방법
  * 더 확장 가능하고, 안전한 빌드 도구를 제공
  * 문서 생성, 소스 코드 재 포맷 등에 사용할 수 있음
  * 쉘 스크립트로 자동화를 작성하고 별도의 워크 플로를 유지하는 대신 Swift를 사용 가능

![Image](https://drive.google.com/uc?export=view&id=1ZlPYFWkcKNKJktztnKI83rVt27Meui_R)    
### docC
  * Objective-C 지원
  * C 지원
  
![Image](https://drive.google.com/uc?export=view&id=14nOvln6tr-TuTpRSNx9wO_dNcpeqBDul)  


![Image](https://drive.google.com/uc?export=view&id=11llrHojvhFRz0ECJIXGMDyv-RpW7uxKF)  
* 추가 빌드 단계를 구현할 수 있는 플러그인
* 예) 소스코드 생성, 리소스 처리

### ModuleAliases
![Image](https://drive.google.com/uc?export=view&id=1mJYlWYX1I9UVbXaZ6XHCDEvyOg7iPsLW)  

* 동일한 이름으로 인한 모듈 충돌 해결

![Image](https://drive.google.com/uc?export=view&id=1UeUT0kCimBOdTFK_nHu_uDO63l2IxmOh)  
* 패키지를 통해 모듈의 이름을 변경할 수 있음

> Package Plugins에 대한 자세한 세션은 아래 참고
![Image](https://drive.google.com/uc?export=view&id=1oy2OVupOIpbVuVWW346mzqRQJcMoDB4m)  
[<i class="fas fa-link"></i> Meet Swift Package plugins](https://developer.apple.com/videos/play/wwdc2022/110359/){:target="_blank"}  
[<i class="fas fa-link"></i> Create Swift Package plugins](https://developer.apple.com/videos/play/wwdc2022/110401){:target="_blank"}  

## Swift driver setting
* Swift 소스코드의 컴파일을 제어
* 별도 실행 대신 Xcode 빌드 시스템 내에서 사용할 수 있음
* 빌드 시간 5~25% 개선

> Swift driver setting 에 대한 자세한 세션은 아래 참고
![Image](https://drive.google.com/uc?export=view&id=1jMw4Jrt_-PY4VyzUD_fzQ6EsayGimELE)  
[<i class="fas fa-link"></i> Demystify parallelization in Xcode builds](https://developer.apple.com/videos/play/wwdc2022/110364/){:target="_blank"}  

## Performance improvements
### Swift 표준 라이브러리가 더 작고 빨라짐
* 이벤트 기반 서버 솔루션에서 장점
  
![Image](https://drive.google.com/uc?export=view&id=1q_nzymfiL1mV0EQ7y-EUa0MLX_kVG55T)  

### 제네릭 검사가 더 빨라짐
* 병렬 빌드화(build parallelization)와 더 빠른 검사 덕분

### 그동안 프로토콜이 많으면 iOS에서 프로토콜 검사가 4초까지 걸렸는데 이를 캐시 함
* Swift에 의존하는 경우 최대 2배까지 향상 가능
    
> 성능에 대한 자세한 세션은 아래 참고
![Image](https://drive.google.com/uc?export=view&id=1CdO13pi2XaSM7trw0W_QLuDhyUeZu4D1)  
[<i class="fas fa-link"></i> Improve app size and runtime performance
](https://developer.apple.com/videos/play/wwdc2022/110363/){:target="_blank"}  

## Concurrency model
### Data race safety
![Image](https://drive.google.com/uc?export=view&id=1LCepA5zdb6ddaaF9okbiYsTB6tFiQnRZ)  
![Image](https://drive.google.com/uc?export=view&id=1JGCXKF-09kdxqlwjUJhIhqwNnxwjdsPi)  

> Data race safety 에 대한 자세한 세션은 아래 참고
![Image](https://drive.google.com/uc?export=view&id=1WWfZAryIe9HhKCUp0kiNVFKPxihsNkbC)  
[<i class="fas fa-link"></i> Eliminate data races using Swift Concurrency
](https://developer.apple.com/videos/play/wwdc2022/110351/){:target="_blank"}  

### async/await/actor가 swift5에 복사된 번들 제공
* 이를 통해 iOS 13 등 더 낮은 OS도 지원 가능
* data race 안정성을 더욱 구체화함 
* actor는 우선순위가 높은 작업을 실행

> Swift 5 가 ABI를 지원한다고 해서 가능한 듯?

### distributed keyword
![Image](https://drive.google.com/uc?export=view&id=1wSHfcX-lPlVIAWVIJDicjX2Ds02DOwin)  
* 네트워크 상의 다른 시스템 액터
* 백앤드를 위한 서버 측 분산 시스템 구축에 중점을 둠

> distributed keyword에 대한 자세한 세션은 아래 참고
![Image](https://drive.google.com/uc?export=view&id=1YhygBkQAE6AQ2nZZHYE6QZ-IiV2369Ch)  
[<i class="fas fa-link"></i> Meet distributed actors in Swift
](https://developer.apple.com/videos/play/wwdc2022/110356/){:target="_blank"}  

### Async Algorithms package
![Image](https://drive.google.com/uc?export=view&id=13EQtkAlYfJH0d339nF-oCM6sibrtcRjE)  
* AsyncSequence - 비동기 스케쥴링 알고리즘을 위한 패키지
* Apple, Linux, Windows 지원

### Swift concurrency instruments
![Image](https://drive.google.com/uc?export=view&id=1Vv78PWllJa7pTp6aRktjDP9f8ybymm2P)  
* Swift Tasks, Swift Actors를 통해 동시성 코드를 시각화
    * 작업의 수, 총 작업 등 통계 제공
    * 작업 간의 상속 관계에 대해 그래프 제공 

> Swift concurrency instruments에 대한 자세한 세션은 아래 참고
![Image](https://drive.google.com/uc?export=view&id=18i-k0d5WJl5fWwD7Tew8QCqpRR6zAHgN)  
[<i class="fas fa-link"></i> Visualize and optimize Swift concurrency
](https://developer.apple.com/videos/play/wwdc2022/110350/){:target="_blank"}  

## Optional unwrapping
![Image](https://drive.google.com/uc?export=view&id=1OnGJnPI-fpu0PXpWsS-nAi2Ws2JyoebR)  
![Image](https://drive.google.com/uc?export=view&id=1RARPSyroHRFXnf3M19_HiGXUhxgQv0up)  

`if let`, `guard` 에 대한 변수 네이밍을 반복하지 않고 Optional Unwrapping 가능

```swift
while let workingDirectoryMailmapURL {
    print (workingDirectoryMailmapURL)
    break
}
```


## Closure type inference
### Closure에 대한 타입 추론이 향상됨
![Image](https://drive.google.com/uc?export=view&id=1AhCJLB3S0MOA2YkF1j0HwO-csIC7YX8S)  

### `String`과 같은 복잡한 Closure의 return Type을 추론할 수 있음
```swift
let scores = [100, 80, 85]

let results = scores.map { score in
    if score >= 85 {
        return "\(score)%: Pass"
    } else {
        return "\(score)%: Fail"
    }
}
```

### closure에 try를 사용할 수 있음
![Image](https://drive.google.com/uc?export=view&id=1HtkWsDEnhBceKtjeEEUo8iT5LOR0bDJT)  

## Permitted pointer conversions
![Image](https://drive.google.com/uc?export=view&id=1yq0s7Egt97zf8U7FbFKg3HeN1w383Mat)  

* Swift <-> C 간 허용 포인터 변환을 개선
* Swift는 기존적으로 Type, Memory에 safety 함
  * 다른 Type의 pointer로 자동으로 변환되지 않음
        
![Image](https://drive.google.com/uc?export=view&id=1x2HQcMVLPpDeavwPu6x-UY3oZEeFB2BV)  
![Image](https://drive.google.com/uc?export=view&id=12DOj8AF_IkvM-5czYzI6Fh_UwciUQILm)  
* C는 특정 포인터로의 변환을 허용(Swift와 다름)
  * 쉽게 전활 할 수 있도록 특별 처리
    
![Image](https://drive.google.com/uc?export=view&id=1n2HRbwvkiGScsR5SzzksDnNKsoWfxV50)  

* Swift는 C API를 사용할 때 문제가 발생했었음
  * Swift는 function, method call에 대한 별도의 규직 집합이 있음
  * 일반적으로 Swift에는 없는 C에서 포인트 변환을 허용  
      
## Swift Regex
### 현재 문자열 구문 분석이 매우 어려움
![Image](https://drive.google.com/uc?export=view&id=1huNmWbvMeBIIV2guSEaWF8W7DG8uisRy)  
* 인덱스를 접근하는 형태는 더 어려움

### 애플은 이런 문제에 대해 정규식으로 해결하는 것을 제안
![Image](https://drive.google.com/uc?export=view&id=1Wqxna3jmO21KQ0_CDBYIgjhcDt7lhlOk)  
* NSRegularExpression를 사용하고 있었음
* 정규식을 만드는 가장 쉬운 방법은 정규식 리터럴을 사용하는 것
  * 정규식 리터럴은 complie tile에 검사를 제공함

### NSRegularExpression도 읽기 어렵다면?
![Image](https://drive.google.com/uc?export=view&id=1kVDwZLC0MFg9FNEEY0Ne6ol77BzC_mep)  
* `RegexBuilder` 통해 더 읽기 쉬운 코드 작성 가능  
* Swift 5.7에서는 구문이 훨씬 간결해 짐
  * SwiftUI와 매우 유사한 방식의 문법

### @RegexComponentBuilder 제공
![Image](https://drive.google.com/uc?export=view&id=1J04Jg5YfABurTj15jxX3EmH4EVm6XhOM)  
* 이를 통해 재사용한 Component를 작성 가능

### `Date`에 대해서도 지원
![Image](https://drive.google.com/uc?export=view&id=1ku-qsWPYTwgp7lGimOqR-GhZGGGgSqrE)  


> Swift Regex에 대한 자세한 세션은 아래 참고
![Image](https://drive.google.com/uc?export=view&id=1piCSXnYhGypZdLletZX0gaJqa-_Pbgqh)  
* 유니코드와 호환
* 최소 버전 : macOS 13, iOS 16, tvOS 16, watchOS 9
[<i class="fas fa-link"></i> Meet Swift Regex
](https://developer.apple.com/videos/play/wwdc2022/110357/){:target="_blank"}  
[<i class="fas fa-link"></i> Swift Regex: Beyond the basics
](https://developer.apple.com/videos/play/wwdc2022/110358/){:target="_blank"}  

## Generics
* "only be used as a generic constraint" 오류를 swift 5.7에서 수정
* 제네릭의 정의를 단순화

![Image](https://drive.google.com/uc?export=view&id=1jXTzU8iP9QSh3vJQOf0QSwOwxQjt-dpM)  
![Image](https://drive.google.com/uc?export=view&id=1M6xyySHVO4_asG2kAvzmVrx1nNXPel10)  
![Image](https://drive.google.com/uc?export=view&id=1f70F69wtt5HN7N1aafYUbSUEpKSgPSq-)  
![Image](https://drive.google.com/uc?export=view&id=15j9kQ55FfXBGvvy7SvnI7YMIB6AgYm0l)  

### Protocol을 Type으로 사용하는 것에 대한 완화
```swift
let tvShow: [any Equatable] = ["Brooklyn", 99]
```

> Generics 에 대한 자세한 세션은 아래 참고
![Image](https://drive.google.com/uc?export=view&id=1HEgP55yowVtj7fyok0gCIRcMLZZQuRnK)  
[<i class="fas fa-link"></i> Embrace Swift generics
](https://developer.apple.com/videos/play/wwdc2022/110352/){:target="_blank"}  
[<i class="fas fa-link"></i> Design protocol interfaces in Swift
](https://developer.apple.com/videos/play/wwdc2022/110353){:target="_blank"}  

## 출처
[<i class="fas fa-link"></i> What's new in Swift](https://developer.apple.com/videos/play/wwdc2022/110354/){:target="_blank"}
