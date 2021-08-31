---
sidebar:
  title: "CS"
  nav: sidebar-cs
title: "Register"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : 
---
[CS](/cs/) / [CPU](/cs/cpu/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
중앙처리장치(CPU) 내에 위치한 기억장치로 많은 수의 레지스터를 CPU내에 포함시키는 것은 어렵기 때문에 특수 목적용 레지스터들과 몇몇 일반 목적용 레지스터만 존재한다.


## 2. 종류
- PC (Program Counter)
    * 다음 인출(Fetch) 될 명령어의 주소를 가지고 있는 레지스터

 

- AC (Accumulator)
    * 연산 결과 데이터를 일시적으로 저장하는 레지스터

 

- IR (Instruction Register)
    * 가장 최근에 인출된 명령어(현재 실행 중인 명령어)가 저장되어 있는 레지스터

 

- SR (Status Register)
    * 현재 CPU 의 상태를 가지고 있는 레지스터

 

- MAR (Memory Address Register) 
    * PC 에 저장된 명령어 주소가 사용되기 전에 일시적으로 저장되는 주소 레지스터

 

- MBR (Memory Buffer Register) 
    * 기억장치에 저장될 데이터 혹은 읽혀진 데이터가 일시적으로 저장되는 버퍼 레지스터
