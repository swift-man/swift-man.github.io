---
sidebar:
  title: "IT"
  nav: sidebar-it
  icon: "fas fa-mobile-alt"
title: "[Apple TV 4K] 6세대 kodi 설치 성공 후기"
toc: true
toc_sticky: true
toc_label: 목차
ga: true
tag: "Apple TV"
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: https://www.linuxadictos.com/wp-content/uploads/kodi-logo.jpg.webp
  caption: "Photo credit: [**Apple**](https://www.apple.com)"
excerpt: "Mac에서 Apple TV 4K에 Xcode로 Kodi 설치하는 방법을 알아봅니다."
---
Apple TV에 [<i class="fas fa-link"></i> Kodi](/clean/dictionary/kodi)를 설치해보고 사용해본 후기를 정리한다.


## 소프트웨어 준비물
* [<i class="fas fa-link"></i> Xcode](https://apps.apple.com/kr/app/xcode/id497799835?mt=12){:target="_blank"}
* [<i class="fas fa-link"></i> Kodi tvOS 19.1](https://kodi.tv/download/tvos){:target="_blank"}
* [<i class="fas fa-link"></i> iOS App Signer](https://www.iosappsigner.com/){:target="_blank"}
* [<i class="fas fa-link"></i> QuickFTP Server](https://apps.apple.com/kr/app/quickftp-server/id1451646819?mt=12){:target="_blank"}
* [<i class="fas fa-link"></i> Korea OTT Package for Kodi 19 (public)-19.0.0.zip](https://github.com/kym1088/tvingM){:target="_blank"}



## Xcode 설정
### 임시 프로젝트 생성
```
Xcode > File > New > Project... > tvOS > App
```
을 선택하고 Next를 클릭하자. 
설정 정보를 입력하는 창이 나오는데, 임의로 입력해도 상관없다.  
확인해 볼만한 것은 Organization Identifier인데, 재설치 시 같은 ID로 설치가 필요하다.  
이 정보가 앱의 고유 ID가 되며, 설치 / 재설치를 판단하게 된다.

### Xcode 계정 설정
```
Xcode > Preferences... > Accounts > Apple IDs
```
아래 하단 + 버튼 클릭하고 애플 계정으로 로그인하자.

>애플 개발자 계정은 두 가지로 나뉘는데, 기본으로 무료 계정이다.<br/>
무료 계정일 경우 7일마다 재설치를 해야하며,<br/>
유료 계정일 경우 1년마다 재설치를 해주어야 한다.  

### Provisioning Profiles 등록
먼저 등록한 애플 계정정보와 App 정보를 연결하는 작업이 필요하다. 이때
[<i class="fas fa-link"></i> Provisioning Profiles](/clean/dictionary/provisioning-profiles)를 등록해주어야 App install이 가능하다.  
왼쪽 File navigator 에 프로젝트를 클릭하면 
```
General / Siging & Capabilities / Resource Tags ...
```
해당 탭에서 `Siging & Capabilities` 를 클릭하자.  
먼저 프로젝트 생성 시 입력한 Organization Identifier가 보이는데 상단에 Team을 자신의 애플 계정으로 설정하면 자동 생성된다.

## AppleTV 에 Kodi tvOS 19.1 ipa 파일 생성
### iOS App Signer로 ipa 파일 생성
다운로드 받은 [<i class="fas fa-link"></i> Kodi tvOS 19.1](https://kodi.tv/download/tvos){:target="_blank"}을 설치할 수 있도록 앞서 설정한 Provisioning Profile 추가 작업이 필요하다.

![Image](https://drive.google.com/uc?export=view&id=1FIBh8itUCJL9oZkErErZKGlEeA5kRBY_)
[<i class="fas fa-link"></i> iOS App Signer](https://www.iosappsigner.com/){:target="_blank"}앱에서 Input File에 다운로드 받은 [<i class="fas fa-link"></i> Kodi tvOS 19.1](https://kodi.tv/download/tvos){:target="_blank"}파일을 등록하자.  
앞서 설정한 Provisioning Profile을 선택하자.  
Start 버튼을 클릭하자.  
export 작업이 하단에 보이게 되고 `Done, output... tvos.ipa` 메시지가 보이면 완료이다.

### Xcode Apple TV 와 연결
ipa 설치를 위해 [<i class="fas fa-link"></i>Xcode와 Apple TV ](/ios/xcode/xcode-build-apple-tv-4k/)를 연결하자.

### Xcode로 Kodi ipa File AppleTV에 설치
이제 생성한 ipa파일을 Xcode를 통해 install하는 작업 진행하자.
```
Xcode > Window > Device and Simulators 
```
![Image](https://drive.google.com/uc?export=view&id=1oejbTzE4Y2PS1qowFYsupDyVx_J8KGl7)  
해당 경로로 이동하면 중간에 `INSTALLED APPS` 의 **+ 버튼을 클릭하고 생성한 ipa파일을 선택**하여 설치하자.  


Xcode 는 아무런 반응이 없는 것으로 보이지만 잘 설치되고 있음을 해당 화면에서 보여준다.  
![Image](https://drive.google.com/uc?export=view&id=12gPtEikxwaOS3H3Lwt93FEEXQdS0CB-B)   
>필자의 경우 약 20분 소요되었다.

## Kodi 설치 완료
### Xcode에서 ipa 설치 완료 확인
![Image](https://drive.google.com/uc?export=view&id=1GaMO_af1Kx12HNBAC1KphK2IhpTyeLSz)  
Xcode 의 `INSTALLED APPS` 의 목록에 kodi가 추가 되었는지 확인하자.  
### Apple TV에서 설치 완료 확인
![Image](https://drive.google.com/uc?export=view&id=1hOJgf_2dHb4mdx8OFwTTmIK13ziCq7-8)  
이제 Apple TV 의 홈 화면에 Kodi 앱 아이콘이 생겼는지 확인해 보자.
## Korea OTT설치
### QuickFTP Server로 Korea OTT Package 설치
설치된 Kodi 앱에 Korea OTT를 사용할 것이라면, [<i class="fas fa-link"></i> Korea OTT Package for Kodi 19 (public)-19.0.0.zip](https://github.com/kym1088/tvingM){:target="_blank"}파일을 설치해야 한다.  
GitHub의 zip 주소로 설치가 가능할 것으로 예상했으나, 불가능했다. 파일의 직접 주소가 아니라서 그런 듯 하다.  

>실패한 경로
* GitHub 파일 주소
* Google Drive
* 개인 Nas (21 포트로 설정해서 실패가 되는 듯하다.)

여러 시도를 한 끝에 [<i class="fas fa-link"></i> QuickFTP Server](https://apps.apple.com/kr/app/quickftp-server/id1451646819?mt=12){:target="_blank"} 로 파일 설치를 성공했다.

먼저 [<i class="fas fa-link"></i> Korea OTT Package for Kodi 19 (public)-19.0.0.zip](https://github.com/kym1088/tvingM){:target="_blank"}의 zip 파일을 다운로드 받은 후 Mac 의 다운로드 폴더를 내부 FTP 망을 만들어 주고 21 포트가 아닌 다른 포트를 설정해 주자.
>해당 폴더에서 Korea OTT Package for Kodi 19 (public)-19.0.0.zip 압축을 풀지 않고 Kodi에서 다운로드 해야한다.

![Image](https://drive.google.com/uc?export=view&id=1yCqZiq_6Vrz_P8Jjws7ePE0T1A_ikSAV)  
Start Server 를 클릭했을 시 오류가 발생한다면 center 탭의 권한을 확인하자. 정상인 경우 Status 가 녹색으로 변하게 된다.

Kodi 앱의 File Manager 에서 `None` 을 클릭하여 설정한 FTP 경로를 입력하고 zip 파일을 다운로드 하자.
```
// Mac IP 주소 : 포트 주소
ftp://192.168.1.xx:31 
```

## Korea OTT Package for Kodi 19 설치 완료
![Image](https://drive.google.com/uc?export=view&id=1_OPO3IA9gBhKDDlgXjm5OQWb_JEYB-ir)  
이제 각 애드온의 설치, 설정하여 즐기자.


## 후기
꼭 해야 하는가? 에 대한 의문이 들었다. 실제로 사용해본 결과 집에 있는 케이블을 끊고 Kodi를 사용할 정도의 만족감은 아니었다.

Korean OTT 의 카카오 TV, 삼성 TV는 문제 없이 재생이 잘 된다.  
필자의 경우 쿠팡 플레이 유저임에도 불구하고 DRM으로 막혀있어 kodi로 플레이가 안 되었다.    
티빙도 네이버 프리미엄 계정이나 Kodi로 플레이가 안 되었다.  

추후 가족과의 협의(?)를 통해 티빙 계정을 업그레이드하여 사용하는 방법은 좋을 듯하다.
쿠팡 플레이도 재생이 된다면 이 환경을 유지해도 좋을 것 같다. 

## 참고
[<i class="fas fa-link"></i> HOW-TO:Install Kodi on Apple TV 4 and 5 (HD and 4K)
](https://kodi.wiki/view/HOW-TO:Install_Kodi_on_Apple_TV_4_and_5_(HD_and_4K)){:target="_blank"}  
