---
sidebar:
  title: "IT"
  nav: sidebar-it
  icon: "fas fa-mobile-alt"
title: "[Bose] Sound Bar 900 업데이트 오류 해결(Feat. Asus라우터)"
toc: false
toc_sticky: true
toc_label: 목차
classes: wide
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

## 결론
* 인터넷 라우터 설정을 변경해 업데이트를 해결해 보자.
  * 방화벽 OFF
  * Bose에서 권고하는 라우터 설정을 해보자.
    * [<i class="fas fa-link"></i> Recommended router settings for use with Bose Wi-Fi products](https://www.bose.com/en_us/support/articles/HC1380/productCodes/soundtouch_120/article.html){:target="_blank"}
  * Asus Router를 사용한다면 멀린펌보단 순정펌을 사용 해 보자.
    * 필자는 멀린펌에서도 업데이트가 정상 동작한 적이 있으나 다시 오류가 발생했고 현재 순정펌을 사용 중이다.

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
업데이트 오류로 사운드바가 작동하지 않아 보스 공식 AS센터에 2번 사운드바를 보냈다.
황당하게도 AS센터에 도착해서 전원을 켜니 5분~20분 후 정상 작동되었다. AS엔지니어분과 자세히 통화했고 AS센터의 Wifi망, 사운드바 제어 여부를 자세히 문의했으나, 별 다른 점은 없었다.  


## 필자의 경우 ASUS RT-AC68U Router를 사용하고 있다.
Bose 사운드바를 사용하는데 인터넷 라우터 장비를 언급하는 이유는 왜 AS센터에는 바로 업데이트가 되었고, 집에서는 안될까 고민하다 Wifi Router 설정이 다른 점을 추측하고 Router 설정을 변경해 보기로 했다.

[<i class="fas fa-link"></i> Cannot connect to Wi-Fi network](https://www.bose.com/en_us/support/articles/HC947/productCodes/soundlink_air/article.html){:target="_blank"}

[<i class="fas fa-link"></i> Connecting to a Wi-Fi network](https://www.bose.com/en_us/support/articles/HC2569/productCodes/bose_home_speaker_500/article.html){:target="_blank"}

[<i class="fas fa-link"></i> Using Recovery mode](https://www.bose.com/en_us/support/articles/HC2620/productCodes/bose_home_speaker_500/article.html){:target="_blank"}




