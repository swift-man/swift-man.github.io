---
sidebar:
  title: "CS"
  nav: sidebar-cs
title: 메모리 공간 분류
toc: true
toc_sticky: true
toc_label: 목차
excerpt : 프로그램을 실행하면 OS는 실행에 필요한 메모리 공간을 할당한다.
---
[CS](/cs/) / [Memory](/cs/memory/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
프로그램을 실행하면 OS는 실행에 필요한 메모리 공간을 할당한다.<br/>
할당되는 공간은 Stack, Heap, Data, Code 영역으로 구분된다.


## 2. Stack
<u>지역변수, 파라미터, 리턴 값 등이 저장되는 영역</u>이다.  LIFO 방식의 스택으로 메모리 공간을 관리한다.

>함수를 실행하면 함수에서 사용되는 <u>모든 지역 변수와 리턴 값이 스택 영역에 추가</u> 된다.<br/>
이때 관련된 모든 메모리는 <u>스택 프레임(stack frame) 내부에 함께 저장</u> 된다.<br/>
스택프레임은 함수의 실행이 종료되면 스택 영역에서 제거되고 다른 함수에서 메모리 영역을 사용할 수 있게 된다.

## 3. Heap
<u>동적으로 할당된 데이터가 저장</u>되는 영역이다.

데이터 영역과 스택 영역은 컴파일러가 미리 할당할 공간의 크기를 예측할 수 있지만 동적으로 할당되는 특성으로 인해 공간의 크기를 예측할 수 없다.<br/>힙 영역에 저장된 데이터는 <u>직접 해제하지 않을 경우 프로그램이 종료될 때까지 유지</u>된다.
    
## 4. Data
<u>정적 변수와 전역변수</u>가 저장된다. 이 이영역에 저장된 데이터는 <u>프로그램이 종료 될때까지 유지</u>된다. 
    
## 5. Code
코드 영역에는 <u>기계어로 번역된 프로그램 코드가 저장</u>된다.