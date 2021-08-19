---
sidebar:
  title: "Git"
  nav: sidebar-git
title: "검색 등록 하기"
toc: true
toc_sticky: true
toc_label: 목차
---

## 1. 개요
- 열심히 만든 블로그가 검색 되면 꾸준한 유지에 도움이 될 것이다.
- 아마 유입량이 적겠지만 그래도 검색되는 것은 몇 가지 설정만으로 가능하니 시도하자.


## 2. Google Search 등록
[xml-sitemaps](https://www.xml-sitemaps.com/) 에서 sitemap.xml 을 생성하자.
![Image](https://drive.google.com/uc?export=view&id=1jwwfAgfwRJYsKlBy2MNXAizlTEOpp1R6)
- textbox 에 자신의 url 을 넣어보자.
- post url 에 특수문자가 있으면 추가가 안될 수 있으므로 한글 url 은 권장하지 않는다.

## 2.1 방법 1 - 외부 사이트에서 생성
![Image](https://drive.google.com/uc?export=view&id=1fBNSGoUWjrsNrxG56mg4SwNZCfspbgbw)
- 이렇게 다운로드를 받을 수 있다.
- 다운로드 받은 sitemap.xml 을 root 에 넣고 push 하자.

## 2.2 방법 2 - 직접 파일 생성
- 직접 파일을 생성하면 jekyll 이 빌드할때 갱신해준다.
- 매번 갱신해주지 않아도 됨으로 이 방법을 권장한다.
- [파일 보러가기](https://github.com/swift-man/swift-man.github.io/blob/main/sitemap.xmll)


[Google Search](https://search.google.com/search-console)
- URL 검사를 하자.
- 색인 생성 요청을 하자.
![Image](https://drive.google.com/uc?export=view&id=1mutAhqrX3idmH9tR4ty3qwN7IFQM3HgX)
- sitemap.xml 을 등록하자.

## 3. Naver 등록
![Image](https://drive.google.com/uc?export=view&id=1MjHALlwQXWoiES09nQaOY1Op1Tp8o8mK)
![Image](https://drive.google.com/uc?export=view&id=19mEvtuiXOiRYLIWV4bnTGaEbk6XhY7bo)
- [파일 보러가기](https://github.com/swift-man/swift-man.github.io/blob/main/feed.xmll)
![Image](https://drive.google.com/uc?export=view&id=1o_vHpIqhZ7seaXbDlZVWCgGsol5i4wIc)

## 4. Daum 등록
![Image](https://drive.google.com/uc?export=view&id=1cQqH6v7GV2ttiGo6yj_NJOiDI8GALFz8)


## 5. robots.txt 등록
* [robots.txt 란?](https://searchadvisor.naver.com/guide/seo-basic-robots)

```
User-agent: *
Allow: /

Sitemap: https://swift-man.github.io/sitemap.xml
```
- root 에 추가하고 push 하자.

{% include utteranc.html %}
