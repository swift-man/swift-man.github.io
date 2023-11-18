---
sidebar:
  title: "Swift"
  nav: sidebar-swift
  icon: "fab fa-swift"
title: "[Swift] async await로 Google 서버 시간 가져오기"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Swift"
depth:
  - title: "Swift"
    url: /swift/
    icon: "fab fa-swift"
  - title: "5.5"
    url: /swift/5.5/
    icon: "far fa-folder-open"
---
오늘은 Swift로 작성된 `GoogleServerTimeService` 클래스를 작성했다. 이 코드는 Google 서버의 현재 시간을 가져오는 기능을 간단하게 구현했다.

### 커스텀 에러 처리
코드에서 정의된 `GoogleServerTimeServiceError` 열거형을 통해, 다양한 에러 상황에 대응하는 방법을 제공한다. 이러한 방식은 오류 발생 시 명확한 정보를 제공하며, 에러 관리를 더욱 체계적으로 할 수 있게 한다.

### 날짜 포맷터의 재사용
`DateFormatter`를 `static` 프로퍼티로 선언함으로써, 메모리 효율성과 성능을 개선한다. 이렇게 재사용 가능한 컴포넌트를 만들어두면, 앱의 전반적인 성능에 긍정적인 영향을 준다.


```swift
import Foundation

enum GoogleServerTimeServiceError: Error {
  case invalidURL
  case invalidResponse
  case networkError(Error)
}

final class GoogleServerTimeService {
  private static let dateFormatter: DateFormatter = {
    let formatter = DateFormatter()
    formatter.dateFormat = "EEE, dd MMM yyyy HH:mm:ss z"
    formatter.locale = Locale(identifier: "en-US")
    return formatter
  }()
  
  func serverTime() async throws -> Date {
    guard let url = URL(string: "https://www.google.com") else {
      throw GoogleServerTimeServiceError.invalidURL
    }
    
    do {
      let (_, response) = try await URLSession.shared.data(from: url)
      guard let httpURLResponse = response as? HTTPURLResponse,
            let dateString = httpURLResponse.allHeaderFields["Date"] as? String,
            let serverTime = GoogleServerTimeService.dateFormatter.date(from: dateString) else {
        throw GoogleServerTimeServiceError.invalidResponse
      }
      return serverTime
    } catch {
      throw GoogleServerTimeServiceError.networkError(error)
    }
  }
}
```



테스트 및 예외 상황 고려에 대한 필요성이 있다. 이 코드가 실제로 어떻게 동작하는지 테스트하는 것이 중요하다. 
예외 상황에 대한 처리도 충분히 고려되었는지 확인해야 한다.
