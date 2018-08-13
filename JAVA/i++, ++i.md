# i++ vs ++i



### # Code

```Java
public class increase {

    public static void main(String[] args) {
        int a = 0;
        int b = 0;
        
        for(int i=0; i<3;){ //0 1 2
            a = i++; // 0 2
            b = ++i; // 2 4
            System.out.println(a); // 0 2
            System.out.println(b); // 2 4
        }
}
}
```
