---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
title: "삽입 정렬"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : performace:O(n^2), space compexity:O(1)*
---
[Algorithm](/algorithm/) / [Sort](/algorithm/sort/) / **삽입 정렬**
{: .notice--warning}

## 1. 개요
- Insertion Sort
- 정렬할때 알맞은 자리를 찾아 삽입을 하기 때문에 삽입 정렬이다.
- [선택 정렬](/algorithm/sort/selection-sort/)과 달리 삽입 정렬은 최선의 경우, 즉 리스트가 이미 정렬 돼 있을때, O(n) 입니다. 
- 정렬된 리스트에 삽입할때에는 매우 효율적입니다. 
- 그러나 평균의 및 최악의 경우에는 O(n^2) 이기 때문에 무작위로 정렬된 많은 데이터를 처리하기에는 좋은 알고리즘이 아닙니다.

 

>performace : O(n^2)<br />
space compexity : O(1)

## 2. 기본 
![](https://w.namu.la/s/e2cca975b1e03bd676ae5e11433526429e9cf77953039ca19a2df4b1112eb75c9c45701ca4f75bcb78194f07ec7b60f28040a4bae7ceed58729887ff62fc13f65bf99eb2564fd0c098557c2af4b7efdbc5f300b3b4c98ef163b96366c9dee952)
1. 삽입 정렬은 두 번째 인덱스부터 시작합니다. 현재 인덱스는 별도의 변수에 저장해주고, 비교 인덱스를 현재 인덱스 -1로 잡습니다.
2. 별도로 저장해 둔 삽입을 위한 변수와, 비교 인덱스의 배열 값을 비교합니다.
3. 삽입 변수의 값이 더 작으면 현재 인덱스로 비교 인덱스의 값을 저장합니다.
4. 비교 인덱스를 -1하여 비교를 반복합니다.
5. 만약 삽입 변수가 더 크면, 비교 인덱스+1에 삽입 변수를 저장합니다.



## 3. Code 
```swift
for i in 1 ..< arr.count {
    let value = arr[i]

    var j = i - 1

    while j >= 0 && value < arr[j] {
        arr.swapAt(j, j + 1)
        j -= 1
    }

    arr[j + 1] = value
}
```

[바로가기](https://github.com/swift-man/swift/blob/master/Sort/InsertionSort.playground/Contents.swift)




{% include utteranc.html %}
