**Syntax:** 

```java
<access modifier> <Class name>(<constructor arguments){
	<body of constructor>
}
```

Constructors are defined within the curly braces that denote a class' body. Typically constructors are placed after class properties. You can have many constructors, so long as they each have different arguments. This is called _constructor overloading_.

Constructors are used to define the initial state of a new object. For our Person class, the default state is that a person has no name, is 0 years old, and is 0 feet tall. This isn't a very good model of reality. Let's add a constructor to resolve this problem:

```java 
/**
 * The Person class represents a person.
 */
public class Person {
    /**
     * The person's name
     */
    public String name = "";

    /**
     * The person's age
     */
    public int age = 0;

    /**
     * The person's height
     */
    public double height = 0;

    /**
     * Create a Person and set the default values;
     * @param name The person's name
     * @param age The person's age
     * @param height The person's height
     */
    public Person(String name, int age, double height){
        this.name = name;
        this.age = age;
        this.height = height;
    }

}
```

Let's look only at the Person constructor we added:

```java
public Person(String name, int age, double height){
	this.name = name;
	this.age = age;
	this.height = height;
}
```

In this example the access modifier is `public`. This means that any other code can call this constructor when instantiating a new `Person` object. For now, we're only going to worry about public constructors.

The next word in the constructor is "`Person`", which must match the class name, and therefore the file name. This is how Java knows that this chunk of code is a constructor. 

What follows next are a the constructor's _arguments_. An argument is a variable passed into a block of code when it's invoked. This constructor takes three arguments when a Person is instantiated, all of which must be provided. These are name, age, and height, which are respectively String, int and double variables. We can use these variables inside the body of the constructor.

Everything between the curly braces is the body of the constructor. In this example the body is:

```java
this.name = name;
this.age = age;
this.height = height;
```

The body of the constructor introduces a new keyword, `this`. The `this` keyword is a reference to the current instance of an object. The `doug` variable we've been working with is an instance of the `Person` class. That instance has it's own state that is distinct from the state of the `liz` instance. The `doug` instance's `this` scope refers only to the properties on the `doug` instance. The `liz` instance's `this` scope refers only to the properties on the `liz` instance.

So, `this.name = name` sets the current instance's name property to be the value passed into the `name` argument. 

Now, when we create a new instance of a `Person` class we must provide three constructor arguments, `name`, `age`, and `height`. Here's how we'd do that:

```java
public class Main {
    public static void main(String[] args){

        // create a Person for Doug
        Person doug = new Person("Doug", 38, 6.0);

        // create a Person for Liz
        Person liz = new Person("Liz", 38, 5.5);

        // Print details to the console
        System.out.println(doug.name + " is " + doug.age + " years old and " + doug.height + " feet tall.");
        System.out.println(liz.name + " is " + liz.age + " years old and " + liz.height + " feet tall.");
    }

}
```

Adding the constructor has enforced our requirement that new instances of `People` be given a name, age, and height. We can still modify these properties after the object is constructed, if we want.
