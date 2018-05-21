# Collection Type(Array, Dictionary, Set)

### # Array : ordered, has index 

### # Dictionary : key and value 

### # Set : not ordered, unique member 



### # Array

```swift
var integers: Array<Int> = Array<Int>();

//Same as
// var integers: Array<Int> = [Int]()
// var integers: Array<Int> = []
// var integers: [Int] = Array<Int>()
// var integers: [Int] = [Int]()
// var integers: [Int] = []
// var integers = [Int]()

//add
integers.append(1)
integers.append(3)
integers.append(5)
integers.append(100)
//integers.append(100.1) not int

print(integers) //[1,3,5, 100]

//contains
print(integers.contains(100)) //true
print(integers.contains(99))  //false

//replace
integers[0]=99
print(integers) //[99, 3, 5, 100]

//remove
integers.remove(at: 1)
integers.removeLast()
integers.removeFirst()
integers.removeAll()


//count
print(integers.count) //0


//integers[5] ---> out of index

//immutable array : can not add or remove
let immutableArray = [1,2,3]

```



### # 2D Array

```swift
//declare

var arr = [[Int]]() 
var arr: [[Int]] = [] 
let points: [[Int]] = [[10, 20], [30, 40]]
var arr = Array(repeating: Array(repeating: 0, count: 2), count: 3)
 //2 col x 3 rows

//0 0
//0 0
//0 0

// add data
arr[0][0] = 12
arr[1] = [123, 456, 789]

//12  0 
//123 456 789
// 0  0

arr[0] += 234

//12  0   234
//123 456 789
//0   0

//count

var rows = arr.count
var columns = arr[0].count

```



### # Dictionary

```swift
var anyDictionary: Dictionary<String,Any> = [String:Any]()

//same as
// var anyDictionary: Dictionary <String, Any> = Dictionary<String, Any>()
// var anyDictionary: Dictionary <String, Any> = [:]
// var anyDictionary: [String: Any] = Dictionary<String, Any>()
// var anyDictionary: [String: Any] = [String: Any]()
// var anyDictionary: [String: Any] = [:]
// var anyDictionary = [String: Any]()

anyDictionary["somekey"]="value"
anyDictionary["anotherKey"]=100
print(anyDictionary) // ["anotherKey": 100, "somekey": "value"]

//replace
anyDictionary["somekey"]="dictionary"
print(anyDictionary) // ["anotherKey": 100, "somekey": "dictionary"]

//romove
anyDictionary.removeValue(forKey: "anotherKey")
anyDictionary["someKey"]=nil

//immutable
let emptyDictionary:[String:String]=[:]
let initializedDictionary:[String:String]=["name":"Alex","gender":"male"]

//emptyDictionary["key"]="value" --> can not change

//let someValue: String = initializedDictionary["name"]
// --> it needs "optional" because name's value can be nil
```



### # Set

```swift
//no simplified version
var integerSet: Set<Int> = Set<Int>()

integerSet.insert(1)
integerSet.insert(2)
integerSet.insert(3)
integerSet.insert(3)

print(integerSet) // {1,2,3}


print(integerSet.contains(1)) //true
print(integerSet.contains(4)) //false

integerSet.remove(3) //{1,2}
integerSet.removeFirst(); //{2}

print(integerSet.count) //1


//use cases
let setA: Set<Int> = [1,2,3,4,5]
let setB: Set<Int> = [3,4,5,6,7]

//union
let union: Set<Int> = setA.union(setB)
print(union) //[2,4,5,6,7,3,1]

let sortedUnion:[Int] = union.sorted()
print(sortedUnion) //[1,2,3,4,5,6,7]

//intersection
let intersection: Set<Int> = setA.intersection(setB)
print(integerSet) //[3,4,5]

//subtracting
let subtracting: Set<Int> = setA.subtracting(setB)
print(subtracting) //[1,2]
```



