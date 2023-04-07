---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "UITabBarController Height 변경하기"
toc: true
toc_sticky: true
toc_label: 목차
tag: "UITabBarController"
depth:
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "UIResponder"
    url: /ios/uiresponder/
    icon: "far fa-file-alt"
  - title: "UITabBarController"
    url: /ios/uiresponder/uitabbarcontroller/
    icon: "far fa-file-alt"
---
`UIStoryBoard`를 사용한다면 `UITabBarItem`을 `CustomClass`로 적용하기 매우 쉽다. 코드 베이스라면 UITabBarItem이 UITabBarController에서 자체적으로 가지고 있기 때문에 `CustomClass`를 적용하기가 애매해진다.  

코드 베이스일때 `init()` `RunTime`에 `object_setClass`를 사용하여 `self.tabBar` `class` 를 `CustomClsss` 로 변경해 `UITabBarItem`의 Height을 변경하는 솔루션이다. 

```swift
final class CustomTabBarController: UITabBarController {
  class CustomHeightTabBar: UITabBar {
    override func sizeThatFits(_ size: CGSize) -> CGSize {
      var sizeThatFits = super.sizeThatFits(size)

      guard let window = UIApplication.shared.connectedScenes
              .compactMap({$0 as? UIWindowScene})
              .first?.windows
              .filter( { $0.isKeyWindow } ).first
      else { return sizeThatFits }

      let tabBarHeight: CGFloat = #HEIGHT#
      sizeThatFits.height = tabBarHeight + window.safeAreaInsets.bottom

      return sizeThatFits
    }
  }

  init() {
    super.init(nibName: nil, bundle: nil)
    object_setClass(self.tabBar, CustomHeightTabBar.self)
  }

  required init?(coder: NSCoder) {
    fatalError("init(coder:) has not been implemented")
  }
}
```

## object_setClass

```swift
// Objective-C 에서 사용 시
objc_setClass(self.tabBar, CustomHeightTabBar.class);
```
