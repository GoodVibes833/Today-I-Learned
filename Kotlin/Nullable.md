# # Nullable



### # topics

- (elvis operator)!

  

```kotlin
fun main(args: Array<String>) {
    // String?
    // Unwrapping
    var name: String? = null

    var unwrapped:Int = if (name != null) name.length else 0

    // ?: (elvis operator)
    var unwrapped2:Int = name?.length ?: 0

    // ? operator : Safe call (unwrap) ?
    var unwrapped3:Int? = name?.length
//    var addTen = unwrapped3!! + 10

    // !! operator : Force unwrap!!
    var unwrapped4:Int = name!!.length // NullPointerException if null


}
```

