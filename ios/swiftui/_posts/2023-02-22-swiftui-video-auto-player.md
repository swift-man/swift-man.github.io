---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "[SwiftUI] auto play AVPlayer"
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
video 를 연속으로 재생하는 플레이어를 간단하게 만들어 봤다.  


```swift
import SwiftUI
import AVKit

struct VideoAutoPlayer: View {
  @State
  private var player: AVPlayer
  private let playerDidFinishNotification = NotificationCenter.default.publisher(for: .AVPlayerItemDidPlayToEndTime)
  
  init(url: URL) {
    _player = State(initialValue: AVPlayer(url: url))
  }
  
  @Environment(\.scenePhase)
  private var scenePhase
  
  var body: some View {
    GeometryReader { proxy in
      VideoPlayer(player: player)
        .frame(height: 400)
        .ignoresSafeArea()
        .frame(width: proxy.size.height * 16 / 9, height: proxy.size.height)
        .position(x: proxy.size.width / 2, y: proxy.size.height / 2)
        .allowsHitTesting(false)
        .onAppear {
          player.play()
        }
        .onDisappear {
          player.pause()
        }
        .onReceive(playerDidFinishNotification) { _ in
          player.seek(to: .zero)
          player.play()
        }
        .onChange(of: scenePhase) { newValue in
          if newValue == .active {
            player.play()
          }
        }
    }
  }
}
```
