---
sidebar:
  title: "CS"
  nav: sidebar-cs
  icon: "fas fa-microchip"
title: "메모리의 저장 단위"
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
메모리의 저장 단위는 다양하게 세분화 되어 있다.


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

[<i class="fas fa-link"></i> 위키백과 - 비트 (단위)](https://ko.wikipedia.org/wiki/%EB%B9%84%ED%8A%B8_(%EB%8B%A8%EC%9C%84)){:target="_blank"}

## Byte
256개의 경우의 수를 표현할 수 있다.

|   양수   | 음수     |
|---    |---    |
|  0 ~ 255     | -128 ~ 127     |

[<i class="fas fa-link"></i> 위키백과 - 바이트](https://ko.wikipedia.org/wiki/%EB%B0%94%EC%9D%B4%ED%8A%B8){:target="_blank"}

## Most Significant Bit(MSB)
가장 왼쪽에 있는 <u>최상위 비트</u>

[<i class="fas fa-link"></i> 위키백과 - 최상위 비트](https://ko.wikipedia.org/wiki/%EC%B5%9C%EC%83%81%EC%9C%84_%EB%B9%84%ED%8A%B8){:target="_blank"}

## Least Significant Bit(LSB)
가장 오른쪽에 있는 <u>최하위 비트</u>

[<i class="fas fa-link"></i> 위키백과 - 최하위 비트](https://ko.wikipedia.org/wiki/%EC%B5%9C%ED%95%98%EC%9C%84_%EB%B9%84%ED%8A%B8){:target="_blank"}

## 음수의 표현
최상위 비트의 값이 0이면 양수로, 1이면 음수로 인식한다. 이러한 역할을 하는 비트를 <u>부호비트</u>라 한다.

### 2의 보수
양수의 비트의 값을 XOR 하여 연산한 다음 1을 더해서 음수를 표현하는 방식이다.

[<i class="fas fa-link"></i> 위키백과 - 2의 보수](https://ko.wikipedia.org/wiki/2%EC%9D%98_%EB%B3%B4%EC%88%98){:target="_blank"}
