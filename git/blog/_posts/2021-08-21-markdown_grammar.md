---
sidebar:
  title: "Git"
  nav: sidebar-git
title: "마크 다운 문법"
toc: true
toc_sticky: true
toc_label: 목차
---
[Git](/git/) / [Blog](/git/blog/) / **{{ page.title }}**
{: .notice--warning}
![](https://pages.github.com/images/logo.svg)

## 1. 개요
- 기본 적인 마크 다운 문법 외 몰랐던 문법들을 정리한다.

    
## 2. 새창으로 링크 걸기
```
- [원문 보러가기(새창)](/git/){:target="_blank"}
```
- [원문 보러가기(새창)](/git/){:target="_blank"}

## 3. 툴팁 사용하기
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
fdafdsa
<div>* 사용자가 커서로 항목을 
가리키면 <p class="tt">말풍선 <span class="tt-text">또는 툴fdafdfdasf
fdafdsaf
dsafdsa
fdasfdsa
fsf팁(tooltip)</span></p>이 나타납니다.</div>


- 말풍선 쉽게 사용할 수 있게 할 줄 아는 분 제발 알려주세요!

## 4. 노트 사용하기
```
---
**NOTE**

It works with almost all markdown flavours (the below blank line matters).

---
```
---
**NOTE**

It works with almost all markdown flavours (the below blank line matters).

---
