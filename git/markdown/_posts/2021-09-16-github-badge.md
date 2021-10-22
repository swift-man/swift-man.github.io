---
sidebar:
  title: "Git"
  nav: sidebar-git
  icon: "fab fa-github"
title: "GitHub Readme에 Badge 만들기"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Markdown"
depth: 
  - title: "Git"
    url: /git/
    icon: "fab fa-github"
  - title: "Markdown"
    url: /git/markdown/
    icon: "far fa-folder-open"
---
오픈소스 프로젝트의 Readme는 뱃지가 있는 경우가 대부분이다. 이러한 뱃지를 통해 이 Repo가 어떤 속성인지를 쉽게 알수 있도록 유저에게 제공 한다. 그럼 뱃지를 어떻게 만들고 게시 할 수 있는지 알아보자.  
뱃지를 생성하고 링크하는 방법은 여러가지가 있다. 
팔저의 경우 [<i class="fas fa-link"></i> shields.io/](https://shields.io){:target="_blank"} 에서 제공해 주는 서비스가 가장 마음에 들어 해당 내용을 포스팅 한다.

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
먼저 [<i class="fas fa-link"></i> 뱃지 서비스를하는 사이트](https://shields.io/){:target="_blank"}부터 방문하여 형태, 컬러, 스타일 등 제공되는 샘플을 볼 수 있다.    
필자의 경우 'flat-square' 스타일이 가장 마음에 들었다.

## Color
기본적으로 아래와 목록에 해당하는 컬러를 지원한다.
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
Hex Color도 지원한다.    
사이트의 샘플과 원하는 컬러 를 이용하며 뱃지를 만들어보자.  

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
이미지의 경우 이미지와 네이밍을 알아야 한다. [<i class="fas fa-link"></i>  simpleicons.org](https://simpleicons.org/){:target="_blank"}에서 제공하고 있다. 방문하여 확인하자.  
검색 후 해당하는 logo name 일 입력해 보자.
```
![Badge](https://img.shields.io/badge/{ label }-{ message }.svg?{ style(optional) }&logo={ logoname }&logoColor={ logo color(optional) })
```
![Badge](https://img.shields.io/badge/swift 5.4-white.svg?style=flat-square&logo=Swift)
![Badge](https://img.shields.io/badge/SwiftUI-001b87.svg?style=flat-square&logo=Swift&logoColor=black)
![Badge](https://img.shields.io/badge/Developer-000000.svg?style=flat-square&logo=iOS&logoColor=white)
![Badge](https://img.shields.io/badge/UI Kit-001b87.svg?style=flat-square&logo=Swift&logoColor=FA7343)
![Badge](https://img.shields.io/badge/RxSwift-B7178C.svg?style=flat-square&logo=ReactiveX)
![Badge](https://img.shields.io/badge/javascript-white.svg?style=flat-square&logo=JavaScript)


## 이제 ReameMe.md 에 붙여보자.
![Image](https://drive.google.com/uc?export=view&id=1c06gGU7fiJw4UePSsGkv0RLJYQH9HWMX)
