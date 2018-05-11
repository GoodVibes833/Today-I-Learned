# LinkedList Concept



### # Code

```java
public class Node {
    private String data;
    private Node next;

    public Node(String data, Node next) {
        this.data = data;
        this.next = next;
    }

    public Node getNext() {
        return next;
    }

    public void setNext(Node next) {
        this.next = next;
    }

    @Override
    public String toString() {
        return data;
    }


    public static void addAt(Node root, int i, Node newNode) {
        if (i == 0) {
            newNode.setNext(root);
            return;
        }
        Node prev = getAt(root, i-1);
        newNode.setNext(prev.getNext());
        prev.setNext(newNode);

    }

    public static Node getAt(Node root, int i) {
        if (i == 0) {
            return root;
        }
        Node result = root;
        int count = 0;
        while (count < i) {
            result = result.getNext();
            count++;
        }
        return result;
    }


   
    public static void main(String[] args) {
        Node n3 = new Node("Sue", null);
        Node n2 = new Node("Victor", n3);
        Node root = new Node("Bianca", n2);
        System.out.println(getAt(root, 1)); //Victor



        addAt(root, 1, new Node("Derrick", null));
        System.out.println(getAt(root, 1)); // Derrick
        System.out.println(getAt(root,2)); // Victor
    }
}
```

