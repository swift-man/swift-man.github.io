---
sidebar:
  title: "CS"
  nav: sidebar-cs
  icon: "fas fa-microchip"
title: "IaaS, PaaS, SaaS"
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
서비스형(as-a-Service)이라는 용어는 제3사에서 클라우드 컴퓨팅 서비스를 제공한다는 의미  
![Image](https://www.redhat.com/cms/managed-files/iaas-paas-saas-diagram5.1-1638x1046.png)

3가지 기본유형에 따라 관리 수준이 다르다.

* 기존의 IDC를 이용한 호스팅
  * 네트워크를 구성하고 다른 업체도 사용할 수 있도록 서비스
  * 서버를 빌려주는 렌탈과 유사

* IDC로 인한 문제점
  * 유연하지 못함

## IaaS(Infrastructure-as-a-Service)
* Instance 를 사용해 가상의 서버를 제공
  * 가상화 인프라 서비스
  * 스토리지 서비스
* 사용자
  * OS, Data, Application, 미들웨어 및 런타임 관리
  * 제공업체의 API 또는 대시보드를 통해 인프라 액서스 및 제어
* 제공업체
  * 네트워크, 서버, 가상화, 스토리지 관리와 액세스 관리
  * 사용자를 대신해 데이터센터를 유지관리하며 업데이트
* 필요한 구성 요소만 구매 가능
  * 확장 또는 축소의 유연성
    * 유지관리비용이 매우 합리적
* 단점
  * 제공업체의 보안 문제 가능성
  * 멀티 테넌트 시스템
    * 여러 클라이언트와 리소스 공유
  * 서비스 신뢰성이 높은 업체를 선정해야 함
  
## PaaS(Platforms-as-a-Service)
* OS, Web, Was, DB 등 플랫폼(Application)을 제공하는 서비스이며 주로 프로그래머에게 유용하다.
* 지속적으로 웹 기반 애플리케이션을 빌드 및 커스터마이징 할 수 있는 방법
* 제공 업체
  * 자체 인프라에서 하드웨어, 소프트웨어를 호스팅
  * 소프트웨어 업데이트
  * 하드웨어 유지 관리
  * 빌드 및 배포 관리 환경 제공
* 사용자
  * 통합 솔루션, 솔루션 스택 또는 인터넷을 통한 서비스로 제공 받음
  * 애플리케이션 코드 작성
* AWS Lamda가 대표적
  * Web, Was를 모르더라도 소스코드와 Endpoint만 알면 가능
* 플랫폼을 바로 제공받기 때문에 사용자는 Application에 집중할 수 있는 장점이 있다.


## Sass(Software-as-a-Service)
* 가장 포괄적인 클라우딩 컴퓨텅 서비스
* 제공업체
  * 모든 애플리케이션 관리
  * 웹 브라우저를 통해 제공
  * 소프트웨어 업데이트
  * 버그 수정
  * 소프트웨어 유지관리 작업 처리
* 사용자
  * 대시보드 또는 API를 통해 애플리케이션 연결
  * 소프트웨어 설치가 필요 없음
  * 프로그램에 대한 그룹 액서스가 원활하고 안정적
* ex)Google Docs, MS365
* 장점
  * 소프트웨어 설치 및 업데이트를 처리할 인력이나 대역폭이 없음
  * 최적화가 그다지 필요하지 않거나 주기적으로 사용되는 애플리케이션이 있는 소기업에 매우 유용
  * 시간과 유지관리를 줄일 수 있음
* 단점
  * 제어, 보안 및 성능과 관련한 비용 소요
  * 신뢰할 수 있는 제공업체 선택이 중요
## 참고
[<i class="fas fa-link"></i> redhat.com/ko/topics/cloud-computing](https://www.redhat.com/ko/topics/cloud-computing/iaas-vs-paas-vs-saas){:target="_blank"}

