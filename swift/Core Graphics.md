# Core Graphics
## CGPoint
 - 2차원 좌표계의 점을 포함하는 구조체

##### CGPoint 구현부

```
public struct CGPoint {

    
    public var x: CGFloat

    public var y: CGFloat

    public init()

    public init(x: CGFloat, y: CGFloat)
}
```

## CGSize
 - 폭과 높이값을 포함하는 구조체

##### CGSize 구현부
```
public struct CGSize {

    public var width: CGFloat

    public var height: CGFloat

    public init()

    public init(width: CGFloat, height: CGFloat)
}
```

## CGRect
 - 직사각형의 위치와 크기를 포함하는 구조체

##### CGRect 구현부

```
public struct CGRect {

    public var origin: CGPoint

    public var size: CGSize

    public init()

    public init(origin: CGPoint, size: CGSize)
}
```
##### 사용법
`let rect = CGRect(origin: CGPoint(x: 0, y: 0), size: CGSize(width: 10, height: 10))`  
`let rect = CGRect(x: 0, y: 0, width: 10, height: 10)`
> (0, 0) 위치에서 폭 10, 높이 10의 직사각형 표현