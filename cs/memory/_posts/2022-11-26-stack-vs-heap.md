---
sidebar:
  title: "CS"
  nav: sidebar-cs
  icon: "fas fa-microchip"
title: Stack Memory vs Heap Memory Speed
toc: true
toc_sticky: true
toc_label: 목차
tag: "CS Memory"
depth:
  - title: "CS"
    url: /cs/
    icon: "fas fa-microchip"
  - title: "Memory"
    url: /cs/memory/
    icon: "far fa-folder-open"
---
Stack Memory가 Heap Memory 보다 속도가 더 빠른 이유에 대해 생각해봤다.  
CPU에서 접근하는 메모리는 CPU 내의 메모리다. DRAM은 CPU에서 주소를 복사해 오고 그곳을 접근한다.

보통 `32-bit`앱은 2G의 가상 주소 공간을 가진다. Stack의 크기가 2MB면 1024개의 스레드를 생성할 수 있다.

`Web Server`에서는 stack의 크기를 100MB로 늘리더라도 바로 100MB를 할당하지 않으며, 스레드 수를 20개로 제한할 수 있다.

> 64-Bit 플랫폼에도 여전히 이러한 제한이 있으며 "stack best pratices"에 익숙해졌기 때문이다.<br/>
큰 객체는 Heap에 놓고 필요할 때만 스택의 크기를 늘리는 것이 좋다.<br/>
그래서 64-Bit 플랫폼에서 어떤 환경도 기본으로 "큰" Stack을 지원하지 않는 이유다.

## 객체 생성에서 Stack이 유리
* Stack 
  * 객체 생성하는 과정이 매우 빠르다.
  * 사용 공간을 [<i class="fas fa-link"></i> CPU Register](/cs/cpu/register/)가 관리
  * 스레드 동기화 불필요
    * 스레드마다 Stack 공간이 각 존재 
* Heap 
  * 객체 생성하는 과정이 매우 느리다.
  * 공용 공간이므로 메모리 파편화 발생
    * 객체 생성에 필요한 사이즈를 메모리에서 찾는 과정이 필요
  * 스레드 동기화 필요
    * 공간 할당 시 다른 스레드가 그 공간을 사용하지 않도록 동기화 비용 발생

## 접근에서 Stack이 유리
* Stack
  * CPU가 메모리의 주소로 바로 값을 읽는다.
* Heap
  * CPU가 메모리의 주소로 Heap에 할당된 주소를 참조하므로 Heap 주소로 다시 값을 읽는다.

## 메모리 크기 결정에서 Stack이 유리
  [<i class="fas fa-link"></i> 메모리 공간 분류와 크기 결정 Time](/cs/memory/memory-space/)

## 할당 속도에서 Stack이 유리
* Stack
  * Run Time에 할당
  * 별도의 연산이 거의 들지 않는다.
* Heap
  * Run Time에 할당
  * 빈 공간을 찾고 alloc에 대한 연산이 필요하다.

## 해제 속도에서 Stack이 유리
* Stack
  * 별도의 연산이 거의 들지 않는다.
* Heap
  * dealloc에 대한 연산이 필요하다.
  * 메모리를 해지하지 않으면 프로그램이 종료될 때까지 유지

## 사이즈에 대한 문제
* Stack
  * 크기가 매우 작아 관리가 쉽지 않음
  * 연속적인 메모리 위치에 저장될 필요가 있음, 따라 랜덤으로 할당 불가능
      * 이를 해결하기 위해 최소한 가상 주소를 예약
      * 예약된 가상 주소 공간이 커질수록 만들 수 있는 스레드 수는 적어짐
* Heap 
  * 가상 메모리(free RAM or virtual memory)의 크기 내에서는 자유롭게 사이즈를 줄 수 있음
  * 페이지 단위를 넘어가면 바로 매핑이 안될 가능성이 있음
  * 오류가 발생하면 다시 페이징 후 다시 가져오는 과정이 반복

## 참조
* [<i class="fas fa-link"></i> 16. 컴퓨터 구조에 대한 네 번째 이야기](https://popcorntree.tistory.com/68){:target="_blank"}  
* [<i class="fas fa-link"></i> 스택의 사이즈는 왜 이렇게 작나요?](https://insalat.tistory.com/10){:target="_blank"}  
* [<i class="fas fa-link"></i> Understanding Swift Performance](https://developer.apple.com/videos/play/wwdc2016/416/){:target="_blank"}  
