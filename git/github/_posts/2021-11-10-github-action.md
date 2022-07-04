---
sidebar:
  title: "Git"
  nav: sidebar-git
  icon: "fab fa-github"
title:  "GitHub Actions"
toc: true
toc_sticky: true
toc_label: 목차
tag: "GitHub"
depth: 
  - title: "Git"
    url: /git/
    icon: "fab fa-github"
  - title: "GitHub"
    url: /git/github/
    icon: "far fa-folder-open"
---
왜 GitHub Actions을 써야하는 이유는 워크플로우를 자동화해준다.
![Image](https://drive.google.com/uc?export=view&id=1U5xZXheOUoErAeQYrdzws_NCT9IwtguV)  

## 다양한 CI/CD 툴스 랜드 스케이프
Jenkins, argo, cicle ci, Travis CI, CI CD, Bamboo TEKTON

## 깃허브 액션의 장점
### 시작하기 쉬워요
- 깃허브만 있으면 깃허브 액션은 즉각 쓸 수 있다.
  - 컴퓨터에 어떤 것을 인스톨 하지 않아도 사용할 수 있다.
  - 세부적인 환경을 신경쓰지 않고 바로 사용할 수 있다.
  
![Image](https://drive.google.com/uc?export=view&id=1uWSu85NrGiewaDEXEWpQluykzHCNpcjI)  
> github 계정의 언어를 분석해 [<i class="fas fa-link"></i> starter-workflow](https://github.com/actions/starter-workflows/tree/main/ci)추천해 준다.

### 저렴한 가격
- public 인 경우 무료(1달에 2000분)
- Public 레포나 [<i class="fas fa-link"></i> Self-Hosted runner](https://docs.github.com/en/actions/using-github-hosted-runners/about-github-hosted-runners#supported-software){:target="_blank"}를 사용하면 무료다.
- [<i class="fas fa-link"></i> 자세한 가격 정책](https://github.com/pricing){:target="_blank"}

### 깃허브 마켓플레이스를 통해 찾을 수 있는 다양한 기능
- 기업과 커뮤니티가 만든 몇천개가 넘는 액션 플러그인을 찾아볼 수 있다.
  - 보안을 향상시키는 액션도 있음.
  
### GitOps 모델을 따른다.
- 깃허브 액션은 깃허브 안에 통합
![Image](https://drive.google.com/uc?export=view&id=111OL9i8xzrq0MAYzYUboSyJZTYYoXgTu)  
![Image](https://drive.google.com/uc?export=view&id=1PL3-emCf3QXRJ3ubc7KVtBsK-N0DvIi2)  

## 깃허브 액션이란?
![Image](https://drive.google.com/uc?export=view&id=1X8ZXxT6jl4A1uHqbz0IGqIy4merDq1-D)  
깃허브 액션은 깃허브가 제공하는 워크플로우를 자동화 시켜주는 제품
- 워크플로우는 YAML파일로 저장
- 깃허브와 완벽하게 통합
- 깃허브 이벤트에 반응
- 라이브 로그와 실행을 시각해 시켜주는 기능
- 워크플로우는 커뮤니티 활동을 통해 뒷바침
- 깃허브가 제공하는 기본 설정 러너가 있지만 직접 설치하는 Self-hosted 러너도 만들 수 있음
- 암호나 비밀값을 저장하는 서비스가 내장

## 깃허브 마켓플레이스
- 오픈소스로 되어 있는 다양한 깃허브 액션 플러그인
- 9000개 이상의 플러그인
- 기업들이 직접 만든 플러그인
- 액션들을 바로 사용 가능
- 깃허브 에디터에 자동 설치

### Xcode 와 관련한 Action 들
* [<i class="fas fa-link"></i> Setup Xcode version](https://github.com/marketplace/actions/setup-xcode-version){:target="_blank"}  
* [<i class="fas fa-link"></i> Xcodebuild Action](https://github.com/marketplace/actions/xcodebuild-action){:target="_blank"}  
* [<i class="fas fa-link"></i> xcresulttool](https://github.com/kishikawakatsumi/xcresulttool){:target="_blank"}  

## 주요 컴포넌트
![Image](https://drive.google.com/uc?export=view&id=1cWsMETmyOKDIfHbxQJ87YT6habN_HHxo)  
> 아키텍처의 기본적인 것을 나타내는 이미지

- 이벤트를 실행시키면 워크플로우가 시작된다.
- 이 잡들은 각각 러너라고 해서, 서플리스 개념으로 일시적으로 시작되었다가 셧다운되는 에이전트 안에서 돌아간다.
- 각 잡 안에서 여러가지 스탭을 정할 수 있다.
- 제공되는 라이브 로그를 통해서 진행과정을 실시간으로 확인 할 수 있다.

## 기본 문법
```
name: Greet Everyone

on:                                               # 이벤트
  push: 

jobs:                                             # Job 
  lint:
    name: Lint Code Base

    runs-on: ubuntu-latest                        # 러너

    steps:                                        # 스탭
    
      - uses: actions/checkout@v2                 # 액션
      
      - uses: actions/checkout@v3
      env:
        GITHUB_TOKEN: \{\{ secrets.GITHUB_TOKEN \}}   # 시크릿
```

## 워크플로우 스타터
깃허브 액션에 내재되어 있는 기능으로 몇번의 클릭으로 스크립트를 자동으로 생성 할 수 있음
- 상당수 프로그래밍 언어와 프레임워크의 통합
- 깃허브가 코드를 해석한 후 선택한 프로그래밍 언어와 프레임워크를 인식하고 자동으로 맞는 워크플로우를 추천
- GHES 3.x: 다양한 스타터 워크플로우 릴리즈를 통해 같이 제공

## 스케쥴링
```
name: cron

on:
  schedule:
    # 실제 스케쥴 작업이 시작될 cron을 등록하면 됩니다.
    # 크론은 https://crontab.guru/ 여기서 확인하면 좋을 것 같습니다.
    # 이 크론은 평일 5시 (한국시간 14시)에 실행됩니다.
    - cron: '0 5 * * 1-5'
```

## Events that trigger workflows
* workflows 의 성공/실패여부를 [<i class="fas fa-link"></i> JobContext](https://docs.github.com/en/actions/learn-github-actions/contexts#job-context){:target="_blank"}로 판단 가능 


## How to Automate XCTests With GitHub Actions
[<i class="fas fa-link"></i> How to Automate XCTests With GitHub Actions](https://betterprogramming.pub/how-to-automate-xctests-with-github-actions-6570fcd21519){:target="_blank"}  
[<i class="fas fa-link"></i> Learn GitHub Actions](https://docs.github.com/en/actions/learn-github-actions){:target="_blank"}  
[<i class="fas fa-link"></i> [CI/CD] Github Actions 를 이용한 xcode build & test 자동화](https://sujinnaljin.medium.com/ci-cd-github-actions-%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%9C-xcode-build-test-%EC%9E%90%EB%8F%99%ED%99%94-73b90a3dcc65){:target="_blank"}  


## 참고
[<i class="fas fa-link"></i> GitHub Actions로 수행하는 CI/CD DevOps, 리포트 만들기, 메시지 보내기 등의 놀라운 작업들](https://www.youtube.com/watch?v=356L7uv_W8Q){:target="_blank"}
