---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "[Xcode] Apple TV 4K 6세대 빌드를 위한 Mac 연결"
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
USB 포트가 없는 Apple TV 4K는 어떻게 빌드를 할까?
Device를 USB로 연결하지 않고 빌드하는 방법을 남긴다.

**Apple TV와 Mac은 같은 Wifi** 에 있어야 쌍으로 연결할 수 있다.

## Apple TV 설정
![Image](https://drive.google.com/uc?export=view&id=1pvDS7pBkZtGp1rWR-Z_-jmjmBMz2lga0)
```
설정 > 블루투스 > 리모컨 앱 및 기기
```
경로로 이동하여 Mac을 추가하여 연결하면 된다. 쌍으로 연결되면 모자이크 영역 부분에 해당 Mac 이 등록이 된다.
   
### 주의할 점 
이 화면이 아니면 쌍으로 연결이 안된다. 
연결이 되었다 하더라도 이 화면이 아니면 연결이 끊긴다.  
시간이 지나 Apple TV의 화면보호기가 더 시간이 지나면 연결이 끊어지게 된다.

## Mac과 쌍으로 연결
### 연결이 안 되는 경로
Xcode 의 Target을 통해 connect device를 하면 아래와 같이 연결이 안된다.
![Image](https://drive.google.com/uc?export=view&id=1pZOvv-1kQPFSTX6rvciirtDzYwmBuAgd)

![Image](https://drive.google.com/uc?export=view&id=1mT6J6tSLSWtjAyOJLGyADvahPkyxwQaZ)
Apple TV는 USB가 없다. Xcode는 USB를 연결하라고 나오고 넘어가 지지 않는다.💢  

### 연결이 되는 경로
Mac에서 Xcode를 실행하고 해당 경로로 이동해 보자.
```
Xcode > Window > Device and Simulators 
```
왼쪽 탭에 기기가 보이면 Pair 버튼을 누르자.  
![Image](https://drive.google.com/uc?export=view&id=1h7KNbhdXBNq3SQmGvmLIjuuah5Mz294p)
이처럼 코드 입력창이 나오고 Apple TV의 화면에서 코드가 보이는 이벤트가 발생한다. 해당 코드를 입력하면 연결이 된다.

## 연결 오류 
Pair 버튼을 통해 코드를 입력했는데, 다시 Pair 버튼이 나오는 경우가 있다.  
이게 오류 메시지 없이 무한반복이 되는데, 오류 현상인지 인지하기가 어렵다.

이 현상이 발생하면 해결방법은 의외로 간단한데 Mac을 재부팅 하면 된다.

## 연결 완료
```
Xcode > Window > Device and Simulators 
```
![Image](https://drive.google.com/uc?export=view&id=1oejbTzE4Y2PS1qowFYsupDyVx_J8KGl7)
이렇게 Apple TV 정보가 나오면 연결 성공이다.

## 참고
[<i class="fas fa-link"></i> XCode build project for the Apple TV 4K)
](https://developer.apple.com/forums/thread/100785){:target="_blank"}  
[<i class="fas fa-link"></i> Apple TV가 Wi-Fi에 연결되지 않는 경우)
](https://support.apple.com/ko-kr/HT204400){:target="_blank"}  
