---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "[Xcode] UIKit 기반 코드 베이스 프로젝트 세팅하기"
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
UIKit 기반 code base 프로젝트를 생성하는 방법이다. 개발을 하다 보면 UIKit 기반 프로젝트가 필요할 때가 있다.  
> 이 글은 Xcode 14.0.1을 기반으로 합니다.

## 왜 UIKit Code Base인가?
`SwiftUI` 프로젝트를 생성하고 계속 개발하고 싶으나, 고대부터 이어온 코드를 모두 바꾸기란 시간과 노력이 필요하다. 현업에서 오래 유지해온 프로젝트라면 아직 UIKit 기반 프로젝트가 많을 것이며, 필자가 현재 현업에서 운영하는 프로젝트는 2022년 기준 10년이 된 프로젝트이다. UIKit 기반 프로젝트를 운영하고 있다.

![Image](https://drive.google.com/uc?export=view&id=1NM-xz0OY7K08yhhwz5mhnppeEffTUGYh)  
> 짜잔 내가 돌아왔다.<br/>
잭스는 출시한 지 오래되었으나, 지속적으로 사람들에게 사랑받은 챔피언이며, 이동, CC, 방어, 공격 등 여러모로 기본기가 좋은 챔피언이다.

### StoryBoard를 써야 하나?
장/단점이 있다. 특히 UI의 property와 구현되어 있는 기본적인 사항을 한눈에 볼 수 있다. 또한 `@IBOutlet`, `@IBAction` 등의 어노테이션으로 뷰를 생성하고 연결해 관련 코드들이 없어져 뷰 로직에 집중할 수 있다. 뷰가 복잡해질수록 코드가 더 줄어들기 때문에 분석하기가 매우 쉽다. 또한 Autolayout의 오류를 시각적으로 보여주기 때문에 관리의 편의성도 있다.  

문제는 xml 기반이라는 것인데, 다른 개발자와 협업하기가 어렵다. 기능은 지속적으로 변한다. 변하는 기능의 코드의 변경사항이 `Git - Pull Request`로 올라오면 다른 개발자는 어떤 코드가 수정되었는지 알기 어렵다. 따라 코드 리뷰를 통해 동료 개발자가 더 빠르게 코드 변경을 인지 하도록 하려면 코드베이스가 좋다.  

Apple의 M1 이상 컴퓨터에서는 속도가 많이 개선되었으나 코드 베이스보다 파일을 읽어오는 속도가 느리다는 단점도 있다.

### 코드 베이스의 단점
UI 코드를 작게 만들면 코드 분석과 재사용성이 증가한다. 복잡해질수록 한눈에 코드를 읽고 UI를 분석하기가 어려워지는데, 이를 해결하기 위해 SwiftUI의 Preview를 사용할 수 있다. 그러나 UIKit 기반의 Preview도 한계가 있다.

### 코드 베이스의 장점
코드 리뷰를 생각한다면 이점이 많다. 개발자끼리의 협업은 매우 중요한데, 단순한 수정사항도 다른 개발자가 빠르게 확인하고 피드백을 받을 수 있다.  

또한 UIKit은 class 기반이며 상속으로 만들어져 있다. 이점을 활용하여 UI 간 상속을 통해 중복되는 코드들을 해결할 수 있다. StoryBoard 베이스의 `custom view`를 만들면 이러한 상속 구조, composable 한 조합의 View들은 구성하기 제약이 있다.

> 복잡한 Autolayout 설계가 필요한 화면을 개발할 때 Storyboard 기반으로 만들고, 이를 Code화 하는 형태로 하면 유용하다.

## 프로젝트 생성
이제 프로젝트를 생성해보자.
```
Xcode > New Project > iOS > App > Next
```

![Image](https://drive.google.com/uc?export=view&id=1Z39uPrP5Ntv8UEyNvVWKhZf6jHkpRlle)  


![Image](https://drive.google.com/uc?export=view&id=1daoAhmUUCjJOR3Hn7QjaYRKOnUmLrik3)  
StoryBoard를 선택하자.

> 언젠가부터 Xcode `New Project - iOS`는 `StoryBoard` 와 `SwiftUI` 기반 프로젝트 생성만 지원한다.

![Image](https://drive.google.com/uc?export=view&id=1MVg46UzSQxWaZ_EgEocDT3UfVi6VnQ_F)  
프로젝트 완성!  
위 이미지의 빨간색 3가지를 건드려야 한다. 종합해 보면
* 완쪽 `File Nvigator` - `main.storyboard` 파일 삭제
* `Info.plist` - `Configuration Name` 필드 삭제
* Build Setting - `UIKit Main StoryBoard File Base Name` 값 삭제 

## File Navigator
왼쪽 파일 목록에서 `Main` 을 오른쪽 클릭하여 `Delete`를 클릭한다.
![Image](https://drive.google.com/uc?export=view&id=1XCJ7iQNmuV6kab52zf3hJFF4WtYvdHK3)  
![Image](https://drive.google.com/uc?export=view&id=1b9sjI6Xn_KwLodl_4eEZFYGf2kEz3SiD)  
파일을 완전히 삭제할 것임으로 `Move to Trash`를 눌러준다.

![Image](https://drive.google.com/uc?export=view&id=1qTC_R4tVZ9NLp6ZuteRgIVn3oO6UaCOz)  
빌드해보면 `Consol Log`에 
>Could not find a storyboard named 'Main' in bundle NSBundle
라는 오류와 함께 Runtime Crash 가 발생한다.

## Info.plist
Info.plist 로 이동하자. 
![Image](https://drive.google.com/uc?export=view&id=143_DlLgC26yCXH69Gvhi7BUtQ1zUppl-)  
[<i class="fas fa-link"></i> info.plist](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Introduction/Introduction.html#//apple_ref/doc/uid/TP40009248-SW1){:target="_blank"}파일은 실행 package에 대한 필수 정보들을 구조화된 텍스트 파일로 세팅할 수 있으며, 앱은 해당 정보를 읽어 프로젝트를 구성한다.  

* Application Scene Manifest
  * Application Session Role
    * Item 0(Default Configuration)
      * Configuration Name (삭제)  

![Image](https://drive.google.com/uc?export=view&id=1dfvU2sxk45Q47XgomG6CcNVJiPUyfk-K)  
필드 자체를 삭제하자.

![Image](https://drive.google.com/uc?export=view&id=1v8Qwqz8wpyK8ZjAMN3iQn6WLuUyNIWTZ)  
필드를 삭제하면 위와 같이 필드가 사라지게 된다.

## Build Settings
빌드 세팅에도 `Main.storyboard` 의 흔적이 있다. 이곳의 정보를 지워야 한다.

![Image](https://drive.google.com/uc?export=view&id=15PfvGVnO0oNXMRX1iGUO6PymFwsK8gsA)  
검색창에 'Main'을 검색해보자. `UIKit Main Storyboard File Base Name` 필드가 보인다. 

![Image](https://drive.google.com/uc?export=view&id=1DgpbIGw5EdBioxJ-sfBDqCuGy182fEuw)  
해당 필드의 값을 지워 공백으로 만들자.

![Image](https://drive.google.com/uc?export=view&id=1AlKg-50sPMnAlhqp-s_uZHIiRkH7lEBD)  



## SceneDelegate Code
이제 프로젝트의 코드를 수정해야 한다.  
기본적으로 `SceneDelegate` 는 화면에 무엇을 보여줄지 관리하는 역할이다.  

```swift
func scene(_ scene: UIScene, 
           willConnectTo session: UISceneSession, 
           options connectionOptions: UIScene.ConnectionOptions) {
  // Use this method to optionally configure and attach the UIWindow `window` to the provided UIWindowScene `scene`.
  // If using a storyboard, the `window` property will automatically be initialized and attached to the scene.
  // This delegate does not imply the connecting scene or session are new (see `application:configurationForConnectingSceneSession` instead).
  guard let _ = (scene as? UIWindowScene) else { return }
}
```
`SceneDelegate`의 `func scene(_ :, willConnectTo, options:)`은 lifecycle 에서 가장 처음 불리며, 새로운 [<i class="fas fa-link"></i> UIWindow](https://developer.apple.com/documentation/uikit/uiwindow){:target="_blank"}
를 생성하고 window의 rootViewController를 생성하는 역할을 한다.
> UIWindow는 사용자가 보는 layer가 아닌, `user interface`에 대한 이벤트를 전달하는 개체이다.


```swift
func scene(_ scene: UIScene, 
           willConnectTo session: UISceneSession, 
           options connectionOptions: UIScene.ConnectionOptions) {
  
  guard let windowScene = (scene as? UIWindowScene) else { return }
  window = UIWindow(windowScene: windowScene)

  window?.rootViewController = ViewController()
  window?.makeKeyAndVisible()
}
```
위와 같이 `UIWindow`를 `UIWindowScene`으로부터 생성하고 `rootViewController`를 설정하자.

## 동작 확인

```swift
class ViewController: UIViewController {

  override func viewDidLoad() {
    super.viewDidLoad()
    
    view.backgroundColor = .systemRed
  }
}
```

ViewController의 backgroundColor를 통해 잘 연결되었는지 확인해보자.  

![Image](https://drive.google.com/uc?export=view&id=1NKVigZtKRkUgpKJCo2sLjrWJ88PNR2HJ)  
> 영롱한 systemRed

![Image](https://drive.google.com/uc?export=view&id=12kqL8y7D59xO_q4oTHX2EnQhUR7QC-Ap)  

완성된 프로젝트는 해당 링크[<i class="fas fa-link"></i> UIKit-Code-Based-Project](https://github.com/swift-man/UIKit-Code-Based-Project){:target="_blank"}에서 확인할 수 있다.
