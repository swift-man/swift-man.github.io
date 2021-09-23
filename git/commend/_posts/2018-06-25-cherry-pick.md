---
sidebar:
  title: "Git"
  nav: sidebar-git
  icon: "fab fa-github"
title:  "[Git] cherry-pick - 다른 브랜치의 일부 커밋만 반영"
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
다른 브랜치의 일부 커밋만 반영하고 싶을 때

## 코드
```
# git checkout next-release
# git cherry-pick b14b975
# git log --pretty=oneline
```

## 참고
[<i class="fas fa-link"></i> git cherry-pick: 다른 브랜치의 일부 커밋만 반영하고 싶을 때](http://meetup.toast.com/posts/45){:target="_blank"}
