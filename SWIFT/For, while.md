# # For-in , while, repeat-while



### # for-in

- Similar with for-each

```swift
var integers = [1,2,3]
let people = ["A" : 1, "B" : 2, "C" : 3]

for integer in integers{
    print (integer) // 1 2 3
}

for (name, age) in people {
    print("\(name): \(age)")
//    C: 3
//    B: 2
//    A: 1

}
```



### # while

```swift
while 조건{
    
}

while integers.count > 1{
    integers.removeLast()
}
print(integers) //[1]
```



### # repeat-while

```swift
repeat {
    integers.removeLast()
} while integers.count > 0
```

