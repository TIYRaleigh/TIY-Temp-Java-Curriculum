Accessors and Mutators, colloquially (and acceptably) known as Getters and Setters are simply methods that are used to read and write private properties. In the case of our `Person` class we could add a "getter" that returns the number of high fives a `Person` object has received. 

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

    /**
     * Gets the number of high fives this Person has received.
     * @return The number of high fives
     */
    public int getHighFivesReceived(){
        return this.highFivesReceived;
    }

}
```

This update to the Person class adds a new method, `getHighFivesReceived()`. Just like the `receiveHighFive()` method, this new method is public and accepts no arguments. However, unlike the `receiveHighFive()` method, this new method returns a value. This is denoted by the `int` keyword after the access modifier and before the method name. This tells Java that any invocations of this method will produce an integer value. 

In the same way that the `+` addition operator returns the sum of two values, invocations of the `getHighFivesReceived()`  will return the number of high fives a particular `Person` object has received.

I'll now update the `Main` class so that we can show how many high fives the `Person` has received.

```java
public class Main {
    
    public static void main(String[] args){

        // create a Person for Doug
        Person doug = new Person("Doug", 38, 6.0);
        doug.receiveHighFive();

        // create a Person for Liz
        Person liz = new Person("Liz", 38, 5.5);

        // Print details to the console
        System.out.println(doug.name + " is " + doug.age + " years old and " + doug.height + " feet tall. This person has received " + doug.getHighFivesReceived() + " high fives.");
        System.out.println(liz.name + " is " + liz.age + " years old and " + liz.height + " feet tall. This person has received " + liz.getHighFivesReceived() + " high fives.");
    }
    
}
```

This results in the following output:

> Doug is 38 years old and 6.0 feet tall. This person has received 1 high fives.
> Liz is 38 years old and 5.5 feet tall. This person has received 0 high fives.
