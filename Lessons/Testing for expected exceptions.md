If your class has a behavior where an exception is thrown, you should make a point of testing that behavior. There are a few ways to do this and we'll cover two for now.

To demonstrate, setting a Person object's age to a smaller value than the current age should result in an Exception being thrown. The Exception object's message should be say, "A person's age can only increase!" Let's take a look at two different approaches to this.

### try/catch and fail()

The old fashioned way to test for expected exceptions is to add a try/catch block to your test.

```java
@Test
/**
 * Given a Person
 * When their age is set to a smaller value than the current age
 * Then an exception should be thrown
 */
public void whenAgeIsDecreasedThenExceptionThrown(){
    try{
        // Arrange
        Person person = new Person("Doug", 38, 6);

        // Act
        person.setAge(32);

        // Assert
        fail();
    } catch (Exception expected){
        // Assert
        assertThat(expected.getMessage(), equalTo("A person's age can only increase!"));
    }
}
```

Adding this method the the `PersonTest` confirms that the an exception with the correct message is thrown if the `Person` class' age is decreased. Note that this test method does not throw an exception. Instead, we catch the thrown exception in a try/catch block. 

We are expecting that `person.setAge(32)`, the "Act" in the `try` block, will throw an exception. If it doesn't the program will continue onto the `fail()` method, failing the test. If an exception is thrown, the we catch it in the `catch` block and assert the exception's message is correct. 

There are a few things that make this test ugly. For example, it's difficult for us to follow the AAA form. We have to have two separate assertions with unrelated, ugly, syntax between them. Also, I named the `Exception` variable `expected` to be extra clear that we actually expected and want that exception. The fact that this is needed suggests that this isn't the best way to approach the problem.

### Expected exception in annotation

An alternative to the try/catch method is to tweak how we're using the `@Test` annotation. Some annotations let you provide additional metadata relevant to the annotation. In the case of the `@Test` annotation you can specify a specific expected exception. If the exception is not thrown, then the test fails.

Here's an alternative version of the `whenAgeIsDecreasedThenExceptionThrown()` method:

```java
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
```

This test passes if an `Exception` is thrown. Note that we did need to add the `throws Exception` to the function signature. The `@Test(expected = Exception.class)` annotation tells JUnit that this method is expected to thrown an `Exception`. The test only passes if the `Exception` is thrown.

In general, this is the easiest and prettiest way to test for exceptions. However, it's not the best solution in our case because the Person class is throwing a generic Exception. We can't tell one generic exception from another generic exception. We could check the exception message, but this annotation approach doesn't have a mechanism to do so.

For example, the `setAge()` method throws an Exception when a person's age is set to a negative number or when the age decreases. We can't tell these apart because they're the same type and the annotation approach doesn't let us inspect the exception's message. We could update our Person to throw unique exceptions, but we don't yet know how to do this.

### Rule

There is another way to handle expected exceptions. This uses a `@Rule` annotation. Using `@Rule` requires knowledge we don't yet have, so I'll skip over that for now. If you're curious, [you can find out more about `@Rule` here](https://github.com/junit-team/junit4/wiki/Rules).
