The following is an example unit test that tests one behavior of the Person class we've been exploring.

```java
import org.junit.Test;
import static org.hamcrest.CoreMatchers.*;
import static org.hamcrest.MatcherAssert.*;

/**
 * Tests Person objects
 */
public class PersonTest {

    @Test
    /**
     * Given a Person,
     * When a high five is received,
     * Then the number of high fives the Person has received increases
     */
    public void whenHighFiveReceivedThenHighFiveCountIncreases() throws Exception{
        // Arrange
        Person person = new Person("Doug", 38, 6);

        // Act
        person.receiveHighFive();

        // Assert
        assertThat(person.getHighFivesReceived(), equalTo(1));
    }

}

```

This only tests one specific behavior of the Person class: receiving high fives. This test doesn't (yet) address any other behaviors, such as a person getting older or growing taller. We'll add more tests as we move forward.

Starting at the top, we have three `import` statements. These import statements tell Java that we're going to use the specified classes.

* **`import org.junit.Test`** 
	This import statement allows us to use the `@Test` annotation, which we'll get to in a bit.
	
* **`import static org.hamcrest.CoreMatchers.*`**
	This import allows us to use _matchers_. Matchers are used check that the data that your classes return is what you expected.

* **`import static org.hamcrest.MatcherAssert.*;`**
	Finally, this import allows us to make _assertions_. Assertions are statements that declare our expectations about how the code we're testing works.

These import statements tell Java that we will be using these imported classes to formally state the way our code _should_ work and compare that to how our code _does_ work.

It is convention to sort classes into the same package structure in the `/test` directory as in the `/src` directory. It is also convention to name a tests the same as the class being tested, but with "Test" as a suffix. Since the `Person` class is being tested, I named the test class `PersonTest`.

Next, we come across some new syntax, `@Test`. The `@` symbol indicates an _annotation_ in Java. An annotation is _metadata_ about a class or method. Metadata is descriptive information. In the same way that [metacognition](https://en.wikipedia.org/wiki/Metacognition) is thinking about thinking, metadata is data about data.

Annotation can change how Java works with a class. In this case, the `@Test` annotation tells Java that the subsequent method is a JUnit test. When we execute our tests, JUnit will load each class in the `/test` directory and execute any methods annotated with `@Test`.

Now, let's take a closer look at the test method's comment:

```java
/**
 * Given a Person,
 * When a high five is received,
 * Then the number of high fives the Person has received increases
 */
```

First off, the function description comment isn't required, but do it anyhow while you're in this class. The comment is in _given-when-then_ format. Given-when-then is a way of thinking about the behaviors of your classes. 

* **Given**
	This is the state of your objects and the scenario you're testing. IE: The context.

* **When**
	This describes an even that occurs.

* **Then**
	This describes the expected outcome. 

Here are a couple example given-when-then statements:

	* Given a scoop of ice cream, when the temperature is over 90 degrees fahrenheit, then the ice cream melts.
	* Given a new baby and a diaper, when it is 3 am, then the diaper is dirty and the baby is hungry and the baby is crying.

Returning back to the comment we're analyzing, it shows the behavior we're testing in a given, when, then format. This helps us understand what the test is testing. It also serves as a form of documentation of what our program actually does. If someone asks us what happens in a given scenario, we can easily refer to this documentation for details.

The next line of code is our test method's signature:

```java
public void whenHighFiveReceivedThenHighFiveCountIncreases() throws Exception{
```

The test method must be public so that JUnit can execute the test. 

The test doesn't return anything so the return type is void.

The method name is based on the when-then part of the given-when-then comment. It describes a scenario and expected outcome.

`when<scenario>Then<expected result>`

Don't worry about long method names. Well, don't be ridiculous. You'll know a bad test name when you see one. 

The end of the method signature declares that the method throws exceptions. We need to declare this when testing the Person class because the Person class can throw an exception when we create a new instance. We could hypothetically use try/catch blocks in our code, but that's inelegant. Since we're not testing the behavior of throwing exceptions, we may as well just pass the exception on to JUnit. JUnit  will report an error (as opposed to a failure).

Within the body of the test method the code has been broken into three distinct sections denoted by comments, Arrange, Act, and Assert. This is a way of thinking about how the test works and structuring it in a way that makes sense and encourages good tests. The mnemonic for Arrange, Act, and Assert is AAA.

* **Arrange**
	This is where you create whatever objects you need and configure them however you need for your test. In our example we instantiate a new instance of the Person class and configure it using the constructor. 

* **Act**
	This is where whatever action is being tested is performed. In our example we're testing receiving high fives, so we call `person.receiveHighFive()`. 

* **Assert**
	We know that the `receiveHighFive()` method is supposed to increment the `highFivesReceived` property of the Person class. Since the Person has not yet received any high fives, the Person class' `getHighFivesReceived()` method should return 1. This is what we assert.

You've probably noticed that AAA is very similar to given-when-then. This is intentional. In this class I want you to explicitly put the Arrange, Act, Assert comments into your test methods. This will help you think about what you're testing and the structure of your tests.

The only code that is unfamiliar in the test method's body is this line:

```java
assertThat(person.getHighFivesReceived(), equalTo(1));
```

Let's start by trying to read this line as if it were english.

> Assert that the number of high fives the person has received is 1.

While it's not actually english, it's fairly easy to translate assertions in this format to something that is.

Let's break this line down. There are three method calls. Going by the order of operations, Java will first execute `person.getHighFivesReceived()`. We know how this works.

Next, Java will execute the `equalTo()` method. The `equalTo()` method returns a type of class called a `Matcher`. A `Matcher` knows how to take two values and make sure they match. There are many different types of matchers. In this case, the `Matcher` will check if a provided value is equal to `1`, the value we passed into the `equalTo()` method.

Finally, the results of these two method calls are passed into the `assertThat()` method. The `assertThat()` method will use the `Matcher` passed into the second argument to check that the value passed into the first argument matches the expected value. 

When it comes down to it, you really don't need to understand the _implementation_, you just need to know that `assertThat()` checks that the value provided matches the second value in the manner that we specified.  The implementation is how the code actually does what it does.
