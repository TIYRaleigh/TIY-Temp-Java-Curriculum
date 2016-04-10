**Syntax:**

```java
<access modifier> <return type> <method name>(<method arguments>){
	<method body>
}
```

There are two defining characteristics of a programatic object:

* It holds its own data
* It has methods that can interact with that data

So far our Person class only holds data, but it doesn't do anything with that data. It's not uncommon to write a class that only holds data. For that matter, you might reasonably have a class that has methods, but no data. Because we are trying to model the real world with our Person class, we should imbue it some behaviors.

You give classes the ability to "do stuff" (not a technical term) using methods. A _method_ is a chunk of code in a class that does stuff. For example, it could perform a calculation, store data in properties, write a file to disk, or anything else.

There are several words in programming that are roughly synonymous with `method`: function, subprocedure, doohicky. In Java the correct term is method and that is the word we will use in class. 

Methods are defined anywhere within the curly braces that define a class' body. Typically these are added after constructors. You can have as many methods as you wish. By convention, method names start with a lower case letter just like variable names. Method names should express what the method does. You can have multiple methods with the same name, but they must accept different arguments. This is called _method overloading_.

Real people in the physical world give high fives to each other. Let's model that in our `Person` class. Let's declare that a Person can receive high five.

```java
/**
 * The Person class represents a person.
 */
public class Person {
    /**
     * The Person's name
     */
    public String name = "";

    /**
     * The Person's age
     */
    public int age = 0;

    /**
     * The Person's height
     */
    public double height = 0;

    /**
     * Used to count how many high fives this Person has received.
     */
    private int highFivesReceived = 0;

    /**
     * Create a Person and set the default values;
     * @param name The person's name
     * @param age The person's age
     * @param height The person's height
     */
    public Person(String name, int age, double height){
        this.name = name;
        this.age = age;
        this.height = height;
    }

    /**
     * Allows a person to receive a high five.
     */
    public void receiveHighFive(){
        this.highFivesReceived++;
    }

}
```

This code has two significant updates. Firstly, we added a new property:

```java
private int highFivesReceived = 0;
```

This is similar to the other properties we already had. The difference is that the access modifier has been set to `private`. The `private` access modifier tells Java that no code other than the Person class itself can set or update the highFivesReceived property. 

**Remember:** Only you can touch your privates.

<!-- todo: demo this in class -->

The other significant bit is the `receiveHighFive()` method itself:

```java
public void receiveHighFive(){
	this.highFivesReceived++;
}
```

This method has a `public` access modifier. This means that any code can invoke this method. The `void` keyword means that this function doesn't return anything to us when we invoke it. The name of the method is `receiveHighFive`. Because the parenthesis are empty, the method doesn't accept any arguments. This means we can't provide any data when the method is invoked. Finally, the body of the method is `this.highFivesReceived++`, which increments the Person class' `highFivesReceived` property.

We can invoke this method as follows:

```java
public class Main {
    public static void main(String[] args){

        // create a Person for Doug
        Person doug = new Person("Doug", 38, 6.0);
        doug.receiveHighFive();

        // create a Person for Liz
        Person liz = new Person("Liz", 38, 5.5);

        // Print details to the console
        System.out.println(doug.name + " is " + doug.age + " years old and " + doug.height + " feet tall.");
        System.out.println(liz.name + " is " + liz.age + " years old and " + liz.height + " feet tall.");
    }

}
```

This shows the `receiveHighFive()` method being invoked on the `doug` instance of the `Person` class. However, when we run this code we can't tell that anything has changed at all. There's really no way we can use this fact in our program yet. We can't simply update our `System.out.println()` expression in the `Main` class. This is because the `Main` class can't access the `Person` class' private `highFivesReceived` property.

This presents us with a bit of a conundrum. If we make the `highFivesReceived` property public, a rouge programmer could easily set this to any value they want. But, if we keep the property private, only the Person itself knows. If only there were an elegant solution to this problem...
