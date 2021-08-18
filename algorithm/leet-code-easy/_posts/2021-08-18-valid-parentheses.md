---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
title: "Leet Code / Easy / 20. Valid Parentheses"
toc: true
toc_sticky: true
toc_label: 목차
---
![](https://leetcode.com/static/packages/interview_landing/images/logo.svg)

## 1. 개요
**Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.
An input string is valid if:**
{: .notice--warning}

    1. Open brackets must be closed by the same type of brackets.
    2. Open brackets must be closed in the correct order.
{: .notice--info}

## 2. Example
```
Input: s = "()"
Output: true
```

```
Input: s = "()[]{}"
Output: true
```

```
Input: s = "(]"
Output: false
```

```
Input: s = "([)]"
Output: false
```

```
Input: s = "{[]}"
Output: true
```

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

{% include utteranc.html %}
