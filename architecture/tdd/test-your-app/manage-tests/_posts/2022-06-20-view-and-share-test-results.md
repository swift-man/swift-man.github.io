---
sidebar:
  title: "Architecture"
  nav: sidebar-architecture
  icon: "fas fa-sitemap"
title: "[XCUITest] View and share test results"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Tuist"
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

또는 `-resultBundlePath` flag를 `xcodebuild` command에 전달하여 result bundle을 지정된 위치에 저장할 수 있습니다. 예를 들어 테스트를 빌드하는 동안 결과 번들을 저장합니다:
```
xcodebuild test -scheme [App Name] -project [Project file path] -resultBundlePath [Result bundle path]
```
더 많은 옵션을 보려면 터미널에 `man xcodebuild`를 입력하세요.

## command-line에서 result bundle 저장
`-resultBundlePath` flag를 `xcodebuild` command에 전달하여 result bundle을 지정된 위치에 저장할 수 있습니다.

* 터미널에서 빌드 작업을 수행하는 동안 결과 번들을 저장합니다:  
```
xcodebuild [action] -scheme [App Name] -project [Project file path] -resultBundlePath [Result bundle path]
```
Pass analyze, build, build-for-testing, test 또는 빌드 없이 test action을 수행합니다.

더 많은 옵션을 보려면 터미널에 `man xcodebuild`를 입력하세요.

## 프로젝트 없이 result bundle 열기
* Double-click the result bundle (a file with a .xcresult file extension).
The result bundle appears in a standalone Report navigator.
![Image](https://help.apple.com/xcode/mac/current/en.lproj/Art/rb_open_result_bundle.png)  

## workspace에서 result bundle 열기
If you [<i class="fas fa-link"></i> open a result bundle without the project](https://help.apple.com/xcode/mac/current/#/devc38fc7392?sub=devae9a50aac){:target="_blank"} open but you have the project folder on your Mac, you can open it in the workspace.

* In the standalone Report navigator, Control-Click the result bundle or a test in the result bundle, then choose Open in Workspace from the pop-up menu (or choose Editor > Open in Workspace).  
The project opens with the result bundle in the Report navigator.

## result bundle의 Object 조회
You can get the contents of a result bundle by using the xcrun xcresulttool command in Terminal.

* To get a human readable description of the objects, enter:
```
xcresulttool formatDescription
```
To get a JSON or Markdown representation, pass --format json or --format markdown.

* To export the root bundle object called ActionInvocationRecord, enter:
```
xcrun xcresulttool get --path [Path to .xcresult file] --format json
```
* To get an object by reference, enter:
```
xcrun xcresulttool get --path [Path to .xcresult file] --id [Object ID]
```
If the reference is an attachment payload, pass --format raw to get the raw bytes. If the reference is to another structured object, pass --format json to get a JSON representation.  

For more options, enter xcrun xcresulttool --help or man xcresulttool in Terminal.

