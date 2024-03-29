---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "[UIActivityViewController] Dismiss Bug 해결"
toc: true
toc_sticky: true
toc_label: 목차
tag: "UIViewController"
depth: 
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "UIResponder"
    url: /ios/uiresponder/
    icon: "far fa-folder-open"
  - title: "UIActivityViewController"
    url: /ios/uiresponder/uiactivityviewcontroller/
    icon: "far fa-folder-open"
---
[<i class="fas fa-link"></i> UIActivityViewController](https://developer.apple.com/documentation/uikit/uiactivityviewcontroller){:target="_blank"}는 OS 공유화면으로 매우 널리 쓰인다.  
String, Image 등 손쉽게 다른 앱에 컨텐츠를 공유할 수 있다.

일반적인 상황은 아래와 같이 사용이 가능하다.
```swift
let title: String
let image: UIImage
let activityViewController = UIActivityViewController(activityItems: [title, image], 
  applicationActivities: nil)
self.present(activityViewController, 
  animated: true, 
  completion: nil)
```

![Image](https://i.stack.imgur.com/XdTuA.gif)

## 문제의 상황
presentViewController에서 UIActivityViewController를 present 시, "이미지 저장" 등 특정 상황에서 UIActivityViewController 가 자동으로 닫히며 presnetViewController 도 같이 닫힌다. 닫기나 다른 앱에 공유하는 액션은 문제되지 않는다.  

![Image](https://drive.google.com/uc?export=view&id=1Q3fkIyhZp0uu0CvwZZRZjZ2fwoWX6ytz)  
> 아마 애플 버그 인듯?

## 해결
[<i class="fas fa-link"></i> `completionWithItemsHandler`](https://developer.apple.com/documentation/uikit/uiactivityviewcontroller/1622022-completionwithitemshandler){:target="_blank"}를 통해 완료 시점의 클로저를 제공해주는데 이를 활용해서 버그를 막을 수 있다. 코드는 아래와 같다.
```swift
let title: String
let image: UIImage
let activityViewController = UIActivityViewController(activityItems: [title, image], 
  applicationActivities: nil)

let tempViewController = UIViewController()
tempViewController.modalPresentationStyle = .overFullScreen
activityViewController.completionWithItemsHandler = { [weak tempViewController] _, _, _, _ in
  if let presentingViewController = tempViewController?.presentingViewController {
      presentingViewController.dismiss(animated: false, completion: nil)
  } else {
      tempViewController?.dismiss(animated: false, completion: nil)
  }
}

present(tempViewController, animated: false) { [weak tempController] in
  tempViewController?.present(activityViewController, 
    animated: true, 
    completion: nil)
}
```
presentViewController 가 같이 닫히는 문제는 해결할 수가 없다.  
그럼 어떻게 처리할까?  
> 우리에겐 꼼수라는 좋은 프로그래밍 방법이 있다.  

버그 발생 시 버그로 닫히는 dummyViewController를 생성하고 버그 발생 시 dummyViewController가 대신 닫히도록 한다.  

이거.. 생각보다 깔끔하게 처리된다.  
