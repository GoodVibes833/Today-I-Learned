# # Lazy



### # it is a property which is created when it is refered.

```swift

class SomeMonth {
    let month: Int
    lazy var nextMonth: SomeMonth = self.getNextmonth()
    
    init(month: Int) {
        self.month = month
    }
    
    func getNextmonth() -> SomeMonth {
        print("Getting Next Month")
        return SomeMonth(month: self.month + 1)
    }
}



let sm = SomeMonth(month: 2)
sm.nextMonth    // 1
sm.nextMonth    // 2
sm.nextMonth    // 3

```

- it refers nextMonth 3 times, but print "Getting Next Year" just one time
- //1 : first referal, return "Getting Next Month"  and keep the value
- //2, 3 : no return
- acting like Cache type

