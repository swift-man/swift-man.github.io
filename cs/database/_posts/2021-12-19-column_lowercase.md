---
sidebar:
  title: "CS"
  nav: sidebar-cs
  icon: "fas fa-microchip"
title: "[Database] 대문자 컬럼(COLUMN_NAME)을 소문자로 만들기"
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
변경하고자 하는 스키마의 모든 테이블의 컬럼을 조회하고 String 을 조합하여 ALTER TABLE 명령어를 만들어 변경한다.  

## ALTER TABLE 명령어 만들기
```
SELECT CONCAT('ALTER TABLE ', TABLE_NAME, ' CHANGE `', COLUMN_NAME, '` `', LOWER(COLUMN_NAME), '` ', COLUMN_TYPE, ';') 
FROM INFORMATION_SCHEMA.COLUMNS 
WHERE TABLE_SCHEMA = 'innodb';
```

## 조회된 명령어를 실행하기
이렇게 조회하면 아래와 같은 결과가 나오게 되고, 아래 결과물을 명령어로 실행하면 변경되게 된다.
```
ALTER TABLE hig_schools CHANGE `id` `id` int(11);
ALTER TABLE hig_schools CHANGE `SCHUL_RDNMA` `schul_rdnma` varchar(42);
ALTER TABLE hig_schools CHANGE `SCHUL_FOND_TYP_CODE` `schul_fond_typ_code` varchar(2);
ALTER TABLE hig_schools CHANGE `FOAS_MEMRD` `foas_memrd` int(11);
ALTER TABLE hig_schools CHANGE `DGHT_SC_CODE` `dght_sc_code` varchar(3);
ALTER TABLE hig_schools CHANGE `FOND_SC_CODE` `fond_sc_code` varchar(2);
...
```
