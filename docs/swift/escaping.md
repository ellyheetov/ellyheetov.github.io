---
layout: default
title: escaping
parent: Swift
---

# @escaping

## escaping은 뭐지?
Optional Type Closure 매개변수로써 escaping과 non-espacing이 있다.

클로저가 함수로 부터 Escape 한다는 것은 해당 함수의 인자로 클로저가 전달되지만, **함수가 반환된 후 실행 되는 것을 의미한다.** 다시말해, 함수의 실행순서를 지정할 수 있게 된다. 

## 일반 변수와 뭐가 다른 걸까?

기존의 알고있는 scope의 개념을 무시한다. 함수에서 선언된 로컬변수가 함수 밖에서도 유효하기 때문이다.

전역변수로 선언하여 함수에 가져와서 사용하는 것과 별반 다를 것 없어 보이지만, 함수의 실행순서를 정할 수 있다는 점에서 유용하다. **A함수가 마무리 된 상태에서만 B함수가 실행되도록** 할 수 있기 때문이다.

## escaping이 언제 필요해?

- escaping을 많이 사용하는 사례는 HTTP 통신의 request, response의 경우이다.

일반적으로 서버에 request를 전송하고 response를 받아오는 함수들은 비동기적으로 작동한다. Request를 보낸 직후 반환하게 되는데, 이 같은 response가 request의 결과를 기다리게 할 수 있도록 하기 위해서는 escaping이 필요하다.

### 예시
```swift
var completionHandlers = [() -> Void]()

func somFunctionWithEscapingClosure(completionHandler: @escaping () -> Void){
    completionHandlers.append(completionHandler)
    /*
    completionHandler는 함수 내에 클로저 변수이지만, 함수 외부에서 선언된 completionHanlders에 추가하고 있다.
    함수 내에서 선언된 변수를 함수 외부에서 사용하기 위해서는 escaping을 사용한다.
    */
}

func someFunctionWithNonescapingClosure(closure: () -> Void) {
    closure()
}

class SomeClass {
    var x = 10
    func doSomthing(){
        somFunctionWithEscapingClosure{ self.x = 100 }
        someFunctionWithNonescapingClosure{ x = 200}
    }
}
```
```swift
let instance = SomeClass()
instance.doSomthing()
print(instance.x) //200

completionHandlers.first?()
print(instance.x) // 100
```


Reference
> https://docs.swift.org/swift-book/LanguageGuide/Closures.html
