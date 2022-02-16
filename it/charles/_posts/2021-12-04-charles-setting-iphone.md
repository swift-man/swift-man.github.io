---
sidebar:
  title: "IT"
  nav: sidebar-it
  icon: "fas fa-mobile-alt"
title: "[Charles] iPhone Device 설정하기"
toc: false
toc_sticky: true
toc_label: 목차
classes: wide
tag: "Charles"
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: https://cdn-laravel.vapor.cloud/image/nstack/translate_values/charles_IPjFgz7Fvv.png
  caption: "Photo credit: [**charlesproxy**](https://www.charlesproxy.com/)"
excerpt: "How we debug with Charle"
---
iPhone에서 네트워크 트래픽을 확인하는 것이 개발에 큰 도움이 될 때가 있다.  
실제 Device에서 Proxy를 사용하여 네트워크의 모니터링을 하여 개발이나 이슈 대응을 빠르게 감지할 수 있는 Charles iPhone Setting 방법에 대해 알아보자.
> Charles를 사용하지 않더라도<br/>
Xcode Instruments에서 무료로 iPhone의 network 모니터링이 가능하다.<br/>
큰 차이점은 없으나 Xcode Instruments는 request와 response에 대해 시각화를 해주며, 장단점이 있다.<br/>
Charles 라이선스가 없다면 Xcode Instruments를 사용을 권장한다.

## SSL Proxying Settings
Charles를 사용하려면, Mac, iOS 시뮬레이터와 동일하게 해당 Device에 인증키를 설치해야 정상적으로 확인이 가능하다. 
Mac에서 Charles의 상단 메뉴의 구성을 보고 설치 하자.
```
맥 상단 메뉴 > Proxy > SSL Proxying Settings...
```
![Image](https://drive.google.com/uc?export=view&id=1eWiuppv7fM_0gry6Lal6zv5-aXVgS3f0)  
Device를 Mac에 연결한뒤 해당 메뉴의 `Install Charles Root Certificate on a Mobile Device or Remote Browser` 를 누르자.  

## iOS Device 구성
1. iOS Device는 맥과 동일한 Wifi에 연결되어있어야 한다. 
![Image](https://drive.google.com/uc?export=view&id=1XMp5Nz-JLInebwL5PKSJrhwrLMiMD8dR)  
2. Wi-Fi Section에 들어가자.
![Image](https://drive.google.com/uc?export=view&id=1921ZYlcEKK6ZYhMtahrbFrVB_k6LbSi4)
3. 활성 Wi-Fi 의 세부정보를 선택하고 가장 하단의 HTTP Proxy 섹션으로 이동하자.
![Image](https://drive.google.com/uc?export=view&id=1NjRwdUwaSY3xepm8Duy4npYMpjTLI-Wp)

4. HTTP 프록시 Section의 프록시 구성을 `수동`으로 구성한다.
![Image](https://drive.google.com/uc?export=view&id=1oXBPePfdt_5-FgT7LSfwicucc-GKb5Zl)
5. 서버는 Charles가 구성된 Mac의 로컬 IP 주소로, Port는 Charles 의 Mac Proxy Port를 선택한다.
> 8888은 Charles에서 기본 설정 포트이다.

## iOS Device 인증서 설치
1. iPhone 사파리에서 [<i class="fas fa-link"></i> http://charlesproxy.com/getssl](http://charlesproxy.com/getssl){:target="_blank"}에 접속하여 인증서를 설치한다. 이때 경고를 허용해야 하니 해당 내용을 읽어보고 허용하는 것을 권장한다.
![Image](https://drive.google.com/uc?export=view&id=18OjwQcO5kFdjogUuKpLVn2PoWECTkBpr)

2. VPN 및 기기 관리에 Section에 접속하자. 1번에서 설치한 인증서가 잘 추가가 되었다면 이 인증서를 허용해야 한다. 구성 프로파일에 가서 추가된 허용되지 않은 Charles 관련 정보를 확인하자.
![Image](https://drive.google.com/uc?export=view&id=17uK4GLzAdyRPN3uZdZXL-GrzxzmyaigQ)

3. 인증서를 확인하면 프록시를 사용할 수 있다.
![Image](https://drive.google.com/uc?export=view&id=17ZmbKCSCTx1C66EFb--okTqygEPXxOBx)

## 인증서 신뢰 하기
```
설정 > 일반 > 정보 > 인증서 신뢰 설정 > 해당 인증서 ON
```
![Image](https://drive.google.com/uc?export=view&id=1hCA90BEdSrSlBWLF0SzUVQWT5sD4ewW-)

이제 프록시를 사용하여 iPhone의 Network 트래픽을 빠르게 맥에서 확인 할 수 있다.

## 참고
[<i class="fas fa-link"></i>  ssl-certificates](https://www.charlesproxy.com/documentation/using-charles/ssl-certificates/){:target="_blank"}
