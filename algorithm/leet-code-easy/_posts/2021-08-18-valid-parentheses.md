---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
title: "Valid Parentheses"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.
---
[Algorithm](/algorithm/) / [Leet Code Easy](/algorithm/leet-code-easy/) / **20. Valid [Parentheses](/clean-code/dictionary/parentheses/)**
{: .notice--warning}
![](https://leetcode.com/static/packages/interview_landing/images/logo.svg)

## 1. 개요
**[Given](/clean-code/dictionary/given/) a string s containing just the characters '(', ')', '{', '}', '[' and ']', [determine](/clean-code/dictionary/determine/) if the input string is valid.
An input string is valid if:**

    1. Open brackets must be closed by the same type of brackets.
    2. Open brackets must be closed in the correct order.
{: .notice--info}

## 2. Example
```swift
Input: s = "()"
Output: true
```

```swift
Input: s = "()[]{}"
Output: true
```

```swift
Input: s = "(]"
Output: false
```

```swift
Input: s = "([)]"
Output: false
```

```swift
Input: s = "{[]}"
Output: true
```
* [풀러가기](https://leetcode.com/problems/valid-parentheses/)

## 3. 문제 이해


## 4. 코드
```swift
func isValid(_ s: String) -> Bool {
    var stack: [Character] = []

    if s.count == 1 {
        return false
    }
    for c in s {
        if c == "(" {
            stack.append(")")
        } else if c == "[" {
            stack.append("]")
        } else if c == "{" {
            stack.append("}")
        } else {
            if !stack.isEmpty {
                let pop = stack.removeLast()
                if pop != c {
                    return false
                }
            } else {
                return false
            }
        }
    }

    return stack.isEmpty
}
```

## 5. 풀이
-

## 6. 다른 분의 멋진 코드
-

## 7. 잘 배웠습니다.
-

{% include utteranc.html %}
