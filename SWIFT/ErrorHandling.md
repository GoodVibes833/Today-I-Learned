# Error(do-catch, try)



### # express errors : define different error cases  

```swift
enum VendingMachineError: Error{
    case invalidInput
    case insufficientFunds(moneyNeeded: Int)
    case outOfStock
}
```



### # throw error : pass errors 

```swift
class VendingMachine{
    let itemPrice: Int = 100
    var itemCount: Int = 5
    var deposited: Int = 0
    
    func receiveMoney(_ money: Int) throws{
        // money < 0 --> throw error (guard: quick exix)
        guard money > 0 else{
            throw VendingMachineError.invalidInput
        }
        // if no error
        self.deposited += money
        print("deposited \(money)")
    }
    
    func vend(numberOfItems numberOfItemsToVend: Int) throws -> String {
        
        //case1 :when numberOfItemsToVend <0
        guard numberOfItemsToVend > 0 else {
            throw VendingMachineError.invalidInput
        }
        
        //case2 
        guard numberOfItemsToVend * itemPrice <= deposited else {
            let moneyNeeded: Int
            moneyNeeded = numberOfItemsToVend * itemPrice - deposited
            throw VendingMachineError.insufficientFunds(moneyNeeded: moneyNeeded)
        }
        
        //case3 : buy < needed --> error
        guard itemCount >= numberOfItemsToVend else {
            throw VendingMachineError.outOfStock
        }
        
        let totalPrice = numberOfItemsToVend * itemPrice
        self.deposited -= totalPrice
        self.itemCount -= numberOfItemsToVend
        
        return "offered \(numberOfItemsToVend)"
    
    }
}
```





### # do-Catch : handling errors 

```swift
let machine: VendingMachine = VendingMachine()
var result: String?


// Use try to call throws function
// do - catch

do{// try this method
    try machine.receiveMoney(0)
}// if there is an error, catch!
catch VendingMachineError.invalidInput{
    print("wrong input")
}catch VendingMachineError.insufficientFunds(let moneyNeeded){
    print("\(moneyNeeded) is insufficient")
}catch VendingMachineError.outOfStock{
    print("out of stock")
}



// Use do-catch with swich

do{
    try machine.receiveMoney(300)
}catch /*(let error --> ommitable)*/{
    switch error {
    case VendingMachineError.invalidInput:
        print("wrong input")
    case VendingMachineError.insufficientFunds(let moneyNeeded):
        print("\(moneyNeeded) is insufficient")
    case VendingMachineError.outOfStock:
            print("out of stock")
    default:
        print("unknown error")
    }
}
// if it doesn't need to be specified
do{
    result = try machine.vend(numberOfItems: 4)
} catch{
    print(error)
}
```





### # try?, try! : without using do-catch 

```swift
// try? : without using do-catch, if there is an error, it returns nil

result = try? machine.vend(numberOfItems: 2) //optional(offered 2)
result = try? machine.vend(numberOfItems: 6) //nil


// try! : when you are sure that there is no error
// it returns result value, not optional value.
// However, if there is an error, it make run time error

result = try! machine.vend(numberOfItems: 1) //offered 1
//result = try! machine.vend(numberOfItems: 6) //error
```

