---
sidebar:
  title: "Git"
  nav: sidebar-git
  icon: "fab fa-github"
title:  "[Git] .gitignore 적용하기"
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
.gitignore란?  
GitHub에 체크인하고 싶지 않은 파일을 무시하도록 Git을 구성

## 패턴
* '#'로 시작하는 라인은 무시한다.
* 표준 Glob 패턴을 사용한다.
* 슬래시(/)로 시작하면 하위 디렉터리에 적용되지(recursivity) 않는다.
* 디렉터리는 슬래시(/)를 끝에 사용하는 것으로 표현한다.
* 느낌표(!)로 시작하는 패턴의 파일은 무시하지 않는다.

## 파일 만들기
터미널을 엽니다.
```
touch .gitignore
```
## .gitignore repo에 적용
```
git rm --cached .
git add *
git commit -m "message"
git push origin branch_name
```
 
## 컴퓨터의 모든 repositories에 구성
```
git config --global core.excludesfile ~/.gitignore_global
```

## 참고
[<i class="fas fa-link"></i> docs.github.com: Ignoring files](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files){:target="_blank"}  
[<i class="fas fa-link"></i> psk84.log: .gitignore 적용하기](https://velog.io/@psk84/.gitignore-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0){:target="_blank"}
