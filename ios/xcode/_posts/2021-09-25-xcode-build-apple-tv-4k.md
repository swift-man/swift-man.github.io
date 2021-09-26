---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "[Apple TV 4K] 6세대 Xcode로 빌드 하기"
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
Device를 USB로 연결하지 않고 빌드하는 방법을 공부했다.  

## Mac과 쌍으로 연결
### 동일한 Wifi
**Apple TV와 Mac은 같은 Wifi** 에 있어야 쌍으로 연결할 수 있다.

### Apple TV 설정
```
설정 > 블루투스 > 리모컨 앱 및 기기
```
위 경로로 이동하여 Mac을 추가하여 연결하면 된다. 
![Image](https://drive.google.com/uc?export=view&id=1pvDS7pBkZtGp1rWR-Z_-jmjmBMz2lga0)  
쌍으로 연결되면 위 이미지 처럼 오른쪽(모자이크 영역)에 Mac이 보이게 된다.
   
### 주의할 점 
Apple TV 가 `리모컨 앱 및 기기` 화면이 아니면 쌍으로 연결이 안된다. 
연결 후 `리모컨 앱 및 기기` 화면에서 다른 화면으로 이동해도 연결이 끊기게 된다.  
잠자기가 설정 되어 있다면 시간이 지나 연결이 끊어지게 되어 불필요하게 잠자기 기능이 동작하지 않도록 해줘야 한다.

## Xcode와 연결
### 연결이 안 되는 경로
Xcode 의 Target의 connected device를 통해 접근 하면 아래와 같이 연결이 안된다.
![Image](https://drive.google.com/uc?export=view&id=1pZOvv-1kQPFSTX6rvciirtDzYwmBuAgd)

![Image](https://drive.google.com/uc?export=view&id=1mT6J6tSLSWtjAyOJLGyADvahPkyxwQaZ)
Apple TV는 USB가 없다. Xcode는 USB를 연결하라고 나오고 넘어가 지지 않는다.💢  

### 연결이 되는 경로
Xcode의 해당 경로로 이동해 보자.
```
Xcode > Window > Device and Simulators 
```
왼쪽 탭에 기기가 보이면 Pair 버튼을 누르자.  
![Image](https://drive.google.com/uc?export=view&id=1h7KNbhdXBNq3SQmGvmLIjuuah5Mz294p)
이처럼 코드 입력창이 나오고 Apple TV의 화면에서 코드가 보이는 이벤트가 발생한다. 코드를 Xcode에 입력해 보자.

### 연결 오류 
Pair 버튼을 통해 코드를 입력했는데, 다시 Pair 버튼이 나오는 경우가 있다.  
이게 오류 메시지 없이 무한반복이 되는데, 오류 현상으로 인지하기 어렵다.  
구글링으로 오류를 해결하였는데, 생각보다 이 현상을 겪는 사람들이 있었다.

이 현상이 발생하면 해결방법은 의외로 간단한데 Mac을 재부팅 하면 된다.

### 연결 완료
```
Xcode > Window > Device and Simulators 
```
![Image](https://drive.google.com/uc?export=view&id=1oejbTzE4Y2PS1qowFYsupDyVx_J8KGl7)
이렇게 Apple TV 정보가 나오면 연결 성공이다.  
이제 해당 기기로 빌드가 가능하다.  

유선 연결 없이 무선으로 빌드가 되는 어떤 상징이 되는 기기가 나온 것 같다.
미래의 아이폰도 케이블 없이 무선 빌드가 될 것으로 예측 된다.

## 참고
[<i class="fas fa-link"></i> XCode build project for the Apple TV 4K
](https://developer.apple.com/forums/thread/100785){:target="_blank"}  
[<i class="fas fa-link"></i> Apple TV가 Wi-Fi에 연결되지 않는 경우
](https://support.apple.com/ko-kr/HT204400){:target="_blank"}  
