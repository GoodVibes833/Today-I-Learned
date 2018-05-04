# Extension

### is a function that add new method, property... to type(struct, class, enum, protocol) 



### Format

```swift
// extension String{}

// also able to conform protocols
// extension String : protocol1, protocol2

```





### Properties and method 

```swift
extension Int{
    
    //Operation Properties
    var isEven: Bool{
        return self % 2 == 0
    }
    var isOdd: Bool{
        return self % 2 == 1
    }
    
    //method
    func multiply(by n: Int) -> Int {
        return self * n
    } 
}

print(1.isOdd) //t
print(2.isOdd) //f

var num: Int = 3
print(num.isEven) //f
print(3.multiply(by: 2)) //6
```





### # initializer 

```swift
extension String{
   
    init(intTypeNum: Int){
        self = "\(intTypeNum)"
        print(self)
    }
    init(doubleTypeNum: Double){
        self = "\(doubleTypeNum)"
        print(self)
    }
}
let StringFromInt: String = String(intTypeNum: 123)
let StringFromDouble: String = String(doubleTypeNum: 123.1)
```

