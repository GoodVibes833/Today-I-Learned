## Time, Space complexity with Big-O Notation



## # Simple definition

```
Time Complexity : algorithm running time
Space Complexity : algorithm usage of memory
	* Time Complexity is more importance because of high performance of memory.
```



## # Time Complexity

```Java
EX1)
public void function(int a, n)
{	 int i=0, j=0;                                    1
     for (i = 0 ; i < n-1 ; i++)                      n            
     for(j=i+1; j<n ; j++)                     (n-1) * n       
     if (a[i] == a[j]) a[j] = 0 ;            (n-1) * (n-1)
}
```

Excution time : 2n²-2n+2

Time Complexity : O(n²)

​	**# asymptotic notation** : only consider **leading coefficient**





```Java
Ex2)
public int function2(int a[], int size, int key)  {
   int i = 0;                                         1
   for (i = 0; i < size; i++)                      size + 1
       if(a[i] == key)                               size
       return i;                                      1
   return -1;                                         1
}
```

Excution time : 2size + 4 

Time Complexity : O(N)



## # Space Complexity



```java
Ex1)
float abc(float a, float b, float c){
     return(a + b + b*c + (a + b - c)/(a + b) + 4.0);
}
```

Space Complexity : 0



```java
Ex2)
float Sum(float a[], int n){
     float s = 0.0;
     for(int i = 1; i < = n; i++)
          s += a[i];
     return s;
}
```

Space Complexity : n+3 (a[] + n s i)





## # Big-O Notation

```
--> worse
O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2ⁿ) < O(n!) < O(nⁿ)
```

![img](http://cfile28.uf.tistory.com/image/260F4850559AB6672C45F1)





