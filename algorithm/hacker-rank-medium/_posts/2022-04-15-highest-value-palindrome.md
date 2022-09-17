---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] (String)Highest Value Palindrome"
toc: true
toc_sticky: true
toc_label: 목차
tag: "HackerRank Medium"
depth:
  - title: "Algorithm"
    url: /algorithm/
    icon: "fas fa-calculator"
  - title: "HackerRank Medium"
    url: /algorithm/hacker-rank-medium/
    icon: "far fa-folder-open"
---
Palindromes are strings that read the same from the left or right, for example madam or 0110.

You will be given a string representation of a number and a maximum number of changes you can make. Alter the string, one digit at a time, to create the string representation of the largest number possible given the limit to the number of changes. The length of the string may not be altered, so you must consider `0`'s left of all higher digits in your tests. For example `0110` is valid, `0011` is not.

Given a string representing the starting number, and a maximum number of changes allowed, create the largest palindromic string of digits possible or the string '-1' if it is not possible to create a palindrome under the contstraints.

## Example
```swift
Input: 
s = '1232'
k = 3
Make 3 replacements to get '9339'.
s = `12321`
k = 1
Make 1 replacements to get '12921'.
```

```swift
Input: 3943, n = 4, l = 1
Output: "3993"

Input: 092282, n = 6, l = 3
Output: "992299"

Input: 0011, n = 4, l = 1
Output: "-1"
```

## Function Description
Complete the highestValuePalindrome function in the editor below.

highestValuePalindrome has the following parameter(s):

* string s: a string representation of an integer
* int n: the length of the integer string
* int k: the maximum number of changes allowed

## Returns
* string: a string representation of the highest value achievable or -1

## Input Format
The first line contains two space-separated integers, `n` and `k`, the number of digits in the number and the maximum number of changes allowed.
The second line contains an `n`-digit string of numbers.

## Constraints
* 0 < n <= 10$^5$
* 0 < k <= 10$^5$
* Each character  in the number is an integer where 0 <= i <= 9.

## 문제 이해
정해진 k 번의 숫자 변경을 해서 가장 큰 Palindrome 을 리턴한다.  
Palindrome이 아니면 "-1"을 리턴한다.

## 코드
```swift
func highestValuePalindrome(s: String, n: Int, k: Int) -> String {
  var checked = [Bool](repeating: false, count: n)
  var s = Array(s)
    
  var k = k
  var l = 0
  var r = n - 1
    
  while l <= r {
    if s[l] != s[r] {
      if s[l] > s[r] {
        s[r] = s[l]
        checked[r] = true
      } else {
        s[l] = s[r]
        checked[l] = true
      }
      k -= 1
    }
  
    l += 1
    r -= 1
  }
    
  guard k >= 0 else { return "-1" }
    
  l = 0
  r = n - 1
  while l <= r {
    if l == r && k >= 1 {
      s[l] = "9"
      break
    }
    if Int(String(s[l]))! < 9 {
      if !checked[l] && !checked[r] && k >= 2 {
        s[l] = "9"
        s[r] = "9"
        k -= 2
      }
      if checked[l] || checked[r] {
        if k >= 1 {
          s[l] = "9"
          s[r] = "9"
          k -= 1
        }
      }
    }
        
    l += 1
    r -= 1
  }
  return String(s)
}
```

## 풀이
-

## 다른 분의 멋진 코드


## 잘 배웠습니다.
-
