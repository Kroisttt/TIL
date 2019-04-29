# Computed Property (연산 프로퍼티)
 - 값을 저장하지 않고 값을 계산해서 반환하는 프로퍼티
 - class, struct, enum에서 정의 가능
 - var 키워드로 정의 (let 키워드로 정의 불가)
 - getter는 필수지만 setter는 선택적 (쓰기 전용으로 구현 불가)

##### [Swift 공식 예시](https://docs.swift.org/swift-book/LanguageGuide/Properties.html)
```
struct Point {
    var x = 0.0, y = 0.0
}

struct Size {
    var width = 0.0, height = 0.0
}

struct Rect {
    var origin = Point()
    var size = Size()
    var center: Point {
        get {
            let centerX = origin.x + (size.width / 2)
            let centerY = origin.y + (size.height / 2)
            return Point(x: centerX, y: centerY)
        }
        set(newCenter) {
            origin.x = newCenter.x - (size.width / 2)
            origin.y = newCenter.y - (size.height / 2)
        }
    }
}

var square = Rect(origin: Point(x: 0.0, y: 0.0), size: Size(width: 10.0, height: 10.0))
let initialSquareCenter = square.center
square.center = Point(x: 15.0, y: 15.0)
print("square.origin is now at (\(square.origin.x), \(square.origin.y))")
// Prints "square.origin is now at (10.0, 10.0)"
```
 - `let initialSquareCenter = square.center` 시점에서 origin은 (0, 0), center의 getter에 의해 `initialSquareCenter`에 들어가는 값은 `Point(x: 5, y: 5)`
 - `square.center = Point(x: 15.0, y: 15.0)` 시점에서 center의 setter에 의해 origin은 (10, 10)으로 위치 변경 

##### [Shorthand Setter Declaration 공식 예시](https://docs.swift.org/swift-book/LanguageGuide/Properties.html)
```
struct AlternativeRect {
    var origin = Point()
    var size = Size()
    var center: Point {
        get {
            let centerX = origin.x + (size.width / 2)
            let centerY = origin.y + (size.height / 2)
            return Point(x: centerX, y: centerY)
        }
        set {
            origin.x = newValue.x - (size.width / 2)
            origin.y = newValue.y - (size.height / 2)
        }
    }
}
```
 - setter에 변수 이름을 지정하지 않아도 `newValue`라는 기본 이름 사용 가능

##### 읽기 전용 예시
```
var str: String {
    return "Hello, playground"
}
```
 - 연산 프로퍼티를 읽기 전용으로 구현시 getter 생략 가능