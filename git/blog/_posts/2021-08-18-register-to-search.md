---
sidebar:
  title: "Git"
  nav: sidebar-git
  icon: "fab fa-github"
title: "GitHub Pages 검색 등록 하기"
group: "Blog"
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

>post url 에 특수문자가 있으면 추가가 안될 수 있으므로 한글 url 은 권장하지 않는다.

## 1. sitemap.xml 생성 
### 1.1 sitemap.xml 외부 사이트에서 생성
[xml-sitemaps](https://www.xml-sitemaps.com/) 에서 sitemap.xml 을 생성하자.

하단 이미지의 textbox 에 블로그의 url 을 넣어보자.
![Image](https://drive.google.com/uc?export=view&id=1jwwfAgfwRJYsKlBy2MNXAizlTEOpp1R6)

Start 를 누르자.
![Image](https://drive.google.com/uc?export=view&id=1fBNSGoUWjrsNrxG56mg4SwNZCfspbgbw)

다운로드버튼이 생성되고 누르면 받을 수 있다.  
다운로드 받은 sitemap.xml 을 root 에 넣고 push 하자.

### 1.2 sitemap.xml 직접 생성
직접 파일을 생성하면 jekyll 이 빌드할때 갱신해준다. 매번 갱신해주지 않아도 됨으로 이 방법을 권장한다.  
[<i class="fas fa-link"></i> sitemap.xml 파일 보러가기](https://github.com/swift-man/swift-man.github.io/blob/main/sitemap.xml){:target="_blank"}

파일 sitemap.xml 을 root 에 넣고 push 하자.

## 2. Google Search 등록
### 2.1 URL 검사
[<i class="fas fa-link"></i> Google Search Console](https://github.com/swift-man/swift-man.github.io/blob/main/sitemap.xml){:target="_blank"}로 가서 URL 검사를 하자.  

### 2.2 색인 생성 요청을 하자.

### 2.3 사이트맵을 추가하자.
![Image](https://drive.google.com/uc?export=view&id=1mutAhqrX3idmH9tR4ty3qwN7IFQM3HgX)  

미리 만들어 두었던 sitemap.xml 을 등록하면 된다.


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
