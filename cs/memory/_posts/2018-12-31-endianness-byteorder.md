---
sidebar:
  title: "CS"
  nav: sidebar-cs
  icon: "fas fa-microchip"
title: Endianness Or Byte order
toc: true
toc_sticky: true
toc_label: 목차
tag: "CS Memory"
depth: 
  - title: "CS"
    url: /cs/
    icon: "fas fa-microchip"
  - title: "Memory"
    url: /cs/memory/
    icon: "far fa-folder-open"
---
엔디언(Endianness)은 컴퓨터의 메모리와 같은 1차원의 공간에 여러 개의 연속된 대상을 배열하는 방법을 뜻하며, 바이트를 배열하는 방법을 특히 바이트 순서(Byte order)라 한다.


## 엔디언(Endianness)
### 빅 엔디언(Big-endian)
최상위 비트를 먼저 배열

### 리틀 엔디언(Little-endian)
최하위 비트를 먼저 배열
>Intel CPU, Apple M1은 CFByteOrderLittleEndian 방식을 사용한다.

```swift
CFByteOrderGetCurrent() // 바이트오더 확인
```

    
## CoreFoundation CFByteOrder 
여기 있는 함수를 통해 바이트오더를 변환할 수 있다.
```swift

/*    CFByteOrder.h
    Copyright (c) 1995-2019, Apple Inc. and the Swift project authors
 
    Portions Copyright (c) 2014-2019, Apple Inc. and the Swift project authors
    Licensed under Apache License v2.0 with Runtime Library Exception
    See http://swift.org/LICENSE.txt for license information
    See http://swift.org/CONTRIBUTORS.txt for the list of Swift project authors
*/

public struct __CFByteOrder : Equatable, RawRepresentable {

    public init(_ rawValue: UInt32)

    public init(rawValue: UInt32)

    public var rawValue: UInt32
}
public var CFByteOrderUnknown: __CFByteOrder { get }
public var CFByteOrderLittleEndian: __CFByteOrder { get }
public var CFByteOrderBigEndian: __CFByteOrder { get }
public typealias CFByteOrder = CFIndex

public func CFByteOrderGetCurrent() -> CFByteOrder

public func CFSwapInt16(_ arg: UInt16) -> UInt16

public func CFSwapInt32(_ arg: UInt32) -> UInt32

public func CFSwapInt64(_ arg: UInt64) -> UInt64

public func CFSwapInt16BigToHost(_ arg: UInt16) -> UInt16

public func CFSwapInt32BigToHost(_ arg: UInt32) -> UInt32

public func CFSwapInt64BigToHost(_ arg: UInt64) -> UInt64

public func CFSwapInt16HostToBig(_ arg: UInt16) -> UInt16

public func CFSwapInt32HostToBig(_ arg: UInt32) -> UInt32

public func CFSwapInt64HostToBig(_ arg: UInt64) -> UInt64

public func CFSwapInt16LittleToHost(_ arg: UInt16) -> UInt16

public func CFSwapInt32LittleToHost(_ arg: UInt32) -> UInt32

public func CFSwapInt64LittleToHost(_ arg: UInt64) -> UInt64

public func CFSwapInt16HostToLittle(_ arg: UInt16) -> UInt16

public func CFSwapInt32HostToLittle(_ arg: UInt32) -> UInt32

public func CFSwapInt64HostToLittle(_ arg: UInt64) -> UInt64

public struct CFSwappedFloat32 {

    public var v: UInt32

    public init()

    public init(v: UInt32)
}
public struct CFSwappedFloat64 {

    public var v: UInt64

    public init()

    public init(v: UInt64)
}

public func CFConvertFloat32HostToSwapped(_ arg: Float32) -> CFSwappedFloat32

public func CFConvertFloat32SwappedToHost(_ arg: CFSwappedFloat32) -> Float32

public func CFConvertFloat64HostToSwapped(_ arg: Float64) -> CFSwappedFloat64

public func CFConvertFloat64SwappedToHost(_ arg: CFSwappedFloat64) -> Float64

public func CFConvertFloatHostToSwapped(_ arg: Float) -> CFSwappedFloat32

public func CFConvertFloatSwappedToHost(_ arg: CFSwappedFloat32) -> Float

public func CFConvertDoubleHostToSwapped(_ arg: Double) -> CFSwappedFloat64

public func CFConvertDoubleSwappedToHost(_ arg: CFSwappedFloat64) -> Double

```

[<i class="fas fa-link"></i> 위키백과 - 엔디언](https://ko.wikipedia.org/wiki/%EC%97%94%EB%94%94%EC%96%B8){:target="_blank"} 
