---
sidebar:
  title: "Git"
  nav: sidebar-git
title: "마크 다운 문법"
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

기본 적인 마크 다운 문법 외 몰랐던 문법들을 정리한다.

## 1. 새창으로 링크 걸기
```
[원문 보러가기(새창)](/git/){:target="_blank"}
```
[원문 보러가기(새창)](/git/){:target="_blank"}

## 2. 툴팁 사용하기
```html
<div>
사용자가 커서로 항목을 가리키면 
<br/>
    <p class="tt">말풍ㄹㅇㅁㄹㅁㄴㄹㅇㅁㄴ\n선 
        <span class="tt-text">또는 툴fdafdfdasf
        fdafdsaf
        dsafdsa
        fdasfdsa
        fsf팁(tooltip)</span>
    </p>
이 나타납니다.
</div>
```

<div>사용자가 커서로 항목을 
가리키면 <p class="tt">말풍선 <span class="tt-text">또는 툴fdafdfdasf
fdafdsaf
dsafdsa
fdasfdsa
fsf팁(tooltip)</span></p>이 나타납니다.</div>


말풍선 쉽게 사용할 수 있게 할 줄 아는 분 제발 알려주세요!

## 3. 밑줄
```
<u>밑줄 있는 텍스트입니다</u>
```
<u>밑줄 있는 텍스트입니다</u>

## 4. 글씨 색
```
<span style="color:yellow">노란 글씨입니다.</span>
```
<span style="color:yellow">노란 글씨입니다.</span>

## 5. Gist
```
<script src="https://gist.github.com/swift-man/ce02c13aa87a79221f3b8e01122a3311.js"></script>
```
<script src="https://gist.github.com/swift-man/ce02c13aa87a79221f3b8e01122a3311.js"></script>

## 6. 게시글 비공개 처리
```
published : true
```
상단 헤더에 넣어준다.
