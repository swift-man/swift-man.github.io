---
sidebar:
  title: "CS"
  nav: sidebar-cs
  icon: "fas fa-microchip"
title: "네트워크 기초"
toc: true
toc_sticky: true
toc_label: 목차
tag: "CS Network"
depth:
  - title: "CS"
    url: /cs/
    icon: "fas fa-microchip"
  - title: "Network"
    url: /cs/network/
    icon: "far fa-folder-open"
---

## 클라이언트
* Browser
* App

## 서버
* Web
* 클라이언트와 서버는 명령어로 주고 받음

## 프로토콜
* 약속
* HTTP
* HTML
* SMTP
  * 이메일 전용 프로토콜
  
## Ajax
* 비동기로 실행되는 대표적인 기능

## 쿠키
* 클라이언트에 저장되는 파일로 남게 된다.

## 세션
* 서버에 저장되나 DB에 저장되는 값이 아닌 Web, Was 서버 수준에서 저장되게 된다.
* 영원히 기억할 수 없다. 서버의 저장공간이 무한대가 아니기 때문에 시간으로 관리되며, 시간이 지나면 세션이 없어진다.
  * 얘)30분 뒤 다시 로그인해야 되는 사이트

## VOIP (Voice over Iternet protoco)
```
음성 -> 데이터 -> IP -> 데이터 -> 음성
```
* 과금요소가 굉장히 저렴하다.
* 연결을 위해서 서버인프라가 필요하고, 연결을 위해서 서버가 계속 동작해야한다.
  * 따라 무료는 아니다.
### TCP
* 정확한 데이터 전달
* 압축
  * 무손실을 기본으로 한다.
  * 1Byte 라도 손실이 나면 압축이 풀리지 않음
### UDP
* VOIP는 UDP를 기본으로 한다.
* 스트리밍 데이터를 전달하는데 유용하다
* UDP는 손실을 허용한다.
* 압축
  * 손실 MPEG(영상)
    * 1개라도 손실이 나면 티가 나지만 크게 티가 나지 않음 
    * 손실에 대한 보정 기술도 있음

## DNS Server
```
www.naver.com -> IPv4 로 연결해주는 중간 서버
```
* 라우팅
  * 서버의 구간을 찾아 연결한다.
* 라우터
  * 전달(연결)을 위한 목적인 장비
### IPv6
많은 Device를 소화할 수 있도록 확장 된 IP 방식

### NAT Server(Network Address Tranration)
Private IP 를 Public IP(공인 IP) 로 전환한다.  
포트를 바꾸는 형태로 내부 IP와 외부 IP를 전환하는 방식

* 모든 서버가 Public 망이 아니다.
  * ip를 할당하는 것 -> 돈
* private ip 를 사용하는 것
  * 보안관점에서 좋다.
* 단점
  * 접속을 할 수 있는 방법이 필요함

## Network 관련 대표적인 명령어(Windows)
```
ipconfig // 할당 받은 IP 주소를 알 수 있다.
ping // ping + IP 를 치면 응답이 오케 된다. 서버에서 막아 놓는 경우도 있음. 무한대로 요청하면 공격이 될 수 있기 때문 
tracent // URL 라우팅
nslookup // 해당하는 도메인의 DNS서버를 조회한다.
```

## 이더넷
규격이며 통신을 할 수 있는 규약
* 물리적인 하단에 있는 접속의 규격

## 허브
* 사무실 내 유선으로 연결되어 있는 경우라면 허브(스위치)에 의해 동작하게 됨
* 브로드캐스팅 - 같은 데이터를 사용하도록 함

## HTTPS
보안(암호화) 통신
* 복호화
* 전자 서명 - 데이터의 원본임을 보장
* 전자 인증 - 기관에서 보장
  * 사용자 증명

## Hash화
* Hash화
  * 단방향으로 암호화만 가능함
  * 주민번호를 DB에 저장할 수 없는 규정이 있을 때 그 사람인지 알고 싶을 때 암호화해서 일치 여부를 검사함

* 암호화 <-> 복호화
  * 양방향으로 암호를 풀고 압축할 수 있음
