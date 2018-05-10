# File in & out (Byte Stream)

    // Serialization: representing an object as a sequence of bytes that includes
    //                the object's data and its type information.
    
    // To read an entire object from or write an entire object to a file.
    // After a serialized object has been written into a file, it can be read from
    // the file and deserialized to recreate the object in the memory.
    
    // Classes: ObjectInputStream & ObjectOutputStream (java.io)
    
    // Objects of classes that implement interface Serializable can be serialized
    // and deserialized with ObjectInputStream & ObjectOutputStream.
    // Interface Serializable is a tagging interface.
    // - it doesn't contain any methods.


### # Model

```java
import java.io.Serializable;

public class SuperHero implements Serializable {

    private int id;
    private String name;
    private int age;
    private String superpower;

    public SuperHero(int id, String name, int age, String superpower) {
        this.id = id;
        this.name = name;
        this.age = age;
        this.superpower = superpower;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getSuperpower() {
        return superpower;
    }

    public void setSuperpower(String superpower) {
        this.superpower = superpower;
    }

    @Override
    public String toString() {
        return "ID: " + id + "\n" + "NAME: " + name + "\n"
                + "AGE: " + age + "\n" + "SUPERPOWER: " + superpower + "\n";
    }
}

```



### # Controller

```java
import java.io.*;
import java.nio.file.Files;
import java.nio.file.Paths;
import java.util.NoSuchElementException;
import java.util.Scanner;

public class SequentialFileIO {


    private static ObjectOutputStream output;
    private static ObjectInputStream input;

    public static void openFileToRead() {
        try {
            input = new ObjectInputStream(Files.newInputStream(Paths.get("SuperHeros.ser")));

        } catch (IOException e) {
            System.err.println("Error Opening file. Terminating...");
            System.exit(1);
        }
    }

    public static void readContent() {
        try {
            while (true) { // read all objects
                SuperHero hero = (SuperHero) input.readObject();
                System.out.println(hero);
            }
        } catch (EOFException e) {
            System.out.println("No more records.");

        } catch (IOException e) {
            System.err.println("Error reading from file. Terminating...");
            System.exit(1);

        } catch (ClassNotFoundException e) {
            System.err.println("Invalid object type. Terminating...");
            System.exit(1);

        }
    }

    public static void openFileToWrite() {
        try {
            output = new ObjectOutputStream(Files.newOutputStream(Paths.get("SuperHeros.ser")));

        } catch (IOException e) {
            System.err.println("Error Opening file. Terminating...");
            System.exit(1);
        }
    }

    public static void writeContent() {
        Scanner scan = new Scanner(System.in);
        System.out.println("ID, NAME, AGE, SUPERPOWER: ");
        while (scan.hasNext()) { // loop until end-of-file indicator
            try {

                SuperHero hero = new SuperHero(scan.nextInt(),
                        scan.next(), scan.nextInt(), scan.next());

                // serialize object and write into file
                output.writeObject(hero);

            } catch (IOException e) {
                System.err.println("Error Writing to file. Terminating...");
                System.exit(1);
            } catch (NoSuchElementException e) {
                System.err.println("Invalid input. Please try again.");
                scan.nextLine();
            }
        }

    }

    public static void closeFile() {
        try {
            if (output != null) {
                output.close();
            }
            if (input != null) {
                input.close();
            }
        } catch (IOException e) {
            System.err.println("Error closing file. Terminating...");
            System.exit(1);
        }
    }


    public static void main(String[] args) {

//        MyFileIO.openFileToWriteInfo("students/Alex.txt");
//        MyFileIO.addInfo();
//        MyFileIO.closeFile();
//        MyFileIO.openFileToReadInfo("students/Alex.txt");
//        MyFileIO.readInfo();
//        MyFileIO.closeFile();
        SequentialFileIO.openFileToWrite();
        SequentialFileIO.writeContent();

        SequentialFileIO.openFileToRead();
        SequentialFileIO.readContent();
        SequentialFileIO.closeFile();
    }
}

```

