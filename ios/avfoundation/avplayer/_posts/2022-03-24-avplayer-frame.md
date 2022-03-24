---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "[AVPlayer] 영상 크기 가져오기"
toc: true
toc_sticky: true
toc_label: 목차
tag: "AVPlayer"
depth: 
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "AVFoundation"
    url: /ios/avfoundation/
    icon: "far fa-folder-open"
  - title: "AVPlayer"
    url: /ios/avfoundation/avplayer
    icon: "far fa-folder-open"
---
iOS 10 부터 지원하는 `videoRect` property 를 사용해서 play 중인 영상의 frame을 가져올 수 있다. 이때 영상이 재생 중이 아닐때는 `.zero` 를 리턴함으로 영상이 재생 중인지 확인 후 가져와야 한다.
```swift
import AVKit

var playerLayer: AVPlayerLayer?
```

```swift
private func setupAVPlayer() {
  let player = AVPlayer(url: videoURL)
  player.addObserver(self,
                     forKeyPath: "timeControlStatus",
                     options: [.old, .new],
                     context: nil)
  player.isMuted = true // 음소거 여부
  let playerLayer = AVPlayerLayer(player: player)
  view.layer.addSublayer(playerLayer)
  
  self.playerLayer = playerLayer
}
```

```swift
override func observeValue(forKeyPath keyPath: String?,
                           of object: Any?,
                           change: [NSKeyValueChangeKey: Any]?,
                           context: UnsafeMutableRawPointer?) {
  guard
    object as AnyObject? === player,
    keyPath == "timeControlStatus",
    player?.timeControlStatus == .playing
  else { return }
  
  print(playerLayer?.videoRect)
}
```
