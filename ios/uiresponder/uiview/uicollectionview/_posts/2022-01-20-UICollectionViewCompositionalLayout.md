---
sidebar:
  title: "iOS"
  nav: sidebar-ios
  icon: "fab fa-app-store-ios"
title: "UICollectionViewCompositionalLayout"
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
### Create a Grid Layout
* NSCollectionLayoutDimension
  * absoulte - 절대 크기
  * estimated - 런타임에 크기가 정해져야 하는 경우 예상 크기 기반으로 동작
  * fractional - SwiftUI 의 GeometryReader와 유사하게 자신의 크기의 비율로 동작, 0 ~ 1.0 사이의 CGFloat 기반
* .fractionalWidth(0.2) 를 사용하여 여러번 반복되는 그리드 height 각 20% 의 크기로 만듬

```swift
let itemSize = NSCollectionLayoutSize(widthDimension: .fractionalWidth(0.2),
                                     heightDimension: .fractionalHeight(1.0))
let item = NSCollectionLayoutItem(layoutSize: itemSize)

let groupSize = NSCollectionLayoutSize(widthDimension: .fractionalWidth(1.0),
                                      heightDimension: .fractionalWidth(0.2))
let group = NSCollectionLayoutGroup.horizontal(layoutSize: groupSize,
                                                 subitems: [item])

let section = NSCollectionLayoutSection(group: group)

let layout = UICollectionViewCompositionalLayout(section: section)
return layout
```


### Add Spacing Around Items
* 가장자리에 균일한 contentInsets 적용

```swift
let itemSize = NSCollectionLayoutSize(widthDimension: .fractionalWidth(0.2),
                                     heightDimension: .fractionalHeight(1.0))
let item = NSCollectionLayoutItem(layoutSize: itemSize)
item.contentInsets = NSDirectionalEdgeInsets(top: 5, leading: 5, bottom: 5, trailing: 5)
```

### Create a Column Layout
* horizontal(layoutSize:subitem:count:). 함수를 통해 그룹을 생성 가능
* 아래는 2열 레이아웃을 만드는 예제.

```swift
let itemSize = NSCollectionLayoutSize(widthDimension: .fractionalWidth(1.0),
                                     heightDimension: .fractionalHeight(1.0))
let item = NSCollectionLayoutItem(layoutSize: itemSize)

let groupSize = NSCollectionLayoutSize(widthDimension: .fractionalWidth(1.0),
                                      heightDimension: .absolute(44))
let group = NSCollectionLayoutGroup.horizontal(layoutSize: groupSize, subitem: item, count: 2)
let spacing = CGFloat(10)
group.interItemSpacing = .fixed(spacing)
```

### Display Distinct Layouts Per Section
* sectionIndex 를 활용하여 각 section에 대해 다른 layout을 구성

```swift
let layout = UICollectionViewCompositionalLayout { (sectionIndex: Int,
    layoutEnvironment: NSCollectionLayoutEnvironment) -> NSCollectionLayoutSection? in

    guard let sectionLayoutKind = SectionLayoutKind(rawValue: sectionIndex) else { return nil }
    let columns = sectionLayoutKind.columnCount

    // The group auto-calculates the actual item width to make
    // the requested number of columns fit, so this widthDimension is ignored.
    let itemSize = NSCollectionLayoutSize(widthDimension: .fractionalWidth(1.0),
                                         heightDimension: .fractionalHeight(1.0))
    let item = NSCollectionLayoutItem(layoutSize: itemSize)
    item.contentInsets = NSDirectionalEdgeInsets(top: 2, leading: 2, bottom: 2, trailing: 2)

    let groupHeight = columns == 1 ?
        NSCollectionLayoutDimension.absolute(44) :
        NSCollectionLayoutDimension.fractionalWidth(0.2)
    let groupSize = NSCollectionLayoutSize(widthDimension: .fractionalWidth(1.0),
                                          heightDimension: groupHeight)
    let group = NSCollectionLayoutGroup.horizontal(layoutSize: groupSize, subitem: item, count: columns)

    let section = NSCollectionLayoutSection(group: group)
    section.contentInsets = NSDirectionalEdgeInsets(top: 20, leading: 20, bottom: 20, trailing: 20)
    return section
}
return layout
```

### Display Distinct Layouts in Different Environments
![Image](https://drive.google.com/uc?export=view&id=1iBMaF4RkzD2FbakohSkyLXyftVmmt-iS)

* NSCollectionLayoutEnvironment
* 다양한 사이즈를 고려 필요 시
  * layoutEnvironment.container.effectiveContentSize 를 사용하여 사용가능한  열 제어

```swift
let layout = UICollectionViewCompositionalLayout {
    (sectionIndex: Int, layoutEnvironment: NSCollectionLayoutEnvironment) -> NSCollectionLayoutSection? in
    guard let layoutKind = SectionLayoutKind(rawValue: sectionIndex) else { return nil }

    let columns = layoutKind.columnCount(for: layoutEnvironment.container.effectiveContentSize.width)

    let itemSize = NSCollectionLayoutSize(widthDimension: .fractionalWidth(0.2),
                                         heightDimension: .fractionalHeight(1.0))
    let item = NSCollectionLayoutItem(layoutSize: itemSize)
    item.contentInsets = NSDirectionalEdgeInsets(top: 2, leading: 2, bottom: 2, trailing: 2)

    let groupHeight = layoutKind == .list ?
        NSCollectionLayoutDimension.absolute(44) : NSCollectionLayoutDimension.fractionalWidth(0.2)
    let groupSize = NSCollectionLayoutSize(widthDimension: .fractionalWidth(1.0),
                                           heightDimension: groupHeight)
    let group = NSCollectionLayoutGroup.horizontal(layoutSize: groupSize, subitem: item, count: columns)

    let section = NSCollectionLayoutSection(group: group)
    section.contentInsets = NSDirectionalEdgeInsets(top: 20, leading: 20, bottom: 20, trailing: 20)
    return section
}
return layout
```

### Add Badges to Items
![Image](https://drive.google.com/uc?export=view&id=13nikC9d85dWTHwDV0voIs7d5Lzfli_IG)

* supplementaryViewProvider 를 이용하여 cell 에 badge 를 추가

```swift
let badgeAnchor = NSCollectionLayoutAnchor(edges: [.top, .trailing], fractionalOffset: CGPoint(x: 0.3, y: -0.3))
let badgeSize = NSCollectionLayoutSize(widthDimension: .absolute(20),
                                      heightDimension: .absolute(20))
let badge = NSCollectionLayoutSupplementaryItem(
    layoutSize: badgeSize,
    elementKind: ItemBadgeSupplementaryViewController.badgeElementKind,
    containerAnchor: badgeAnchor)

let itemSize = NSCollectionLayoutSize(widthDimension: .fractionalWidth(0.25),
                                     heightDimension: .fractionalHeight(1.0))
let item = NSCollectionLayoutItem(layoutSize: itemSize, supplementaryItems: [badge])
item.contentInsets = NSDirectionalEdgeInsets(top: 5, leading: 5, bottom: 5, trailing: 5)
```

### Add Headers and Footers to Sections
![Image](https://drive.google.com/uc?export=view&id=1R1f8L3aRoqTPmhM3RIvbI-tSs53gbhU3)

* .boundarySupplementaryItems 를 사용하여 Section의 HeaderView, FooterView를 생성 가능

```swift
let headerFooterSize = NSCollectionLayoutSize(widthDimension: .fractionalWidth(1.0),
                                             heightDimension: .estimated(44))
let sectionHeader = NSCollectionLayoutBoundarySupplementaryItem(
    layoutSize: headerFooterSize,
    elementKind: SectionHeadersFootersViewController.sectionHeaderElementKind, alignment: .top)
let sectionFooter = NSCollectionLayoutBoundarySupplementaryItem(
    layoutSize: headerFooterSize,
    elementKind: SectionHeadersFootersViewController.sectionFooterElementKind, alignment: .bottom)
section.boundarySupplementaryItems = [sectionHeader, sectionFooter]
```
---
* 아래 예제는 FooterView 추가

```swift
let headerRegistration = UICollectionView.SupplementaryRegistration
<TitleSupplementaryView>(elementKind: SectionHeadersFootersViewController.sectionHeaderElementKind) {
    (supplementaryView, string, indexPath) in
    supplementaryView.label.text = "\(string) for section \(indexPath.section)"
    supplementaryView.backgroundColor = .lightGray
    supplementaryView.layer.borderColor = UIColor.black.cgColor
    supplementaryView.layer.borderWidth = 1.0
}
```
---
* .diffable datasource의 supplementaryViewProvider 를 사용하여 section 별 Header/Footer 에 대해 제어 가능

```swift
dataSource.supplementaryViewProvider = { (view, kind, index) in
    return self.collectionView.dequeueConfiguredReusableSupplementary(
        using: kind == SectionHeadersFootersViewController.sectionHeaderElementKind ? headerRegistration : footerRegistration, for: index)
}
```


### Pin Section Headers to Sections
![Image](https://drive.google.com/uc?export=view&id=1LhRNND-nZmvyrv7sFVbFZQclGlXFyAlS)

*  pinToVisibleBounds,  zIndex 를 통해 고정된 section을 제공 가능.

```swift
let sectionHeader = NSCollectionLayoutBoundarySupplementaryItem(
    layoutSize: NSCollectionLayoutSize(widthDimension: .fractionalWidth(1.0),
                                      heightDimension: .estimated(44)),
    elementKind: PinnedSectionHeaderFooterViewController.sectionHeaderElementKind,
    alignment: .top)
let sectionFooter = NSCollectionLayoutBoundarySupplementaryItem(
    layoutSize: NSCollectionLayoutSize(widthDimension: .fractionalWidth(1.0),
                                      heightDimension: .estimated(44)),
    elementKind: PinnedSectionHeaderFooterViewController.sectionFooterElementKind,
    alignment: .bottom)
sectionHeader.pinToVisibleBounds = true
sectionHeader.zIndex = 2
section.boundarySupplementaryItems = [sectionHeader, sectionFooter]
```
---
* diffable datasource의 supplementaryViewProvider 를 사용하여 section 별 Header/Footer 의 고정 여부를 제어 가능

```swift
dataSource.supplementaryViewProvider = { (view, kind, index) in
    return self.collectionView.dequeueConfiguredReusableSupplementary(
        using: kind == PinnedSectionHeaderFooterViewController.sectionHeaderElementKind ? headerRegistration : footerRegistration, for: index)
}
```

### Create Custom Layouts by Nesting Groups
![Image](https://drive.google.com/uc?export=view&id=1_gob6vyG2zZrSxsWGnQD8dHDjCxw1QQ-)
* NSCollectionLayoutDecorationItem.background(elementKind:)decorationItems 
  * Section의 background를 생성

```swift
let leadingItem = NSCollectionLayoutItem(
    layoutSize: NSCollectionLayoutSize(widthDimension: .fractionalWidth(0.7),
                                      heightDimension: .fractionalHeight(1.0)))
leadingItem.contentInsets = NSDirectionalEdgeInsets(top: 10, leading: 10, bottom: 10, trailing: 10)

let trailingItem = NSCollectionLayoutItem(
    layoutSize: NSCollectionLayoutSize(widthDimension: .fractionalWidth(1.0),
                                      heightDimension: .fractionalHeight(0.3)))
trailingItem.contentInsets = NSDirectionalEdgeInsets(top: 10, leading: 10, bottom: 10, trailing: 10)
let trailingGroup = NSCollectionLayoutGroup.vertical(
    layoutSize: NSCollectionLayoutSize(widthDimension: .fractionalWidth(0.3),
                                      heightDimension: .fractionalHeight(1.0)),
    subitem: trailingItem, count: 2)

let nestedGroup = NSCollectionLayoutGroup.horizontal(
    layoutSize: NSCollectionLayoutSize(widthDimension: .fractionalWidth(1.0),
                                      heightDimension: .fractionalHeight(0.4)),
    subitems: [leadingItem, trailingGroup])
```
---
* register(_:forDecorationViewOfKind:)
    * 를 통해 UIView를 등록하고 백그라운드로 등록 가능 

```swift
let layout = UICollectionViewCompositionalLayout(section: section)
layout.register(
    SectionBackgroundDecorationView.self,
    forDecorationViewOfKind: SectionDecorationViewController.sectionBackgroundDecorationElementKind)
return layout
```

### Create Custom Layouts by Nesting Groups
* Custom Layout을 만들고, 정렬 할 수 있음

![Image](https://drive.google.com/uc?export=view&id=1Oc8ppLE9xq6p8T2IDGLXPyrQkyv2CyAK)

```swift
let leadingItem = NSCollectionLayoutItem(
    layoutSize: NSCollectionLayoutSize(widthDimension: .fractionalWidth(0.7),
                                      heightDimension: .fractionalHeight(1.0)))
leadingItem.contentInsets = NSDirectionalEdgeInsets(top: 10, leading: 10, bottom: 10, trailing: 10)

let trailingItem = NSCollectionLayoutItem(
    layoutSize: NSCollectionLayoutSize(widthDimension: .fractionalWidth(1.0),
                                      heightDimension: .fractionalHeight(0.3)))
trailingItem.contentInsets = NSDirectionalEdgeInsets(top: 10, leading: 10, bottom: 10, trailing: 10)
let trailingGroup = NSCollectionLayoutGroup.vertical(
    layoutSize: NSCollectionLayoutSize(widthDimension: .fractionalWidth(0.3),
                                      heightDimension: .fractionalHeight(1.0)),
    subitem: trailingItem, count: 2)

let nestedGroup = NSCollectionLayoutGroup.horizontal(
    layoutSize: NSCollectionLayoutSize(widthDimension: .fractionalWidth(1.0),
                                      heightDimension: .fractionalHeight(0.4)),
    subitems: [leadingItem, trailingGroup])
```

### Scroll Sections Horizontally
기본적으로 세로 스크롤이지만 옵션을 통해 가로 스크롤 제공
* orthogonalScrollingBehavior
  * .continuous
  * .continuousGroupLeadingBoundary
  * .paging
  * .groupPaging
  * .groupPagingCentered
  * .none(기본 세로 스크롤)

```swift
section.orthogonalScrollingBehavior = .continuous
```



### Choose Horizontal Scrolling and Paging Behavior
* UICollectionLayoutSectionOrthogonalScrollingBehavior 를 사용한 Section별 스크롤 동작의 예

```swift
case continuous, continuousGroupLeadingBoundary, paging, groupPaging, groupPagingCentered, none
func orthogonalScrollingBehavior() -> UICollectionLayoutSectionOrthogonalScrollingBehavior {
    switch self {
    case .none:
        return UICollectionLayoutSectionOrthogonalScrollingBehavior.none
    case .continuous:
        return UICollectionLayoutSectionOrthogonalScrollingBehavior.continuous
    case .continuousGroupLeadingBoundary:
        return UICollectionLayoutSectionOrthogonalScrollingBehavior.continuousGroupLeadingBoundary
    case .paging:
        return UICollectionLayoutSectionOrthogonalScrollingBehavior.paging
    case .groupPaging:
        return UICollectionLayoutSectionOrthogonalScrollingBehavior.groupPaging
    case .groupPagingCentered:
        return UICollectionLayoutSectionOrthogonalScrollingBehavior.groupPagingCentered
    }
}
```


### Create a Simple List Layout
* list(using:) 를 사용하여 기본 목록 Layout을 만들 수 있음.
* system-defined list appearances 중 하나를 선택하여 구성

```swift
let config = UICollectionLayoutListConfiguration(appearance: .insetGrouped)
return UICollectionViewCompositionalLayout.list(using: config)
```

### Choose a List Appearance
* UICollectionLayoutListConfiguration.Appearance
  * NavigationBar 를 변경할 수 있는 옵션을 제공
* UICollectionLayoutListConfiguration.HeaderMode.firstItemInSection
  * 를 통해 HeaderMode를 선택할 수 있음. 

```swift
var config = UICollectionLayoutListConfiguration(appearance: self.appearance)
config.headerMode = .firstItemInSection
```

### Customize List Cells
* UICollectionViewListCell
  * custom cell subclass를 의 구성 설정을 로드하여 set 할 수 있는 defaultListContentConfiguration 을 제공

```swift
var content = defaultListContentConfiguration().updated(for: state)
```
---
* configuration
  * 구성 값을 지정하고 configuration property 에 할당
  * updateConfiguration(using:) 을 통해 미리 지정한 설정을 복사할 수 있음.

```swift
categoryIconView.tintColor = valueConfiguration.imageProperties.resolvedTintColor(for: tintColor)
categoryIconView.preferredSymbolConfiguration = .init(font: valueConfiguration.secondaryTextProperties.font, scale: .small)
```
---
* custom cell subclass를 사용하기 위해 cell registration 을 사용해야 함

```swift
let cellRegistration = UICollectionView.CellRegistration<CustomListCell, Item> { (cell, indexPath, item) in
    cell.updateWithItem(item)
    cell.accessories = [.disclosureIndicator()]
}
```
---
* diffable data source 에서 cell 을 사용할 땐 아래와 같이 사용해야 함

```swift
return collectionView.dequeueConfiguredReusableCell(using: cellRegistration, for: indexPath, item: item)
```

### Build a Layout with Multiple Section Types
* Cell에 Swipe Action 을 제공합니다.

![Image](https://drive.google.com/uc?export=view&id=1V1zJ2ARPaulA6j5x7v49joMT7iS5TR7D)

```swift
configuration.leadingSwipeActionsConfigurationProvider = { [weak self] (indexPath) in
    guard let self = self else { return nil }
    guard let item = self.dataSource.itemIdentifier(for: indexPath) else { return nil }
    return self.leadingSwipeActionConfigurationForListCellItem(item)
}
```

## 참고
[<i class="fas fa-link">developer.apple.com</i> Title](https://developer.apple.com/documentation/uikit/views_and_controls/collection_views/implementing_modern_collection_views){:target="_blank"}  
* 여기에 가시면 샘플 예제와 함께 더 자세한 내용을 보실 수 있어요!
