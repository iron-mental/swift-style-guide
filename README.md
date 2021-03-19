# swift-style-guide

 >__Terminal__ 프로젝트 협업 Swift 스타일 가이드입니다. 프로젝트 현황에 따라서 수시 변동될 수 있습니다.
 
 - 스타일 컨벤션의 일부는 [SwiftLint](https://github.com/realm/SwiftLint) 준수합니다.

## 커밋 TYPE

- feat : 새로운 기능 추가
- fix : 버그 수정
- docs : 문서의 수정
- style : (코드의 수정 없이) 스타일(style)만 변경(들여쓰기 같은 포맷이나 세미콜론을 빼먹은 경우)
- refactor : 코드를 리펙토링
- chore : (코드의 수정 없이) 설정을 변경

## 코드 레이아웃

### 임포트
- 임포트는 알파벳 순서로 합니다. 코코아 프레임워크를 먼저 임포트 하고, 이외 프레임워크를 임포트 합니다. 
```swift
import UIkit
import Foundation
import Alamofire
import Then
```

### 코드 들여쓰기
- 코드의 들여쓰기는 탭(tab)으로 구분합니다.

### 클래스 
- 클래스 이름에는 UpperCamelCase를 사용합니다.

### 함수
- lowerCamelCase를 사용합니다.

### 변수
- lowerCamelCase를 사용합니다.
- 변수의 정렬 순서는 disposebag, instance들, ui 요소들, 그 외의 변수 순으로 정렬합니다.
- 변수는 성격별로 구분 짓고 주석을 덧붙힙니다.

### 상수
- lowerCamelCase를 사용합니다.

### 약어
- 약어로 시작하는 경우 소문자로 표기하고, 그 외의 경우에는 항상 대문자로 표기합니다.

**좋은 예:**

```swift
let userID: Int?
let html: String?
let websiteURL: URL?
let urlString: String?
```

**나쁜 예:**

```swift
let userId: Int?
let HTML: String?
let websiteUrl: NSURL?
let URLString: String?
```

### 클로저
- 파라미터와 리턴 타입이 없는 Closure 정의시에는 () -> Void를 사용합니다.

**좋은 예:**

```swift
let completionHandler: (() -> Void)?
```

**나쁜 예:**

```swift
let completionHandler: (() -> ())?
let completionHandler: ((Void) -> (Void))?
```
- Closure 정의시 파라미터에는 괄호를 사용하지 않습니다.

**좋은 예:**

```swift
{ first, second in
  // doSomething()
}
```

**나쁜 예:**

```swift
{ (first, second) in
  // doSomething()
}
```


### 주석
- //를 사용해서 문서화에 사용되는 주석을 남깁니다.

```swift
// 사용자 프로필을 그려주는 뷰
class ProfileView: UIView {

    // 사용자 닉네임을 그려주는 라벨
    var nameLabel: UILabel!
}
```
- // MARK:를 사용해서 연관된 코드를 구분짓습니다.
Objective-C에서 제공하는 #pragma mark와 같은 기능으로, 연관된 코드와 그렇지 않은 코드를 구분할 때 사용합니다.

```swift
// MARK: - Init

override init(frame: CGRect) {
  // doSomething()
}

deinit {
  // doSomething()
}


// MARK: - Layout

override func layoutSubviews() {
  // doSomething()
}


// MARK: - Actions

override func menuButtonDidTap() {
  // doSomething()
}
```


### 프로그래밍 권장사항
- 가능하다면 변수를 선언을 한 뒤 attribute, layout 함수에 성격에 맞게 정의합니다.

```swift
var checkBox = UIButton()
var idLabel = UILabel()

func attribute {
	checkBox.do {
		$0.frame = CGRect(x: 0, y: 0, width: 300, height: 300)
	}
	idLabel.do {
		$0.font = .systemFont(ofSize: 18, weight: .light)
		$0.textColor = .black
	}
}

func layout {
	view.addsubview(checkBox)
	view.addsubview(idLabel)
	
	checkBox.snp.makeconstraint {
		$0.right.equalToSuperview().offset(-20)
		$0.centerY.equalToSuperview()
	}
	idLabel.snp.makeconstraint {
		$0.centerY.equalToSuperview()
		$0.left.equalTo(userImageView.snp.right).offset(10)
	}
}
```

- 더이상 상속이 발생하지 않는 클래스는 항상 final 키워드로 선언합니다.
- 프로토콜을 적용할 때에는 extension을 만들어서 관련된 메서드를 모아둡니다.

**좋은 예:**

```swift
final class MyViewController: UIViewController {
  // ...
}

extension MyViewController: UITableViewDelegate, UITableViewDataSource {
  // ...
}
```

**나쁜 예:**

```swift
final class MyViewController: UIViewController, UITableViewDataSource, UITableViewDelegate {
  // ...
}
```

## 라이센스 
본 문서는 [스타일쉐어](https://github.com/StyleShare/swift-style-guide) 스타일 가이드를 인용하였으며, 저작권은 [전수열님](https://github.com/devxoul)과 [StyleShare](https://www.styleshare.kr/)에게 있습니다.

