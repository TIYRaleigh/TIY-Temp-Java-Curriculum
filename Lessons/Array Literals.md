**Syntax:** `{<item 1>, <item 2>, <item 3>, ....}`

In addition to the syntax we've already discussed, Arrays also have a literal syntax. Here are the previous examples using the literal syntax:

```java
public class Main {

    public static void main(String[] args){

        String[] myStuff = {
            "Paddle game",
            "Remote control",
            "Matches",
            "Lamp",
            "Chair"
        };

        System.out.println(myStuff[3]);
    }
}
```

In this example the literal syntax communicates to Java that we're creating an array of five `String` instances. 

```java
public class Main {

    public static void main(String[] args){

        try {
            Person[] myPeople = {
                    new Person("Doug", 38, 6),
                    new Person("Liz", 38, 5.5),
                    new Person("Collin", 12, 5),
                    new Person("Audrey", 9, 4.8)
            };

            System.out.println(myPeople[3].describe());

        } catch (Exception e){
            System.out.println(e.getMessage());
        }
    }
}
```

This creates an array of 4 `Person` objects.
