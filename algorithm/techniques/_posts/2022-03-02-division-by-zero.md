---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "0으로 나누기는 왜 안될까?"
toc: true
toc_sticky: true
toc_label: 목차
tag: "기법"
depth:
  - title: "Algorithm"
    url: /algorithm/
    icon: "fas fa-calculator"
  - title: "기법"
    url: /algorithm/techniques/
    icon: "far fa-folder-open"
---
컴퓨터는 왜 0으로 나누기가 안될까?
```
0 ÷ 10 // NaN(Not a number)
5 ÷ 0 // NaN(Not a number)
```

개발을 하다 보면 1년에 한 번씩은 해당 오류를 경험한다.😭
잊을 만 하면 발생하는 이 오류는 반드시 0이 아닌 숫자로 나눗셈을 해야 한다는 꼼꼼함을 일깨워 준다.  
![Image](https://drive.google.com/uc?export=view&id=1ybXyPVLH8gULqSXrhmB-q_iwqIkUnOFE)  

컴퓨터는 6÷2를 계산하면 6을 0이 될 때까지 2로 여러 번 빼서 뺀 횟수를 나눗셈의 몫으로 가져온다.

```
(아무 수) ÷ 0
```
0을 무한히 빼게 되고 무한루프에 빠지게 된다.

## 참고
[<i class="fas fa-link"></i> 나무위키](https://namu.wiki/w/0%EC%9C%BC%EB%A1%9C%20%EB%82%98%EB%88%84%EA%B8%B0#s-3){:target="_blank"}

