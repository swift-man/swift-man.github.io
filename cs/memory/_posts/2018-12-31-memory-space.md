---
sidebar:
  title: "CS"
  nav: sidebar-cs
  icon: "fas fa-microchip"
title: 메모리 공간 분류와 크기 결정 Time
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
프로그램을 실행하면 OS는 실행에 필요한 메모리 공간을 할당한다.  
할당되는 공간은 Stack, Heap, Data, Code 영역으로 구분된다.

![Image](https://drive.google.com/uc?export=view&id=1zmTs6_m0H2m9TCySQvY7qdDVeMm17L9Z)

## Run Time 시 크기가 결정되는 영역
### Stack
프로그램이 자동으로 할당하는 임시메모리이며, <u>지역변수, 파라미터, 리턴 값 등이 저장되는 영역</u>이다.  LIFO 방식의 스택으로 메모리 공간을 관리한다.

>함수를 실행하면 함수에서 사용되는 <u>모든 지역 변수와 리턴 값이 스택 영역에 추가</u> 된다.<br/>
이때 관련된 모든 메모리는 <u>스택 프레임(stack frame) 내부에 함께 저장</u> 된다.<br/>
스택프레임은 함수의 실행이 종료되면 스택 영역에서 제거되고 다른 함수에서 메모리 영역을 사용할 수 있게 된다.

### Heap
프로그래머가 <u>동적으로 할당된 데이터가 저장</u>되는 영역이다.

```
malloc, free, new, delete
```

데이터 영역과 스택 영역은 컴파일러가 미리 할당할 공간의 크기를 예측할 수 있지만 동적으로 할당되는 특성으로 인해 공간을 효율적으로 사용가능하지만, 공간의 크기를 예측할 수 없다.<br/>힙 영역에 저장된 데이터는 <u>직접 해제하지 않을 경우 프로그램이 종료될 때까지 유지</u>된다.

## Compile 시 크기가 결정되는 영역
### Data
<u>정적 변수(static)와 전역변수(global)</u> 중 컴파일 타임에 초기화 된 데이터가 저장된다. 이 이영역에 저장된 데이터는 <u>프로그램이 종료 될때까지 유지</u>된다.

### BSS(Block Stated Symbol)
<u>정적 변수(static)와 전역변수(global)</u> 중 컴파일 타임에 초기화 되지 않은 데이터가 저장된다. 사용이 필요하면 런타임에 초기화 해야한다. 이 이영역에 저장된 데이터는 <u>프로그램이 종료 될때까지 유지</u>된다.

### Code
코드 영역에는 <u>기계어로 번역된 프로그램 코드가 저장</u>된다. 이 부분은 "read only" 영역이라 쓰기 작업이 들어오면 "access violation"이 발생한다.
