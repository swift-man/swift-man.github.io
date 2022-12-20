---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "UITabBarController Height 사이즈 조절"
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
UIStoryBoard 를 사용한다면 CustomClass 를 적용하기 매우 쉽다. 코드 베이스라면 `init()` `RunTime`에 `object_setClass`를 사용하여 `self.tabBar` `class` 를 CustomClsss 로 변경해 Height을 변경하는 솔루션이다. 

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
