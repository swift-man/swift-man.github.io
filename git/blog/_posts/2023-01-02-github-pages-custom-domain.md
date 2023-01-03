---
sidebar:
  title: "Git"
  nav: sidebar-git
  icon: "fab fa-github"
title: "Github 블로그 AWS로 커스텀 도메인 설정"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Blog"
depth:
  - title: "Git"
    url: /git/
    icon: "fab fa-github"
  - title: "Blog"
    url: /git/blog/
    icon: "far fa-folder-open"
---
GitHub는 다양한 Custom Domain 설정 방법이 있다.
* A
* CNAME

필자는 `blog.domain.com` 을 사용할 것이기 때문에 CNAME으로 설정할 것이다.  
> `domain.com` 와 같이 루트도메인을 사용한다면 DNS 설정과 중복되어 A 타입으로 설정이 필요하다.  


## 1. Github Pages설정 하기
```
Setting > Github Pages > Custom domain
```
![Image](https://drive.google.com/uc?export=view&id=16zZZQ-oJWikqH_CfAu2PCyXBEk2MJ0To)  
원하는 도메인을 설정하고 저장하자.

## 2. AWS - Route53 설정
### 2.1 Route53은 도메인을 관리할 수 있는 매우 편리한 서비스다.
![Image](https://drive.google.com/uc?export=view&id=1kL9bnkmkPciKsw64nZIJRbCC02DghS81)  

### 2.2 sub domain 설정
> DNS 연결은 다루지 않는다. 

![Image](https://drive.google.com/uc?export=view&id=1hkbSwyEQADs_C7zmMSkfEc3uz1e8qWK-)  
* 레코드 유형 : CNAME
* 값 : 자신의 블로그 domain
> 값에 `https://` 는 생략


![Image](https://drive.google.com/uc?export=view&id=1Z_E3YkOpMw6TljRHwTVSgWkslFf6e8xs)  
으음? 잘되는군!
