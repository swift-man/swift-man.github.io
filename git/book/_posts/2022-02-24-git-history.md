---
sidebar:
  title: "Git"
  nav: sidebar-git
  icon: "fab fa-github"
title:  "[Git] 기초"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Git Book"
depth: 
  - title: "Git"
    url: /git/
    icon: "fab fa-github"
  - title: "Book"
    url: /git/book/
    icon: "far fa-folder-open"
---
## 역사
* 리눅스 커널은 패치 파일과 단순 압축 파일로 관리
* 2002년 BitKeeper라는 상용 DVCS를 사용
* 2005년에 BitKeeper의 무료 사용이 제고됨
* 리눅스 개발 커뮤니티가 자체 도구를 만드는 계기
* 목표
  * 빠른 속도
  * 단순한 구조
  * 비선형적 개발 (수천 개의 동시 다발적인 브랜치)
  * 완벽한 분산
  * 리눅스 커널 같은 대형 프로젝트에도 유용할 것(속도나 데이터 크기 면에서)
* 2005년 Git탄생

## Git과 GitHub의 차이?
* Git: 분산형 버전 관리 시스템
* GitHub: 분산형 버전 관리 시스템을 호스팅해주는 서비스

## 델타가 아니라 스냅샷
### Subversion이나 비스한 VCS
* 각 파일의 변화를 시간순으로 관리

![Image](https://git-scm.com/book/en/v2/images/deltas.png)  

### Git
* Git의 데이터는 파일의 스냅샷
* 파일이 달라지지 않으면 이전 버전의 링크만 저장

![Image](https://git-scm.com/book/en/v2/images/snapshots.png)  

> 링크만 저장하기 때문에 빠른속도로 전환이 가능하다.

## 거의 모든 명령을 로컬에서 실행
* 거의 모든 명령이 로컬 파일과 데이터만 사용
* 프로젝트의 모든 히스토리가 로컬 디스크에 있기 때문에 모든 명령을 순식간에 실행
  * ex) 프로젝트의 히스토리를 서버 없이 조회 -> 빠른 조회 가능
* 비행기나 기차 등에서 작업하고 네트워크에 접속하고 있지 않아도 커밋 가능

## Git의 무결성
* 모든 데이터를 저장하기 전 체크섬(해시)를 구하고 그 체크섬으로 데이터를 관리
* SHA-1 해시 사용
* 40자 길이의 16진수 문자열
  * ex) 48656c6c6f20537461636b4f766572666c6f77
* 파일을 이름으로 저장하지 않고 해당 파일의 해시로 저장

## 세 가지 상태
* Committed
  * 데이터가 로컬 데이터베이스에 안전하게 저장 됨
* Modified
  * 수정한 파일을 아직 로컬 데이터베이스에 커밋하지 않음
* Staged
  * 수정한 파일을 곧 커밋할 것이라고 표시

![Image](https://git-scm.com/book/en/v2/images/areas.png)  

* Git으로 하는 기본적인 일
  * 워킹 디렉토리에서 파일을 수정
  * Staging Area에 파일 Stage해서 커밋할 스냅샷을 만듦
  * Staging Area에 있는 파일들을 커밋해서 Git 디렉토리에 영구적인 스냅샷으로 저장

## 출처
[<i class="fas fa-link"></i> 시작하기 - Git 기초](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EA%B8%B0%EC%B4%88){:target="_blank"}  
[<i class="fas fa-link"></i> 시작하기 - Git 기본기](https://jhouse0317.tistory.com/entry/13-%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EA%B8%B0%EB%B3%B8%EA%B8%B0){:target="_blank"}
