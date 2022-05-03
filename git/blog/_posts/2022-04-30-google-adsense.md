---
sidebar:
  title: "Git"
  nav: sidebar-git
  icon: "fab fa-github"
title: "Jekyll 블로그에 Google AdSence 광고 탑재하기"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Blog"
depth:
  - title: "Git"
    url: /git/
    icon: "fab fa-github"
  - title: "Blog"
    url: /git/blog/
    icon: "far fa-folder-open"
---
필자의 블로그는 수익이 전혀 없다.  
![Image](https://drive.google.com/uc?export=view&id=1xeF0tT3n_Pn4VHn-6VVjwxNGepjgV_M2)  
 
블로그에 광고를 추가했다. 이유는 간단하다. Google AdSense를 사용해보고 싶었고, jekyll 블로그를 통한 광고 개재 가능 여부 등을 알고 싶었다. 1개의 게시물에 광고를 시험적으로 추가했다. 역시 클릭수는 0이다.😁
무분별한 광고는 추가하지 않을 예정이며, 필자가 세운 기준은 사용자의 관심사가 증가한 게시물 중 글자수 500, 이미지 4개 이상이 되는 게시물에 추가해볼 예정이다.  
포스팅 제목과는 다르게 수익 창출과는 무관하게도 필자의 수익은 없을 것으로 예상되며 앞으로도 크게 기대하지 않고 있다.😊  

이번에 Google AdSence 추가했던 일을 포스팅한다.  

{% include ga-display-quadrangle.js %}

## Google AdSense 로그인

[<i class="fas fa-link"></i> Google AdSense](https://www.google.com/adsense/){:target="_blank"}에 접속하면 아래와 같은 화면이 나온다. 상단의 로그인이나 시작하기 버튼으로 구글 계정 로그인을 하자.
![Image](https://drive.google.com/uc?export=view&id=1E36Nivj917eOby7wb1qYgOyL5gJ0Aqvm)  

### 로그인 오류 해결
만약 로그인 시도 중 아래와 같은 문제가 발생하면 로그인이 불가한데, 이게 어떤 방법으로든 해결이 되지 않았다.
![Image](https://drive.google.com/uc?export=view&id=14640vqGllL_ZHKsyzoLdklXGVn-yU5yo)  

만약 로그인이 되지 않는 다면, 구글 계정을 여러 개 사용하고 있어서 문제가 되는 거 같다.  
따라 크롬의 `시크릿 모드`를 사용해서 [<i class="fas fa-link"></i> Google AdSense](https://www.google.com/adsense/){:target="_blank"}를 접속하고, 해당 아이디로 로그인 하자.
  
## 로그인 완료  
![Image](https://drive.google.com/uc?export=view&id=1yutaA5HLygTRjygZS0KiJvwb761Z94E7)  
로그인을 완료하면 좌측의 결제 정보와 오른쪽의 사이트 연결이 매우 중요하다. 가운데 선택사항은 건드리지 않았다. 추후 필요성을 느끼면 시도 해보는 것으로...

### 결제 정보
진입하면 나오는 여러 항목 들(카드 번호 등)을 입력하도록 하자.

### 사이트 연결
```javascript
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-2802708598024982"
     crossorigin="anonymous"></script>
```
이런 형태의 코드를 볼 수 있으며, Root 경로에 삽입하라고 나올 것이다. 이 코드는 필자 사이트의 코드라서 반드시 본인의 코드를 head 영역에 추가하자. 필자의 경우 다음 날 연결되었다는 메일을 받을 수 있었다.

## 심사 등록 및 
사이트 연결 후 심사 등록을 버튼을 통해 심사 등록을 하자.  
심사를 등록하면 며칠 후 심사 결과에 대한 이메일이 오게 된다.  
필자는 2022-04-25(월)~2022-04-29(금) 5 영업일이 이후 심사 성공 이메일을 받을 수 있었다.  

![Image](https://drive.google.com/uc?export=view&id=12b7OPY-x79EHVheN_cEnTSZ2oD-6ZGYx)  

## 광고
왼쪽 상단의 더보기 버튼을 누르면 `광고`메뉴가 있다.  
![Image](https://drive.google.com/uc?export=view&id=1V2Hc2SxSFq1ic2ruU9d2363CTsaYgHLl)  
해당 메뉴를 통해 광고를 만들 수 있다. 클릭하자.  

### 자동 광고
![Image](https://drive.google.com/uc?export=view&id=1FIdWgjzkD8Xsg0f9TW9IFg14jYZGQpW9)  
처음에 연결 되면 자동 광고를 추천해주는데, 선택하지 않았다.  
자동으로 되면 편하긴 하겠지만 '수동으로 제어 하는 것이 더 맞겠다.'라고 생각했고, 검색 결과 또한 자동 광고가 좋은 평가는 아니었다.  

### 광고 선택
![Image](https://drive.google.com/uc?export=view&id=1wdj3VVePl5JJ1u3voia7QJ9j3XgvYO_w)  
본인의 블로그에 알맞은 광고를 만들어서 코드를 제공받자. 제공받은 코드를 추가하면 광고가 노출 된다! 매우 쉬움!    
* 광고가 미 노출되는 케이스
  * jekyll의 경우 로컬 IP에서는 광고가 미 노출된다.
  * Ad Block 이 있을 경우
  * 광고 삽입 후 1시간 이내(구글 애드센스에 1시간 정도 걸린다고 써있으니 참고!)

필자는 디스플레이 광고를 주로 만들었으며, 해당 코드를 따로 `google-adsence-display-horizontal.html` 파일로 만들어 재사용 가능하게 관리하도록 했다.
```
// google-adsence-display-horizontal.html
{% include ga-display-horizontal.js %}
```
>현재 포스팅에 있는 광고가 디스플레이-가로형 광고다.  

{% include ga-display-horizontal.js %}  

## ads.txt
![Image](https://drive.google.com/uc?export=view&id=17jOmIvJf0fdgore8GXgp_U4-FCN-_B2A) 
상단에 이런 메시지가 뜨는 것을 볼 수 있는데, 상위 도메인과 서브 도메인 모두 추가했다.  
Git Pages repo의 root 경로에 추가해주면 된다.


