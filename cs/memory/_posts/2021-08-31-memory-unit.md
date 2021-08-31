---
sidebar:
  title: "CS"
  nav: sidebar-cs
title: "메모리의 저장 단위"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : 메모리의 저장 단위는 Bit 부터 YB 까지 다양하게 세분화 되어 있다.
---
[CS](/cs/) / [Memory](/cs/memory/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
메모리의 저장 단위는 Bit 부터 YB 까지 다양하게 세분화 되어 있다.


| 저장단위     | 크기     |
|---    |---    |
| bit     | 0과 1을 저장할 수 있는 기본 단위     |
| nibble     | 4bit     |
| byte     | 8bit     |
| word     | 2byte(16bit) 또는 4byte(32bit)     |
| KB(kilobyte)     | 1024byte     |
| MB(Megabyte)     | 1024KB     |
| GB(Gigabyte)     | 1024MB     |
| TB(Terabyte)     | 1024GB     |
| PB(petabyte)     | 1024TB     |
| EB(Exabyte)     | 1024PB     |
| ZB(Zettabyte)     | 1024EB     |
| YB(yottabyte)     | 1024ZB     |

## Bit
메모리가 0 또는 1을 저장할 수 있는 가장 작은 공간
- 컴퓨터 공학에서 정보의 기분 단위로 사용되고 있다.

## Byte
256개의 경우의 수를 표현할 수 있다.

|   양수   | 음수     |
|---    |---    |
|  0 ~ 255     | -128 ~ 127     |

## Most Significant Bit(MSB)
가장 완쪽에 있는 "최상위 비트"

## Least Significant Bit(LSB)
가장 오른쪽에 있는 "최하위 비트"

## Sign Bit
최상위 비트의 값이 0이면 양수로, 1이면 음수로 인식한다. 이러한 역할을 하는 비트를 "부호비트"라 한다.

## 2의 보수
초창기 컴퓨터를 음수를 저장하기 위해 부호비트를 1로 바꾸고 나머지 비트는 야수와 동일한 비트를 사용하는 방식을 사용하였다.
하지만 여러 가지 문제점으로 인해 더이상 사용되지 않으며 "2의 보수" 방식을 사용하고 있다.

2의 보수 방식은 양수의 비트의 값을 XOR 하여 연산한 다음 1을 더해서 음수를 표현하는 방식이다.
```
-22를 2의 보수 방식을 사용해서 2진수로 표현
00010110
11101001 // XOR
11101010 // +1
```
