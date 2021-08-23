---
sidebar:
  title: "iOS"
  nav: sidebar-ios
title: "App Thinning(iOS, tvOS, watchOS)"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : 최소한의 설치 공간으로 사용자의 특정 장치 및 운영 체제 버전의 기능에 맞게 앱 제공을 조정하여 iOS, tvOS 및 watchOS 앱 설치를 최적화
---
[iOS](/ios/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
- App Store 및 운영 체제는 **최소한의 설치 공간으로 사용자의 특정 장치 및 운영 체제 버전의 기능에 맞게 앱 제공을 조정하여 iOS, tvOS 및 watchOS 앱 설치를 최적화**합니다. 
- thinning 이라고 하는 이 최적화를 통해 대부분의 기기 기능을 사용하고 최소 디스크 공간을 차지하며 Apple에서 적용할 수 있는 향후 업데이트를 수용하는 앱을 생성할 수 있습니다. 
- 더 빠른 다운로드와 다른 앱과 콘텐츠를 위한 더 많은 공간은 더 나은 사용자 경험을 제공합니다.

- [WWDC 2015 - App Thinning in Xcode](https://developer.apple.com/videos/play/wwdc2015/404)

## 2. App Slicing(iOS, tvOS)
- 슬라이싱 은 다양한 대상 장치 및 운영 체제 버전에 대한 앱 번들의 변형을 만들고 제공하는 프로세스입니다. 
- 변형은 대상 장치 및 운영 체제 버전에 필요한 경우에만 실행 아키텍처와 리소스가 포함되어 있습니다. 
- 앱의 전체 버전을 계속 개발하고 App Store Connect에 업로드합니다. App Store는 앱이 지원하는 기기 및 운영 체제 버전에 따라 다양한 변형을 만들고 제공합니다. 
- App Store에서 각 변형에 적합한 이미지, GPU 리소스 및 기타 데이터를 선택할 수 있도록 자산 카탈로그를 사용하십시오. 
- 사용자가 앱을 설치하면 사용자의 장치 및 운영 체제 버전에 대한 변형이 다운로드되어 설치됩니다.

- Xcode는 개발 중에 슬라이싱을 시뮬레이션하므로 로컬에서 변형을 만들고 테스트할 수 있습니다. 
    - Xcode는 기기나 시뮬레이터에서 앱을 빌드하고 실행할 때 앱을 슬라이싱합니다. 
    - 아카이브를 만들 때 Xcode에는 앱의 전체 버전이 포함되지만 아카이브에서 변형을 내보낼 수 있습니다.

![Image](https://help.apple.com/xcode/mac/current/en.lproj/Art/app_thinning_2x.png)

## 3. Bitcode
- Bitcode 는 컴파일된 프로그램의 중간 표현입니다. Bitcode가 포함된 App Store Connect에 업로드하는 앱은 App Store에서 컴파일 및 연결됩니다.
        - Bitcode를 포함하면 Apple이 앱의 새 버전을 App Store에 제출할 필요 없이 향후 [app binary](https://help.apple.com/xcode/mac/current/#/dev7af8b1d18) 를 다시 최적화할 수 있습니다 .

- iOS 앱의 경우 Bitcode가 기본값이지만 선택 사항입니다. 
    - watchOS 및 tvOS 앱의 경우 Bitcode가 필요합니다. 
    - Bitcode를 제공하면 앱 번들의 모든 앱과 프레임워크(프로젝트의 모든 대상)에 Bitcode가 포함되어야 합니다.

- Xcode는 기본적으로 앱의 symbols을 숨기므로 Apple에서 읽을 수 없습니다. 
    - [앱을 App Store Connect에 업로드](https://help.apple.com/xcode/mac/current/#/dev442d7f2ca)할 때 기호를 포함할 수 있는 옵션이 있습니다. 
    - [앱 충돌 보고서를 제공합니다.](https://help.apple.com/xcode/mac/current/#/dev861f46ea8) 
    - [TestFlight를 사용하여 응용 프로그램을 배포](https://help.apple.com/xcode/mac/current/#/dev2539d985f) 또는 [앱 스토어를 통해 응용 프로그램을 배포](https://help.apple.com/xcode/mac/current/#/dev067853c94) 가능. 
    - 충돌 보고서를 직접 수집하고 싶다면 기호를 업로드할 필요가 없습니다. 
        - 대신 앱을 배포한 후 [비트코드 컴파일 dSYM](https://help.apple.com/xcode/mac/current/#/devef5928039) 파일 을 [다운로드](https://help.apple.com/xcode/mac/current/#/devef5928039) 할 수 있습니다.


## 4. On-demand Resource
- 키워드로 태그를 지정하고 태그별로 그룹으로 요청할 수 있는 이미지 및 사운드와 같은 리소스입니다. 
- App Store는 Apple 서버의 리소스를 호스팅하고 다운로드를 관리합니다. 
- 또한 App Store는 on-demand resource를 분할하여 앱 변형을 더욱 최적화합니다.

- 더 나은 사용자 경험을 제공합니다.
    - 앱 크기가 작아서 앱 다운로드 속도가 빨라져 최초 실행 경험이 향상됩니다.
    - 사용자가 앱을 탐색하는 동안 필요에 따라 on-demand resource 가 백그라운드에서 다운로드됩니다.
    - 운영 체제는 더 이상 필요하지 않다고 판단하고 디스크 공간이 부족할 때 on-demand resource를 제거합니다.
- 예를 들어 앱은 리소스를 수준으로 나누고 앱에서 사용자가 해당 수준으로 이동할 것으로 예상하는 경우에만 다음 수준의 리소스를 요청할 수 있습니다. 
- 마찬가지로, 앱은 사용자가 해당 인앱 구매를 할 때만 인앱 구매 리소스를 요청할 수 있습니다.

![Image](https://help.apple.com/xcode/mac/current/en.lproj/Art/on_demand_resources_2x.png)

>참고: [앱을 등록된 장치](https://help.apple.com/xcode/mac/current/#/dev7ccaf4d3c) (App Store 외부)에 [배포하는](https://help.apple.com/xcode/mac/current/#/dev7ccaf4d3c) 경우 주문형 리소스를 직접 호스팅해야 합니다.

- 앱에서 on-demand resources 를 설정하려면 아래 가이드를 확인하자.
    - [On-Demand Resources Guide](https://developer.apple.com/library/prerelease/content/documentation/FileManagement/Conceptual/On_Demand_Resources_Guide/index.html#//apple_ref/doc/uid/TP40015083)
    - [NSBundleResourceRequest](https://developer.apple.com/reference/foundation/nsbundleresourcerequest)

- 출처 - [What is app thinning? (iOS, tvOS, watchOS)](https://help.apple.com/xcode/mac/current/#/devbbdc5ce4f)
