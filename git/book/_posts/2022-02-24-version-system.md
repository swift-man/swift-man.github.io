---
sidebar:
  title: "Git"
  nav: sidebar-git
  icon: "fab fa-github"
title:  "[Git] 버전 관리 시스템"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Git book"
depth: 
  - title: "Git book"
    url: /git/
    icon: "fab fa-github"
  - title: "book"
    url: /git/book/
    icon: "far fa-folder-open"
---
## Version Control System; VCS
* 파일의 변화를 시간에 따라 기록하여 과거 특정 시점의 버전으로 불러올 수 있는 시스템
* 개별 파일 혹은 프로젝트 전체를 이전 상태로 되돌리기
* 시간에 따른 변경 사항을 검토
* 문제가 되는 부분을 누가 마지막으로 수정하였는지 찾기
* 파일을 잃어버리거나 무언가 잘못되어도 대개 쉽게 복구 가능

## Local Version Control System
* 대부분의 사람들이 버전 관리를 위해 쓰는 방법은 파일을 다른 디렉토리, 다른 이름으로 복사하는 것
* 이 방법은 간단하지만 실수가 발생하기 쉬움
  * 파일을 덮어쓰거나 의도하지 않은 위치로 복사
* 이 문제를 해결하기 위하여 오래전 프로그래머들은 간단한 데이터베이스에 파일의 변경 사항을 기록하는 로컬 버전 관리 세스템을 만듦
  * ex) RCS
  
![Image](https://drive.google.com/uc?export=view&id=1ZgK025VTg82BDjMuMTOSKuptAzvllHq7)

## 중앙집중식 버전 관리 시스템
* 여러 개발자들과 함께 작업하려면?
* 중앙집중식 버전 관리 시스템(Centralized Version Control System; CVCS)탄생
  * ex) CVS, Subversion, Perforce
* 파일을 저장하는 하나의 서버
* 중앙 서버에서 파일을 가져오는 다수의 클라이언트

### 장점
* 누구나 다른 사람이 무엇을 하고 있는지 알 수 있음
* CVCS를 관리하는 것은 수많은 클라이언트의 로컬 데이터베이스를 관리하는 것보다 쉬움

### 단점
* <u>중앙 서버가 잘못되면 모든 것이 잘못된다.</u>
* 서버가 다운될 경우 다시 복구할 때까지 다른 사람과 협업도 진행 중이던 작업을 버전 관리하는 것도 불가능

![Image](https://drive.google.com/uc?export=view&id=1A15kmihvx7NTpGG-vzSsWQtZGAI--I35)  


## 분산 버전 관리 시스템
* Distributed Version Control System; DVCS
  * Git, Mercurial, Bazaar, Darcs
* 클라이언트가 저장소를 통째로 복사
* 서버에 문제가 생겨도 어느 클라이언트든 복제된 저장소를 다시 서버로 복사하면 서버가 복구됨

![Image](https://drive.google.com/uc?export=view&id=1WJl4sae8mR4C1RltXp0-Hu3dmpNvhkHX)  

