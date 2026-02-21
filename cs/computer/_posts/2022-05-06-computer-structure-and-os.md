---
sidebar:
  title: "CS"
  nav: sidebar-cs
  icon: "fas fa-microchip"
title: "컴퓨터 구조"
toc: true
toc_sticky: true
toc_label: 목차
tag: "CS Computer"
depth:
  - title: "CS"
    url: /cs/
    icon: "fas fa-microchip"
  - title: "CPU"
    url: /cs/cpu/
    icon: "far fa-folder-open"
---
프로그래밍 - 어떤 Input 을 올바른 Output 으로 만드는 것
개발자들은 C, Java, C++ 과 같은 언어를 통해
컴파일을 하게 되고 .exe, .dll 등이 만들어 진다.

컴퓨터는 .exe, dll(dynimic linked library) 파일로 변경되게 되고 이게 컴파일이라고 한다.


## 컴퓨터 구조
폰노이만
```
CPU <-IO-> Memory <-IO-> Disk
```

### CPU
* 계산을 처리한다.
* ALU + 레지스터는 연산을 처리한다.
  * 레지스터는 캐시메모리라는 것이 있다.
* 시분할
```
P1(프로세서)
P2
P3
P4 
여러개의 프로세스를 시간으로 나눈 것을 말한다.
```
  * 우선순위나 시간단위의 관리를 CPU 스케쥴링이라 한다.
  * 스케쥴링 방식
    * 선점형 스케쥴링(preemptive) 방식이 오늘 날에도 많이 사용된다.
      * 우선순위가 높은 프로세스부터 더 많은 권한을 준다.
    

### Memory
* 임시 저장 공간
```
cost⬆️ -> cost⬇️
speed⬆️ <- spped⬇️
```

* 실행된 프로그램의 명령어 중에 처리하려는 명령어는 CPU가 처리하게 된다.
* Disk에 있던 프로그램이 실행되면서 메모리에 올라오는 것을 프로세스라 한다.
* 프로세스가 된 프로그램들은 사실상 컴퓨터에 많은 프로그램이 동시에 존재한다.
  * 사실상 동시는 맞지 않다.
    * CPU 프로세서가 하나라고 가정 했을 때, 프로세스에 한번씩의 기회를 준다.
* 메모리는 고비용의 장치다. 
  * 일부는 메모리에 올라오고, 일부는 메모리에 내려가야 한다.
    * 따라 어떤 메모리는 올라와야 하고, 어떤 메모리는 내려가야 하는지 메모리 관리 교체 알고리즘이 필요하다.
    

### Disk
저장소
* .exe 파일을 실행하면 코드와 리소스를 담고 있다.
  * 프로그램을 실행하면 일부 코드와 리소스가 메모리에 저장된다.

### OS 가 하는 일
여러가지 프로그램들이 동시에 최적의 성능을 낼 수 있도록 메모리, CPU를 관리해준다.
