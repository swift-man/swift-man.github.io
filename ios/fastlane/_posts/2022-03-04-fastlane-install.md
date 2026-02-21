---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "Fastlane으로 프로젝트 관리하기"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Fastlane"
depth:
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "Fastlane"
    url: /ios/fastlane/
    icon: "far fa-folder-open"
---
Fastlane 은 iOS개발을 도와주는 좋은 도구이다.    
배포 자동화를 도와주는 툴이며, 많은 iOS개발자들이 사용할 수 있다.
대표적인 장점은 수동으로 배포를 하다 보면 실수를 할 수 있는데, 이를 방지할 수 있는 장점이 있다.   

## 설치
### Fastlane 설치
터미널을 열자.
```
brew install fastlane
```

or Apple silicon

```
gem install fastlane
```
![Image](https://drive.google.com/uc?export=view&id=1y39DEbx2BHRvDCA5WvNMNNLSDwcynSHd)  
>M1 iMac에서 잘된다!

### Bundler 설치
```
gem install bundler
```

## Fastlane 업데이트
```
bundle update
```

## 기본 설정
터미널을 열고 해당 프로젝트 경로로 가자.
```
fastlane init
```

## 설치 오류 모음
### permission denied
```
ERROR:  While executing gem ... (Errno::EACCES)
    Permission denied @ rb_sysopen - /Users/name/.rbenv/versions/3.0.2/lib/ruby/gems/3.0.0/gems/rouge-2.0.7/Gemfile
```
    
```
sudo
```

### GemNotFoundException
```
/Users/name/.rbenv/versions/3.0.2/lib/ruby/3.0.0/rubygems.rb:281:in `find_spec_for_exe': can't find gem fastlane (>= 0.a) with executable fastlane (Gem::GemNotFoundException)
  from /Users/name/.rbenv/versions/3.0.2/lib/ruby/3.0.0/rubygems.rb:300:in `activate_bin_path'
  from /Users/name/.rbenv/versions/3.0.2/bin/fastlane:23:in `<main>'
```

```
gem update --system
```
