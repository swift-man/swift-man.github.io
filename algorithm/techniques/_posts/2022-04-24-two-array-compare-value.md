---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "두개의 배열의 값의 같거나 작은 값을 출력하기"
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
```
target: [4, 5, 6, 2]
a: [1, 5, 2, 4, 7]
output : [3, 4, 3, 2]
```

타겟이 되는 배열을 sort 후 1부터 비교할 값을 hash 값에 차례로 넣어 새로운 배열을 만들고 hash와 대상을 비교한다. 

```
let arr = a.sorted()
print(arr) // [1, 2, 5]
var dic: [Int: Int]
for i in 0 ..< arr.max() {
  dic[i] = max(dic[i - 1, default: 0], arr[safe: i] ?? 0)
}
print(dic)
/*
dic[0] = 1
dic[1] = 2
dic[2] = 5
dic[3] = 
dic[4] = 
dic[5] = 
*/
```
0을 무한히 빼게 되고 무한루프에 빠지게 된다.

## 참고
[<i class="fas fa-link"></i> 나무위키](https://namu.wiki/w/0%EC%9C%BC%EB%A1%9C%20%EB%82%98%EB%88%84%EA%B8%B0#s-3){:target="_blank"}

