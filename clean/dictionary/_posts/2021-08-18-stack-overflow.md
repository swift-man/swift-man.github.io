---
sidebar:
  title: "Clean"
  nav: sidebar-clean
  icon: "fab fa-weixin"
title: "Stack overflow"
toc: true
toc_sticky: true
toc_label: 목차
depth: 
  - title: "Clean"
    url: /clean/
    icon: "fab fa-weixin"
  - title: "Dictionary"
    url: /clean/dictionary/
    icon: "far fa-folder-open"
---
소프트웨어에서 [<i class="fas fa-link"></i> 스택](/algorithm/data-structure/stack/) 포인터가 스택의 경계**를 넘어설 때 일어난다. 호출 스택은 제한된 양의 주소 공간을 이루며 대개 프로그램 시작 시 결정된다.

프로그램이 호출 스택에서 이용 가능한 공간 이상을 사용하려고 시도할 때, 스택이 오버플로(overflow)된다고 하며 이에 대한 적당한 대처방안이 준비되어 있지 않으면 다른 메모리 영역을 침범할 수 있게 된다. 이 경우 일반적으로 프로그램 충돌이 발생하게 된다.

보통 잘못된 재귀호출 등으로 인해 지나치게 많은 버퍼를 요청하여 운영체제가 더이상 할당을 할 수 없게 될 때 발생한다.

이를 이용한 해킹 기법도 존재한다.
