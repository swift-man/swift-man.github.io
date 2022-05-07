---
sidebar:
  title: "Clean"
  nav: sidebar-clean
  icon: "fab fa-weixin"
title: "코드 리뷰 피라미드"
toc: true
toc_sticky: true
toc_label: 목차
tag: "CodeReview"
depth: 
  - title: "Clean"
    url: /clean/
    icon: "fab fa-weixin"
  - title: "Code"
    url: /clean/code/
    icon: "far fa-folder-open"
---
코드 리뷰는 스타일 논의에 많은 시간을 할애하는 경우가 많다. 정말 중요한 코드의 기능, 프로젝트를 더 장기적으로 더 좋은 프로젝트를 위해 코드리뷰를 하고 있으며 `코드리뷰를 어디에 더 집중해야 하는가?`를 정리한 `코드리뷰 피라미드`를 보게 되어 이를 소개한다.  
![Image](https://drive.google.com/uc?export=view&id=1TyWLnzN4W-uAD4GTcOdeF-NdoHAFgV1P)  

## 이 부분을 리뷰하는데 집중하자
### API ⭐️⭐️⭐️⭐️⭐️
- API는 적절한 크기로 구현되었나요? 필요한 만큼 잘 구현되었나요?
- 일관성을 잘 지키고 있나요? 너무 크게 변경되지는 않았나요?
- API와 내부 로직이 깔끔하게 나누어져 있나요?
- API 사용 부분에서 하위 호환되지 않는 변경점은 없나요? (예. API classes, 설정, metrics, 로그 포맷 등)
- 새로운 API가 전반적으로 사용 가능한가요? 혹시 너무 특정 사용만 가능하진 않나요?

### 구현 ⭐️⭐️⭐️⭐️
- 요구사항을 모두 만족하고 있나요?
- 모든 로직이 올바른 가요?
- 불필요하게 복잡하진 않나요?
- 문제 될 수 있는 상황들에 대해 꼼꼼히 고려했나요? (예. 동시성 이슈나, 에러 핸들링 등)
- 성능이 좋은가요?
- 안전하게 짜였나요? (예. SQL 인섹젼 등)
- 모니터링할 수 있나요? (예. metrics, logging, tracing 등)
- 새로 추가된 의존성이 그들의 역할을 제대로 하고 있나요? 라이센스 문제는 없나요?

### 문서화 ⭐️⭐️⭐️
- 새로 추가된 기능들이 적절히 문서화되었나요?
- 관련 문서 모두 확인되었나요? README, API 문서, 유저 가이드, 레퍼런스 문서 등
- 문서는 모두 이해하기 쉽고, 중요한 오타나 문법 오류는 없나요?


## 자동화 하세요
### 테스트 ⭐️⭐️
- 모든 테스트가 통과했나요?
- 새로 추가된 기능들이 모두 적절하게 테스트 되었나요?
- 코너 케이스(여러 환경과 변수로 인한 복합적인 원인으로 발생하는 문제)도 테스트 되었나요?
- (가능한 한) 유닛 테스트와 (필요한 경우에 대한) 통합 테스트가 되었나요?
- 비기능 요건(NFR, Non-functional requirement)에 대한 테스트도 되었나요?(예. 성능)

### 코드 스타일 ⭐️
- 이 프로젝트에는 포매팅 스타일이 적용되었나요?
- 네이밍 컨벤션은 잘 지켜졌나요?
- 중복은 없나요? DRY(Don't Repeat Yourself) 했나요?
- 코드는 충분히 가독성 있나요?


## 출처
[<i class="fas fa-link"></i> NGunnar Morling](https://www.morling.dev/about/)  
[<i class="fas fa-link"></i> The Code Review Pyramid](https://www.morling.dev/blog/the-code-review-pyramid)  
[<i class="fas fa-link"></i> @xguru-Geeknews](https://jiyeonseo.github.io/2022/04/03/the-code-review-pyramid/)  
[<i class="fas fa-link"></i> Jiyeon Seo 2020](https://jiyeonseo.github.io/2022/04/03/the-code-review-pyramid/)
