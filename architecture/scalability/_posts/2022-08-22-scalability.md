---
sidebar:
  title: "Architecture"
  nav: sidebar-architecture
  icon: "fas fa-sitemap"
title: "Scalability"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Architecture"
depth:
  - title: "Architecture"
    url: /architecture/
    icon: "fas fa-sitemap"
  - title: "EDD"
    url: /architecture/edd/
    icon: "far fa-folder-open"
---
산업이 성장하면서 앱이 크게 발전하고 있음. 이를 해결하기 위한 해결책은 좋은 아키텍처임
앱의 규모가 커짐에 따라 PR 을 머지하기 어려워짐

산업이 성장, 증가함에 따라 더 복잡해질 수 밖에 없음. 

## Scale과 연관된 다양한 문제들
* 개발자가 겪는 문제
  * 빌드 시간 증가
  * 코드 충돌 증가
  * QA, 디버깅 시간 증가
  * 끊이지 않는 회귀 버그
  * 개발 소요 시간 증가

* 사용자가 겪는 문제
  * 앱 Startup 시간 증가
  * 과도한 자원 사용(배터리, 네트워크)
    * 개발자의 최적화에 대한 세부적인 계획 필요
    * 중복된 네트워크로 자원을 낭비
  * 앱 용량 증가
    * 이미지, 로티 이미지
    * 번역어
  * 버그 증가
  * 앱 안정성 하락

## 확장 가능한 앱 아키텍처의 특징
### 명확한 역할 구분
객체/모듈은 하나의 역할만 수행하며, 데이터의 흐름을 쉽게 따라갈 수 있다.

로직을 분산시키고 다시 조립하는 방법

### 변화에 유연
의존성은 decoupling 되어있고, 구조가 단순하기 때문에 유연하다.

어떻게 모듈로 나누고 

### 테스트가 용이
유닛 테스트가 어렵다면 구조 개선이 필요하다는 신호이며, 테스트는 품질 관리에 유용하다.

품질 관리에 대한 자동화 테스트는 필수이다.
