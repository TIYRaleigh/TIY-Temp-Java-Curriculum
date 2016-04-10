**Syntax:** `<return value> = <instance of an object>.<method name>(<zero or more method arguments>)`. 

In the real world, objects typically _do_ things; you can interact with them in some way. A person might jump up and down, a playing card can be flipped over, a rock can be thrown.

In Java, objects can have _methods_ that provide ways to interact with the object. For example, a `String` has methods to get its length, what characters are in specific positions, to extract a specific subset of the String, and [much more](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#method.summary).

The `String` class' `length()` method is used to get the number of characters in a `String`. Behind the scenes, the `String` class is just a chunk of code that some other programmer wrote. The `String` class' `length()` method is just a specific subset of the String class' code. 

We can use the syntax shown above to _invoke_ the String class's `length()` method. When we invoke a method we're telling the String class to execute that specific chunk of code and tell us the results of running that code.

```java
public class Example {
    public static void main(String[] args){
    
      	String message = "No pain, no gain";
        int length = message.length();
      
      	System.out.println("The message \"" + message + "\" is " + length + " characters long."); 
    }
}
```

This sample indicates that there are 16 characters in "No pain, no gain", which is correct!

Remember that Java recognizes the string literal "No pain, no gain" and creates an instance of a `String` object. We can invoke the `length()` method on this instance object as shown.

The etymology of invoke may be helpful in understanding this:

* **in-** Latin prefix. 
	1. Prefixed to certain words to give the senses of in, into, towards, within.
* **vocare** Italian
	1. (transitive) to call, name

So, the verb invoke means to call into code within a class.

Oftentimes you hear people refer to _calling_ or _running_ a method. This is just shorthand for invoking. It's perfectly ok to use this language, but I encourage you to be explicit and try to use the word invoke instead.

In the same way that two houses built from the same blueprint don't share a single kitchen sink, each object instantiated from a class gets its own methods. 

```java
public class Example {
    public static void main(String[] args){
    
      	String noPain = "No pain, no gain";
        int noPainLength = noPain.length();
        System.out.println(noPain  + ": " + noPainLength);

        String lotaPain = "Lots of pain, lot of gain";
        int lotaPainLength = lotaPain.length();
        System.out.println(lotaPain  + ": " + lotaPainLength);
    }
}
```

This example shows two `String` variables, `noPain` and `lotaPain`. Each of these `String` objects have their own `length()` method. When invoked, these methods return the length of their respective strings.

Another notable method on the `String` class is `substring()`. Unlike the `length()` method, the `substring()` method accepts two `int` arguments, `beginIndex`, and `endIndex`. These tell the method to find the substring of text starting from `beginIndex` and continuing to (but not including) `endIndex`. The `substring()` returns this text as a new `String` object.

```java
public class Example {
    public static void main(String[] args){
    
      	String deepThought = "No pain, no gain";
		System.out.println( deepThought.substring(3, 11) );
    }
}
```

![no pain no gain substring.png](https://tiy-learn-content.s3.amazonaws.com/53697f9f-no%20pain%20no%20gain%20substring.png)

[You can find the full documentation for the String class here.](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html)
