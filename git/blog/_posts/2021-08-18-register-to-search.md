---
sidebar:
  title: "Git"
  nav: sidebar-git
  icon: "fab fa-github"
title: "[GitHub Pages] 포털사이트에 검색 등록 하기"
tag: "Blog"
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
열심히 만든 블로그가 검색 되면 꾸준한 유지에 도움이 될 것이다. 시작 단계라 유입량이 적겠지만 그래도 검색되는 것은 몇 가지 설정만으로 가능하니 시도해보자.

>post url 에 특수문자가 있으면 추가가 안될 수 있으므로 `한글 url` 은 권장하지 않는다.  

## 1. sitemap.xml 생성
sitemap을 생성하는 방법은 여러가지가 있다.

### 1.1 sitemap.xml 외부 사이트에서 생성
[xml-sitemaps](https://www.xml-sitemaps.com/) 에서 sitemap.xml 을 생성하자.

하단 이미지의 textbox 에 블로그의 url 을 넣고 Start!
![Image](https://drive.google.com/uc?export=view&id=1jwwfAgfwRJYsKlBy2MNXAizlTEOpp1R6)

아래와 같이 만들어진 파일을 무료로 다운로드 할 수 있다.
![Image](https://drive.google.com/uc?export=view&id=1fBNSGoUWjrsNrxG56mg4SwNZCfspbgbw)

다운로드 받은 sitemap.xml 을 root 에 넣고 push 하자.

### 1.2 sitemap.xml 직접 생성
직접 파일을 생성하면 jekyll 이 빌드할때 갱신해준다. 매번 갱신해주지 않아도 됨으로 이 방법을 권장한다.  

[<i class="fas fa-link"></i> sitemap.xml 파일 보러가기](https://github.com/swift-man/swift-man.github.io/blob/main/sitemap.xml){:target="_blank"}

파일 `sitemap.xml` 을 root 폴더에 push 하자.

## 2. Google Search 등록
검색 노출에 중요한 요소가 몇가지 있는데 구글은 `모바일 최적화`도 확인한다. 그래서 검색에 등록될 사이트가 모바일 친화적인지 확인하면 좋다.

### 2.1 URL 검사
[<i class="fas fa-link"></i> Google Search Console](https://search.google.com/search-console/){:target="_blank"}로 가서 도메인을 등록 하자.  

### 2.2 소유권 검사
![Image](https://drive.google.com/uc?export=view&id=1T7TBZhmWmXsfe2Yfpo0F_NxUNnf7aQcu)  
DNS 소유권 검사가 필요하다. `Google Search Consol`에 검사할 때만 위 스크린샷의 DNS설정을 하고, 인증이 완료되면 다시 원하는 DNS로 원복 하자.  


![Image](https://drive.google.com/uc?export=view&id=1nMZUSbe8ry0qsAWisj8XZ9YTbacdhhlt)  
만약 소유권이 실패하면 더 이상 진행이 되지 않는다.

![Image](https://drive.google.com/uc?export=view&id=1w3SHOND5F1QKfgqpSJUkh-vN4tNIZbxa)  
DNS 설정을 마치면 소유권이 확인된다. 이후 `sitemap`을 등록하고 색인을 생성하자.

* 구글 검색에서 색인 등록 시 메타 태그사용을 하는 것을 권장한다. 
  * 각 페이지의 `<head>` 섹션에 메타 태그를 추가해야 검색 엔진에 페이지 내용을 더 잘 설명할 수 있다.
  * 현재 필자의 블로그는 많은 페이지의 메타 섹션이 부족한 상태다.

## 3. Naver 등록
### 3.1 웹 페이지 수집을 등록하자.
![Image](https://drive.google.com/uc?export=view&id=1MjHALlwQXWoiES09nQaOY1Op1Tp8o8mK)  
수집 요청 URL 입력인데 솔직히 잘 몰라서 index 를 입력했다.

### 3.2 sitemap.xml 을 등록하자.
![Image](https://drive.google.com/uc?export=view&id=1o_vHpIqhZ7seaXbDlZVWCgGsol5i4wIc)

### 3.3 RSS 제출을 하자!
![Image](https://drive.google.com/uc?export=view&id=19mEvtuiXOiRYLIWV4bnTGaEbk6XhY7bo)
RSS 을 생성하여 GitHub Repo Root 경로에 추가 후 Push 하자.  
[<i class="fas fa-link"></i> RSS 파일 보러가기](https://github.com/swift-man/swift-man.github.io/blob/main/feed.xml){:target="_blank"}  

## 4. Daum 등록
[<i class="fas fa-link"></i> Daum 검색등록](https://register.search.daum.net/index.daum){:target="_blank"}에 방문하자.  
![Image](https://drive.google.com/uc?export=view&id=1cQqH6v7GV2ttiGo6yj_NJOiDI8GALFz8)

다음은 url 만 등록하면 되는 거 같다. 사이트검색 / 블로그 등록 두가지 모두 등록 하였다.


## 5. robots.txt 등록
[<i class="fas fa-link"></i> robots.txt 란?](https://searchadvisor.naver.com/guide/seo-basic-robots){:target="_blank"}  

```
User-agent: *
Allow: /

Sitemap: https://swift-man.github.io/sitemap.xml
```
GitRepo Root 에 추가하고 push 하자.

## 검색 엔진 최적화
* 사이트 속도
  * 페이지 로딩 시간을 최적화하여 사용자 경험을 개선하고 검색 엔진 순위를 높혀야 한다.
* Backlink(다른 웹사이트에서 당신의 웹사이트로 연결되는 링크) 구축
  * 다른 웹사이트로부터의 Backlink는 검색 엔진 순위를 향상시키는 데 도움이 된다. 관련 있는 고품질 웹사이트와의 연결을 구축하는 것이 필요하다.

![Image](https://drive.google.com/uc?export=view&id=1-Kk829zWdqrL1F6iuzRcC8SGB_605FEJ)  

결과적으로 검색 엔진 최적화(SEO)는 기술적인 부분도 중요하지만, 결국 `콘텐츠의 품질`이 가장 중요하다. 유용하고, 독창적이며, 정기적으로 업데이트되는 콘텐츠를 제공해야하는데, 참 어려운 일이다.

