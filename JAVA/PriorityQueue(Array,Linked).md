# PriorityQueue (ArrayList and LinkedList)



### # PriorityQueue defined by ArrayList

```java
import java.util.ArrayList;
import java.util.List;

public class PriorityArrayList {
    private List<Student> list;

    public PriorityArrayList() {
        this.list = new ArrayList<>();
    }

    // add new elements at the end or array
    public void enqueue(Student newStudent){
        list.add(newStudent);
    }

    
    //compare scores before dequeue
    public List<Student> dequeue(){
        if(list.isEmpty()){
            System.out.println("empty");
            return null;
        }

        Student firstStu = list.get(0);

        for(int i =0; i<list.size(); i++){
            if(list.get(i).compareTo(firstStu)<0){
                firstStu = list.get(i);
                 list.remove(firstStu);
            }
        } return list;
    }

    public Student peek(){
        if(list.isEmpty()){
            System.out.println("empty");
        }
        Student firstStu = list.get(0);

        for(int i =0; i<list.size(); i++){
            if(list.get(i).compareTo(firstStu)<0){
                firstStu = list.get(i);
            }
        }return firstStu;
    }
    
    public int size(){
        return list.size();
    }
    
    public boolean isEmpty(){
       return list.isEmpty();
    }
}
```



### # PriorityQueue defined by LinkedList

```java

import java.util.ArrayList;
import java.util.LinkedList;
import java.util.List;

public class PriorityLinkedList {
    private List<Student> list;

    public PriorityLinkedList() {
        // maintain our list sorted!
        this.list = new LinkedList<>();
    }

    // enqueue (offer)
    public void enqueue(Student newStudent) {
        if (list.size() == 0) {
            list.add(newStudent);
        } else {
            for(int i = 0; i < list.size(); i++) {
                if (newStudent.compareTo(list.get(i)) < 0) {
                    list.add(i, newStudent);
                }
            }
        }
    }

    // dequeueMin (poll)
    public Student dequeueMin() {
        if (list.isEmpty()) {
            System.out.println("The Queue is empty.");
            return null;
        }

        return list.remove(0);
    }

    // peek()
    public Student peek() {
        if (list.isEmpty()) {
            System.out.println("The Queue is empty.");
            return null;
        }

        return list.get(0);
    }

    // size()
    public int size() {
        return this.list.size();
    }

    // isEmpty()
    public boolean isEmpty() {
        return this.list.isEmpty();
    }
}

```



### # Driver

```java
import java.util.PriorityQueue;

public class Client {

    public static void main(String[] args) {

        Student s1 = new Student("Giada", 100);
        Student s2 = new Student("Yukako", 120);
        Student s3 = new Student("Javier", 112);
        Student s4 = new Student("Alex", 121);
        Student s5 = new Student("Kenta", 60);
        Student s6 = new Student("Rei", 61);
        Student s7 = new Student("Charles", 70);
        Student s8 = new Student("Natsumi", 200);

        // PriorityQueue defined based on arrayList
        PriorityArrayList arr = new PriorityArrayList();
        arr.enqueue(s1);
        arr.enqueue(s2);
        arr.enqueue(s3);
        arr.enqueue(s4);
        arr.enqueue(s5);
        arr.enqueue(s6);
        arr.enqueue(s7);
        arr.enqueue(s8);

        System.out.println(arr.size()); //8
        System.out.println(arr.isEmpty()); //false
        System.out.println(arr.peek()); //Kenta
        System.out.println(arr.dequeue()); //[Giada, Yukako, Javier, Alex, Rei, Charles, Natsumi]

        // PriorityQueue defined based on LinkedList
        PriorityLinkedList linked = new PriorityLinkedList();
        linked.enqueue(s1);
        linked.enqueue(s2);
        linked.enqueue(s3);
        linked.enqueue(s4);
        linked.enqueue(s5);
        linked.enqueue(s6);
        linked.enqueue(s7);
        linked.enqueue(s8);

        System.out.println(linked);
        System.out.println(linked.size()); 
        System.out.println(linked.isEmpty());
        System.out.println(linked.peek()); 
        System.out.println(linked.dequeue()); 


        // already defied PriorityQueue class
        PriorityQueue<Student> pq = new PriorityQueue<>();
        pq.offer(s1);
        pq.peek();
        pq.poll();
        pq.size();
        pq.isEmpty();
        pq.clear();

    }
}

```

