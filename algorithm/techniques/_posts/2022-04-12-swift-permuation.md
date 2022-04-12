---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] 순열"
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
Swift 순열은 직접 구현해야 한다. 알고리즘을 풀다 보면 자주 접하게 되는데 구현하려고 하면 매번 기억이 안 나는 마법에 빠져있다.

```swift
func permute(_ nums: [Int]) -> [[Int]] {
  // 중복을 허용하지 않게 만들어야 하므로 아래와 같이 사용여부를 체크해줍니다.
  var result: [[Int]] = [] 
  var visited: [Bool] = [Bool](repeating: false, count: nums.count)
  
  // 만약 현재 순열의 원소 수가 주어진 원소수와 같다면 결과에 추가!
  func permutation(_ nowPermute: [Int]) { 
    if nowPermute.count == nums.count {
      result.append(nowPermute)
      return
    }
    
    // 이미 사용한 값이라면 넘어갑니다.
    for i in 0..<nums.count { 
      if visited[i] { 
        continue 
      } else {
        visited[i] = true
        permutation(nowPermute + [nums[i]])
        visited[i] = false
      }
    }
  }
  
  permutation([])
  return result
}
```

## 출처
[<i class="fas fa-link"></i> PinguiOS](https://icksw.tistory.com/180){:target="_blank"}

