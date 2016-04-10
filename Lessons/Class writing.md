**Syntax:**

```java
<access modifier> class <Class name>{
	<body of class>
}
```

The syntax described above is not exhaustive, but it will do for now. We're going to start out with only the most basic of classes and build up to much more complex classes as we move through our material. The syntax shown above is very minimal and focused on what we care about right now.

You might remember that the very first class we saw was this:

```java
class Example {}
```

This class has no access modifier and no body, but it is entirely valid. Because there is no access modifier, only classes in the same directory can instantiate this class.

Since classes are supposed to represent concepts, let's make a class that models a person. Let's start our person model with the most minimal code required:

```java
public class Person {}
```

Note that `Person` is capitalized. It is _convention_ in Java to capitalize class names. Don't be "that person" who doesn't capitalize their class names. This file this class is in must be named Person.java. 

I gave the Person class a `public` access modifier. This access modifier tells Java that any other Java code is allowed to instantiate this class. We're not going to concern ourself with any other class access modifiers for now.

Let's create another class with a `main` method. We can use this to experiment with our `Person` class as we go along.

```java
public class Main {
    public static void main(String[] args){
        Person doug = new Person();

		System.out.println(doug);
    }
}
```

In this example we're creating a new variable of type `Person`. The variable's name is `doug` and we're assigning a new instance of a `Person` object to that variable. We're also outputting Java's own `String` representation of the variable to the console. The output looks something like this:

> Person@511d50c0

The first part of the output is the class name. The second part, after the @ sign, is the hash code of this object instance. The hash code uniquely identifies this instance of this class. Each time you run this program you will get a different hash code. You, as a developer, can change what is output here and we'll do that later on.

### Instances

```java
public class Main {
    public static void main(String[] args){
        Person doug = new Person();
        Person liz = new Person();

		System.out.println(doug);
		System.out.println(liz);
    }
}
```

Here we have added a second instance of the Person object. Note that the output shows this:

> Person@511d50c0
> Person@60e53b93

The hash code for these two objects are different because they are different instances of the object. In your computer's memory, these two objects are sitting in different places. 

We can make two different variables reference the exact same object. 

```java
public class Main {
    public static void main(String[] args){
        Person doug = new Person();
        Person liz = doug;

		System.out.println(doug);
		System.out.println(liz);
    }
}
```

This outputs:

> Person@511d50c0
> Person@511d50c0

In this case, the hash code is the same because both variables reference the same instance of the Person object. 

Imagine a person holding an apple. Now, imagine a different person holding another apple.

* How many people are there? Two.
* How many apples are there? Two. 

Now imagine those same two people. They are both holding onto the same apple. (Perhaps they're fighting over it?!)

* How many people are there? Two.
* How many apples are there? One. 

Multiple variables can _point_ to the same object instance.
