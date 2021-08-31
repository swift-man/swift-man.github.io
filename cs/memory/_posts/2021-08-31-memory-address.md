---
sidebar:
  title: "CS"
  nav: sidebar-cs
title: "메모리 주소"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : 메모리에 저장된 값은 고유한 주소를 가진다.
---
[CS](/cs/) / [Memory](/cs/memory/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
메모리에 저장된 값은 고유한 주소를 가진다.
1바이트를 저장할 수 있는 공간마다 고유한 메모리 주소가 할당되고, CPU 는 이 주소를 통해 메모리에 저장된 값에 접근한다.

| 메모리 주소     | 메인 메모리     |
|---    |---    |
| 1023     | 1byte     |
| 1022     | 1byte     |
| 1021    | 1byte     |
| 1020     | 1byte     |
| ...     | ...     |
| 2     | 1byte     |
| 1     | 1byte     |
| 0    | 1byte     |

* 예를 들어 1KB 의 크기의 메모리는 최소 저장단위인 1바이트로 구분된 1024개의 공간을 할당할 수 있다.

## 2. CPU 의 접근
CPU 는 메모리 주소를 저장하고 특정 위치에 접근하기 위해 [Register](/cs/cpu/address-register) 를 사용한다.
