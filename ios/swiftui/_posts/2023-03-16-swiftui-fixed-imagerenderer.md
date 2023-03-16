---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "[SwiftUI] ImageRender Image 화질 문제 for scale"
toc: true
toc_sticky: true
toc_label: 목차
tag: "SwiftUI"
depth:
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "SwiftUI"
    url: /ios/swiftui/
    icon: "far fa-folder-open"
---
iOS 16 버전부터 SwiftUI 전용 `ImageRenderer` 를 통해 뷰를 이미지로 캡쳐 할 수 있다.  
일반적인 사용법은 아래와 같다.

## ImageRenderer
```swift
struct ContentView: View {
  @Environment(\.displayScale)
  var displayScale: CGFloat
  
  @State 
  var renderedImage = Image(systemName: "photo")
  
  var body: some View {
    Text("Hello ImageRender")
      .onAppear {
        let renderer = ImageRenderer(content: Text("Hello ImageRender"))

        // make sure and use the correct display scale for this device
        renderer.scale = displayScale
        
        if let uiImage = renderer.uiImage {
          renderedImage = Image(uiImage: uiImage)
        }
      }
  }
}
```

## displayScale
* [<i class="fas fa-link"></i> @Environment(\.displayScale)](https://developer.apple.com/documentation/swiftui/environmentvalues/displayscale){:target="_blank"}
Display의 scale을 넘겨준다.

## sacle
* `ImageRenderer`는 `sacle`을 세팅해도 이미지가 매우 <b>저화질</b>로 생성된다.

## AsyncImageRenderer
이 문제를 해결하려면 [<i class="fas fa-link"></i> AsyncImageRenderer](https://github.com/swift-man/AsyncImageRenderer){:target="_blank"}를 사용해 해결할 수 있다.  
`aysnc/await`를 사용해 해결하였다.

|AsyncImageRenderer|ImageRenderer|
|------|---|
|![Image](https://github.com/swift-man/AsyncImageRenderer/raw/main/Resources/fixed.png)|![Image](https://github.com/swift-man/AsyncImageRenderer/raw/main/Resources/original.png)|
|Fixed|Original|

```swift
import AsyncImageRenderer

struct ContentView: View {
  @State 
  var renderedImage = Image(systemName: "photo")
  
  var body: some View {
    Text("Hello ImageRender")
      .onAppear {
        Task {
          if let image = await AsyncImageRenderer.image(Text("Hello ImageRender")) {
            self.renderedImage = image
          }
        }
      }
  }
}
```

---

![Image](https://drive.google.com/uc?export=view&id=1-x64JqKoxRME0rz3tBHpv9GFmGb3Z3Bx)  
추후 `ImageRender`는 애플에서 더 좋게 개선해 줄 것이니 믿고 기다려 보자.  

