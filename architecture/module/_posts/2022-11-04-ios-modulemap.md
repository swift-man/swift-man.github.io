---
sidebar:
  title: "Architecture"
  nav: sidebar-architecture
  icon: "fas fa-sitemap"
title: "[iOS] ModuleMap"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Module"
depth:
  - title: "Architecture"
    url: /architecture/
    icon: "fas fa-sitemap"
  - title: "Module"
    url: /architecture/module/
    icon: "far fa-folder-open"
---
.moduleMap은 Objective-C API 와 Swift API 의 중간 다리 역할을 한다. iOS 개발은 Objective-C, Swift 언어로 개발이 가능하다.   

![Image](https://i.stack.imgur.com/0QJ8P.png)

오래된 프로젝트라면 Objective-C를 충분히 포함할 수 있으며, Swift로의 전환의 과도기라면, 프로젝트는 두가지의 언어로 개발될 수 있다. 이러한 두 언어를 모두 컴파일러가 빌드하려면 개발자는 어떤 것들이 서로 상호작용해야하는지 컴파일러에게 알려주어야 한다. 모듈은 [<i class="fas fa-link"></i> Module Map Language](https://clang.llvm.org/docs/Modules.html#module-map-language){:target="_blank"}를 모두 지원하기 위해 Bridge-Header 를 통해 상호 지원하고 있다.  

![Image](https://i.stack.imgur.com/cEuwx.png)
 
### modulemap Name
> `.modulemap` 의 파일명은 모듈의 네이밍과 같아야 한다.

### Path
```
module_name.framework/Modules/module_name.modulemap
```


`Clang`는 Objective-C와 Swift에서 서로 필요한 .h 파일을 알 수 없다. 따라 .modulemap 에 수동 등록해주어, 독립형 추가 모듈 및 하위 모듈을 만드는데 도움을 줄 수 있다.

## 생성 방법 링크
* [<i class="fas fa-link"></i> Library manually](https://stackoverflow.com/questions/32125338/how-can-i-use-an-a-static-library-in-swift/59215981#59215981){:target="_blank"}
* [<i class="fas fa-link"></i> Framework automatically](https://stackoverflow.com/questions/24272184/connect-objective-c-framework-to-swift-ios-8-app-parse-framework/59216086#59216086){:target="_blank"}
* [<i class="fas fa-link"></i> Custom framework module map](https://stackoverflow.com/questions/30704268/no-umbrella-header-found-for-target-module-map-will-not-be-generated/57665560#57665560){:target="_blank"}
