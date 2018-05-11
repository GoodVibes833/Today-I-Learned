# # Set, Map



### # Set

```java
import java.util.HashSet;
import java.util.Set;

public class SetDemo {
    public static void main(String[] args) {

        Set<Integer> mySet = new HashSet<>();
        mySet.add(2);
        mySet.add(3);
        mySet.add(4);
        mySet.add(5);
        mySet.add(1);
        mySet.add(1); //added the same element

        System.out.println(mySet);			// [1, 2, 3, 4, 5]
        System.out.println(mySet.size()); 	//5
        
        mySet.add(1); //added the same element
        
        System.out.println(mySet);			// [1, 2, 3, 4, 5]
        System.out.println(mySet.size()); 	//5
    }

}
```



### # Map

```java
package MapAndSet;

import java.util.HashMap;
import java.util.Map;

public class MapDemo {
    public static void main(String[] args) {
        Map<String,Integer> myMap = new HashMap<>();
        myMap.put("a",11);
        myMap.put("b",22);
        myMap.put("c",33);
        myMap.put("a",11); // not added when add the same kye

        System.out.println(myMap); 					//{a=11, b=22, c=33}
        System.out.println(myMap.size()); 			//3
        System.out.println(myMap.get("a")); 		//11
        System.out.println(myMap.remove("c"));		//33
        System.out.println(myMap);					//{a=11, b=22}
        System.out.println(myMap.containsKey("a")); //True
        System.out.println(myMap.containsValue(11));//True

    }
}
```

