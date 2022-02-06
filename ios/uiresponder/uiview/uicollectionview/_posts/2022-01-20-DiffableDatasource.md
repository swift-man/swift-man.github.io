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
* TableView(또는 CollectionView)를 그리기 위한 데이터를 관리하고 UI를 업데이트 하는 역할
* Data Source와 달리 데이터가 달라진 부분을 추적하여 자연스럽게 UI를 업데이트
* UI Data를 관리하고, 변경된 데이터만 UI를 자연스럽게 업데이트 해주는 객체
* Hash 값을 이용하여 변화된 부분을 인지
* Diffable Data Source를 이용하면 코드량이 줄어든다.
* UI Transition 
* 데이터 자동 동기화로 에러를 방지

![Image](https://koenig-media.raywenderlich.com/uploads/2020/02/phone-animation.gif)

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

## Item Model
```swift
class Video: Hashable {
  var id = UUID()
  var title: String
  var thumbnail: UIImage?
  var lessonCount: Int
  var link: URL?
  
  init(title: String, thumbnail: UIImage? = nil, lessonCount: Int, link: URL?) {
    self.title = title
    self.thumbnail = thumbnail
    self.lessonCount = lessonCount
    self.link = link
  }
  
  static func == (lhs: Video, rhs: Video) -> Bool {
    lhs.id == rhs.id
  }
  
  func hash(into hasher: inout Hasher) {
    hasher.combine(id)
  }
}
```

## Section Model
```swift
class Section: Hashable {
  var id = UUID()
  var title: String
  var videos: [Video]
  
  init(title: String, videos: [Video]) {
    self.title = title
    self.videos = videos
  }
  
  func hash(into hasher: inout Hasher) {
    hasher.combine(id)
  }
  
  static func == (lhs: Section, rhs: Section) -> Bool {
    lhs.id == rhs.id
  }
}
```

## CollectionView 적용
```swift
typealias DataSource = UICollectionViewDiffableDataSource<Section, Video>
func makeDataSource() -> DataSource {
  let dataSource = DataSource(
    collectionView: collectionView) { (collectionView, indexPath, video) -> UICollectionViewCell? in
      let cell = collectionView.dequeueReusableCell(withReuseIdentifier: "VideoCollectionViewCell", for: indexPath) as? VideoCollectionViewCell
      cell?.video = video
      return cell
    }
    
  dataSource.supplementaryViewProvider = { collectionView, kind, indexPath in
    guard kind == UICollectionView.elementKindSectionHeader else {
      return nil
    }
    
    let view = collectionView.dequeueReusableSupplementaryView(
      ofKind: kind,
      withReuseIdentifier: SectionHeaderReusableView.reuseIdentifier,
      for: indexPath) as? SectionHeaderReusableView

    let section = self.dataSource.snapshot()
      .sectionIdentifiers[indexPath.section]
    view?.titleLabel.text = section.title
    return view
  }
  return dataSource
}
```

## snapshot 생성 및 적용
```swift
typealias Snapshot = NSDiffableDataSourceSnapshot<Section, Video>
func applySnapshot(animatingDifferrences: Bool = true) {
  var snapshot = Snapshot()
  snapshot.appendSections(sections)
  sections.forEach { section in
    snapshot.appendItems(section.videos, toSection: section)
  }
  dataSource.apply(snapshot, animatingDifferences: animatingDifferrences)
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
  
## UICollectionViewCompositionalLayout 적용
```swift
private func configureLayout() {
  collectionView.register(
    SectionHeaderReusableView.self,
    forSupplementaryViewOfKind: UICollectionView.elementKindSectionHeader,
    withReuseIdentifier: SectionHeaderReusableView.reuseIdentifier
  )
  
  collectionView.collectionViewLayout = UICollectionViewCompositionalLayout(sectionProvider: { (sectionIndex, layoutEnvironment) -> NSCollectionLayoutSection? in
    let isPhone = layoutEnvironment.traitCollection.userInterfaceIdiom == UIUserInterfaceIdiom.phone
    let size = NSCollectionLayoutSize(
      widthDimension: NSCollectionLayoutDimension.fractionalWidth(1),
      heightDimension: NSCollectionLayoutDimension.absolute(isPhone ? 280 : 250)
    )
    let itemCount = isPhone ? 1 : 3
    let item = NSCollectionLayoutItem(layoutSize: size)
    let group = NSCollectionLayoutGroup.horizontal(layoutSize: size, subitem: item, count: itemCount)
    let section = NSCollectionLayoutSection(group: group)
    section.contentInsets = NSDirectionalEdgeInsets(top: 10, leading: 10, bottom: 10, trailing: 10)
    section.interGroupSpacing = 10
    
    // Supplementary header view setup
    let headerFooterSize = NSCollectionLayoutSize(
      widthDimension: .fractionalWidth(1.0),
      heightDimension: .estimated(20)
    )
    let sectionHeader = NSCollectionLayoutBoundarySupplementaryItem(
      layoutSize: headerFooterSize,
      elementKind: UICollectionView.elementKindSectionHeader,
      alignment: .top
    )
    section.boundarySupplementaryItems = [sectionHeader]
    
    return section
  })
}
```
[<i class="fas fa-link"></i> UICollectionViewCompositionalLayout에 대한 Post는 여기 가기](/ios/uiresponder/uiview/uicollectionview/UICollectionViewCompositionalLayout/)로 가시면 되요~!😍

[<i class="fas fa-link"></i> 해당 프로젝트 보러 가기](https://github.com/swift-man/iOS-Tutorial-Collection-View-and-Diffable-Data-Source){:target="_blank"}   
## 출처
[<i class="fas fa-link"></i> ZeddiOS](https://zeddios.tistory.com/1197){:target="_blank"}  
[<i class="fas fa-link"></i> ellyheetov.devlog](https://velog.io/@ellyheetov/UI-Diffable-Data-Source){:target="_blank"}  
[<i class="fas fa-link"></i> Demian의 기술블로그](https://demian-develop.tistory.com/22){:target="_blank"}  
[<i class="fas fa-link"></i> { import Foundation }](https://velog.io/@haanwave/iOS-Swift-UICollectionViewCompositionalLayout-in-iOS-13){:target="_blank"}  
[<i class="fas fa-link"></i> NamS의 iOS일기](https://nsios.tistory.com/150){:target="_blank"}  


