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
iOS 10 부터 지원하는 [<i class="fas fa-link"></i> videoRect](https://developer.apple.com/documentation/avfoundation/avplayerlayer/1385745-videorect){:target="_blank"} property 를 사용해서 play 중인 영상의 frame을 가져올 수 있다.  

영상이 재생 중이 아닐때는 `.zero` frame을 리턴하게 된다. 그래서 영상의 사이즈를 가져오려면 영상의 재생 여부를 옵저빙 후 가져와야 한다.
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
AVPlayer와 AVPlayerLayer 세트의 생성 코드이다. 여기서 "timeControlStatus"를 KVO하여 플레이어의 상태를 옵져빙한다.


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
이후 영상이 플레이가 되면 이벤트가 발생하고 videoRect를 얻어 올 수 있다. 해당 frame으로 영상에 맞는 서브뷰들을 배치할 수 있다!
