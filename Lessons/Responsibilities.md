I like to think of classes as having _responsibilities_. I am responsible for writing this document and making it understandable. You are responsible for reading it and learning the material. The Person class is responsible for all things Person-y in our program.

It doesn't make sense for multiple bits of code to do the same thing. As an example, let's think about the description of the `Person` objects the `Main` class is outputting. 

What if I wrote some other class that also interacts with the `Person` class? What if that other class also needs a description of a `Person` object? Do I copy and paste the code from the `Main` class? What if the description needs to be changed at some point? 

I don't think the `Main` class (or any other class) should have the responsibility to describe a `Person` class. The `Person` class should be solely responsible for that. Furthermore, the Main class is already doing a lousy job of it as it doesn't take into account plurality. For example, "This person has received 1 high fives."

To facilitate this, we could add a method to the `Person` class that returns a description of a `Person` object.

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
    public Person(String name, int age, double height) throws Exception{
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
    public void setHeight(double height) throws Exception{
        // is height less than 0?
        if(height < 0) {
            throw new Exception("A person can't have a negative height!");
        }

        // we're good. update the height
        this.height = height;
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
    public void setAge(int age) throws Exception{
        // age can't be negative
        if(age < 0) {
            throw new Exception("A person can't have a negative age!");
        }

        // age can only increase
        if (this.age >= age){
            throw new Exception("A person's age can only increase!");

        }

        // looks like we're good! Update the age
        this.age = age;
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

    /**
     * I return a description of the Person
     * @return The Person's description
     */
    public String describe(){
        String years = this.getAge() == 1 ? "year" : "years";
        String feet = this.getHeight() == 1 ? "foot" : "feet";
        String fives = this.getHighFivesReceived() == 1 ? "five" : "fives";

        return this.getName() + " is " +
                this.getAge() + " " + years + " old and " +
                this.getHeight() + " " + feet + " tall. " +
                this.getName() + " has received " +
                this.getHighFivesReceived() + " high " + fives + ".";
    }

}
```

In here you can see that I've added another public method, `describe()`. The `describe()` method returns a description of the person. Now I can use this function anywhere I want to get a description of the person.

On a side note, these three lines each use the [ternary operator](https://en.wikipedia.org/wiki/%3F:):

```java
String years = this.getAge() == 1 ? "year" : "years";
String feet = this.getHeight() == 1 ? "foot" : "feet";
String fives = this.getHighFivesReceived() == 1 ? "five" : "fives";
```

The ternary operator is similar to an if conditional, but otherwise unique to its own syntax. You can read the first line like this:

> If `this.getAge()` is 1, then return "year". Otherwise return "years".

The other lines are the same.

```java
public class Main {

    public static void main(String[] args){

        // create a Person for Doug
        try {
            Person doug = new Person("Doug", 38, 6.0);
            doug.receiveHighFive();

            // create a Person for Liz
            Person liz = new Person("Liz", 38, 5.5);

            // Print details to the console
            System.out.println(doug.describe());
            doug.setAge(72);
            System.out.println(doug.describe());

            System.out.println(liz.describe());
            liz.setHeight(5.49);
            System.out.println(liz.describe());

        } catch (Exception e){
            System.out.println("Oops! There was an exception: " + e.getMessage());
        }
        
    }

}
```

In this code I'm now invoking the describe() method on the Person objects instead of writing out my own long version. Rather than having four copies of the same ugly chunk of code I now have one ugly chunk of code in a logical place that I invoke four times. As a result the Person class has responsibility for describing itself and the Main class is significantly cleaner and easy to read. (I also removed the code that was causing exceptions to be thrown.)

<!-- exercise / assignment: model a single playing card -->

<!-- assignment: 99 bottles of beer on the wall song written out long hand (ninety-nine bottles of beer on the wall ) -->
