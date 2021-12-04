---
sidebar:
  title: "IT"
  nav: sidebar-it
  icon: "fas fa-mobile-alt"
title: "[Charles] 설정하기"
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
앱을 처음 켜면 WEB DEBUG PROXY 라고 나오지만, 안드로이드, iOS 시뮬레이터도 동작하는 네이티브 개발자에게도 유용한 개발 도구다. 해당 디바이스에서 호출되는 API의 정상 여부, 각 상세 정보 등을 확인할 수 있어 매우 유용하다.

Map Local, Rewrite 등 매우 유용한 기능도 탑재하고 있어 강력하다.  
추후 이 기능들에 대해 포스팅하도록 하겠다.

Charles를 아주 가끔 세팅하기 때문에 세팅법을 항상 잊어버리게 된다. 그래서 이참에 세팅법을 적기로 했다.  
![Image](https://drive.google.com/uc?export=view&id=1UZ3lhBiWu3eeTDLpkIodF4Aj3KWhyWb2)  
개발 도구라고 느껴지지 않는 아주 고급스러운 디자인의 아이콘이다. 

## 실행
![Image](https://drive.google.com/uc?export=view&id=13q7tLNemRV_yKCcpnx_HEL75Lji9K8T5)  
기본적으로 등록하지 않은 URL의 상세 정보는 알 수 없지만 호출되는 Request의 Domain은 모두 목록에 뜨게 된다.  
Domain의 상세 URL, Header, Body, Response 등 자세한 정보를 알고 싶으면 해당 Domain을 SSL Proxying Settings 메뉴에 등록해 주어야 한다.

## SSL Proxying Settings
```
맥 상단 메뉴 > Proxy > SSL Proxying Settings...
```
![Image](https://drive.google.com/uc?export=view&id=15NWw6DrvFH1pPql2K9DZ66-lRgSkdUic)  

![Image](https://drive.google.com/uc?export=view&id=1Zmjxk3VRE4dQN9jKKfm8IUOFcC74aYRj)  
메뉴를 클릭하면 상단의 메뉴가 열리게 되고 Include 에 추적하고 싶은 URL 주소를 넣으면 된다.  
필자의 경우 예로 github.com을 등록했다.
>필자가 개발할 시 개발하는 서버의 URL을 여기에 넣고 목록은 개발 URL로 필터링을 걸어 사용한다.

![Image](https://drive.google.com/uc?export=view&id=1Y0yXcHxxD7tPhBU-kMuFnwO6AyS8D3zF)  
`Add` 버튼을 누르면 팝업이 뜨게 되며, Host와 Port를 입력하면 된다. 규칙은 간단히 `*` `?` 를 입력할 수 있다.



## Mac Keychine Settings
```
맥 상단 메뉴 > Help > SSL Proxying > 
```
에 가면 다양한 Certificate를 제공하고 있다. 여기서 iOS Simutaror 도 제공되는데 호출되는 network 의 정보를 Mac 에서 볼 수 있어 개발 시 매우 유용하다.  
![Image](https://drive.google.com/uc?export=view&id=1Tfnf2tF7wt3mmkjMGcR60juflDnOGWKz)
Root Certificate는 자신의 컴퓨터가 대상이 되며, 개발용 시뮬레이터도 설치가 가능하다. 개발용 시뮬레이터에 인증서를 설치할 시 시뮬레이터를 켜둔 상태에서 `Install Charles Root Certificate in iOS Simulators` 메뉴를 누르면 된다.
> iOS 시뮬레이터의 경우 시뮬레이터를 완전히 종료 후 재구동 시 정상 작동된다.

![Image](https://drive.google.com/uc?export=view&id=1OkEotKDlpjkULxRcgAHoUf5zoPyc-oqv)   
맥에서 사용 시 키체인에 인증서를 허용해주어야 한다. 인증서 설치 메뉴를 누르면 신뢰하지 않는 인증서가 키체인에 추가되게 된다. 이 인증서를 자세히 보기 하여 `항상 신뢰`로 변경해주면 된다.

![Image](https://drive.google.com/uc?export=view&id=13QhN6Dtey65aw143hHl0_1Q0pqc90a0f)  

만약 찰스를 더 이상 사용하지 않거나, Proxy를 사용할 때만 신뢰를 하고 싶다면 키체인에서 `항상 신뢰` <-> `신뢰하지 않음`을 ~~안타깝게~~ 수동으로 변경해주어야 한다.

## 라이선스 구매
[<i class="fas fa-link"></i> Charles의 공식 홈페이지](https://www.charlesproxy.com/buy/){:target="_blank"}의 Buy 탭에서 구매할 수 있다.  
구매 페이지에 입력란이 있는데 기관이 아닌 개인이라면 Individual 을 선택하도록 하자.

![Image](https://drive.google.com/uc?export=view&id=1mZpM31Z5zQDXTJwlcH0xVxqNJJllAYZ4)    
### 가격
![Image](https://drive.google.com/uc?export=view&id=1bFFDtvQK_-A5pSuPxbsus2AptqayG7DI)  

### 구매 완료
![Image](https://drive.google.com/uc?export=view&id=1NRHLnbmj0ITL2I3AuxF1bw1_-ieHVwcK)  
구매 완료 시 이메일을 5분 안에 보내주며, 라이선스를 받을 수 있다.

### 라이선스 적용
![Image](https://drive.google.com/uc?export=view&id=1umLpBxldjHH3DZg_MmqvcSvctDUnEKX5)  
라이선스를 적용하면 register Charles Menu 가 Unregister Charles.. 로 변경된다.  
처음 사용해보는 사용자는 **Trial** 기간이 있기 때문에 구매하지 않아도 사용할 수 있다.


## 지원되는 OS
[<i class="fas fa-link"></i> Charles의 공식 홈페이지](https://www.charlesproxy.com/download/){:target="_blank"}에서 다운로드가 가능하다.


![Image](https://drive.google.com/uc?export=view&id=15DRm3s7GFv-UzIIvbU5zKIqElVEJw2zc)

지원되는 OS
- Windows 64Bit  
- MacOS
- Linux 64 Bit


## 추후 참고
[<i class="fas fa-link"></i> how we debug with charles](https://www.nodesagency.com/how-we-debug-with-charles/){:target="_blank"}

