---
sidebar:
  title: "Git"
  nav: sidebar-git
  icon: "fab fa-github"
title:  "[Git] iOS 앱 개발 시 브랜치 관리"
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
iOS 앱 개발 시 브랜치 관리는 배포와 애플의 심사가 관여된다.  
최근 애플의 심사기간은 보통 1~2일 정도이며 예전보다 많이 짧아져서 배포 브랜치 관리는 좀 더 유연해 졌다.

브랜치 종류는 크게 4가지로 분류할 수 있다.
* 신규 개발을 하는 Feature 브랜치
* QA를 진행하는 Release 브랜치
* 배포를 완료한 Master 브랜치
* 개발 리뷰가 된 Develop 브랜치

배포가 완료되면 master로 정상적으로 머지를 진행하며, develop으로 머지를 진행한다. 이때 컨플릭 수정이 필요할 수 있다.

대략 그림을 그리자면 아래와 같다.
```
심사신청 -> 심사완료 -> release 브랜치 master 머지/태깅 -> 버전 업데이트 develop 머지
```
or
```
심사신청 -> release 브랜치 master 머지/태깅 -> 버전 업데이트 develop 머지
```

브랜치 전략은 애플 심사완료 시점과 상관 없이 신규 개발 프로세스에 영향이 없는 것이 가장 좋다.  
상황에 따라 애플 심사 리젝시 master에서 hotfix로 처리 후 머지하는 것도 방법 일 수 있다.

아마 회사마다, 사람마다 조금씩 다를 수 있기 때문에 위와 같이 할 수 있다는건 참고만 하면 좋겠다.


