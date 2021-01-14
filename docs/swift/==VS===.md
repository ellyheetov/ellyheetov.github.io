---
layout: default
title: == VS ===
parent: Swift
nav_order: 3
---

# Difference between == and ===

### == operator

> == operator checks if their instance values are equal, "equal to"

인스턴스가 가지고 있는 value 값이 같은지 확인한다.

### === operator

> === operator checks if the references point the same instance, "identical to"

비교하는 인스턴스가 정확히 같은 인스턴스 인지 확인한다.

### 예시 

```swift
class Person : Equatable{
    let ssn : Int 
    let name : String
    
    init(ssn: Int, name: String){
        self.ssn = ssn
        self.name = name
    }
    static func == (lhs: Person, rhs:Person) -> Bool {
        return lhs.ssn == rhs.ssn
    }
}
```
```swift
let person1 = Person(ssn: 5, name: "Bob")
let person2 = Person(ssn: 5, name: "Bob")

/*
동일하게 ssn = 5, name="Bob"으로 생성하였다.
person1의 ssn과 person2의 ssn이 같으므로 true값을 return 한다.
*/
if person1 == person2 {
    print("the two instance are equal")
}
/*
클래스 내에있는 ssn과 name은 같지만 같은 인스턴스가 아니다.
같은 인스턴스가 아니라는 말은 동일한 메모리에 저장되어있지 않다는 것을 의미한다.
가르키고 있는 주소값이 다르므로 ===는 false를 return 하게된다.
*/
if person1 === person2 {
    print("the two instance are identical")
} else {
    print("the two instance are not identical")
}
```

#### Reference 
https://stackoverflow.com/questions/24002819/difference-between-and
