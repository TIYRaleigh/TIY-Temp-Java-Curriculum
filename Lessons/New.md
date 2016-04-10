**Syntax:** `<new object instance> = new <name of class>(<constructor arguments>)`

The `new` keyword is what you use when you're creating a new instance of an object without using literal syntax. This is most of Java. The process of creating an instance of a class is called _instantiation_. You instantiate instances of classes. 

The etymology of instantiate may be helpful in understanding this:

* **īnstantia** Latin. 
	1. a being near, presence
* **-ate** Latin suffix
	1. (in adjectives) having the specified thing
	2. (in adjectives) characterized by the specified thing
	3. (in adjectives) resembling the specified thing

So, the verb instantiate is the act of making the specified thing (the object your class describes) be present. The noun instantiation is the presence of the specified thing.

Remember how classes describe objects? The `String` class describes `String` objects. `"Hello World!"` is an instance of the `String` class. `"Insert deep thought here..."` would also be an instance of a `String`. `"This is an instance of a string."` would be too.

Since String is a class, we don't have to use the string literal syntax, we _could_ use the `new` keyword.

```java
public class Example {
    public static void main(String[] args){
    
      	String emptyString = new String();
    }
}
```

This creates a new string object. It's the equivalent to this:

```java
public class Example {
    public static void main(String[] args){
    
      	String emptyString = "";
    }
}
```

Let's try this with a different class, `Date`. The Date class is one way of working with dates in Java. It should be noted that many methods of the `Date` class are _deprecated_. This means they are slated to be removed from Java in the future and shouldn't be used for new code. There's a new set of classes for working with dates that we'll go over in future lectures.

```java
import java.util.Date;
 
public class Example {
    public static void main(String[] args){
    
      	Date rightNow = new Date();
		System.out.println( rightNow );
    }
}
```

There's a few new things here that we haven't seen before. At the very top we have `import java.util.Date;`. This tells Java we want to use the `Date` class. Classes in Java are sorted into _packages_. The Date class is in `java.util` package, which we need to specify as a part of the import statement. I'll go over packages more later.

In the body of the main method we have `Date rightNow = new Date();`. To the left of the `=` assignment operator we declare a variable named `rightNow` that is of type `Date`. 

To the right of the assignment operator we have `new Date()`. The keyword `new` tells Java we're instantiating a new object. `Date` tells Java the type (IE: the class) of object we're creating.

The parenthesis tell Java to call a _constructor_ on the new Date object. A constructor is a special method on an object that is called when the object is instantiated. Constructors are defined by the class. A constructor is used to configure an object before it's used. 

In the example above we're calling a constructor that accepts no arguments. This constructor causes the new `Date` object to use the current date and time. The Date class has [several constructors](https://docs.oracle.com/javase/8/docs/api/java/util/Date.html#constructor.summary).

Here's an example using the deprecated constructor `Date(int year, int month, int date, int hrs, int min)`.

```java
import java.util.Date;

public class Example {
    public static void main(String[] args){

        Date birthday = new Date(1977, 11, 9, 5, 56);
        System.out.println("Doug was born: " + birthday);

    }
}
```
