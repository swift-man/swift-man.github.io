---
sidebar:
  title: "Architecture"
  nav: sidebar-architecture
  icon: "fas fa-sitemap"
title: "[XCUITest] View and share test results"
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
  - title: "Test your app"
    url: /architecture/tdd/test-your-app/
    icon: "far fa-folder-open"
  - title: "Manage tests"
    url: /architecture/tdd/test-your-app/manage-tests/
    icon: "far fa-folder-open"
---
`result bundle`을 팀 구성원과 공유할 수 있으며, 팀 구성원은 관련 프로젝트 없이도 독립 실행형 [<i class="fas fa-link"></i> Report navigator](https://help.apple.com/xcode/mac/current/#/dev7bb5cf385){:target="_blank"}에서 결과를 열 수 있습니다.  

먼저 [<i class="fas fa-link"></i> UI test or unit test](https://help.apple.com/xcode/mac/current/#/dev42b289fbc?sub=devae9a50aac){:target="_blank"}를 실행한 다음 `Test navigator`에서 [<i class="fas fa-link"></i> view the test reports](https://help.apple.com/xcode/mac/current/#/devba2c7e1bc?sub=devae9a50aac){:target="_blank"}를 확인합니다. 테스트를 Control-클릭하고 팝업 메뉴에서 보고서로 Jump to Report를 선택하여 보고서를 엽니다.  

그런 다음 [<i class="fas fa-link"></i> Finder에 result bundle을 표시](https://help.apple.com/xcode/mac/current/#/devc38fc7392?sub=dev4b5be04e0){:target="_blank"}하고 파일을 팀원과 공유합니다. 팀원은 [<i class="fas fa-link"></i> 프로젝트 없이 result bundle을 열 수 있습니다.](https://help.apple.com/xcode/mac/current/#/devc38fc7392?sub=devae9a50aac){:target="_blank"} command-line tools를 사용하여 [<i class="fas fa-link"></i> view the object in a result bundle](https://help.apple.com/xcode/mac/current/#/devc38fc7392?sub=dev0fe9c3ea3){:target="_blank"} 볼 수도 있습니다.

## Finder에 result bundle 조회

1. Report navigator(버튼 클릭)에서, Control-Click a test or a test action (for example, Build or Log).
![Image](https://help.apple.com/xcode/mac/current/en.lproj/Art/rb_show_in_finder.png)  

2. 팝업 메뉴에서 Show in Finder를 선택합니다.
result bundle(파일 확장명이 .xcresult인 파일)이 Finder에서 하이라이트되어 표시됩니다.  

또는 `-resultBundlePath` flag를 `xcodebuild` command에 전달하여 result bundle을 지정된 위치에 저장할 수 있습니다. 예를 들어 테스트를 빌드하는 동안 result bundle을 저장합니다:
```
xcodebuild test -scheme [App Name] -project [Project file path] -resultBundlePath [Result bundle path]
```
더 많은 옵션을 보려면 터미널에 `man xcodebuild`를 입력하세요.

## command-line에서 result bundle 저장
`-resultBundlePath` flag를 `xcodebuild` command에 전달하여 result bundle을 지정된 위치에 저장할 수 있습니다.

* 터미널에서 빌드 작업을 수행하는 동안 result bundle을 저장합니다:  
```
xcodebuild [action] -scheme [App Name] -project [Project file path] -resultBundlePath [Result bundle path]
```
Pass analyze, build, build-for-testing, test 또는 빌드 없이 test action을 수행합니다.

더 많은 옵션을 보려면 터미널에 `man xcodebuild`를 입력하세요.

## 프로젝트에서 원하는 result bundle 열기
* result bundle(파일 확장명이 .xcresult인 파일)을 Double-click 합니다.
result bundle은 Report navigator에 나타납니다.
![Image](https://help.apple.com/xcode/mac/current/en.lproj/Art/rb_open_result_bundle.png)  

## workspace에서 result bundle 열기
[<i class="fas fa-link"></i> open a result bundle without the project](https://help.apple.com/xcode/mac/current/#/devc38fc7392?sub=devae9a50aac){:target="_blank"}를 열었지만 Mac에 프로젝트 폴더가 있으면 workspace에서 열 수 있습니다.
* Report navigator에서 result bundle 또는 test in the result bundle을 Control-Click한 다음 팝업 메뉴에서 choose Open in Workspace를 선택합니다(또는 Editor > Open in Workspace).  
Report navigator에서 result bundle과 함께 프로젝트가 열립니다.

## result bundle의 Object 조회
터미널에서 `xcrun xcresulttool` command를 사용하여 result bundle의 내용을 가져올 수 있습니다.

* Object에 대한 사람이 읽을 수 있는 설명을 얻으려면 다음을 입력하십시오:
```
xcrun xcresulttool formatDescription
```
JSON 또는 Markdown 표현을 가져오려면 `--format json` 또는 `--format Markdown` 을 추가합니다.

* `ActionInvocationRecord`라는root bundle object를 export하려면 다음을 입력하십시오:
```
xcrun xcresulttool get --path [Path to .xcresult file] --format json
```
* object by reference를 가져오려면 다음을 입력하십시오:
```
xcrun xcresulttool get --path [Path to .xcresult file] --id [Object ID]
```
만약 reference가 attachment payload인 경우 `--format raw`를 전달하여 raw bytes를 가져옵니다. 만약 reference가 다른 structured object에 대한 것이라면 `--format json`을 전달하여 JSON 표현을 가져옵니다.

더 많은 옵션을 보려면 터미널에 `xcrun xcresulttool --help` 또는 `man xcresulttool`을 입력하십시오.

 

## 참고
[<i class="fas fa-link"></i> Building from the Command Line with Xcode FAQ](https://developer.apple.com/library/archive/technotes/tn2339/_index.html){:target="_blank"}  
[<i class="fas fa-link"></i> View and share test results](https://help.apple.com/xcode/mac/current/#/devc38fc7392?sub=devae9a50aac){:target="_blank"}
