---
sidebar:
  title: "IT"
  nav: sidebar-it
  icon: "fas fa-mobile-alt"
title: "[TradingView] 자동결제 환불 성공기"
toc: true
toc_sticky: true
toc_label: 목차
tag: "TradingView"
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: https://drive.google.com/uc?export=view&id=1JaHrf04wdyhqTVxNsnH470klH0z2-5UL
excerpt: "자동결제 환불 가능할까?"
---
TradingView 에서 차트를 보고, 공유하고, 커뮤니티를 제공하는 서비스가 있다.  
필자는 약 3년간 무료로 사용했고, 작년 블랙프라이데이에 1년 유료 결제를 하여 사용하였다.  

![Image](https://drive.google.com/uc?export=view&id=1gLk_MjELcyeZ_xaoGFWZuJJEDAnlvBz0)

문제의 발단은 올해 자동 결제가 되는지 모르고 있었다.  
아마 결제할 할 당시는 인식하였으나 시간이 되어 잊어버렸다.  
그리고 1년 뒤 그래서 어제, 아래와 같은 문자를 받았다.  

![Image](https://drive.google.com/uc?export=view&id=1DH661-eSogEbZ67kd17HRrG9WC0wfEXp)

해당 서비스는 매우 좋지만 "무료도 아주 좋다"라는 생각에 환불받고 싶었다.  
환불에 대한 내용을 검색결과는 대부분 환불받기 어렵고, TradingView 에서도 환불해주지 않으려고 한다는 글이 많았다.  
그래서 직접 사이트를 조사해 환불조치 받았고, 그 과정을 적었다.

## 자동결제 사전에 방지하기
환불까지 가지 않고 사전에 자동결제를 취소하는 방법이 가장 좋다.  
왜냐하면, 블랙프라이데이에 할인받은 가격으로 구매했더라도, 자동 결제는 그런 거 없다.  
재사용을 고려하더라도 할인가에 다시 구매하는 것이 좋다.  
구매 즉시, 또는 유료 플랜 사용 중 자동 결제를 비활성화 하고 다시 할인 시기가 오면 결제해서 사용하는 방법이 비용 측면에서 훨씬 저렴하다.

### 페이팔 자동결제 취소하여 사전에 방지하기
```
설정 -> 결제 -> 자동결제 관리 -> 활성 표시
```
![Image](https://drive.google.com/uc?export=view&id=1Z01QzIdDHg7Ml6kE6xnZRal_GLPTx0k5)  
해당 결제를 누르고 상태를 취소하면 자동결제는 취소된다.  
![Image](https://drive.google.com/uc?export=view&id=1Gx4EVvLZ72-CKTPWgJXDOXsk5rb0rWGr)  

> 활동 내역으로 자동결제 설정으로 이동이 가능하다.<br/>해당 결제 상세를 확인 후 결제관리를 클릭하면 해당 메뉴로 이동된다.

![Image](https://drive.google.com/uc?export=view&id=1rKcOlX1A1cDbp8DlvK5wKVTrSiT_i_PA)
비활성화탭으로 이동된 것을 확인하자.

### 트레이딩뷰에서 자동결제 취소하기
```
홈 -> 계정 -> 결제 및 빌링
```
빌링 히스토리 섹션에서 취소하도록 하자.  
![Image](https://drive.google.com/uc?export=view&id=12BRsioEskI1vZDKobl_tsPv2i8pDDPfp)  

취소가 완료되면 아래와 같이 리스트가 추가된다.  
![Image](https://drive.google.com/uc?export=view&id=1YLyDiLP2gUhKalKO0pQtcbWvQwCb13sM)

> 필자는 환불과 동시에 자동결제를 취소했다.

## 이미 결제되었다면 환불받기
### 환불 정책 확인하기

정책은 변경될 수 있으니 공식 홈페이지의 내용을 확인하자. 
[<i class="fas fa-link"></i> 자동으로 1해 / 2해 비용이 청구되었습니다. 리펀드 받고 싶습니다](https://kr.tradingview.com/support/solutions/43000471716/){:target="_blank"}

환불을 원한다면 결제일로부터 14일 이내에 환불 신청을 해야한다.  

### 환불 신청하기
페이팔에 있는 정보의 메일로 환불요청을 하면 안 된다.  
![Image](https://drive.google.com/uc?export=view&id=1s_Evcs7MDHBEu-9ghoNJPmtjGuzDuyjq)  
필자가 메일을 보내니 티켓으로 연동되고 있으니 티켓을 작성하라는 답변을 받았다.
![Image](https://drive.google.com/uc?export=view&id=1DQ1WUZ4I7mo-zB3h2qClHWALUjTcT6Xv)
TradingView를 사용했으나 티켓을 몰랐던 필자는 매우 당황하였으나 JIRA와 같은 티켓과 유사하다.

### 마이 서포트 티켓에 티켓 작성하기
```
홈 -> 계정 -> 헬프 센터 -> 마이 서포트 티켓
```

[<i class="fas fa-link"></i> TradingView tickects](https://kr.tradingview.com/support/tickets/){:target="_blank"}으로 이동하면 된다.  

필자의 경우 티켓의 내용을 아래와 같이 생성했다.
```
Hello. please help me!

Request a refund for the transaction.

I would like to get a refund for the $155.40 I paid today.

I don't want service.

tradingView transaction ID: 트레이딩뷰에서 확인하자.
paypal deal id: 페이팔에서 확인하자.


thank you.
```

답변은 약 2시간이 안 돼서 매우 빠르고 친절하게 왔다.
환불해준다는 것이었다!

감사의 인사를 티켓 마지막에 추가했다.  
![Image](https://drive.google.com/uc?export=view&id=1asTx9VV4nlil5LgYllb-dENjft1I6NQ5)  

### 티켓 종료하기
 `이슈 풀렸음. 클로즈 티켓`을 터치하자.  
![Image](https://drive.google.com/uc?export=view&id=1JFBPiep_KWHuT4RTP3DwaMjWUVljQ7lT)  
![Image](https://drive.google.com/uc?export=view&id=18VmvtmBjDnmSJ_Bpl-cDwgvc_jJxGzRz)  

마지막으로 피드백을 하면 마무리된다.
![Image](https://drive.google.com/uc?export=view&id=1bQ527_Gdp_WhudhOrWGaNgV6AMMQoK75)

## 환불 완료
환불은 크게 3가지를 확인하면 된다.  
가장 중요한 것은 카드사에서 취소된 것을 확인하자.
### 카드사
![Image](https://drive.google.com/uc?export=view&id=1wlt0D1alMPm-WTZmmv8VNtussAZBfnf-)  

### 트레이딩뷰로 부터 이메일
![Image](https://drive.google.com/uc?export=view&id=1JaHrf04wdyhqTVxNsnH470klH0z2-5UL)  

### 페이팔
![Image](https://drive.google.com/uc?export=view&id=1KHOZEreCTaG9cpU-aGoarq_G2J2jF6uw)  

필자와 같은 상황이신 분이 계신다면 이 글을 보고 꼭 문제를 해결했으면 좋겠다.
