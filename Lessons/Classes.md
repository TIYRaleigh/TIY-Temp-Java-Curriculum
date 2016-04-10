In programming, we model the world and abstract concepts using classes. A _class_ is a code that describes a type of _object_, its properties, and what it can do. 

A class is like a blueprint for a house. A blueprint is a detailed plan for building a house. It shows the placement and measurements of all rooms, where fixtures will be placed, where utilities will be run, how the roof will be assembled, and much more. 

![House_Plans_(Blueprints).jpg](https://tiy-learn-content.s3.amazonaws.com/b9067c2c-House_Plans_%28Blueprints%29.jpg)

An object is like a house you built using a blueprint. You can make many houses using the same blueprint, but each house is distinct.

![what a house might look like.jpg](https://tiy-learn-content.s3.amazonaws.com/70364e47-what%20a%20house%20might%20look%20like.jpg)

Remember our original hello world program?

```java
public class Example {
    public static void main(String[] args){
        System.out.println("Hello World!");
    }
}
```

In this example we wrote a class named `Example`. In fact, the entire file  represents a class. In Java, a file maps to a class. This is why we must name the file our `Example` class is in `Example.java`. 

Classes are pervasive in Java. The example above uses several classes other than the `Example` class itself.

* `String[]` - This is actually two classes, String and Array.
* `System` - The system class. It has system-specific behaviors and properties.
* `"Hello World!"` - Another String.
* `Object` - All classes are derived from this class.

<!-- todo: consider digging into the String class to see how many classes it uses, etc. Can this even be done? I imagine so. -->
