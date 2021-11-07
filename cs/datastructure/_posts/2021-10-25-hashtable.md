---
sidebar:
  title: "CS"
  nav: sidebar-cs
  icon: "fas fa-microchip"
title: "Hash Table"
toc: true
toc_sticky: true
toc_label: 목차
tag: "DataStructure"
depth:
  - title: "CS"
    url: /cs/
    icon: "fas fa-microchip"
  - title: "DataStructure"
    url: /cs/datastructure/
    icon: "far fa-folder-open"
---

F(key)->hashCode->Index->Value

## HashCode
입력데이터가 같으면 동일한 해시코드를 만들어내는 알고리즘

## 장점
검색속도가 매우 빠르다.O(1)
해시코드는 정수다. 해시코드가 바로 Index로 사용되기 때문에 저장소에 바로 접근이 가능하다.

## 충돌현상(Collison)
해시함수의 알고리즘은 입력받은 키를 가지고 얼마나 잘 분배하느냐가 좋은 알고리즘에 속한다.
O(N)

알고리즘이 아무리 좋아도 중복되는 키를 가질 수 밖에 없다.

충돌을 해결하기 위한 방법은 크게 2가지다. 

### 개별 체이닝(Separate Chaining)
배열의 타입을 LinkedList로 선언하여 체이닝 하는 방법이 있다.
LinkedList에 데이터가 체이닝 된다면 검색 속도는 O(N)이 될 수 있다.

### 오픈 어드레싱(Open Addressing)
무한정 저장할 수 있는 체이닝 방식과 달리, 오픈 어드레싱 방식은 전체 슬롯의 개수 이상은 저장할 수 없다. 충돌이 일어나면 테이블 공간 내에서 탐사(Probing)를 통해 빈 공간을 찾아 해결하며, 이 때문에 개별 체이닝 방식과 달리, 모든 원소가 반드시 자신의 해시값과 일치하는 주소에 저장된다는 보장은 없다.  

저장된 데이터가 적으면 성능이 좋은편이나, 수용률이 넘어서게 되면 저장/조회 성능이 모두 점점 떨어지게 된다. 이를 해결하는 방법으로 더 큰 리스트를 만들어 적당한 타이밍에 점진적으로 몇 개씩 옮기다가 다 옮기면 기존 테이블을 제거하고 확장하는 방식도 있다.

## ConvertToIndex(HashCode)
HashCode % array.size 로 Index 로 환산할 수 있다.


