---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: Codesign wants to access key "access" in your keychain
toc: true
toc_sticky: true
toc_label: 목차
tag: "Xcode Build Error"
depth:
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "Build Error"
    url: /ios/build-error/
    icon: "far fa-folder-open"
---
회사에서 신규 장비를 받았다. '역시나' Xcode를 신규 세팅하면 예기치 못한 오류를 만나게 되는데, 
바로
```
Codesign wants to access key "access" in your keychain
```

![Image](https://drive.google.com/uc?export=view&id=1PU01WmCu8JM8_VcV1WtrTp9xDipxstKE)  
```
codesign 이(가) 변경하려고 합니다. 허용하려면 관리자 이름 및 암호를 입력하십시오.  
codesign 이(가) '시스템' 키체인을 사용하고자 합니다.  
```
OS 버전마다 문구가 다르지만 이전에는 "항상 허용"으로 처리해서 별 문제없었으나 macOS Monterey에서는 해당 옵션이 없고 매번 팝업이 뜨며 개발자를 괴롭힌다. 

## 원인 
해당 원인은 iCloud의 키체인과 현재 시스템의 키체인의 충돌로 인해 접근이 불가한 상태일 때 발생하며, 암호를 무한정 입력해도 오류 메시지 없이 무한정 계정과 비밀번호를 물어보기 때문에 해결되지 않는다.
```
시스템 환경설정 -> Apple ID -> iCloud
```
여기에 키체인이 활성화되어 있는지 확인하자. 만약 체크해서 해결된다면 땡큐! 
하지만 해결되지 않는 다면?  

![Image](https://drive.google.com/uc?export=view&id=1IJqscBpg2qH-NcFnEjg-jLgKsGGeXLYg)   
구글링 결과 2017년에도 해당 문제를 겪고 있는 개발자들이 있었다. 애플! 언제 해결해 주는 거냐고..

## 해결
```
1.In Finder Select Go > Go to folder (⇧⌘G)
2.In the window that appears, type the following: ~/Library/Keychains/
3.Click OK.
4.Look for a folder with a random name similar to this "A8F5E7B8-CEC1-4479-A7DF-F23CB076C8B8"
5.Move this folder to the Trash.
6.Immediately choose Apple Menu () > Restart… to restart your Mac.
```
### 1. In Finder Select Go > Go to folder (⇧⌘G)
![Image](https://drive.google.com/uc?export=view&id=1STUBGWldnZ8El01LxYASvdeCVFgZP_8a)  

### 2. In the window that appears, type the following
```
~/Library/Keychains/
```
![Image](https://drive.google.com/uc?export=view&id=1o8TR_jGKuvf_XTrBmRigpMXCpIAMMp0L)  
Click OK.

### 3. Look for a folder with a random name similar to this "A8F5E7B8-CEC1-4479-A7DF-F23CB076C8B8"
![Image](https://drive.google.com/uc?export=view&id=1gLM38fG4WbDhFyXjIBXxkjLMBMn5QVaG)  
### 4. Move this folder to the Trash.
![Image](https://drive.google.com/uc?export=view&id=1rBpscNzU2VTmEOmDIEgCVHwtWPaEpzNt)  
### 5. Immediately choose Apple Menu () > Restart… to restart your Mac.
재부팅 후 다시 시스템 환경설정의 `AppleID`에 들어오면 다시 암호를 요구한다. 입력하자.
![Image](https://drive.google.com/uc?export=view&id=1-5LTN-Hrgb2whOwdeVOtV09hvOajxbE0) 

## iCloud 키체인 ON
![Image](https://drive.google.com/uc?export=view&id=1TGLfhFMJIv1N_lfjUtOMHJNoAkAYhUkG)  

> 에러 해결~

## 회사 장비 스펙
여담으로 회사 장비가 너무 좋다. 매우 빨라서 프로젝트에서 카르타고를 걷어내려고 한다.😍
![Image](https://drive.google.com/uc?export=view&id=1EukFfK56EsJ-8Khkm3_pdpWWhGyYqoL9)  
16인치  
CPU Apple M1 Pro  
RAM: 32GB  
HDD: 500
