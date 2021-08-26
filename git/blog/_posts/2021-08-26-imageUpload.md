---
sidebar:
  title: "Git"
  nav: sidebar-git
title: "블로그에 이미지 올리기"
toc: true
toc_sticky: true
toc_label: 목차
---
[Git](/git/) / [Blog](/git/blog/) / **{{ page.title }}**
{: .notice--warning}
![](https://pages.github.com/images/logo.svg)

## 1. 개요
블로그에 이미지를 업로드하는 방법은 여러가지가 있다. 
나의 경우 추후 Github 용량을 고려하여 Google Drive 를 쓰기로 했다.

## 2. 링크 만들기
![Image](https://drive.google.com/uc?export=view&id=1ofLmA9slWa9shjtZtoSNHsPkWLXC5ynY)
![Image](https://drive.google.com/uc?export=view&id=1FN7DqMxK2PDohPq7d0pSLL2-1RKOrPR_)
구글 드라이브에 이미지를 업로드 하고 모두에게 공유로 링크를 만들면 아래와 같은 링크가 나온다.
```
ex) https://drive.google.com/file/d/1CuhXzbSrIdJjjs4DpbOl_O18oKV4FiL_/view?usp=sharing
https://drive.google.com/file/d/{ id }/view?usp=sharing
```

이것을 실제 이미지 주소로 가져와야 하는데 URL 룰은 아래와 같다.
```
ex) https://drive.google.com/uc?export=view&id=1CuhXzbSrIdJjjs4DpbOl_O18oKV4FiL_
https://drive.google.com/uc?export={ id }
```

## 3. markdown 문법으로 post 에 붙이기
```
![Image](https://drive.google.com/uc?export=view&id=1CuhXzbSrIdJjjs4DpbOl_O18oKV4FiL_)
```
- 이미지 테그를 추가해서 이미지가 나오는지 확인하자.

## 4. MacOS 용 이미지 컨버터 툴 만들기
나의 경우는 하나하나 만들고 이미지를 올리기 까지 반복되는 작업이 귀찮아 툴을 하나 만들었다.
막상 사용해보니
Parse, Copy 버튼을 상태에 따라 변경해줘야할 것 같다.

![Image](https://drive.google.com/uc?export=view&id=1wWGjb9e9HM-lh6JbTji7t3puTVMCjH8G)
공유 URL 을 넣으면~
![Image](https://drive.google.com/uc?export=view&id=1mSNdxAtzrnsI0lyJuvoqUca9UKFIlcmC)
컨버팅 해준다.



프로그램 배포는 아쉽게도 어려워 코드라도 공개해 놓았다.
[소스보기](https://github.com/swift-man/GoogleDriveOriginalURL)
