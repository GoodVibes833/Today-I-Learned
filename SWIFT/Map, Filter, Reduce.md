# map, filter, reduce (higher order function) 



### # map : applied to all elements   

```swift
let numbers: [Int] = [0,1,2,3,4]
var doubledNumbers: [Int]
var strings: [String]


//1. for

doubledNumbers = [Int]()
strings = [String]()

for number in numbers {
    doubledNumbers.append(number * 2)
    strings.append("\(number)")
}
print(doubledNumbers)//[0, 2, 4, 6, 8]
print(strings)       //["0", "1", "2", "3", "4"]


//2. map method

doubledNumbers = numbers.map({(number: Int) -> Int in
    return number * 2
})
strings = numbers.map({(number: Int) -> String in
    return "\(number)"
})
print(doubledNumbers)//[0, 2, 4, 6, 8]
print(strings)       //["0", "1", "2", "3", "4"]



//2-1 using closer

doubledNumbers = numbers.map{$0 * 2}
print(doubledNumbers) //[0, 2, 4, 6, 8]

    // $0 indicates first parameter($0, $1, ..)
```



### # filter : select some elements when it meets a condition   

```swift
// 1.for

var filtered:[Int] = [Int]()

for number in numbers{
    if number % 2 == 0{
    filtered.append(number)
    }}
print(filtered)     //[0, 2, 4]



//2. filter method (return type: bool)

var evenNumbers:[Int] = numbers.filter{(number: Int)-> Bool in
    return number % 2 == 0
}
print(evenNumbers) //[0, 2, 4]



//2-1 using closer

evenNumbers = numbers.filter{
    $0 % 2 == 0}
print(evenNumbers) //[0, 2, 4]
```



### # reduce : make contents to one   

```swift
let someNumbers: [Int] = [2, 8, 15]

//1. for

var result: Int = 0
for num in someNumbers{
    result += num
}
print(result) //25


//2. reduce method

var sum: Int = someNumbers.reduce(0, {(first: Int, second: Int) -> Int in
    print("\(first) + \(second)")
//    0 + 2
//    2 + 8
//    10 + 15

    result = first + second
    return first + second
})
print(result)   //25

var subtract: Int = someNumbers.reduce(0, { (first: Int, second: Int) -> Int in
    print("\(first) - \(second)")
    
    result = first - second
    return first - second
})
print(result)   //-25


// 2-1 using closer
sum = someNumbers.reduce(3){$0 + $1 }
print(sum) //28

```

