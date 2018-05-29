## Greedy Algorithms



### # What is Greedy Algorithms ?

```
Always makes the choice that seems to be the best at that moment.
* Fast, but does not return the best results.
```



### # Examples

```
1. Kruskal Algorithm
2. Prim Algorithm
3. Dijkstra Algorithm
4. Giving changes
5. Task Scheduling Problem
```



### 1. Kruskal Algorithm

```
Select small value of edges among all edges.(except for cycle case)
```

![img](http://cfile26.uf.tistory.com/image/2617CA4057755ADC07D005)

 

### 2. Prim Algorithm

```
From a vertex(point), select smallest value of edge. (except for cycle case)
```

 ![img](http://cfile5.uf.tistory.com/image/236CA03757755D3705E638)



### 3. Dijkstra Algorithm

```
Find shortest path by selecting smallest numbers
```

 ![img](http://cfile9.uf.tistory.com/image/231DF94157755EFC0A84FD)



### 4. Giving changes

```Java
int[] array = {500,400,100,50,10,5,1};

//ex) when we get 800 as a changes, we should get 400 x 2.
// but it choose 500, 100 x3
```



### 5. Task Scheduling Problem

```
To run a task with a minimum waiting time when we already know running time(burst time)
--> choose a task which has minimum burst time
```

![img](http://cfile4.uf.tistory.com/image/277AFC4F5775651D08B774)