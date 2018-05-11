# # Casting errors



### # Parents

```java
public class ParentsDemo {
    public void eat(){
        System.out.println("eat");
    }}
```



### # Child

```java
public class ChildDemo extends ParentsDemo {
    public void learn(){
        System.out.println("learn");
    }}
```



### # Driver

```java
public class Driver {
    public static void main(String[] args) {

        ParentsDemo pa1 = new ParentsDemo();
        pa1.eat(); //eat

        ChildDemo ch1 = new ChildDemo();
        ch1.learn(); //learn
        ch1.eat(); //eat  :  parent's method

        
// # parents type
        ParentsDemo pa2 = new ChildDemo(); 
        
        // upcasting
        pa2.eat(); //eat

        //pa2.learn(); ------> compile error
        // parents don't have learn method, need to cast-down
        ((ChildDemo) pa2).learn(); //learn

        
// # Child type 
//      ChildDemo ch2 =  new ParentsDemo(); ------> compile error
		// Parents can not be a child, need to cast-down
        ChildDemo ch2 = (ChildDemo) new ParentsDemo();
        // parents can be down casted to child but can not use child method
        
        ch2.eat();// -----> runtime error
        ch2.learn(); //-----> runtime error

    }
}
```



### 