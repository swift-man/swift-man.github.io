---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "UICollectionViewDiffableDatasource 개발기"
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


## 후기
* RxDataSource 나 기존 UICollectionViewLayout 으로 구현 불가능한 세로/가로 스크롤형 뷰를 생성 가능
* 이전 버전에 대한 대응 노하우가 쌓인다면 사용해볼만 함
* 지원하는 OS 버전이 낮을 수록 안정성이 떨어짐
    * 최소버전을 15이상 지원한다면 사용해볼만 함

![Image](https://drive.google.com/uc?export=view&id=1z9W8-LFJsx08gwTUTWIniTZB3oLk8uDh)  

## collectionView 생성
```swift
let collectionView = UICollectionView(
    frame: .zero,
    collectionViewLayout: createLayout()
)
```

## Snapshot 생성
```swift
private typealias Snapshot = NSDiffableDataSourceSnapshot<SectionHeaderReactor, CellReactor>
var currentSnapshot = Snapshot()
```
* ReactorKit을 사용한다면 RxDataSource보다 호환성이 떨어지며 Snapshot의 역할이 모호해짐
* Reactor.State 는 Data, SnapShot 은 View 를 직접 관리 용도로 사용 함

### ApplySnapshot
```swift
func applySnapshot(animatingDifferrences: Bool = true) {
    guard let reactor else { return }
    
    self.currentSnapshot = Snapshot()
    reactor.currentState.sectionReactors.forEach { collection in
      self.currentSnapshot.appendSections([collection])
    }
    
    self.dataSource?.apply(self.currentSnapshot,
                           animatingDifferences: animatingDifferrences)
 }
```

* 버전에 따른 snapshot 적용 동작
    * iOS 14 이하
        * animatingDifferences : true : Diff
        *  animatingDifferences : false : ReloadData

### ReloadCompletionHandler


```swift
func applySnapshot(animatingDifferrences: Bool = true, completion: (() -> Void)? = nil) {    
  //...
    
  self.dataSource?.apply(self.currentSnapshot,
                         animatingDifferences: animatingDifferrences,
                         completion: completion)
 }
```

* iOS 15+ [applySnapshotUsingReloadData(_:completion:)](https://developer.apple.com/documentation/uikit/uicollectionviewdiffabledatasource/3804470-applysnapshotusingreloaddata)


### Reactor Bind
```swift
public func bind(reactor: Reactor) {
    reactor.state.map { $0.sectionReactors }
      .distinctUntilChanged()
      .observe(on: MainScheduler.instance)
      .subscribe(onNext: { [weak self] _ in
        self?.applySnapshot(animatingDifferrences: false)
      })
      .disposed(by: disposeBag)
}
```
* Bind 로 collectionViewDataSource를 연결하는 것이 아닌 방식

## DataSource 생성
```swift
typealias DataSource = UICollectionViewDiffableDataSource<SectionHeaderReactor, CellReactor>
func configureDataSource() {
    configureSections()
    configureCells()
    
    applySnapshot()
}
```

### configureCell
```swift
func configureCells() {
  typealias CellRegistration = UICollectionView.CellRegistration<Cell, CellReactor>
  let cellRegistration = CellRegistration { cell, _, cellReactor in
    cell.bind(reactor: cellReactor)
  }

  dataSource = DataSource(collectionView: collectionView) { collectionView, indexPath, cellReactor -> UICollectionViewCell? in
    return collectionView.dequeueConfiguredReusableCell(using: cellRegistration,
                                                        for: indexPath,
                                                        item: cellReactor)
  }
}
```

```swift
func configureSections() {
  typealias SectionHeaderViewRegistration = UICollectionView.SupplementaryRegistration<SectionHeaderView>
  let headerRegistration = SectionHeaderViewRegistration(
    elementKind: SectionHeaderView.elementKind) { [weak self] supplementaryView, _, indexPath in
     
    guard let self else { return }
    let sectionReactor = self.currentSnapshot.sectionIdentifiers[indexPath.section]
    supplementaryView.bind(reactor: sectionReactor)

    supplementaryView.plusButtonTap
      .subscribe(onNext: { [weak self] _ in
        //
      })
      .disposed(by: supplementaryView.disposeBag)
      
    dataSource?.supplementaryViewProvider = { collectionView, elementKind, indexPath in
        return collectionView.dequeueConfiguredReusableSupplementary(using: headerRegistration, for: indexPath)
    }
}
```

## reconfigureItems
* iOS 15+ [reconfigureItems(_:)](https://developer.apple.com/documentation/uikit/nsdiffabledatasourcesnapshot/3804468-reconfigureitems)

* 새로운 cell을 dequeuing and configuring 하지 않고 exisiting cell 을 업데이트
    * 성능이 좋아짐, 

## UICollectionViewLayout 생성
![Image](https://drive.google.com/uc?export=view&id=1UF4cRSjFLTKjGd1L103xDX9v9sekDMXg)  


```swift
func createLayout() -> UICollectionViewLayout {
    let config = UICollectionViewCompositionalLayoutConfiguration()
    let layout = UICollectionViewCompositionalLayout(sectionProvider: sectionProvider, configuration: config)
    return layout
}
```

### createSection
```swift
func createSection(at sectionIndex: Int,
                   with group: NSCollectionLayoutGroup) -> NSCollectionLayoutSection {
  let section = NSCollectionLayoutSection(group: group)
  section.orthogonalScrollingBehavior = .continuous
  section.interGroupSpacing = 8

  section.contentInsets = NSDirectionalEdgeInsets(top: 0,
                                                  leading: 12,
                                                  bottom: 12,
                                                  trailing: 12)

  let sectionHeader = createSectionHeader()

  section.boundarySupplementaryItems = [sectionHeader]
  return section
}
```

#### interGroupSpacing
![Image](https://drive.google.com/uc?export=view&id=1Nwj2LcFLIX9YShEpAkO0UZa9P7UZQTCC)  

### createGroup
![Image](https://drive.google.com/uc?export=view&id=1X6S81n01zg24IE_df_Tp8BGLU40oGR3f)  

![Image](https://drive.google.com/uc?export=view&id=1NaeRf4sFMvJU1VWV06X-4ahq9Ss9jst6)  
```swift
func createGroup(at sectionIndex: Int,
                 with item: NSCollectionLayoutItem,
                 snapshot: Snapshot) -> NSCollectionLayoutGroup {
  let groupSize: NSCollectionLayoutSize
  if let sectionReactor = snapshot.sectionIdentifiers[safe: sectionIndex],
    sectionReactor.currentState.cellReactors.isEmpty {
    groupSize = NSCollectionLayoutSize(widthDimension: .fractionalWidth(1),
                                         heightDimension: .absolute(0))
  } else {
    groupSize = NSCollectionLayoutSize(widthDimension: .estimated(1200),
                                         heightDimension: .absolute(72))
  }

  let group = NSCollectionLayoutGroup.horizontal(layoutSize: groupSize, subitems: [item])
  return group
}
```
![Image](https://drive.google.com/uc?export=view&id=188-aYz5ZXyPCUmfiuFqNJbp6HqBILcrk)  

### createItem
![Image](https://drive.google.com/uc?export=view&id=1jJhmNhUCzmwDXurjo1r9-Wpno-1vIT8N)  

```swift
func createItem() -> NSCollectionLayoutItem {
   let itemSize = NSCollectionLayoutSize(widthDimension: .absolute(100),
                                         heightDimension: .absolute(72))
   let item = NSCollectionLayoutItem(layoutSize: itemSize)
   return item
}
```


### createSectionHeader

```swift
func createSectionHeader() -> NSCollectionLayoutBoundarySupplementaryItem {
  let titleSize = NSCollectionLayoutSize(widthDimension: .absolute(view.frame.width),
                                         heightDimension: .absolute(48))

  let sectionHeader = NSCollectionLayoutBoundarySupplementaryItem(
    layoutSize: titleSize,
    elementKind: SectionHeaderView.elementKind,
    alignment: .top)

  if #available(iOS 15, *) {
    sectionHeader.pinToVisibleBounds = true
    sectionHeader.zIndex = 2
  }

  return sectionHeader
 }
```

![Image](https://drive.google.com/uc?export=view&id=1AkrlYJGtHcd9zNWTpJE42CzQl6qiM7ZF)  
* `fractionalWidth(1)` 를 사용하지 않은 이유
    * `section.contentInsets` 상대로 사이즈가 잡혀서 원하는 `full size`가 잡히지 않음

## pinToVisibleBounds
![Image](https://drive.google.com/uc?export=view&id=1fpKZFvvzjdflC6QVCI7WKT9qUWtkNf4O)  

* iOS 14 이하에서 화면이 깨지는 버그가 있음
![Image](https://drive.google.com/uc?export=view&id=1TON4UKC6VRflIS4ojhGxLAiw-h2R1bEr)  

```swift
@available(iOS 13.0, *)
open var pinToVisibleBounds: Bool
open var zIndex: Int
```

### sectionProvider
```swift
let sectionProvider = { [weak self] (sectionIndex: Int, _: NSCollectionLayoutEnvironment)
      -> NSCollectionLayoutSection? in
  guard let self else { return nil }

  let item = createItem()
  let group = createGroup(at: sectionIndex,
                          with: item,
                          snapshot: self.currentSnapshot)
  let section = createSection(at: sectionIndex,
                              with: group,
                              snapshot: self.currentSnapshot)
  return section
}
```

## UISwipeActionsConfiguration
![Image](https://drive.google.com/uc?export=view&id=1e-_GPpId-UAf4MLOGSI4DJj825OmW6MO)  

* 시뮬레이터에서 버그가 있음(Xcode 13 기준)

![Image](https://drive.google.com/uc?export=view&id=1sBTZRw50bAFxqyx7MIEcsSd_JB7uelJw)  
* 시뮬레이터에서 삭제 기능을 별도로 구현함
