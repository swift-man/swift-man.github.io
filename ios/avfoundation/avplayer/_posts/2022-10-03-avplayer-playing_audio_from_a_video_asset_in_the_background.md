---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "[AVPlayer] 백그라운드에서 제어"
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
[<i class="fas fa-link"></i> AVPlayer](https://developer.apple.com/documentation/avfoundation/avplayer){:target="_blank"}는 [<i class="fas fa-link"></i> Application의 Life Cycle](/ios/uiresponder/uiapplicationmain/lifecycle/)에 영향을 받는다. UI는 Background에 진입하면 동작을 멈추고, UI가 아닌 기능은 Background에서 동작한다. 

> 영상은 UI영역에 해당함으로 Background에 진입하면 자동으로 멈추게 된다.<br/>아쉽게도 자동으로 멈춘 영상은 다시 Foreground 상태가 되더라도 자동 재생되지 않는다. 따라 개발자가 다시 재생해주거나 player layer를 다시 세팅해줄 필요가 있다.

![Image](https://drive.google.com/uc?export=view&id=12zQCboBmaZY8M-lO6Cqag4-Si8fCcS0g)  

Player를 가진 Controller는 Application의 Life Cycle 과 영상 종료시점을 Notification을 통해 이벤트를 전달 받도록 하였다.
```swift
NotificationCenter.default.addObserver(self,
                                       selector: #selector(didBecomeActiveNotification(_:)),
                                       name: UIApplication.didBecomeActiveNotification,
                                       object: nil)
                                       
@objc
func didBecomeActiveNotification(_ noti: Notification?) {
  guard
      let player,
          !player.isFinished
  else { return }

  makeTimer()
  player.play()
}
```

## 특정 시간 마다 영상 플레이 타임 제어
요구사항에 따라 영상 플레이 타임을 계산해 특정 이벤트를 제어할 필요가 있다. 필자는 Rx의 Timer를 이용하였고 특정 시간을 아래와 같이 제어하여 영상의 플레이타임을 가져왔다.

```swift
NotificationCenter.default.addObserver(self,
                                       selector: #selector(didEnterBackgroundNotification(_:)),
                                       name: UIApplication.didEnterBackgroundNotification,
                                       object: nil)
                                       
NotificationCenter.default.addObserver(self,
                                       selector: #selector(avplayerItemDidPlayToEndTime),
                                       name: .AVPlayerItemDidPlayToEndTime, 
                                       object: nil)
                                         
@objc
func didEnterBackgroundNotification(_ noti: Notification?) {
  timerDisposable?.dispose()
}

@objc
func avplayerItemDidPlayToEndTime() {
  timerDisposable?.dispose()
}
    
func makeTimer() {
  timerDisposable?.dispose()
  timerDisposable = Observable<Int>.interval(.seconds(1), scheduler: MainScheduler.instance)
    .subscribe(onNext: { [weak self] _ in
      guard let self else { return }

      let currentSeconds = self.player?.currentItem?.currentTime().seconds ?? 0
    })
}
```
위의 코드는 1초마다 플레이 타임을 얻어오는 코드이다.

![Image](https://drive.google.com/uc?export=view&id=1JLM9EWK2bafjCHUKNswZd3e83AlQTtLK)  

## 참고
[<i class="fas fa-link"></i> Playing Audio from a Video Asset in the Background](https://developer.apple.com/documentation/avfoundation/media_playback/creating_a_basic_video_player_ios_and_tvos/playing_audio_from_a_video_asset_in_the_background){:target="_blank"}

