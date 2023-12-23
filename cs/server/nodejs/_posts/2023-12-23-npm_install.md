---
sidebar:
  title: "CS"
  nav: sidebar-cs
  icon: "fas fa-microchip"
title: "NPM 터미널에서 설치 및 실행"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Server"
depth:
  - title: "CS"
    url: /cs/
    icon: "fas fa-microchip"
  - title: "Server"
    url: /cs/server/
    icon: "far fa-folder-open"
  - title: "Node.js"
    url: /cs/server/nodejs/
    icon: "far fa-folder-open"
---
터미널에서 `npm` (Node Package Manager)을 실행하려면 먼저 Node.js가 설치되어 있어야 합니다. `npm`은 Node.js와 함께 제공되므로, Node.js를 설치하면 자동으로 npm도 설치됩니다. 다음 단계를 따라 `npm`을 실행할 수 있습니다.

{% include ga-display-horizontal.js %}

## Node.js 설치 확인
이미 설치되어 있는지 확인하려면 터미널을 열고 `node -v` 및 `npm -v` 명령어를 입력하여 Node.js와 npm의 버전을 확인합니다. 버전 번호가 표시되면 이미 설치된 것입니다.

## Node.js 설치
Node.js가 설치되어 있지 않다면 [<i class="fas fa-link"></i> Node.js 공식 웹사이트](https://nodejs.org/){:target="_blank"}에서 다운로드하여 설치할 수 있습니다. LTS 버전을 권장합니다.

## 터미널에서 npm 실행
설치가 완료되면, 터미널을 열고 `npm` 명령어를 사용할 수 있습니다. 예를 들어, 새로운 패키지를 설치하려면 `npm install [패키지명]`을, 전역으로 설치하려면 `npm install -g [패키지명]`을 사용합니다.

## npm 명령어 사용
기본적인 npm 명령어는 다음과 같습니다
```
npm init #새로운 Node.js 프로젝트를 시작합니다.
npm install #package.json에 명시된 모든 의존성을 설치합니다.
npm update #설치된 패키지를 최신 버전으로 업데이트합니다.
npm run [스크립트]: package.json의 scripts 섹션에 정의된 스크립트를 실행합니다.
```
이러한 단계를 따라 `npm`을 사용하여 Node.js 프로젝트를 관리하고 다양한 패키지를 설치하고 관리할 수 있습니다.
