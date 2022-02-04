---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "UICollectionViewDiffableDatasource"
toc: true
toc_sticky: true
toc_label: 목차
tag: "UICollectionView"
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
![Image](https://koenig-media.raywenderlich.com/uploads/2020/02/phone-animation.gif)

* TableView(또는 CollectionView)를 그리기 위한 데이터를 관리하고 UI를 업데이트 하는 역할
* Data Source와 달리 데이터가 달라진 부분을 추적하여 자연스럽게 UI를 업데이트
* UI Data를 관리하고, 변경된 데이터만 UI를 자연스럽게 업데이트 해주는 객체
* Hash 값을 이용하여 변화된 부분을 인지
* Diffable Data Source를 이용하면 코드량이 줄어든다.
* UI Transition 
* 데이터 자동 동기화로 에러를 방지

## 특징
* 소개
    * WWDC19 Diffable Datasource
* iOS 13부터 사용가능
* 종류
    * UITableViewDiffableDataSource
    * UICollectionViewDiffableDataSource


![Image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https://blog.kakaocdn.net/dn/DtgEe/btq1Wi0huao/rlCewFvENr4tA4coJYunok/img.png)  
![Image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https://blog.kakaocdn.net/dn/A8IQV/btq1TNtbl6F/uc3BoDoGNyT2rxbbeUksOk/img.png)


## UICollectionViewDiffableDataSource
![Image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https://blog.kakaocdn.net/dn/n77qE/btq1ZMMVQX0/YiHkIwRwIjQQrT3GvKTKNK/img.png)

### SectionIdentifierType
```swift
enum Section: CaseIterable {    
    case main 
}

UICollectionViewDiffableDataSource<Section, String>
```
### ItenIdentifierType
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
> 자연스럽게 UI를 업데이트 한다.  

* tableView.reloadData() 
  * 해당 에러는 데이터의 변경 상황을 수동으로 관리하고 동기화 해야함
* 사용자 경험(UX) 
  * reloadData()의 경우 TableView를 모두 랜더링
  * Diffable Data Source를 사용하는 경우 변경된 데이터만 랜더링

## 성능
* 속도 개선
  * O(N) (N: the number of item)
  * 모든 아이템의 hash 값을 비교해 보아야 하므로 선형 탐색 시간과 동일
* BackgroundQueue
  * DataSource의 apply작업이 오래걸린다면, background queue에서 수행 가능
  * BackgroundQueue에서 이뤄지더라도 안전성 보장
  * Framework는 diffable을 계산이 완료되면 MainQueue 에서 결과 적용

## 출처
[<i class="fas fa-link"></i> ZeddiOS](https://zeddios.tistory.com/1197){:target="_blank"}  
[<i class="fas fa-link"></i> ellyheetov.devlog](https://velog.io/@ellyheetov/UI-Diffable-Data-Source){:target="_blank"}  
[<i class="fas fa-link"></i> Demian의 기술블로그](https://demian-develop.tistory.com/22){:target="_blank"}  
[<i class="fas fa-link"></i> { import Foundation }](https://velog.io/@haanwave/iOS-Swift-UICollectionViewCompositionalLayout-in-iOS-13){:target="_blank"}  
[<i class="fas fa-link"></i> NamS의 iOS일기](https://nsios.tistory.com/150){:target="_blank"}  


