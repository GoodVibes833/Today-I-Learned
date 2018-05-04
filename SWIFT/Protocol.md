# Protocol



### Protocol is similar with Interface in JAVA

```Swift

protocol Talkable{

    //properties
    var topic: String{ get set }
    var language: String { get }

    
    //method
    func talk()
    

    //initializer
    init(topic: String, language: String)
}

```



### Client

```Swift
struct Person: Talkable{
    var topic: String
    var language: String
    
    
//    var subject = " "
//    var topic: String{
//        set{
//            self.subject = newValue
//        }
//        get{
//            return self.subject
//        }
//    }
//    var language: String{
//        return "English"
//    }
    
    func talk() {
        print("talk about (topic) in (language)")
    }
    
    init(topic: String, language: String) {
        self.topic = topic
        self.language = language
    }
}
```



### able to Inherentance

```Swift

protocol Readable{
    func read()
}
protocol Writable{
    func write()
}
protocol ReadSpeakable: Readable{
    func speak()
    //no need read(), but still reqire to be implemented
}
protocol ReadWriteSpeakable: Readable, Writable{
    func speak()
    //no need read(), write()
}
struct SomeStruct: ReadWriteSpeakable{
    
    func speak() {
        print("speak")
    }
    func read() {
        print("read")
    }
    func write() {
        print("write")
    }
}
```



### inherantance and protocol together

```Swift
class SuperClass: Readable{
    func read(){
        print("read")
}
}
//            : inherantance, protocol 1, protocol 2
class SubClass: SuperClass, Writable, ReadSpeakable{
    func write() {
        print("write")
    }
    func speak() {
        print("speak")
    }
}

```



### is, as

```Swift

let sup: SuperClass = SuperClass()
let sub: SubClass = SubClass()
var someAny: Any = sup
someAny is Readable //true
someAny is Writable //false
someAny = sub
someAny is Readable //true
someAny is Writable //true
someAny = sup
if let someReadable: Readable = someAny as? Readable{
    someReadable.read()
    //read, protocol type Readable <- down casted someAny
}
//if let someReadSpeakable: ReadSpeakable = someAny as? Readable{
//    someReadSpeakable.read()
//}
someAny = sub
if let someReadable: Readable = someAny as? Readable{
    someReadable.read()
    //read
}
if let someReadable: Writable = someAny as? Writable {
    someReadable.write()
    //write
}
```

