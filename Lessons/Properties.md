**Syntax:** `<access modifier> <variable definition>`

Properties are variables that belong to a class. This is the data that defines your object. Properties are defined within the curly braces that define a class' body. Typically these are added immediately after the opening curly brace, at the very top of the class' body. You can define as many properties as you wish, but they must all have different names.

One property that all real people have is a name. Let's make our programatic model of a person have a name.

```java
public class Person {
    // this is the person's name
    public String name = "";
}
```

This code adds a single `String` property named `name` to the `Person` class. Because we set the access modifier to public, any other code can get or set the name of a Person object.

```java
public class Main {
    public static void main(String[] args){
        Person doug = new Person();
        doug.name = "Doug";

        Person liz = new Person();
        liz.name = "Liz";

        System.out.println(doug.name);
        System.out.println(liz.name);
    }

}
```

In this example we're again creating two different instances of the `People` class and assigning them to the variables `doug` and `liz`. We then set the `name` property for that instance, which is the property we just defined. Take note of the `.` "dot" character. This dot tells Java to get the value of the `name` property from the specific `Person` instance in the variable `doug`.

A person is not defined by a single property. I am not just my name. So, let's add a few more properties to our Person class. I've also added some comments to help explain what the code.

```java
/**
 * The Person class represents a person.
 */
public class Person {
    /**
     * The person's name.
     */
    public String name = "";

    /**
     * The person's age
     */
    public int age = 0;

    /**
     * The person's height
     */
    public double height = 0;   
}
```

Now we have more properties we can use.

```java
public class Main {
    public static void main(String[] args){

        // create a Person for Doug
        Person doug = new Person();
        doug.name = "Doug";
        doug.age = 38;
        doug.height = 6.0;

        // create a Person for Liz
        Person liz = new Person();
        liz.name = "Liz";
        liz.age = 38;
        liz.height = 5.5;

        // Print details to the console
        System.out.println(doug.name + " is " + doug.age + " years old and " + doug.height + " feet tall.");
        System.out.println(liz.name + " is " + liz.age + " years old and " + liz.height + " feet tall.");
    }

}
```

This code should be fairly clear. As before, we're creating two Person objects and setting their properties. Also, outputting more information about each Person instances to the console than previously.
