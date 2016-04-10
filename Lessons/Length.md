**Syntax:** `<array>.length`

Arrays are objects. Objects can have properties. The only property that arrays expose is `length`. To find out how many elements an array can hold, you use its `length` property. 

```java
public class Main {

    public static void main(String[] args){

        try {
            Person[] myPeople = new Person[4];

            myPeople[0] = new Person("Doug", 38, 6);
            myPeople[1] = new Person("Liz", 38, 5.5);
            myPeople[2] = new Person("Collin", 12, 5);
            myPeople[3] = new Person("Audrey", 9, 4.8);

            System.out.println(myPeople.length);

        } catch (Exception e){
            System.out.println(e.toString());
        }
    }
}
```

This code uses `System.out.println(myPeople.length)` to print out the number of elements the array can hold:

> 4

The `length` property is read-only. You can't change the size of an array by setting the `length` property. This is inconsistent with the rest of Java. I can't think of another case of a read-only property.
