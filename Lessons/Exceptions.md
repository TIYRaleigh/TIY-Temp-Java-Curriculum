You might be realizing as we work through this Person example that programming is all about progressively improving your code. As an experienced programmer you begin to be able to sense "code smell". It's almost a 6th sense you develop. A bad code smell might indicate code that works, but isn't very good or doesn't follow best practices. In general, it's a good idea to try to find a way to deodorize stinky code. 

I'm noticing some malodorous code in the setters for `height` and age in the `Person` class. Specifically, I don't like how setting invalid values results in messages being output to the console and no change to property values. The `Main` class has no way to know if something went wrong when setting the `age` or `height` properties. Furthermore, the `Main` class has no way of knowing _why_ there were problems. Another is a issue is that, if you instantiate a new `Person` with a negative age, the new Person object will actually be created with an age of 0! 

I would take exception if you tried to tell me I was getting younger. And that's exactly what we need our `Person` class to do. An _exception_ is how our code tells Java that something went wrong. 

There are two parts to exceptions: producing them and handling them.

### Throws

**Syntax in Methods:** 

```java
<access modifier> <return type> <method name>(<method arguments>) throws <exception types>{
	<method body>
}
``` 

**Syntax in Constructors:** 

```java
<access modifier> <Class name>(<constructor arguments) throws <exception types>{
	<body of constructor>
}
```

We use the `throws` keyword when defining a method or constructor to tell Java that the method might produce a specific exception. For example, our `setAge()` method should produce an exception if we try to set an invalid age. 

This syntax is the same method syntax as before, but with `throws <exception types>` after the method arguments, but before the curly braces. Exception types is a list of exceptions that the method might produce if something goes wrong.

There are many, many, types of exceptions. For example, if your code tries to read a file that doesn't exist, Java will throw a [FileNotFoundException](https://docs.oracle.com/javase/8/docs/api/java/io/FileNotFoundException.html). Exception is another class. We can make our own Exception classes, but, for now, we're not going to do that. Instead we'll use Java's built-in Exception class. 

I would prefer that my Person class more forcefully reject bad data. This means that my setAge() and setHeight() methods need to be able to _throw_ exceptions. "Throw" just means that the method produces the exception. Think of it like someone who doesn't know how to do something. They might just throw their hands up in frustration and quit. That's what our methods will do.

### Throw

**Syntax:** `throw <exception instance>`

The `throw` keyword is how we actually throw exceptions. Any time Java sees the `throw` keyword it will immediately stop executing the current method and, as if it were a hot potato, throw the indicated Exception object back to whatever is invoked the method. That code knows to expect this eventuality because we told it to when we added the `throws` keyword to our method.

Putting it together, we can update our Person class like so:

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

}
```

I have updated the `setHeight()` and `setAge()` methods. They now indicate that they throw exceptions. Within these methods I now throw an Exception when bad data is provided. Let's take a closer look at this:

```java
throw new Exception("A person can't have a negative age!");
```

This is a `throw` statement I added. We already know that the `throw` keyword tells Java that the method has encountered a problem. In this case an Exception is thrown when setting the Person's age to a negative value.

The `new` keyword should be familiar to you as it is how we instantiate a new instance of a class. In this case we're creating a new instance of a class that Java provides called `Exception`. The `Exception` class has [many constructors](https://docs.oracle.com/javase/8/docs/api/java/lang/Exception.html#constructor.summary), but we're using the one that allows us to specify an error message. 

The `throws` keyword added to our `setHeight()` and `setAge()` methods is what allows us to throw an `Exception`.

I also updated the constructor for the `Person` class by adding a `throws` keyword indicating that the constructor might thrown an `Exception`. This is because the constructor invokes `setHeight()` and `setAge()`, both of which throw exceptions. Since I don't want to handle these exceptions in the Person class, I have to allow them to be thrown all the way back to whatever invoked the Person class' constructor. 

Take note that the Exception class represents the abstract concept of Something That Went Wrong. The Exception class has properties that describe what went wrong. One such property is "message". Another property is StackTrace which can be used to tell us exactly where the exception occurred. The Exception object also has a constructor to set its initial state and methods to interact with that state. I write all of this here to try to point out these patterns which you will see over, and over, and over, and over in programming.

### Try, Catch

**Syntax:**

```java
try {
	<code that might throw an exception>
} catch(<exception type> <variable name>) {
	<code to handle the exception>
} 
```

We've already updated our Person class to throw exceptions if we provide bad data. But, Java requires you to handle all exceptions. This means that you have to explicitly write code to handle the exceptions raised by the `Person` class. This is done with a `try` / `catch` statement.

The keyword `try` tells Java that the block code we're about run inside the following curly braces might throw an exception. The `catch` keyword is used to tell Java what to do if a specific type of exception is thrown. 

If the block potentially throws multiple types of exceptions we would need a catch statement for each exception type. (This isn't strictly true, but it's a good enough for now.) Here's what this might look like if the block of code after the `try` keyword threw FileNotFoundException or WriteAbortedException exceptions:

```java
try{
	// code that could throw FileNotFoundException or WriteAbortedException exceptions
} catch (FileNotFoundException exception){
	// code that does something when a file isn't found
} catch (WriteAbortedException exception){
	// code that does something when a write is aborted
}
```

For now, we're only using Java's built in `Exception` class so we'll only have one catch statement. 

```java
public class Main {

    public static void main(String[] args){

        // create a Person for Doug
        try {
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

        } catch (Exception e){
            System.out.println("Oops! There was an exception: " + e.getMessage());
        }


    }

}
```

This code shows how I've wrapped the the code in the `main()` method's body in one big try/catch block. As soon as any code in the `try` block throws errors, Java will skip to the catch block and output a message to the console.

The way I've handled exceptions here is a bit heavy handed. As soon as any exception is thrown I just give up. I could have wrapped each line, or specific subsets of lines in their own try / catch blocks and handled the exceptions more gracefully.

### Finally

<!-- todo: consider not having this here -->

**Syntax:**

```java
try {
	<code that might throw an exception>
} catch(<exception type> <variable name>) {
	<code to handle the exception>
} finally {
	<code that always runs>
}
```

The `finally` keyword is another optional part of the try / catch statement. The finally block is always run, whether the try block competes successfully or if exceptions are thrown and handled. 
