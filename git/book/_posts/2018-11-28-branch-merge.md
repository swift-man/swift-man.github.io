---
sidebar:
  title: "Git"
  nav: sidebar-git
  icon: "fab fa-github"
title:  "[Git] iOS 앱 개발/배포 브랜치 관리"
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
Gitflow를 소프트웨어 개발에서 많이 사용한다. 각 브랜치 별 역할이 나눠지고, 개발자들의 협업에 매우 유연하게 개발이 가능하기 때문이다.  

Gitflow에서는 브랜치 종류는 크게 5가지로 분류할 수 있다.
* 신규 개발을 하는 feature 브랜치
* QA를 진행하는 release 브랜치
* 배포를 완료한 master 브랜치
* 다음 개발 버전을 위한 develop 브랜치
* 긴급 패치를 위한 hotfix 브랜치

![Image](https://techblog.woowahan.com/wp-content/uploads/img/2017-10-30/git-flow_overall_graph.png) 

## develop 브랜치는 왜 필요할까?
한 프로젝트에 여러 feature는 병행되어 개발된다. feature는 마일스톤(일정) 개념으로 관리되며 해당 마일스톤에 배포될 기능들을 개발 브랜치에 통합한다. 여러 개발자/ 여러 feature는 '잘' 개발될 수 있도록 코드 동기화가 수시로 필요하고, 동기화를 위한 코드 머지도 신중해야 한다. 개발자의 입장에서는 사업/기획의 요구 사항 외 버그 수정이나 리펙토링, 대규모 구조변경도 개발자의 입장에선 모두 feature다. 그래서 모든 브랜치는 develop의 최신 노드로부터 만들어지고 feature 개발이 완료되면 코드 리뷰를 통해 다시 develop으로 머지한다. 작업한 feature 브랜치는 삭제하는 것을 원칙으로 한다. 

그럼 왜 develop에 머지를 해야 할까? 개발자 간 협업은 매우 중요한데, develop이 없으면 작업의 병목현상이 생긴다. A feature와 B feature가 병행되어 개발된다라고 가정하면 A, B 가 완전히 연관성이 없더라도 기획의 방향의 변경이나, 동일 기능에 대해 재사용이 가능할 수 있다. 이런 것을 효율적으로 하려면 개발자 중심의 브랜치에서 코드의 동기화가 필요하다. 

코드의 동기화는 매우 중요하다고 생각한다. 한 명의 개발자가 매일 200~400라인을 수정한다고 하면 10명의 개발자는 매일 2000~4000라인을 수정하게 된다. 그게 5일이 지나면 5일 전 develop의 코드와 오늘의 코드는 매우 달라져 있을 것이다. 따라 신규 feature는 develop의 가장 최신의 노드에서 시작하는 게 비용과 관리 측면에서 매우 유리하다. 

그래서 develop에 머지될 개발된 브랜치는 테스트 코드와 코드 리뷰가 매우 중요하다. develop에 머지하기 위해서는 상호 검증을 통해 매우 신중을 기하게 된다. QA를 타지 못한 코드는 당연히 버그가 있을 수 있고 이 버그는 팀원에게 좋지 못한 경험을 선사하기 때문이다.

## feature 브랜치는 왜 필요할까?
앞서 말한 것처럼 개발은 병행으로 이루어진다. 여러 개발자는 develop 중심의 코드 관리를 통해 여러 개발자가 개선된 구조/로직 등을 동기화하며 이를 이용해 개발한다. 하나의 feature는 하위 feature의 트리구조로 만들 수 있다.  

개발이 완료되면 코드 리뷰를 통해 develop에 머지하도록 PR을 만들어 개발자들의 코드 리뷰를 거치게 되며 승인이 되면 develop에 머지할 수 있는 자격이 생긴다. 

develop에서 release가 만들어지기 때문에 PR을 만드는 시기는 release 브랜치가 만들어지는 시기와 매우 밀접한데, 해당 마일스톤의 QA 전에 develop에 머지되는 것이 원칙이다.  

마일스톤이 이번 release가 아니라 다음 release인데 PR을 만들면 안 되며, 이런 경우 해당 개발 일정을 잘 산정했는지, 우선순위가 잘 정렬되었는지 생각해볼 문제다.

## release 브랜치는 왜 필요할까?
iOS 앱 개발 시 브랜치 관리는 배포와 애플의 심사가 관여된다. 
최근 애플의 심사기간은 보통 1~2일 정도이며 예전보다 많이 짧아져서 배포 브랜치 관리는 좀 더 유연해졌다. 

develop 은 새로운 release 1.2.4 버전의 브랜치가 만들어지면 그다음 버전의 release 1.3.0 버전 배포로 목표가 변경된다. release 1.2.4에서 QA를 통해 여러 수정사항이 발생되게 되는데 develop에서 진행했던 작업을 release로 관점을 그대로 옮긴다. QA 수정사항이나 기획 변경사항은 release 브랜치에서 수정한다. develop과 release는 투 트랙으로 관리하여 효율적으로 관리가 가능하다.

## master 브랜치는 왜 필요할까?
배포가 완료되면 master로 정상적으로 머지를 진행하며, develop으로 머지를 진행한다. 이때 컨플릭 수정이 필요할 수 있다.

대략 그림을 그리자면 아래와 같다.
```
심사신청 -> 심사완료 -> release 브랜치 master 머지/태깅 -> 버전 업데이트 develop 머지
```
or
```
심사신청 -> release 브랜치 master 머지/태깅 -> 버전 업데이트 develop 머지
```

## hotfix 브랜치는 왜 필요할까?



브랜치 전략은 애플 심사완료 시점과 상관 없이 신규 개발 프로세스에 영향이 없는 것이 가장 좋다.  
상황에 따라 애플 심사 리젝시 master에서 hotfix로 처리 후 머지하는 것도 방법 일 수 있다.

아마 회사마다, 사람마다 조금씩 다를 수 있기 때문에 위와 같이 할 수 있다는건 참고만 하면 좋겠다.


## 참고
[<i class="fas fa-link"></i> 우린 Git-flow를 사용하고 있어요](
https://techblog.woowahan.com/2553/){:target="_blank"}  
