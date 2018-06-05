

# # Collections Class



### # sort, shuffle, add Array

```Java

import java.util.*;

public class CollectionsEx {

    public static void main(String[] args) {

        List<Integer> list = new ArrayList<Integer>();
        list.add(2);
        list.add(3);
        list.add(4);
        list.add(5);
        list.add(6);
        list.add(7);

        System.out.println(Collections.max(list)); // 7
        System.out.println(Collections.min(list)); // 2

        Collections.sort(list);
        System.out.println(list);//[2, 3, 4, 5, 6, 7]

        Collections.shuffle(list);
        System.out.println(list);//[3, 5, 6, 2, 4, 7]

        Collections.addAll(list, 1,2);
        System.out.println(list);// [6, 2, 5, 4, 7, 3, 1, 2]

        Integer[] intArr = {33, 44};
        Collections.addAll(list, intArr);
        System.out.println(list);// [6, 2, 5, 4, 7, 3, 1, 2, 33, 44]
    }




}
```
