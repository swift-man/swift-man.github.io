---
sidebar:
  title: "iOS"
  nav: sidebar-ios
title: "UIApplication Life Cycle"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : Not running, Inactive, Active, Background, Suspended
---
[iOS](/ios/) / [UIResponder](/ios/uiresponder/) / [UIApplicationMain](/ios/uiresponder/uiapplicationmain/)  / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
- Not running
- Inactive 
- Active 
- Background 
- Suspended

![Image](https://miro.medium.com/max/1400/1*n8zDfF0RCd3keeFqAqWBGA.png)

## 2. The Main Run Loop
앱의 메인 런 루프 는 모든 사용자 관련 이벤트를 처리한다. UIApplication Timer와 View 기반 인터페이스에 이벤트와 핸들 업데이트를 처리하는 데 사용의 메인 실행 루프까지 개체를 설정한다. 메인 스레드에서 실행된다. 유저 터치 이벤트를 수신된 순서대로 순차적으로 처리한다.


![Image](https://miro.medium.com/max/700/1*oDckiqvUj_95hNrFliDisw.png)

이벤트는 앱에 의해 내부적으로 대기되고 실행을 위해 하나씩 Main Run Loop 에 전달된다. UIApplication 객체는 이벤트를 수신하고 수행해야하는 항목에 대한 결정을 할 수있는 첫 번째 object 이다. 이후 터치가 발생한 뷰로 이벤트를 전달한다.

## 3. Execution States for Apps

![Image](https://miro.medium.com/max/700/1*6V0s6gR2wV81LXMAbpte6A.png)



### 3.1 Not running
앱이 실행 되지 않았거나, 실행 중이었지나 시스템에 의해 종료 상태이다.
```swift
func applicationWillTerminate(_ application: UIApplication) {
}
```

### 3.2 Foreground
#### 3.2.1 Inactive
Foreground에서 실행 중이지만 현재 이벤트를 수신하고 불가 상태. 
일반적으로 다른 상태로 전환될 때 이 상태에 잠시 동안 유지된다.
```swift
// Active -> Inactive
func applicationWillResignActive(_ application: UIApplication) {
}
```

#### 3.2.2 Active
Foreground 실행 중이며 이벤트를 수신하고 있는 상태이다.
```swift
func applicationDidBecomeActive(_ application: UIApplication) {
}
```

### 3.3 Background
Background 있고 코드를 실행 중 상태. 대부분의 앱은 일시 중단되는 도중 잠시 이 상태에 들어갑니다. 그러나 추가 실행 시간을 요청하는 앱은 일정 시간 동안 이 상태를 유지할 수 있다. 또한 백그라운드로 직접 실행되는 앱은 비활성 상태가 아닌 이 상태가 된다.

```swift
// Foreground -> Background
func applicationDidEnterBackground(_ application: UIApplication) {
}
```

```swift
// Background -> Foreground
func applicationWillEnterForeground(_ application: UIApplication) {
}
```

### 3.4 Suspended
Background 있고 코드 미 실행 상태. 시스템은 앱을 자동으로 이 상태로 이동하고 앱에 알려주지 않는다.  메모리 부족 상태가 발생하면 시스템은 Foreground 앱을 위한 더 많은 공간을 확보하기 위해 예고 없이 Suspended 된 앱을 종료할 수 있다.

## 4. The lunch cycle
### 4.1 Launching an app into the foreground
![Image](https://miro.medium.com/max/700/1*0XS9grFLWcz6Quzdu5syGw.png)
### 4.2 Launching an app into the background
![Image](https://miro.medium.com/max/700/1*5LKm3FR67tuGYEeh_eDgIA.png)
### 4.3 Moving from the foreground to the background
![Image](https://miro.medium.com/max/700/1*xPCYq-6QcCR8FvB1L1_jfw.png)

- 출처 : [https://medium.com/@neroxiao/ios-app-life-cycle-ec1b31cee9dc](https://medium.com/@neroxiao/ios-app-life-cycle-ec1b31cee9dc)
