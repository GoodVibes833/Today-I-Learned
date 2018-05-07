# STRUCT : value type



### # struct format

```swift
struct Sample{
    
	var mutableProperty: Int = 100
	let immutableProperty: Int = 100
	static var typeProperty: Int = 100

	func instanceMethod(){
	print("instance method")
	}

	static func typeMethod(){
	print("type method")
	}
}
```



### # client1(var)

```swift
var mutable: Sample = Sample()

mutable.mutableProperty=200

//mutable.immutableProperty =200
// error -> immutable
```



### # client2(let)

```swift
let immutable: Sample = Sample()

//immutable.mutable = 200
// error -> immutavle instance
```

