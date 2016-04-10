
Hamcrest assertions are a newer style of assertions. They were designed to be more readable and produce better failure messages, among other features. 

The name Hamcrest is an anagram of "matchers". This is relevant because Hamcrest is much more concerned with matcher classes than assertion methods. In fact, there is only one assertion method in Hamcrest, `assertThat()`, but many matchers.

As a note, the Hamcrest matchers included in JUnit are a subset of a larger library that could be used. Later in the class we'll go over how to use third party classes. The [full Hamcrest matchers library](http://hamcrest.org/JavaHamcrest/) might be one you could experiment with. In general, the classic assertions and Hamcrest matchers should get you where you need to go 99% of the time.

### assertThat()

**Syntax:** `assertThat(<actual value>, <matcher method>(<expected value>))`

The assertThat() method is used to assert that the actual value provided matches the expected value, according to the specified matcher.

Matchers can actually be nested. We've already seen the `equalTo()` matcher method. However, another matcher method is `not()`. The not() matcher negates the matcher passed into it.

```java
assertThat(123, not(equalTo(234)));
```

The assertion above passes because 123 is not equal to 234. Again, this is an example of how more more expression Hamcrest assertions are than classic assertions. The classic assertion would be this:

```java
assertEquals(123, 234);
```

The syntax is simpler, but it doesn't read like english. 

Let's go over some common matchers now. For a complete list of the built-in matchers, [check out the Javadocs for org.hamcrest.CoreMatchers](http://hamcrest.org/JavaHamcrest/javadoc/1.3/org/hamcrest/CoreMatchers.html).

### equalTo()

**Syntax:** `assertThat(<actual value>, equalTo(<expected value>))`

The equalTo() matcher matches when the actual value and the expected value are equal to each other.

### not()

**Syntax:** `assertThat(<actual value>, not(<matcher method>(<expected value>)))`

The `not()` matcher is used to negate the matcher passed into it. For example, you could use the following to assert that 123 is not equal to 234.

```java
assertThat(123, not(equalTo(234)));
```

### is()

**Syntax:** `assertThat(<actual value>, is(<expected value or matcher>))`

The `is()` matcher is the same as `equalTo()`. It's really _syntactic sugar_. Syntactic sugar is syntax you can use to make code easier to read or write, but which is not strictly necessary. For example, consider this `not()` matcher expression:

```java
assertThat(123, not(equalTo(234)));
```

You can make this easier to read using is():

```java
assertThat(123, is(not(equalTo(234))));
```

In some cases it might be easier to read `is()` instead of `equalTo()`. This can also make reading the resulting assertion failure messages easier to understand. It's up to you whether or not to use this. 

### containsString()

**Syntax:** `assertThat(<actual string>, containsString(<expected string>))`

The containsString() matcher confirms that the actual string value contains the expected string value. Here's an example usage that passes:

```java
assertThat("A long time ago...", containsString("long time"));
```

### startsWith()

**Syntax:** `assertThat(<actual string>, startsWith(<expected string>))`

The `startsWith()` matcher asserts that the actual string provided must start with the specified expected string. Here's an example usage that passes:

```java
assertThat("A long time ago...", startsWith("A long"));
```

### endsWith()

**Syntax:** `assertThat(<actual string>, endsWith(<expected string>))`

The `endsWith()` matcher is similar to `startsWith()`, it just asserts that the actual string provided must end with the specified expected string. Here's an example usage that passes:

```java
assertThat("A long time ago...", endsWith("ago..."));
```

### nullValue()

**Syntax:** `assertThat(<actual value>, nullValue())`

The `nullValue()` matcher simply asserts that the actual value is null. If the value is not null it doesn't pass.

### notNullValue()

**Syntax:** `assertThat(<actual value>, notNullValue())`

The `notNullValue()` matcher asserts that the actual value is _not_ null. If the value is null it doesn't pass. 

As a note, you could also accomplish this with `not(nullValue())` or even `is(not(nullValue))`.

### allOf()

**Syntax:** ``assertThat(<actual value>, allOf(<comma delimited list of matchers>))`

The `allOf()` matcher is used to match multiple matchers against the actual value provided. For example, I could use all of to check that a string begins with a specific value and ends with a specific value. Of course, this could also be accomplished with two separate `assertThat()` invocations. 

Whether or not to use this is situational. Perhaps it reads well syntacticly. Perhaps it makes your tests easier to understand. It's up to you.

Here's an example usage that passes:

```java
assertThat("A long time ago...", allOf(startsWith("A long"), containsString("time"), endsWith("ago...")));
```
	
However, this example does not pass because the actual string value does not contain "time".

```java
assertThat("A long hotdog ago...", allOf(startsWith("A long"), containsString("time"), endsWith("ago...")));
```

### anyOf()

**Syntax:** ``assertThat(<actual value>, anyOf(<comma delimited list of matchers>))`

The `anyOf()` matcher is similar to `allOf()`, except that it passes if any of the provided matchers passes. 

These two examples pass:

```java
assertThat("A long time ago...", anyOf(nullValue(), startsWith("A long")));
```

```java
assertThat(null, anyOf(nullValue(), startsWith("A long")));
```

This example does not pass:

```java
assertThat("A long time ago...", anyOf(nullValue(), startsWith("Once upon a time")));
```

### hasItem()

**Syntax:** ``assertThat(<collection of values>, hasItem(<a specific value>))`
<!-- todo: write this? or was I planning to remove this? -->
