---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "[Xcode Build Error] Cocoapods Error"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Xcode Build Error"
depth:
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "Build Error"
    url: /ios/build-error/
    icon: "far fa-folder-open"
---
```
File not found: 
/Applications/Xcode.app/Contents/Developer/Toolchains
/XcodeDefault.xctoolchain/usr/lib/arc/libarclite_iphonesimulator.a
```

## 해결
PodFile

```
post_install do |installer|
  installer.generated_projects.each do |project|
    project.targets.each do |target|
      target.build_configurations.each do |config|
        config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '16.0' # Dev Version
      end
    end
  end
end
```
