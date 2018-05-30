# # class & subclass



### # Ex1

```kotlin
package Example

// instance var, getter, setter, toString, equals, hashCode, copy
data class User(var username: String, var id: Int, var first: String, var last: String)

// enum (associated value)
enum class Color(var rgb: Int) {
    RED(0xFF0000),
    GREEN(0x00FF00),
    BLUE(0x0000FF)
}

// Sealed
sealed class Car {

}
class Toyota: Car() {

}
class Honda: Car() {

}

fun topSellingCar(car: Car): String {
    return when (car) {
        is Toyota -> "Camry"
        is Honda -> "Civic"
    }
}
```









### # Ex2-1

```kotlin
package Example

open class Aquarium(var length: Int = 100, var width: Int = 100, var height: Int = 100) {
    // nothing gets stored in the memory
    var volume: Int // computed property
        get() {
            return length * width * height
        }
        private set(value) {
            height = (value * 1000) / (width * length)
        }

    open var water = volume * 0.9

    // secondary constructor - always call primary, this()
    constructor(numberOfFish: Int): this(200, 200, 200) {
        val water = numberOfFish * 2000 // local var
        val tank = water + water * 0.1  // local var
        height = (tank / (length * width)).toInt()
    }

    override fun toString(): String {
        return "Aquarium $length $height $width"
    }

    override fun equals(other: Any?): Boolean {
        return height == (other as Aquarium).height
    }
}

class TowerTank(): Aquarium() {
    override var water: Double
        get() = super.water * 1.1
        set(value) {}
}


class Tower(): Aquarium() {
    override var water: Double
        get() = super.water * 1.1
        set(value) {}
}

```



### # Ex2-2 (MAIN)

```kotlin
package Example

fun main(args: Array<String>) {
    val myAquarium = Aquarium(100, 100 , 50)
    val vanAquarium = Aquarium(100)
    println(myAquarium)

    var towerTank = TowerTank()
    println(towerTank.length)
    println(towerTank.width)
    println(towerTank.height)
    println(towerTank.water)

    println(myAquarium.length)
    println(myAquarium.width)
    println(myAquarium.height)

    println("Volume? ${myAquarium.volume}")
    // myAquarium.volume = 100 // private
    // volume = length * width * height
    println("Water Amount? ${myAquarium.water}")

    var u1 = User("rei1234", 1, "Rei", "Toyota")
    var u2 = User("rei1234", 1, "Rei", "Suzuki")
    var u3 = u2.copy(last = "Honda")
    println(u1)
    println(u1 == u2)

}
```

