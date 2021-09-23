---
sidebar:
  title: "Swift"
  nav: sidebar-swift
  icon: "fab fa-swift"
title: "Dictionary"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Swift Collections"
depth:
  - title: "Swift"
    url: /swift/
    icon: "fab fa-swift"
  - title: "Collections"
    url: /swift/collections/
    icon: "far fa-folder-open"
---
Value type 이다.  
```
@frozen public struct Dictionary<Key, Value> where Key : Hashable
```

## subscript(_:)
```
O(N)
```



## count
```
O(N)
```



## contains(where:)
```
O(N)
contains(_:) method는 없다. (key로 바로 참조하면 알 수 있기 때문)
```

## index(forKey:)
```
평균 O(1)
bridged NSDictionary으로 Wrap된 경우 O(N)
```

## mapValues(_:)
```
O(N)
```



## compactMapValues(_:)
```
O(M+N)
N은 기존 Dictionary의 크기
M은 결과 Dictionary의 크기
```


## remove(at:), removeValue(forKey:), removeAll(keepingCapacity:)
```
O(N)
```



## popFirst()
```
평균 O(1)
```


## rereversed()
```
O(N)
```
## 출처
[<i class="fas fa-link"></i> github.com/apple/swift/blob/main/stdlib/public/core/Dictionary](https://github.com/apple/swift/blob/main/stdlib/public/core/Dictionary.swift){:target="_blank"}
