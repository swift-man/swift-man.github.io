---
sidebar:
  title: "Swift"
  nav: sidebar-swift
title: "async await"
toc: true
toc_sticky: true
toc_label: 목차
excerpt : Javascript, kotlin, google-promises 등 그 동안 다른 언어에서 제공되던 기능이 Swift 5.5 에 강력하게 들어왔다.
---
[Swift](/swift/) / [5.5](/swift/5.5/) / **{{ page.title }}**
{: .notice--warning}

## 1. 개요
- Javascript, kotlin, google-promises 등 그 동안 다른 언어에서 제공되던 기능이 Swift 5.5 에 강력하게 들어왔다.
- 비동기 프로그래밍은 그동안 delegate 패턴이나, closur 를 통해 해왔다면 앞으로는 async, await 를 통한 동기 프로그래밍을 작성하는 것 처럼 비동기 프로그래밍을 할 수 있게 되었다.
>컴파일 타임에 concurrency 에 대한 문제 파악이 가능하다고 한다.

## 2. async
- 비동기 함수 정의
```swift
func listPhotos(inGallery name: String) async -> [String] {
    let result = // ... some asynchronous networking code ...
    return result
}
```
## 3. await
- 비동기 함수의 실행을 동기시키는 명령
- 스레드에서 해당 비동기 함수의 실행이 끝날 때까지 대기(yielding the thread)
```swift
let photoNames = await listPhotos(inGallery: "Summer Vacation")
let sortedNames = photoNames.sorted()
let name = sortedNames[0]
let photo = await downloadPhoto(named: name)
show(photo)
```

- listPhotos(inGallery: "Summer Vacation") 가 완료 될때까지 대기했다가 다시 실행된다.

## 4. 비동기 시퀀스
```swift
let handle = FileHandle.standardInput
for try await line in handle.bytes.lines {
    print(line)
}
```
- 시퀀스도 가능하다.
- "for- await- in" 루프를 실험해봐야 할 것 같다.
- 추후 작성 

## 5. 병렬 비동기 함수 호출
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

## 4. Task
- 비동기 작업의 단위
- 생성 시 우선순위를 줄 수 있다.
```swift
let newPhoto = // ... some photo data ...
let handle = Task {
    return await add(newPhoto, toGalleryNamed: "Spring Adventures")
}
let result = await handle.value
```
[Task](https://developer.apple.com/documentation/swift/task)

## 5. Task Groups
```swift
await withTaskGroup(of: Data.self) { taskGroup in
    let photoNames = await listPhotos(inGallery: "Summer Vacation")
    for name in photoNames {
        taskGroup.async { await downloadPhoto(named: name) }
    }
}
```
- Task Groups 을 통한 병렬 실행
[TaskGroup](https://developer.apple.com/documentation/swift/taskgroup)

## Task Cancellation
```swift
Task.checkCancellation() throw == CancellationError// 취소 확인
Task.isCancelled // 취소 확인
Task.cancel() // 취소
```

## 5. 코드 작성
- 일단 한번 작성해 보자! 작성해보고 돌려보고 싶었다.
- 가장 쉽고 적당한(?) 이미지 다운로드를 해보자.
    - ![Image](https://images.unsplash.com/photo-1629491011862-af5720ac882a?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=200&q=80)

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

### 6. 디버깅
```swift
DispatchQueue.main.async {

}
```
- 기존 방식대로라면 위의 코드를 넣어 메인스레드에서 image 를 추가해 주어야 한다.
- 그런데 작성한 코드가 메인쓰레드로 변경해주는 코드가 없다.
- Task 의 코드의 current thread 의 영향으로 보인다. 직접 확인 해보자.

![Image](https://drive.google.com/uc?export=view&id=1tVBRDMNw3YHusrD1QlntS7y1KN8lIkye)
![Image](https://drive.google.com/uc?export=view&id=1NEyDQqvyXoUtIW2JXgZDJ0ASmqMom7y9)
![Image](https://drive.google.com/uc?export=view&id=1J6IZofxyIMha6kTbWCLK4JQJT8m0hk1a)
- 쓰레드 변경
![Image](https://drive.google.com/uc?export=view&id=1sqB8U8QiQ2QCj_8kumDPs6-N6bCJpMF0)
![Image](https://drive.google.com/uc?export=view&id=1eldTeQ98NqtoHCpImZEWgymm2bxZnhfJ)

![Image](https://drive.google.com/uc?export=view&id=1GZ3ikiGb-kUjvLlOMa6b59Yd3CUq3R7t)
- 하지만 다시 메인쓰레드에서 set 해주는걸 알 수 있다.
- 디버깅이 어려운 Rx 에 비해 너무 간편하고 쉽다라는 생각이 들었다.

참고: [Swift.org - Concurrency](https://docs.swift.org/swift-book/LanguageGuide/Concurrency.html)
