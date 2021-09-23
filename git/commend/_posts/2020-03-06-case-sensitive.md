---
sidebar:
  title: "Git"
  nav: sidebar-git
  icon: "fab fa-github"
title: "[Git] commit 파일명 대소문자 인식"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Git Commend"
depth: 
  - title: "Git"
    url: /git/
    icon: "fab fa-github"
  - title: "Commend"
    url: /git/commend/
    icon: "far fa-folder-open"
---
Git 은 기본적으로 파일/폴더 명에 대한 대소문자 인식을 구분하지 않는다.
이를 수정했을때 인식되지 않아 오류가 발생할 수 있는데 이것을 구분하기 위한 설정이 필요하다.

## 코드
```
git config core.ignorecase false
```
