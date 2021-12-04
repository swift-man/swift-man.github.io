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
실제 Device 에서 Proxy 를 사용하여 네트워크의 모니터링을 할 수 있다. 
> Charles를 사용하지 않더라도<br/>
Xcode Instsruments에서 무료로 iPhone의 network 모니터링이 가능하다.<br/>
큰 차이점은 없으나 Xcode Instruments는 request와 response 에 대해 시각화를 해주며, 장단점이 있다.<br/>
Charles 라이선스가 없다면 Xcode Instruments를 확인하는 것을 권장한다.

## SSL Proxying Settings
```
맥 상단 메뉴 > Proxy > SSL Proxying Settings...
```
![Image](https://drive.google.com/uc?export=view&id=1eWiuppv7fM_0gry6Lal6zv5-aXVgS3f0)  
해당 메뉴의 `Install Charles Root Certificate on a Mobile Device or Remote Browser` 를 누르자.  
이때 Device 가 USB 에 연결되어야 한다. 
## iOS Device 구성
1. iOS Device 는 맥과 동일한 Wifi에 연결 되어있어야 한다. 
![Image](https://drive.google.com/uc?export=view&id=1XMp5Nz-JLInebwL5PKSJrhwrLMiMD8dR)  
2. Wi-fi Section에 들어가자.
![Image](https://drive.google.com/uc?export=view&id=1921ZYlcEKK6ZYhMtahrbFrVB_k6LbSi4)
3. 활성 Wifi 의 세부정보를 선택하고 가장 하단의 HTTP Proxy 섹션으로 이동하자.
![Image](https://drive.google.com/uc?export=view&id=1NjRwdUwaSY3xepm8Duy4npYMpjTLI-Wp)

4. HTTP 프록시 Section의 프록시 구성을 `수동`으로 구성한다.
![Image](https://drive.google.com/uc?export=view&id=1oXBPePfdt_5-FgT7LSfwicucc-GKb5Zl)
5. 서버는 Charls가 구성된 Mac의 로컬 IP 주소로 선택한다.
6. Port는 Charls 의 Mac Proxy Port 를 선택한다.
> 8888 기본 포트이다.

## iOS Device 인증서 설치
1. iPhone 사파리에서 [<i class="fas fa-link"></i> http://charlesproxy.com/getssl](http://charlesproxy.com/getssl){:target="_blank"}에 접속하여 인증서를 설치한다. 이때 경고를 허용해야 하니 해당 내용을 읽어보고 허용하는 것을 권장한다.
![Image](https://drive.google.com/uc?export=view&id=18OjwQcO5kFdjogUuKpLVn2PoWECTkBpr)

2. VPN 및 기기 관리에 Section에 접속하자. 1번에서 설치한 Cerification이 유효하다면 구성 프로파일에 보면 허용되지 않은 Charles 관련 섹션이 존재한다.
![Image](https://drive.google.com/uc?export=view&id=17uK4GLzAdyRPN3uZdZXL-GrzxzmyaigQ)

3. 인증서를 확인하면 프록시를 사용할 수 있다.
![Image](https://drive.google.com/uc?export=view&id=17ZmbKCSCTx1C66EFb--okTqygEPXxOBx)

proxy 구성하면 iPhone의 Network 트래픽을 빠르게 맥에서 확인 할 수 있으며, 개발 및 트러블슈팅에 빠르게 대응할 수 있다.

## 참고
[<i class="fas fa-link"></i>  ssl-certificates](https://www.charlesproxy.com/documentation/using-charles/ssl-certificates/){:target="_blank"}
