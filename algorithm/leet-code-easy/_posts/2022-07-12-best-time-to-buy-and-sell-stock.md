---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] Best Time to Buy and Sell Stock"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Leet Code Easy"
depth:
  - title: "Algorithm"
    url: /algorithm/
    icon: "fas fa-calculator"
  - title: "Leet Code Easy"
    url: /algorithm/leet-code-easy/
    icon: "far fa-folder-open"
use_math: true
---
You are given an array `prices` where `prices[i]` is the price of a given stock on the <b>i$^{th}$</b> day.  

You want to maximize your profit by choosing a <b>single day</b> to buy one stock and choosing a <b>different day in the future</b> to sell that stock.  

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return `0`.


## Example 1:
```swift
Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
```

## Example 2:
```swift
Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transactions are done and the max profit = 0.
```

{% include b-link.html title="풀러가기" url="https://leetcode.com/problems/best-time-to-buy-and-sell-stock/" %}

## 문제 이해


## 코드
```swift
func maxProfit(_ prices: [Int]) -> Int {
  var currentMax = 0 
  var posMax = 0
  for i in 1 ..< prices.count {
      currentMax += prices[i] - prices[i - 1]
      currentMax = max(0, currentMax)
      posMax = max(currentMax, posMax)
  }
  return posMax
}
```

## 풀이
-

## 다른 분의 멋진 코드
```swift
func maxProfit(_ prices: [Int]) -> Int {
  var buyPrice = prices.first!
  var right = 0
  var profit = 0
  while right < prices.count {
      let price = prices[right]
      profit = max(profit, price - buyPrice)
      
      if price < buyPrice {
          buyPrice = price
      }
      
      right += 1
  }

  return profit
}
```

## 잘 배웠습니다.
- [<i class="fas fa-link"></i> Kadane's Algorithm to Maximum Sum Subarray Problem](https://www.youtube.com/watch?v=86CQq3pKSUw&ab_channel=CSDojo){:target="_blank"}

