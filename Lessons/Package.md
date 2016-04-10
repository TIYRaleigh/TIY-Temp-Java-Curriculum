**Syntax**: `package <dot notated path to package>`

When you start organizing your classes into packages you will need to specify the name of the package your class is in on the first line in your class. 

For example, if we move our `Person` class into the `com.theironyard.example` package, we would need to add a package statement like this:

```java
package com.theironyard.example;

public class Person {
    /**
     * The person's name.
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
}
```

![person in package.png](https://tiy-learn-content.s3.amazonaws.com/b25267a0-person%20in%20package.png)
