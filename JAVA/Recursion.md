# # Recursion



### # Simple example

```java
package Recursion;

public class Recursion {

    public static int factorial(int n) {
     int result = 1;
     for (int i = 1; i <= n; i++) {
         result *= i;
        }return result;
    }


    public static int factorial_recursion(int n){
        int result;
        if(n == 1){
            return  1;
        }
        result = n * factorial_recursion(n-1);
        return result;
    }


    public static void main(String[] args) {
        System.out.println(factorial(4)); //24
        System.out.println(factorial_recursion(4)); //24
    }
}
```

