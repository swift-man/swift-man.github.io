---
sidebar:
  title: "CS"
  nav: sidebar-cs
  icon: "fas fa-microchip"
title: "Hash Table"
icon: "fab fa-youtube"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Encryption"
depth:
  - title: "CS"
    url: /cs/
    icon: "fas fa-microchip"
  - title: "DataS"
    url: /cs/Encryption/
    icon: "far fa-folder-open"
---

F(key)->hashCode->Index->Value

## HashCode
입력데이터가 같으면 동일한 해시코드를 만들어내는 알고리즘

## 장점
검색속도가 매우 빠르다.O(1)
해시코드는 정수또는 16진수 결과적으로 숫자다. 해시코드가 바로 Index로 사용되기 때문에 저장소에 바로 접근이 가능하다.

## 충돌현상(Collison)
해시함수의 알고리즘은 입력받은 키를 가지고 얼마나 잘 분배하느냐가 좋은 알고리즘에 속한다.
O(N)

알고리즘이 아무리 좋아도 중복되는 키를 가질 수 밖에 없다.

## ConvertToIndex(HashCode)
HashCode % array.size 로 Index 로 환산할 수 있다.


