---
sidebar:
  title: "CS"
  nav: sidebar-cs
  icon: "fas fa-microchip"
title: "[MariaDB] Auto Increment 사용하기"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Database"
depth:
  - title: "CS"
    url: /cs/
    icon: "fas fa-microchip"
  - title: "Database"
    url: /cs/database/
    icon: "far fa-folder-open"
---
TABLE 의 PK에 Auto Increment 속성을 명령어로 주는 방법을 공부했다. 

## 사용하기
```
CREATE TABLE universities(
  id INTEGER  NOT NULL AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(19) NOT NULL
)DEFAULT CHARSET=utf8;
```
id는 자동 증가되므로 INSERT 명령어는 name만 입력하면 된다.

## 초기화
```
ALTER TABLE universities AUTO_INCREMENT = 1;
```
> value 에 대한 valid 체크를 하기 때문의 주의해야 한다.

## 초기화 후 정렬
```
ALTER TABLE universities AUTO_INCREMENT=1;
SET @COUNT = 0;
UPDATE universities SET id = @COUNT:=@COUNT+1;
```
