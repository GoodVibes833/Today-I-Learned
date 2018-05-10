# Class

### # reference type , mutiple inherantance X 



### # Sample

```swift
class Sample{
    var mutableProperty: Int = 100
    let immutableProperty: Int = 100
    static var typeProperty: Int = 100
    
    func instanceMethod(){
        print("Instance method")
    }
    
    // type method : override X
    static func typeMethod(){
        print("type method - static")
    }
    
    // type moethod : override O
    class func classMethod(){
        print("type method - class")
    }
    
}

var mutableReference: Sample = Sample()
mutableReference.mutableProperty = 200
//mutableReference.immutableProperty = 200 --> "let"

let immutableReference: Sample = Sample()
immutableReference.mutableProperty = 200 // still possible to change property values
//immutableReference.immutableProperty = 200

// able to call type property, method without init
Sample.typeProperty = 300
Sample.typeMethod()
```





### # Ex) Student

```swift
class Student{
    var name: String = "unknown"
    var `class`: String = "swift"
    
    //type method
    class func selfIntroduction(){
        print("student")
    }
    
    //instance method
    func selfIntroduce(){
        print("I am \(name), \(self.class)")
    }
}

Student.selfIntroduction() // student

var Alex: Student = Student()
Alex.name = "Alex"
Alex.class = "Java"
Alex.selfIntroduce() // I am Alex, Java

let Han: Student = Student()
Han.name = "Han"
Han.selfIntroduce() // I am Han, swift

```

