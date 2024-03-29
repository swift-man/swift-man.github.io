---
sidebar:
  title: "Architecture"
  nav: sidebar-architecture
  icon: "fas fa-sitemap"
title: "소프트웨어 아키텍처 정의"
icon: "fab fa-youtube"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Clean Architecture"
depth:
  - title: "Architecture"
    url: /architecture/
    icon: "fas fa-sitemap"
  - title: "Clean Architecture"
    url: /architecture/clean-architecture/
    icon: "far fa-folder-open"
---
"아키텍트"라는 단어는 제가 늘 어색하고도 이상하게 느끼는 단어입니다.

<iframe width="640" height="360" src="https://www.youtube-nocookie.com/embed/4E1BHTvhB7Y" frameborder="0" allowfullscreen></iframe>

개인적으로 소프트웨어 아키텍처라는 단어를 썩 좋아하지는 않는데요.
왜냐하면 이 단어는 어떤 조직의 시니어급 사람을 연상하게 되는데
이 사람은 소프트웨어가 어떻게 만들어져야 하는지 규칙과 표준을 정하지만, 실제로 10년~20년간 직접 코딩을 하지 않은 사람이기 때문입니다.

그리고 Joel Splisky 가 "아키텍처 우주비행사"라는 용어로 부르는 이 아키텍트라는 사람은
소프트웨어 프로젝트에서 자주 많은 문제를 유발합니다.

아케텍트와 아키텍처라는 단어의 차이가 이런 어감을 가지고 있다는 것은 우리가 소프트웨어 산업에서
뭔가 바꿀 필요가 있다는 뜻이기도 합니다.
왜냐면 **우리가 쓰는 코드들이 중요하기 때문입니다.**

이번 컨버런스가 열릴 때 오프닝에서 여러분들은 소프트웨어 코드들이 박힌 영상을 보셨을 거에요.
그만큼 **오픈소스 커뮤니티에서 코드란 매우 중요한 것으로 여겨지고 있기 때문입니다.**

하지만 만약 여러분이 전문적인 사람이 되고 싶다면 여러분은 프로그래밍이 편안하고 개발하는데 익숙한 사람이 되어야 합니다.

물론 아키텍처가 프로그래밍을 넘어서는 것이라는 개념은 꾀 오랫동안 지속하여 왔습니다.

그리고 만약 여러분이 아키텍트라면 여러분은 더는 프로그래밍을 해서는 안 된다는 이미지가 있습니다.
이 부분이 바로 제가 항상 뭔가 잘못되었다고 생각했던 부분입니다.

하지만 늘 아키텍처란 무엇인가 소프트웨어 분야에서 이 단어가 무엇을 의미하는가 하는 의문만 제기되어 왔습니다.

## What?

왜냐하면 이 단어는 건물, 건설 분야에서 왔지만, 소프트웨어 분야에서 아키텍처의 의미는 완전히 다르기 때문입니다.
오늘은 이 의문에 대해서는 다루지 않을 것입니다.

만약 여러분들이 아키텍처의 공식적인 정의가 무엇인지 알고 싶다면 아마 이게 가장 답에 근접한 정의일 것입니다.

>구성요소들간의 관계, 환경, 설계와 발전을 관리하는 원칙으로 이루어진 시스템의 근본적인 구조.<br/>- IEEE 소프트웨어 정의

아키텍처에 대해서는 저런 정의가 그동안 존재해왔습니다.

## Ralph Johnson
하지만 개인적으로 아키텍처가 무엇인지 무슨의미를 담고 있는지 생각했을 때 저는 사실 이분과 동일한 생각을 했습니다.

![Image](https://live.staticflickr.com/2331/1499817187_4d208050f1.jpg)

이분을 모르시는 분이 얼마나 있는지는 모르겠지만 이분은 디자인패턴 책을 집필한 것으로 잘 알려져 있는
[<i class="fas fa-link"></i> Gof(Gang of Four)의 Ralph Johnson](https://en.wikipedia.org/wiki/Ralph_Johnson_(computer_scientist)){:target="_blank"}  입니다.

그는 다른 사람들에게도 그렇듯이 제 경력에서 많은 영향을 끼쳤는데요.

그는 리펙터링의 개념을 공식화 하였고 리펙터링 도구에 대한 개념을 처음으로 알렸습니다.
그래서 저는 Ralph 로 부터 많은 영감을 얻을 수 있었습니다.

저는 그와 이메일을 주고 받았었는데요.
소프트웨어 아키텍처에 대한 정의에 대해 논의했습니다.

저는 이메일을 써서 주고 받은 내용이 매우 인상깊었기 때문에 이메일 본문을 통째로 가져다 칼럼에 포함시켰습니다.

[<i class="fas fa-link"></i> Who Needs an Architect?](http://martinfowler.com/ieeeSoftware/whoNeedsArchitect.pdf){:target="_blank"}


Ralph 는 IEEE 의 정의를 보고
>이 정의의 문제점은 너무 포괄적인 컴포넌트 개념으로 정의했다는 점입니다.

아키텍처에 대해 이야기할 때 거시적으로 이야기했다는 뜻입니다.

이게 무슨 소리냐고 물으실텐데요. 어떤 컴포넌트를 고르는 게 답일까요? 어떤 연관 관계를 가져가는 게 중요할까요?

사실 엄청난 수의 컴포넌트와 연관 관계가 생길 수 있습니다.
어떤 것을 선택하고 어떤 것을 배제하는 게 아키텍처에서 정말로 중요한 개념일까요?

Ralph의 생각은

>소프트웨어 프로젝트를 잘 꾸려나가고 있을 때 중요한 점은 프로젝트 내부 소스 코드에 대해 잘 알고 있는 프로젝트에 참여하는 개발자들이 있을 건데, 그 개발자들은 상식적으로 어떻게 코드들이 실행되는지 알고 있을 것입니다.<br/>이 개발자들의 상식이 아키텍처에 영향을 미칠 거란 점입니다.


## 전문 개발자들은 시스템 디자인에 대한 지식을 공유한다.

이건 중요한 사실인데요. 아키텍처라고 불리는 이 정의에서 사회적 요소나 꾀나 영향이 크기 때문입니다.

정말 중요한 것은 이미 가지고 있는 지식의 깊이이기 때문입니다.

물론 **다이어그램을 이리저리 그리고 문서를 작성하고 아키텍처를 적을 수 있지만 그것들은 단지 표현일 뿐이고 보통 지식을 공유하는 불완전한 표현일 뿐**입니다.

여러분들이 소프트웨어 프로젝트를 진행하고 특히 소프트웨어 프로젝트가 지속해서 커지고 있을 때는 **프로젝트를 주도하고 있는 팀원들 간에 프로젝트에 대한 이해도가 잘 공유될 때** 입니다.

이게 진짜 중요한 사실입니다. 하지만 저 아키텍처에 대한 정의는 아주 일반적인데요. 또 하나더 중요하게 살펴봐야 할 사실이 있습니다.

## 아키텍처 디자인은 먼저 진행되어야 한다.
**아키틱처는 반드시 프로젝트가 시작되기 전에 잘 정의되어야 한다**는 점입니다.

Ralph는 여기에 대해서도 한마디 거들었는데요
>왜냐면 그때로 돌아가고 싶지 때문이지

## 결정은 변경하기 어렵다.
>올바른 결정은 더 빨리 내려지는 것을 원한다.

왜냐면 모든 결정에서는 정보가 없으면 더 일찍 할 수 없거든요. 보통 소프트웨어 프로젝트를 진행할 때 가장 걱정하는 사실 중 하나는 한번 결정하면 변경하기가 매우 어렵다는 점입니다.

>결정은 변경하기 어렵다.

사실 이건 아키텍처를 이야기할 때 꽤 유용합니다.

무엇이 바꾸기 어려울까요?
몇 가지 달라지는 점들이 컴포넌트에서 수정되는데요.
왜냐면 프로그래밍 언어를 변경하는 것은 결정하기 매우 어려운 일입니다.

하지만 이런 이야기들은 보통 거시적으로 이야기할 때 논의되지 않죠.

## 아키텍처에 대한 정의
그래서 우리는 2가지 갈림길을 확인했는데요.
>지식을 공유하고 바꾸기 어렵다는 점

이 어려운 2개가 합쳐질 때(지식을 공유하는 것, 바꾸기 어려운 것) 비로소 아키텍처에 대한 정의를 정할 수 있었습니다.

![Image](https://drive.google.com/uc?export=view&id=1dO3Q6yLIWABUSd67Cm0n_fLjJqvNBNWn)
이 말이 바보같이 들리기 때문이겠죠?

"뭔가 중요한 것"이라니 그게 뭐든 간에 말이죠.

하지만 제 생각엔 이 정의는 매우 심오한 뜻을 지니고 있다고 생각합니다.
당신이 소프트웨어 시스템이나 아키텍처를 설계할 때 무엇이 중요한지 **핵심 가치**에 대해서 생각할 겁니다.

팀장으로서 소프트웨어 프로젝트를 이끌어나갈 때 무엇을 핵심 가치로 둘 것인가 정할 겁니다.
혹은 혼자 프로젝트를 진행할 때도 무엇이 핵심인지 고민합니다.
코드를 짤 때도 무엇이 가장 중요한지 핵심을 생각하면서 소스 코드에 녹입니다.

**아키텍처에서는 이런 핵심 가치를 위한 결정들이 중요한 것**입니다.

그런 결정들은 다른 어떤 문제보다도 중요합니다.
그래서 사람들이 저에게 아키텍처의 정의가 무엇이냐고 물어본다면 Ralph의 견해와 같이 소프트웨어 아키텍처란 "뭔가 중요한 것"이라고 대답할 겁니다.

여기까지 아키텍처가 무엇인지에 대해 이야기를 해 보았습니다.

## 참고
[<i class="fas fa-link"></i> https://martinfowler.com/](https://martinfowler.com/){:target="_blank"}
