---
sidebar:
  title: "Git"
  nav: sidebar-git
  icon: "fab fa-github"
title: "GitHub Readme에 Badge 만들기"
toc: true
toc_sticky: true
toc_label: 목차
depth: 
  - title: "Git"
    url: /git/
    icon: "fab fa-github"
  - title: "Blog"
    url: /git/blog/
    icon: "far fa-folder-open"
---
오픈소스 프로젝트의 Readme 에 한눈에 알 수 있게 뱃지가 달려있는데 어떻게 만들고 달 수 있는지 알아보자.  
뱃지를 생성하고 링크하는 방법은 여러가지가 있으나  [<i class="fas fa-link"></i> https://shields.io/](https://shields.io/) 에서 제공해 주는 서비스가 가장 마음에 들어 해당 내용을 포스팅 한다.

## 타 Repo 에 있는 뱃지 샘플
<img src="https://img.shields.io/github/contributors/badges/shields" />
<img src="https://img.shields.io/opencollective/backers/shields" />
<img src="https://img.shields.io/opencollective/sponsors/shields" />
<img src="https://img.shields.io/github/commit-activity/m/badges/shields" />
<img src="https://img.shields.io/circleci/project/github/badges/shields/master" alt="build status">
<img src="https://img.shields.io/circleci/project/github/badges/daily-tests?label=service%20tests"
alt="service-test status">
<img src="https://img.shields.io/coveralls/github/badges/shields"
alt="coverage"/>
<img src="https://img.shields.io/lgtm/alerts/g/badges/shields"
alt="Total alerts"/>
<img src="https://img.shields.io/discord/308323056592486420?logo=discord"
alt="chat on Discord">
<img src="https://img.shields.io/twitter/follow/shields_io?style=social&logo=twitter"
alt="follow on Twitter">

정말 멋지다.

## 스타일
먼저 [<i class="fas fa-link"></i> 뱃지 서비스를하는 사이트](https://shields.io/)부터 방문하여 형태, 컬러, 스타일이 어떻게 제공되는지 샘플이 있으므로 간단하게 확인할 수 있다.    
나의 경우 flat-square 스타일이 가장 마음에 들었다.

## Color
기본적으로 
```
brightgreengreen
yellowgreen
yellow
orange
red
lightgrey
blue
success
important
critical
```
이렇게 제공이 되고 Hex 값도 지원하기 때문에 원하는 컬러만 안다면 된다.
사이트의 샘플을 이용하며 뱃지를 만들어보자.  

### critical color
```
[Generic badge](https://img.shields.io/badge/version-0.0.1-critical.svg)
```
![Generic badge](https://img.shields.io/badge/version-0.0.1-critical.svg)

### important color
![Generic badge](https://img.shields.io/badge/version-0.0.1-important.svg)


## Text 로고
### 단일 Text
```
![Badge](https://img.shields.io/badge/{ label }-{ color }.svg?{ style(optional) })
```
![Badge - Alamofire](https://img.shields.io/badge/Alamofire-brightgreen?style=flat-square)

### Message 를 포함한 Text
```
![Badge](https://img.shields.io/badge/{ label }-{ message }-{ color }.svg?{ style(optional) })
```
![Badge - Version](https://img.shields.io/badge/Version-0.0.1-1177AA?style=flat-square)
![Badge - Swift Package Manager](https://img.shields.io/badge/Swift Packgage Manager-compatible-orange?style=flat-square)
![Badge - Pod](https://img.shields.io/badge/pod-v5.4.3-blue?style=flat-square)
![Badge - Carthage](https://img.shields.io/badge/Carthage-compatible-green?style=flat-square)

## 이미지 로고
제공해 주는 이미지와 네이밍을 알아야 하기 때문에 [<i class="fas fa-link"></i> 여기](https://simpleicons.org/)에 방문하여 검색 후 해당하는 logo name 일 입력해 보자.
```
![Badge](https://img.shields.io/badge/{ label }-{ message }.svg?{ style(optional) }&logo={ logoname }&logoColor={ logo color(optional) })
```
![Badge](https://img.shields.io/badge/swift 5.4-white.svg?style=flat-square&logo=Swift)
![Badge](https://img.shields.io/badge/SwiftUI-001b87.svg?style=flat-square&logo=Swift&logoColor=black)
![Badge](https://img.shields.io/badge/Developer-000000.svg?style=flat-square&logo=iOS&logoColor=white)
![Badge](https://img.shields.io/badge/UI Kit-001b87.svg?style=flat-square&logo=Swift&logoColor=FA7343)
![Badge](https://img.shields.io/badge/RxSwift-B7178C.svg?style=flat-square&logo=ReactiveX)
![Badge](https://img.shields.io/badge/javascript-white.svg?style=flat-square&logo=JavaScript)


