---
sidebar:
  title: "Git"
  nav: sidebar-git
title:  "Cherry-pick"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : "다른 브랜치의 일부 커밋만 반영하고 싶을 때"
---
[Git](/git/) / [Commend](/git/commend/) / **Cherry-pick**
{: .notice--warning}
![](https://git-scm.com/images/logo@2x.png)

## 1. 개요
- 다른 브랜치의 일부 커밋만 반영하고 싶을 때

## 2. 코드
```
# git checkout next-release
# git cherry-pick b14b975
# git log --pretty=oneline
```

- 참고: [git cherry-pick: 다른 브랜치의 일부 커밋만 반영하고 싶을 때](http://meetup.toast.com/posts/45)

{% include utteranc.html %}
