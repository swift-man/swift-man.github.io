---
sidebar:
  title: "IT"
  nav: sidebar-it
  icon: "fas fa-mobile-alt"
title: "[Bose] Sound Bar 900 업데이트 오류 해결(feat. Asus라우터)"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Bose"
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: https://assets.bose.com/content/dam/Bose_DAM/Web/consumer_electronics/global/products/speakers/bose_smart_soundbar_900/images/CTP-26403_Angus_PDP_Gallery_2_16_9.jpg/jcr:content/renditions/cq5dam.web.1920.1920.jpeg
  caption: "Photo credit: [**bose**](https://bose.com/)"
excerpt: "보스 사운드바 900 무한 update error"
---
이 글은 Bose Sound Bar 900의 스피커 성능을 다루지 않습니다.  
Bose 소프트웨어의 좋은 점과 아쉬운 점을 다루어 보고, 2022년 초부터 2022년 하반기까지의 업데이트 오류로 인한 해결 삽질기를 다룹니다.  

{% include ga-display-horizontal.js %}

## 결론
* 인터넷 라우터 설정을 변경해 업데이트를 해결
  * 방화벽 설정에서 OFF 하고 업데이트를 재시도
  * Bose에서 권고하는 라우터 설정
    * [<i class="fas fa-link"></i> Recommended router settings for use with Bose Wi-Fi products](https://www.bose.com/en_us/support/articles/HC1380/productCodes/soundtouch_120/article.html){:target="_blank"}
  * Asus Router를 사용한다면 멀린펌보단 순정펌을 사용
    * 멀린펌에서 업데이트 완료된 적이 있으나 다시 오류가 발생했고 현재 순정펌으로 변경해 이를 해결한 적이 있으며 현재 순정펌을 사용 중이다.

## Bose Sound Software 좋은 점
![Image](https://is4-ssl.mzstatic.com/image/thumb/Purple122/v4/c4/ad/be/c4adbe9e-294e-ca27-1a71-9d9f30c82239/ProdRelease-0-1x_U007emarketing-0-7-0-0-85-220.png/460x0w.webp)

* [<i class="fas fa-link"></i> Bose Music](https://www.bose.com/en_us/apps/bose_music.html){:target="_blank"} 하나의 App에서 각 하드웨어 컨트롤이 가능하다.
  * 헤드폰은 블루투스 기반 연결이며, 한번 연결한 하드웨어가 앱에 저장되어 최대 2개까지 연결이 가능해 매우 편하다.
  * 사운드바는 같은 Wifi에 있으면 앱에 연결이 가능하도록 설정할 수 있어 가족 누구나 컨트롤이 가능해진다.
* 애플 기기를 사용한다면, AirPlay2를 지원함으로 손쉽게 음악 재생이 가능하다.
* 사운드바의 경우 다른 하드웨어를 홈 모듈에 추가하기가 매우 쉽다. 특히 홈 사운드는 스테레오/모노, 영화관과 같은 사운드 구성을 선 연결 없이 앱 하나로 추가가 가능하고 Wifi 레이턴시도 적어 장비만 있으면 계속 추가할 수 있다.

## Bose Sound Software 아쉬운 점
* 자동 업데이트 기반이며, 유저가 업데이트를 선택할 수 없다. 즉 강제 업데이트다.
* 현재 업데이트 진행 상태에 대해 하드웨어든 소프트웨어든 표시해 주지 않는다.
  * 최소한의 프로그래스바만 있어도 좋으련만..
* 업데이트가 완료가 되지 않는 벽돌현상을 해결할 때까지 사운드바를 사용할 수 없다.
  
## 보스의 업데이트 오류는 많은 사람들이 겪고 있는 문제이다.
* [<i class="fas fa-link"></i> 보스 900 펌웨어 업데이트 단념 합니다](https://dprime.kr/g2/bbs/board.php?bo_table=soundbar&wr_id=41238){:target="_blank"}
* [<i class="fas fa-link"></i> Bose 900 Soundbar Firmware Loop](https://www.reddit.com/r/bose/comments/y4mqi9/bose_900_soundbar_firmware_loop/){:target="_blank"}

## 사운드바의 간단한 상태는 LED로 확인 가능하다.
[<i class="fas fa-link"></i> Understanding LED indicator status lights and information](https://www.bose.com/en_us/support/articles/HC2472/productCodes/bose_soundbar_500_system_pkg/article.html){:target="_blank"}

### Updating system
![GIF](https://bose-ce-as.custhelp.com/fas/resources/bose_ce/hierarchal/$TENANTID$/$TENANTID$_LIBRARY/TENANT/HELP_CONTENT/home_speaker_500_light_bar_slide_left_to_right_white_452x12.gif)  
* 이 상태는 필자의 경험으론 15분~20분 정도 걸린다. 
  * 공식 AS센터에서는 이 상태에서 절대 사운드바를 종료해서는 안된다고 한다.
    * 만약 1시간 이상 이 상태가 유지된다면, 업데이트가 안되고 있는 것이다.
    * 지속적으로 이 상태라면 재부팅해보는 것을 권장한다. 
      * 일주일을 기다려도 이 상태라서 어쩔 수 없다.
  
* 업데이트가 잘 되면 슬라이드 LED는 꺼지고 정상 업데이트 완료 된 것이다. 



## 공식 AS센터 입고 후기
### 공식 AS센터에서는 수동 USB업데이트를 안내해주고, 이게 안되면 입고를 안내해준다.
  
```  
수동 업데이트 방법
USB 케이블로 수동 업데이트
1. 인터넷 주소창에  밑의 주소를 치고 다운로드를 진행해 주세요
https://worldwide.bose.com/support/SB900FW
2.product_update.zip 파일을 데스크탑에 저장하십시오 (파일 이름을 바꾸지 마십시오)
3. PC 의 USB 포트와 제품의 Service 단자에 Micro-USB 를 연결 합니다 
4.웹 브라우저 주소창에 (가급적 Chrome 또는 Safari)를 사용하여 http://203.0.113.1:17008/update.html 로 이동합니다.
5. 업데이트 화면에서 다운받은  파일을 선택 합니다.
업로드를 클릭하고 업데이트가 진행 됩니다. 설치가 완료 되면 시스템이 재부팅 됩니다.
소요 시간은 20~30분 가량 소요 될수 있습니다. 설치가 완료 되면 시스템이 재부팅 됩니다.
```
> 위의 Updating system 상태라면 서비스모드로 진입하지 못하기 때문에 수동 업데이트는 작동하지 않는다.

### 입고
보스 공식 AS센터에 2번 사운드바를 보냈다.
황당하게도 AS센터에 도착해서 전원을 켜니 5분~20분 후 정상 작동되었다. AS엔지니어분과 자세히 통화했고 AS센터의 Wifi망, 사운드바 제어 여부를 자세히 문의했으나, 별 다른 점은 없었다.  

> 웬만하면 입고를 추천하지 않으며 필자와 비슷한 상태라면 인터넷 Router의 설정을 변경해서 문제를 해결하길 바란다.<br/>1회는 처리가 될지 몰라도 Bose는 1~2달 간격으로 업데이트를 하기 때문에 다시 업데이트가 안될 수 있다.<br/>하드웨어는 택배 처리 과정에서의 충격이 있을 수 있으며, 센터에서도 자동업데이트가 안되면 메인보드를 뜯어야 하는데 AS엔지니어분은 메인보드 뜯는 것 자체가 제품이 좋지 않다고 말해주었다.

{% include ga-display-quadrangle.js %}

## 필자의 경우 ASUS RT-AC68U Router를 사용하고 있다.
Bose 사운드바를 사용하는데 인터넷 라우터 장비를 언급하는 이유는 왜 AS센터에는 바로 업데이트가 되었고, 집에서는 안될까 고민하다 Wifi Router 설정이 다른 점을 추측하고 Router 설정을 변경해 보기로 했다.

[<i class="fas fa-link"></i> Cannot connect to Wi-Fi network](https://www.bose.com/en_us/support/articles/HC947/productCodes/soundlink_air/article.html){:target="_blank"}

[<i class="fas fa-link"></i> Connecting to a Wi-Fi network](https://www.bose.com/en_us/support/articles/HC2569/productCodes/bose_home_speaker_500/article.html){:target="_blank"}

[<i class="fas fa-link"></i> Using Recovery mode](https://www.bose.com/en_us/support/articles/HC2620/productCodes/bose_home_speaker_500/article.html){:target="_blank"}

## Wifi Update
http://192.168.1.53:17008/update.html


[<i class="fas fa-link"></i> Product stopped working after updating it](https://www.boselatam.com/en_ar/support/articles/HC1075/productCodes/bose_smart_soundbar_900/article.html){:target="_blank"}

[<i class="fas fa-link"></i> Resetting your product](https://www.bose.com/en_us/support/articles/HC2563/productCodes/bose_smart_soundbar_900/article.html){:target="_blank"}

[<i class="fas fa-link"></i> Software or firmware update will not install](https://www.bose.com/en_us/support/articles/HC2555/productCodes/bose_smart_soundbar_900/article.html){:target="_blank"}

[<i class="fas fa-link"></i> Updating the software or firmware of your product](https://www.bose.com/en_us/support/articles/HC2474/productCodes/bose_smart_soundbar_900/article.html){:target="_blank"}
