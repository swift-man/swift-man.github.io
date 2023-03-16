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

## Frame과 Position
영상이 16:9 비율로 제작된 영상인데, 뷰의 크기가 16:9가 아니면 위아래 `검은 바` 가 생기므로 비율을 뷰 중심으로 가져가려고 추가했다.  

## @Environment(\.scenePhase)
Video는 UI라 AppLifeCycle에 영향을 받는다. 따라 자동 재생 코드를 추가해 주었다.

## .allowsHitTesting(false)
자동 재생만 되고 유저의 비디오 조작을 원하지 않으므로 `allowsHitTesting`은 `false`로 세팅해 주었다.

## AVPlayerItemDidPlayToEndTime
영상이 종료되면 다시 자동 재생 돼야 함으로 NotificationCenter를 통해 다시 재생시켜준다.
