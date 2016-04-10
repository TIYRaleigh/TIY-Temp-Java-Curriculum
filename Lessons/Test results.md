Unit tests can have three possible outcomes:

### Success

A successful unit test is one in which all assertions successfully passed. As shown above, this results in a most-beautiful green light.

### Failure

A failing test is one in which an assertion did not successfully pass. For example, if our `Person` received a high five, but the `getHighFivesReceived()` method returned 0 instead of 1, then the we have a failure. If a test method has multiple assertions, then the first assertion that fails immediately stops the current test and reports a failure. In IntelliJ a failed test shows an unsightly orange light.

![failed test.png](https://tiy-learn-content.s3.amazonaws.com/93556976-failed%20test.png)

The right side of this window has some textual output explaining what happened:

    java.lang.AssertionError: 
    Expected: <2>
	    but: was <1>

This tells you in rather plain english what was expected and what was actually received. In this case we expected two high fives, but only received one. 

A little bit after that you also see this:

    at org.hamcrest.MatcherAssert.assertThat(MatcherAssert.java:20)
    at org.hamcrest.MatcherAssert.assertThat(MatcherAssert.java:8)
    at PersonTest.whenHighFiveReceivedThenHighFiveCountIncreases(PersonTest.java:25) <26 internal calls>

This is part of a _stack trace_. A stack trace is an outline of exactly how Java reached a line of code that had a problem. We'll dig into how to read stack traces later. 

The last line in the stack trace above identifies the class, `PersonTest`, the method, `whenHighFiveReceivedThenHighFiveCountIncreases()`, the file, `PersonTest.java`, and the line number of the failing assertion, `25`. We can actually click on `PersonTest.java:25` in the stack trace to go directly to that specific line of code.

All in all, we get really useful information to help us track down and resolve the problem. When we resolve the problem we are rewarded with lovely green lights.

### Error

And error is the result of an uncaught exception. For example, if I instantiate a Person and pass in a negative age, the Person class will thrown an exception indicating that a Person can't have a negative age. In IntelliJ an error shows a hideous red light.

![error test.png](https://tiy-learn-content.s3.amazonaws.com/5cc724ce-error%20test.png)

The right side of this window shows the exception's message and stack trace:

    java.lang.Exception: A person can't have a negative age!

	    at Person.setAge(Person.java:82)
	    at Person.<init>(Person.java:33)
	    at PersonTest.whenHighFiveReceivedThenHighFiveCountIncreases(PersonTest.java:19) <26 internal calls>

As with the failing test, you can use the stack trace to find out exactly where the exception was thrown.

As with failures, when you fix the problem you will again see a fantastic green light.
