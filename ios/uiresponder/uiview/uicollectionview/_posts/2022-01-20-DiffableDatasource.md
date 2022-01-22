---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "DiffableDatasource"
toc: true
toc_sticky: true
toc_label: 목차
tag: "UIView Drawing Cycle"
published : false
depth: 
  - title: "iOS"
    url: /ios/
    icon: "fab fa-app-store-ios"
  - title: "UIResponder"
    url: /ios/uiresponder/
    icon: "far fa-folder-open"
  - title: "UIView"
    url: /ios/uiresponder/uiview/
    icon: "far fa-folder-open"
  - title: "UICollectionView"
    url: /ios/uiresponder/uiview/uicollectionview/
    icon: "far fa-folder-open"
---
# Diffable Datasource, UICollectionViewCompositionalLayout
![image](https://blog.kakaocdn.net/dn/bRnvoK/btqW1seXKlM/iEIO6As8fahW65UQcVnvG1/img.gif)
## Diffable Datasource
https://developer.apple.com/documentation/uikit/views_and_controls/collection_views/implementing_modern_collection_views

* TableView(또는 CollectionView)를 그리기 위한 데이터를 관리하고 UI를 업데이트 하는 역할
* Data Source와 달리 데이터가 달라진 부분을 추적하여 자연스럽게 UI를 업데이트
* UI Data를 관리하고, 변경된 데이터만 UI를 자연스럽게 업데이트 해주는 객체
* Hash 값을 이용하여 변화된 부분을 인지
* Diffable Data Source를 이용하면 코드량이 줄어든다.
* UI Transition이 추가 
* 데이터 자동 동기화로 에러를 방지

## 특징
* 소개
    * WWDC19 Diffable Datasource
* iOS 13부터 사용가능
* 종류
    * UITableViewDiffableDataSource
    * UICollectionViewDiffableDataSource

## 구조
* 간단하여 빠르게 작성이 가능
* 유연한구조
* 보통 Controller가 DataSource를 지원


|  |  |
| --- | --- |
| ![Image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https://blog.kakaocdn.net/dn/DtgEe/btq1Wi0huao/rlCewFvENr4tA4coJYunok/img.png) | ![Image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https://blog.kakaocdn.net/dn/A8IQV/btq1TNtbl6F/uc3BoDoGNyT2rxbbeUksOk/img.png) |


## UICollectionViewDiffableDataSource
![Image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https://blog.kakaocdn.net/dn/n77qE/btq1ZMMVQX0/YiHkIwRwIjQQrT3GvKTKNK/img.png)

### SectionIdentifierType, 
```swift
enum Section: CaseIterable {    
    case main 
}

UICollectionViewDiffableDataSource<Section, String>
```
ItenIdentifierType
```swift
class UITableViewDiffableDataSource<SectionIdentifierType, ItemIdentifierType> : NSObject 
  where SectionIdentifierType : Hashable, ItemIdentifierType : Hashable
```
```swift
struct NSDiffableDataSourceSnapshot<SectionIdentifierType, ItemIdentifierType> 
  where SectionIdentifierType : Hashable, ItemIdentifierType : Hashable
```
* Diffable Data Source는 SectionIdentifierType, ItenIdentifierType 두개의 generic parameter로 결정된다. 
* 이 두 파라미터는 반드시 Hashable

apply시에 각 hash value를 비교하여 추가 or 삭제된 부분을 인지하게 된다.

## CollectionView 적용
```swift
self.dataSource = UICollectionViewDiffableDataSource<Section, String>(collectionView: self.collectionView) { (collectionView, indexPath, dj) -> UICollectionViewCell? in 
    guard let cell = collectionView.dequeueReusableCell(withReuseIdentifier: "cell", for: indexPath) as? DJCollectionViewCell else { preconditionFailure() } 
    cell.configure(text: dj) 
    return cell 
}
```

## snapshot 생성 및 적용
```swift
var snapshot = NSDiffableDataSourceSnapshot<Int, MyModel>()
snapshot.appendSections(storage.sections)

for section in storage.sections {
  snapshot.appendItems(storage.modelsForSection(section), toSection: section)
}

datasource.apply(snapshot)
```

## Hash Value가 같아서 구별 할 수 없는 경우
```swift
struct Mountain: Hashable {
    let name: String
    let height: Int
    let identifier = UUID()
    
    func hash(into hasher: inout Hasher) {
        hasher.combine(identifier)
    }
}
```


## UITableViewDataSource, UICollectionViewDataSource와 차이점
* UITableViewDataSource, UICollectionViewDataSource는 Protocol
    * UIViewController가 주로 제어
    * seciton의 개수 (the number of sections)
    * 각 section의 아이템의 개수 (the number of items)
    * cellForItemAt - cell의 render (content renders)
* UITableViewDiffableDataSource Generic Class
    * UIViewController로 부터 분리 설계 가능
    * 추가적인 코드작업 없이도, 퀄리티 있는 에니메이션 적용 가능
    * 개선된 Data Source 매커니즘은 완벽하게 동기적인 버그나, 예외, 충돌 상황 제거
    * UI 데이터와 비지니스 로직 분리의 일관성
    * Identifier와 Snapshot을 사용해 간소화 된 Data 모델을 정의해, UI 랜더링


## 사용했을때 장점
### Index 관련 오류 미 발생
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https://blog.kakaocdn.net/dn/FPxgo/btq1XVwaKmt/aKQfmw1ikX9CML9pAimjTk/img.png)

### DiffableDataSource를 사용 필요성
"자연스럽게 UI를 업데이트 한다."

*  tableView.reloadData()
    * 해당 에러는 데이터의 변경 상황을 수동으로 관리하고 동기화 해야함

* 사용자 경험(UX)
    *  reloadData()의 경우 TableView를 한번에 업데이트 하므로 뚝 뚝 끊어지는 UI
    *  Diffable Data Source를 사용하는 경우 변경된 데이터 부분만 UI 효과가 적용



|  |  |
| --- | --- |
| ![Image](https://koenig-media.raywenderlich.com/uploads/2020/02/phone-animation.gif) |  |

## 성능
* 속도 개선
    * O(N) (N: the number of item)
    * 모든 아이템의 hash 값을 비교해 보아야 하므로 선형 탐색 시간과 동일
* BackgroundQueue
     * DataSource의 apply작업이 오래걸린다면, background queue에서 수행 가능
     * BackgroundQueue에서 이뤄지더라도 안전성 보장
     * Framework는 diffable을 계산이 완료되면 MainQueue 에서 결과 적용

## 출처
https://www.google.com/search?q=Diffable+Data+Source&rlz=1C5CHFA_enKR963KR963&oq=Diffable+Data+Source&aqs=chrome..69i57j0i512l6j69i61.1028j0j7&sourceid=chrome&ie=UTF-8


https://www.google.com/search?q=UICollectionViewCompositionalLayout&lr=lang_ko&newwindow=1&rlz=1C5CHFA_enKR963KR963&biw=1042&bih=1056&tbs=lr%3Alang_1ko&ei=gl7pYbuqBsqHoATGxIvwAw&ved=0ahUKEwi789LyssD1AhXKA4gKHUbiAj4Q4dUDCA4&uact=5&oq=UICollectionViewCompositionalLayout&gs_lcp=Cgdnd3Mtd2l6EAMyBQgAEIAEMgUIABCABDIFCAAQgAQyBQgAEIAEMgUIABCABDIFCAAQgAQyBQgAEIAEMgUIABCABDIFCAAQgAQyBwgAEIAEEApKBAhBGABKBAhGGABQAFgAYL8CaABwAngAgAF1iAF1kgEDMC4xmAEAoAECoAEBwAEB&sclient=gws-wiz


https://zeddios.tistory.com/1197

https://velog.io/@ellyheetov/UI-Diffable-Data-Source

https://demian-develop.tistory.com/22

https://velog.io/@haanwave/iOS-Swift-UICollectionViewCompositionalLayout-in-iOS-13

https://nsios.tistory.com/150

