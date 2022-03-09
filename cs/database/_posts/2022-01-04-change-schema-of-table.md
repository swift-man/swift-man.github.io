---
sidebar:
  title: "CS"
  nav: sidebar-cs
  icon: "fas fa-microchip"
title: "[MariaDB] Table Schema 변경하기"
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
스키마를 설계 후 기존 테이블을 다른 스키마로 옮기고 싶었다.   
방법은 TABLE을 renamed 하는 형태로 `ALTER TABLE` 명령어를 사용하여 스키마를 변경하면 된다.

```
ALTER TABLE old.table_name RENAME new.table_name;
```
