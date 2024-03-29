---
sidebar:
  title: "Swift"
  nav: sidebar-swift
  icon: "fab fa-swift"
title: "[Swift 5.5] async await"
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
Javascript, kotlin, google-promises 등 그 동안 다른 언어에서 제공되던 기능이 Swift 5.5 에 강력하게 들어왔다.  
비동기 프로그래밍은 그동안 delegate 패턴이나, closur 를 통해 해왔다면 앞으로는 async, await 를 통한 동기 프로그래밍을 작성하는 것 처럼 비동기 프로그래밍을 할 수 있게 되었다.
>컴파일 타임에 concurrency 에 대한 문제 파악이 가능하다고 한다.

[<i class="fas fa-link"></i> WWDC 21 - Meet AsyncSequence](https://developer.apple.com/videos/play/wwdc2021/10058/){:target="_blank"}  
[<i class="fas fa-link"></i> WWDC 21 - Explore structed concurrency in Swift](https://developer-rno.apple.com/videos/play/wwdc2021/10134){:target="_blank"}

## async
비동기 함수 정의
```swift
func listPhotos(inGallery name: String) async -> [String] {
    let result = // ... some asynchronous networking code ...
    return result
}
```

## await
비동기 함수의 실행을 동기시키는 명령  
스레드에서 해당 비동기 함수의 실행이 끝날 때까지 대기(yielding the thread)
```swift
let photoNames = await listPhotos(inGallery: "Summer Vacation")
let sortedNames = photoNames.sorted()
let name = sortedNames[0]
let photo = await downloadPhoto(named: name)
show(photo)
```

- listPhotos(inGallery: "Summer Vacation") 가 완료 될때까지 대기했다가 다시 실행된다.

## 비동기 시퀀스
```swift
let handle = FileHandle.standardInput
for try await line in handle.bytes.lines {
    print(line)
}
```
- 시퀀스도 가능하다.
- "for- await- in" 루프를 통해 접근한다.
- AsyncSequence 프로토콜도 지원하는데, API 의 progress 처럼 지속적인 값을 가져올 시 필요한 듯 하다.(확실 치 않음)

## 병렬 비동기 함수 호출
```swift
let firstPhoto = await downloadPhoto(named: photoNames[0])
let secondPhoto = await downloadPhoto(named: photoNames[1])
let thirdPhoto = await downloadPhoto(named: photoNames[2])

let photos = [firstPhoto, secondPhoto, thirdPhoto]
show(photos)
```
- 순차 실행 - Rx 의 concat 이라고 이해 했다.

```swift
async let firstPhoto = downloadPhoto(named: photoNames[0])
async let secondPhoto = downloadPhoto(named: photoNames[1])
async let thirdPhoto = downloadPhoto(named: photoNames[2])

let photos = await [firstPhoto, secondPhoto, thirdPhoto]
show(photos)
```
- 병렬 실행(**async-let**)

## Task
비동기 작업의 단위, 생성 시 우선순위를 줄 수 있다.
```swift
let newPhoto = // ... some photo data ...
let handle = Task {
    return await add(newPhoto, toGalleryNamed: "Spring Adventures")
}
let result = await handle.value
```
[<i class="fas fa-link"></i> Task](https://developer.apple.com/documentation/swift/task){:target="_blank"}

### Task Groups
```swift
await withTaskGroup(of: Data.self) { taskGroup in
    let photoNames = await listPhotos(inGallery: "Summer Vacation")
    for name in photoNames {
        taskGroup.async { await downloadPhoto(named: name) }
    }
}
```
[<i class="fas fa-link"></i> TaskGroup](https://developer.apple.com/documentation/swift/taskgroup){:target="_blank"}을 통한 병렬 실행  

### Task Cancellation
```swift
Task.checkCancellation() throw == CancellationError// 취소 확인
Task.isCancelled // 취소 확인
Task.cancel() // 취소
```

## 코드 작성
한번 작성해 보자! 가장 쉽고 적당한(?) 이미지 다운로드를 해보자.  
![Image](https://images.unsplash.com/photo-1629491011862-af5720ac882a?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=200&q=80)

```swift
class ViewController: UIViewController {
    @IBOutlet weak var imageView: CustomImageView!
    let viewModel = ImageViewModel()

    // ViewController 에서는 UIImageView 를 가지고 viewDidLoad 가 되면 이미지 다운로드 시작을 하고 싶었다.
    override func viewDidLoad() {
        super.viewDidLoad()

        Task {
            do {
                let image = try await viewModel.fetchImage(with: "https://images.unsplash.com/photo-1629491011862-af5720ac882a?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=634&q=80")

                imageView.image = image
            } catch {

            }
        }
    }
}
```

```swift
//  이미지 다운로드 시 에러를 정의해 주었다.
enum ImageDownloadError: Error {
    case invalidURLString
    case invalidImage
    case invalidResponse
}
```

```swift
class ImageViewModel {
    // 실제 이미지 다운로드 처리를 하는 곳이다.
    func fetchImage(with urlString: String) async throws -> UIImage {
        guard let url = URL(string: urlString) else {
            throw ImageDownloadError.invalidURLString
        }

        // 1. await 사용
        let (data, response) = try await URLSession.shared.data(from: url, delegate: nil)

        guard let response = response as? HTTPURLResponse, response.statusCode == 200 else {
            throw ImageDownloadError.invalidResponse
        }

        // 2. await 사용
        // 여기에 왜 await 가 들어가는지 잘 모르겠다. 안넣으면 에러가 나서 일단 넣었다. 추후 알아봐야 겠다.
        guard let image = await UIImage(data: data, scale: UIScreen.main.scale) else {
            throw ImageDownloadError.invalidImage
        }

        // 기존 코드와 다른 점은 return image 로 데이터를 내보낸다.
        return image
    }
}
```
![Image](https://drive.google.com/uc?export=view&id=1M1ZAn1jVSghPojGshGD4DMLBXBjI1zux)
- 실행 화면이다. 잘된다!

### 디버깅
```swift
DispatchQueue.main.async {

}
```
기존 방식대로라면 위의 코드를 넣어 메인스레드에서 image 를 추가해 주어야 한다. 그런데 작성한 코드가 메인쓰레드로 변경해주는 코드가 없다.

![Image](https://drive.google.com/uc?export=view&id=1tVBRDMNw3YHusrD1QlntS7y1KN8lIkye)
![Image](https://drive.google.com/uc?export=view&id=1NEyDQqvyXoUtIW2JXgZDJ0ASmqMom7y9)
![Image](https://drive.google.com/uc?export=view&id=1J6IZofxyIMha6kTbWCLK4JQJT8m0hk1a)
쓰레드 변경
![Image](https://drive.google.com/uc?export=view&id=1sqB8U8QiQ2QCj_8kumDPs6-N6bCJpMF0)
![Image](https://drive.google.com/uc?export=view&id=1eldTeQ98NqtoHCpImZEWgymm2bxZnhfJ)

![Image](https://drive.google.com/uc?export=view&id=1GZ3ikiGb-kUjvLlOMa6b59Yd3CUq3R7t)
`imageView.image = image` 가 메인스레드에서 동작한는 것은 `viewDidLoad()` 에서 다운로드 완료를 await 하고 완료 되었을대 실행 해준다.
디버깅이 어려운 Rx 에 비해 코드가 간결하고 쉽다라는 생각이 들었다.

## 참고
[<i class="fas fa-link"></i> Swift.org - Concurrency](https://docs.swift.org/swift-book/LanguageGuide/Concurrency.html){:target="_blank"}
