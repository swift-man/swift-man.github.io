---
sidebar:
  title: "Architecture"
  nav: sidebar-architecture
  icon: "fas fa-sitemap"
title: "[XCUITest] resultBundle"
toc: true
toc_sticky: true
toc_label: 목차
tag: "XCUITest"
depth:
  - title: "Architecture"
    url: /architecture/
    icon: "fas fa-sitemap"
  - title: "TDD"
    url: /architecture/tdd/
    icon: "far fa-folder-open"
---
UITest에서 수행한 결과에 대한 Session 데이터를 resultBundle 에 저장
* 번들에는 build log, code coverage가 포함
* reports, XML property list, test result, screenshots, attachments collected, testing 등을 활용 가능

## Report Navigator
Local 환경인 경우 Xcode 에서 가장 쉽게 결과 확인 가능
![Image](https://drive.google.com/uc?export=view&id=1uilWDO76nOl2UnWvVcGEwQ_6xF5DhKQB)  

## Finder
아래 경로에 Finder로 만들어진 .xcresult 확인 가능
![Image](https://drive.google.com/uc?export=view&id=1kVEdbTuyJgiG5cGz4n7yhX2lgvrfOHHb)  

```
Xcode/DerivedData/[App]/Logs/Test/[scheme].xcresult
```

## -resultBundlePath
xcodebuild commend 를 이용해 원하는 위치에 저장 가능
```
xcodebuild test -scheme [App Name] -project [Project file path] -resultBundlePath [Result bundle path]
```

> 주의
> 이미 해당 경로에 같은 resultBundle 이 있다면 오류 발생
> 반드시 지우고 다시 실행 필요

### -resultBundlePath flag
* analyze
* build
* build-for-testing
* test 
...
action 목록과 설명은 'man xcodebuild' 참고

```
xcodebuild [action] -scheme [App Name] -project [Project file path] -resultBundlePath [Result bundle path]
```

## result bundle 열기
![Image](https://drive.google.com/uc?export=view&id=1E1gTGxlaAqFGpnM1lNm2cnCJNv3hTlna)  

## result bundle 조회
기본적으로 resultBundle 은 사람이 읽을 수 있는 형태로 저장되지 않으며 data 형태로 저장
앞서 설명한 Xcode에서 GUI를 통한 조회가 가능하나 터미널을 이용해 조회 가능

[<i class="fas fa-link"></i>  xcparse](https://github.com/ChargePoint/xcparse){:target="_blank"}
 를 이용하여 더 쉽게 데이터를 조회하고, 이미지를 추출 및 정리할 수 있음.
* format 지정
```
xcrun xcresulttool formatDescription
```

* export
```
xcrun xcresulttool get --path [Path to .xcresult file] --format json
```

