**Syntax**: `import <package>.<class>`

By default, if you have classes in the same package they can all instantiate, call methods on, and access properties of each other (unless the constructors, methods, or properties are private). All classes also automatically  have access to all classes in the [`java.lang` package](https://docs.oracle.com/javase/8/docs/api/java/lang/package-summary.html).

To use any other classes you must specify the package name. One way to do this is to just specify the entire package name whenever you use the class. For example, our `Person` class is now in a package named `com.theironyard.example`. Our `main` method now would look like this:

```java
public class Main {
    public static void main(String[] args){

        // create a Person for Doug
        com.theironyard.example.Person doug = new com.theironyard.example.Person();
        doug.name = "Doug";
        doug.age = 38;
        doug.height = 6.0;

        // create a Person for Liz
        com.theironyard.example.Person liz = new com.theironyard.example.Person();
        liz.name = "Liz";
        liz.age = 38;
        liz.height = 5.5;

        // Print details to the console
        System.out.println(doug.name + " is " + doug.age + " years old and " + doug.height + " feet tall.");
        System.out.println(liz.name + " is " + liz.age + " years old and " + liz.height + " feet tall.");
    }

}
```

Notice all the uses of `com.theironyard.example.Person`. This is the _fully qualified name_ of the `Person` class. It is rather ugly, to put it nicely. 

Without us specifying the `com.theironyard.example` package, Java  doesn't know to look there for the class named `Person`. Luckily, there's another way to tell Java where to look for classes; the import statement. The import statement lets you access the class by name alone by telling Java where to look for it. 

We add an `import` statement to our `Main` class like this:

```java
import com.theironyard.example.Person;

public class Main {
    public static void main(String[] args){

        // create a Person for Doug
        Person doug = new Person();
        doug.name = "Doug";
        doug.age = 38;
        doug.height = 6.0;

        // create a Person for Liz
        Person liz = new Person();
        liz.name = "Liz";
        liz.age = 38;
        liz.height = 5.5;

        // Print details to the console
        System.out.println(doug.name + " is " + doug.age + " years old and " + doug.height + " feet tall.");
        System.out.println(liz.name + " is " + liz.age + " years old and " + liz.height + " feet tall.");
    }

}
```

### Wildcard imports

**Syntax**: `import <package>.*`

You don't necessarily have to import individual classes. You can also import _all_ of the classes in a given package. For example, if I wanted to import all of the classes in the `java.math` package I could use this import statement:

```java
import java.math.*;

// ... other code goes here ...
```

This is not typically done. Chances are that you're not actually using all of the classes in a package. It's cleaner to indicate which specific  classes you are using explicitly. It also helps speed up compiling time. Beyond that, IDEs like IntelliJ do a really good job of helping you manage your imports. 

### IDE Managed

If you use attempt to use a class that hasn't been imported yet, IntelliJ will highlight it in red.

![class not imported.png](https://tiy-learn-content.s3.amazonaws.com/b22902a6-class%20not%20imported.png)

IntelliJ can also help you manage your import statements. As you type, IntelliJ will check to see if a class you're trying to use has been imported. If not, it will give you a list of packages and classes to choose from or automatically import the correct class.

![suggesting a class.png](https://tiy-learn-content.s3.amazonaws.com/ab14d681-suggesting%20a%20class.png)

### Default imports

By default, Java automatically imports the entire [java.lang package](https://docs.oracle.com/javase/8/docs/api/java/lang/package-summary.html). This package includes classes that represent primitives (Integer, Double, Boolean), String, and other commonly used classes. This is why you can use the String class without needing to explicitly import it.

### Conflicting class names

Java ships with no less than three `Color` classes:

* `javafx.scene.paint.Color`
* `java.awt.Color`
* `com.sun.prism.paint.Color`

You can't import more than one of these classes at a time. Doing so is an error.

![duplicate import.png](https://tiy-learn-content.s3.amazonaws.com/9d5601e9-duplicate%20import.png)

If you really need to use two (or more) classes that have the same name, you will have to either address both classes using their fully qualified name or import one class and reference the others by their fully qualified name. For example:

```java
import javafx.scene.paint.Color;

public class Main {
    public static void main(String[] args){

        Color javaFxRed = new Color(255, 0, 0, 1);

        java.awt.Color awtBlue = new java.awt.Color(0, 0, 255, 255);
        
    }
}
```
