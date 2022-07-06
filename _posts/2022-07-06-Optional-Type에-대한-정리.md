---
title: Optional Type에 대한 정리
tags: [Swift]
style: fill
color: warning
description: Optional Type에 대해서 가볍게 정리해보았다.
---

## Optional 타입에 대한 이해

변수를 메모리에서 조회할 때, 값이 없으면 에러가 나게 된다.
이 때 에러가 나지 않도록 임시적인 타입을 담아두는 개념이 Optional이다.

```swift
var optionalValue: String? = "Jobs"
var optionalName: String?
```

아래처럼 값 없이 임시적인 타입을 넣어놓아도 에러가 나지 않는다.

1) Optional 에는 nil 을 대입 할 수 있다  
2) 선언 시 값을 넣지 않는다면, 자동으로 nil 로 초기화 된다

## Optional Value를 추출하는 4가지 방법

1) Forced Unwrapping -> 값이 있다는 것이 확실할 때

```swift
print(str!)
```

2) if문으로 nil이 아니라는 것 확인한 후, Forced Unwrapping
```swift
if str != nil{
    print(str!)
}
```

3) Optional Binding(if let binding)
바인딩이 된다는 것은 nil이 아니라는 의미이기 때문에, 작업을 진행할 수 있다.

```swift

if let s = str {  
    print(s)
}

var optionalName: String? = "홍길동"

if let name = optionalName {
    print(name)
}

// 실제 앱을 만들때 guard let 바인딩 많이 사용

func doSomething(name: String?) {
    guard let n = name else { return }
    print(n)
}

doSomething(name: "hello")
```

4) Nil-Coalescing) 연산자를 사용하는 방법

> Coalesce: 더 큰 덩어리로 합친다

Optional Type 에서 Default 값을 제공할 수 있을 때 사용  
```swift
var serverName: String? = "홍길동"


var userName = serverName ?? "미인증사용자"    // String타입

var hello = "인사하겠습니다. " + (str ?? "Say, Hi")
print(hello)



str = nil
print(str ?? "Say, Hi")
```
