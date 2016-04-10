It's important to know the basic process by which JUnit loads and executes your tests. JUnit will instantiate an entirely new instance of your test class for each method annotated with `@Test` in your test class. This means that tests are stateless, outside of the state created while running a test. 

Also, the order in which tests are executed is not guaranteed. JUnit doesn't necessarily execute the test methods from the top of your class down. As such, you should not attempt to make tests that depend on other tests being executed first. 

JUnit has a few other annotations beyond the `@Test`. An important one is `@Before`. Methods annotated with `@Before` are run, in no guaranteed order, before each `@Test` method. `@Before` methods are very useful for consolidating code that might otherwise be repeated. 

Let's check out our full `PersonTest` class. This class uses the `@Test(expected = Exception.class)` annotation to indicate that the `whenAgeIsDecreasedThenExceptionThrown()` method is expected to thrown an exception.

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
     * Given a Person
     * When a high five is received
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

    @Test(expected = Exception.class)
    /**
     * Given a Person
     * When their age is set to a smaller value than the current age
     * Then an exception should be thrown
     */
    public void whenAgeIsDecreasedThenExceptionThrown() throws Exception{
        // Arrange
        Person person = new Person("Doug", 38, 6);

        // Act
        person.setAge(32);
    }

}
```

### `@Before`

Looking closely, you might notice that both of the test functions start out by creating an instance of Person. This isn't really a big deal since this is only one line of code, but if you require many lines of code to arrange your test, you can consolidate them into a single method that executes before your test methods. This is done with an `@Before` annotation.

```java
import org.junit.Before;
import org.junit.Test;

import static org.hamcrest.CoreMatchers.*;
import static org.hamcrest.MatcherAssert.*;

/**
 * Tests Person objects
 */
public class PersonTest {

    /**
     * This is the Person we're testing against
     */
    private Person person;

    @Before
    /**
     * Instantiates and configures the Person object we're testing.
     */
    public void setup() throws Exception{
        // Arrange
        person = new Person("Doug", 38, 6);
    }

    @Test
    /**
     * Given a Person
     * When a high five is received
     * Then the number of high fives the Person has received increases
     */
    public void whenHighFiveReceivedThenHighFiveCountIncreases() throws Exception{
        // Act
        person.receiveHighFive();

        // Assert
        assertThat(person.getHighFivesReceived(), equalTo(1));
    }

    @Test(expected = Exception.class)
    /**
     * Given a Person
     * When their age is set to a smaller value than the current age
     * Then an exception should be thrown
     */
    public void whenAgeIsDecreasedThenExceptionThrown() throws Exception{
       // Act
        person.setAge(32);
    }

}

```

Here we've added a `@Before` annotation where we create an instance of a `Person` class that we use in both `@Test` methods. The `Person` object is stored in a class property so that the functions can `@Test` have access to it.

When JUnit runs this test it will do the following:

1. Inspect the PersonTest class to find annotated methods.
2. Create an instance of the PersonTest class.
3. Execute methods annotated with `@Before` in no particular order.
4. Execute one of the methods annotated with `@Test`. There is no guarantee which one.
5. JUnit will create another new, separate instance of the PersonTest class.
6. Execute methods annotated with `@Before` in no particular order.
7. Execute the other method annotated with `@Test`. There is no guarantee which one.

### `@After`

The `@After` annotation is the opposite of `@Before`. Any methods annotated with `@After` are executed after each `@Test` method, in no guaranteed order.

The `@After` annotation is usually used for cleaning up after your tests. For example, maybe your tests generate a file or some data that should be tidied up. This is where you'd put that cleanup code.
