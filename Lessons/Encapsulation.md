Getters and Setters enable a concept called _encapsulation_. In programming, encapsulation means data hiding. The `highFivesReceived` property of the `Person` class is inaccessible to any code other than the `Person` class itself. The only way that other code can interact with that data is by using the `getHighFivesReceived()` method we created. 

Ostensibly, the `Person` class is a black box. Without reading the code itself, you don't know how the `Person` class keeps track of the number of high fives received. Sure, it probably has a private property, but maybe it saves the data a file on disk? Maybe it just makes lucky guesses each time? Smoke signals? 

![black-box.png](https://tiy-learn-content.s3.amazonaws.com/d41dffcc-black-box.png)

Encapsulation is incredibly powerful. If your object's properties aren't public then _you_ can control how others interact with them. Let's ponder this...

Real people don't have negative heights or ages, but our Person class has no problem with this. 

```java
public class Main {
    public static void main(String[] args){

        // create a Person for Doug
        Person doug = new Person("Doug", -38, 6.0);

        // create a Person for Liz
        Person liz = new Person("Liz", 38, 5.5);
        liz.age = -38;

        // Print details to the console
        System.out.println(doug.name + " is " + doug.age + " years old and " + doug.height + " feet tall.");
        System.out.println(liz.name + " is " + liz.age + " years old and " + liz.height + " feet tall.");
    }

}
```

This demonstrates that we are able to set a person's age to a negative value in both the constructor and directly in via a property. This is the major disadvantage to using public properties as we have. 

In a professional environment many different developers will likely work with your code. You can't guarantee that they'll do what you want expect them to. Heck, you can't even guarantee that a year from now you'll remember what you intended. 

We need a way to enforce some rules:

* A Person can not have a negative height.
* A Person can not have a negative age.
* A Person's age can only increase, not decrease.
* A Person gets their name when instantiated and it can't be changed.

Encapsulating gives us the power to do this. We can add mutators and accessors (ok, ok, I'll call them getters and setters!) to the Person class and add logic to enforces these rules.

```java
/**
 * The Person class represents a person.
 */
public class Person {
    /**
     * The Person's name
     */
    private String name = "";

    /**
     * The Person's age
     */
    private int age = 0;

    /**
     * The Person's height
     */
    private double height = 0;

    /**
     * Used to count how many high fives this Person has received.
     */
    private int highFivesReceived = 0;

    /**
     * Create a Person and set the default values;
     * @param name The Person's name
     * @param age The Person's age
     * @param height The Person's height
     */
    public Person(String name, int age, double height){
        this.name = name;
        setAge(age);
        setHeight(height);
    }

    /**
     * Allows a Person to receive a high five.
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

    /**
     * Sets the height of a Person. A Person can not have a negative height.
     * @param height The height
     */
    public void setHeight(double height){
        if(height >= 0){
            this.height = height;
        } else {
            System.out.println("A person can't have a negative height!");
        }
    }

    /**
     * Gets the Person's height
     * @return The Person's height
     */
    public double getHeight(){
        return this.height;
    }

    /**
     * Sets the Person's age. A Person's age can only be positive.
     * When updated, a Person's age can only increase.
     * @param age The new age
     */
    public void setAge(int age){
        if(age < 0){ // age can't be negative
            System.out.println("A person can't have a negative age!");

        } else if (this.age >= age){ // age can only increase
            System.out.println("A person's age can only increase!");

        } else { // looks like we're good!
            this.age = age;

        }
    }

    /**
     * Gets the Person's age
     * @return The Person's age
     */
    public int getAge(){
        return this.age;
    }

    /**
     * Gets the Person's name
     * @return The Person's name
     */
    public String getName(){
        return this.name;
    }

}
```

There's a fair amount of code changed and added in this example. Firstly, all of the Person class' properties have been made private; they're only accessible to the Person itself. Towards the bottom of the class I've added a few methods:

* `setHeight(int height)` 
* `getHeight()`
* `setAge(int age)`
* `getAge()`
* `getName()`

These include a getter and setter for the height property. The setter has a conditional statement that prevents you from setting the height to be a negative value. 

I also added a getter and setter for the age property. As with the height property, age can't be set to a negative value. I also added logic to keep age from decreasing.

Lastly, I added a getter for the name property, but no setter. I didn't want code external to the Person class to be able to set the name except for when a Person is instantiated.

The other change made was to the constructor. Our setters now enforce our rules, but the constructor doesn't. We could (and shouldn't) add the same logic to the constructor to control these properties, but instead we can just reuse that same logic by calling the setters from the constructor.

If we attempt to set the age or height to invalid values our Person class prints a message to the console. 

Let's update our Main class and see what happens when we run it.

```java
public class Main {

    public static void main(String[] args){

        // create a Person for Doug
        Person doug = new Person("Doug", 38, 6.0);
        doug.setAge(-10);
        doug.setAge(25);
        doug.receiveHighFive();

        // create a Person for Liz
        Person liz = new Person("Liz", 38, 5.5);
        liz.setHeight(-5.5);

        // Print details to the console
        System.out.println(doug.getName() + " is " + doug.getAge() + " years old and " + doug.getHeight() + " feet tall. This person has received " + doug.getHighFivesReceived() + " high fives.");
        doug.setAge(72);
        System.out.println(doug.getName() + " is " + doug.getAge() + " years old and " + doug.getHeight() + " feet tall. This person has received " + doug.getHighFivesReceived() + " high fives.");

        System.out.println(liz.getName() + " is " + liz.getAge()+ " years old and " + liz.getHeight() + " feet tall. This person has received " + liz.getHighFivesReceived() + " high fives.");
        liz.setHeight(5.49);
        System.out.println(liz.getName() + " is " + liz.getAge()+ " years old and " + liz.getHeight() + " feet tall. This person has received " + liz.getHighFivesReceived() + " high fives.");

    }

}
```

This code outputs the following:

> A person can't have a negative age!
> A person's age can only increase!
> A person can't have a negative height!
> Doug is 38 years old and 6.0 feet tall. This person has received 1 high fives.
> Doug is 72 years old and 6.0 feet tall. This person has received 1 high fives.
> Liz is 38 years old and 5.5 feet tall. This person has received 0 high fives.
> Liz is 38 years old and 5.49 feet tall. This person has received 0 high fives.

In this example I'm still creating the People objects as before, but now I can only access and modify the Person properties via the getters and setters. If I try to set invalid values I see the appropriate message output to the console. Because all of the properties are now private, I also had to update the calls to `System.out.println()` to use the new getter methods.
