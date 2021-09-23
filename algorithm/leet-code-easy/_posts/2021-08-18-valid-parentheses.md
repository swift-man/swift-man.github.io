---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] Valid Parentheses"
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
---
Valid {% include link.html title="Parentheses" url="/clean-code/dictionary/parentheses/" %}

{% include link.html title="Given" url="/clean-code/dictionary/given/" %} a string s containing just the characters '(', ')', '{', '}', '[' and ']', {% include link.html title="determine" url="/clean-code/dictionary/determine/" %} if the input string is valid.
An input string is valid if:

    1. Open brackets must be closed by the same type of brackets.
    2. Open brackets must be closed in the correct order.
{: .notice--warning}

## Example
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
{% include b-link.html title="풀러가기" url="https://leetcode.com/problems/valid-parentheses/" %}

## 문제 이해


## 코드
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

## 풀이
-

## 다른 분의 멋진 코드
-

## 잘 배웠습니다.
-
