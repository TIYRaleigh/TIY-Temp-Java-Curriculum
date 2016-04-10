JUnit comes with a heck of a lot of assertions you can use. There are two general classifications of assertions, classic assertions and Hamcrest assertions. Classic assertions are generally easier to use, but can be less expressive than the newer Hamcrest style we saw above. 

For a given test class, choose either classic or Hamcrest assertions. While you can use both in one test, it's moderately more complex and we haven't yet covered some relevant topics yet.

The following import statement will let you use any of the classic annotations.

```java
import static org.junit.Assert.*;
```

Here are some of the more common classic assertions. For a list of all classic assertions, [visit the Javadocs for org.junit.Assert](http://junit.sourceforge.net/javadoc/org/junit/Assert.html).

### assertTrue

**Syntax:** `assertTrue(<boolean value or expression>)`

The assertTrue() assertion method is used to assert that a value or expression evaluates to true. If the value or expression does not evaluate to true, then the assertion fails.

### assertFalse

**Syntax:** `assertFalse(<boolean value or expression>)`

The `assertFalse()` assertion method asserts that a value or expression evaluates to false. This is the exact opposite of `assertTrue()`. 

### fail

**Syntax:** `fail(<optional message>)`

The `fail()` method forces a test to fail. You can provide an optional message to display when the test fails.

### assertEquals

**Syntax:** `assertEquals(<expected value>, <actual value>)`

**Syntax for doubles:** `assertEquals(<expected value>, <actual value>, <maximum difference allowed>)`

The `assertEquals()` assertion method asserts that two values are equal. Note that these values must be the same type. You can't compare an `int` to a `String`, only to another `int`. 

Because doubles are only estimates in Java, two doubles may be very close, but not equal. In this case you can specify a third argument to indicate how close together they must be to be considered equal.

For example, the following fails:

```java
assertEquals(8.2+0.1, 8.4-0.1);
```

The failure message is:

    junit.framework.AssertionFailedError: 
    Expected :8.299999999999999
    Actual   :8.3

However, this passes:

```java
assertEquals(8.2+0.1, 8.4-0.1, 0.00001);
```
