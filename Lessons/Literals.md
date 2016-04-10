Because Java is strongly typed, you have to specify the type of data that any variable holds. You can only set the variable to values that are of that type. For example:

```java
boolean foo = true;
int x = 123;
double y = 1.23d;
char z = 'z';
```

Let's focus on the values to the right of the `=` assignment operator. These are all _literals_. A literal is a special bit of syntax that instructs Java to create an instance of a specific type of data. Java infers the type of data based on the syntax of the literal.

For example, Java automatically interprets `123` as an `int`. Furthermore, Java knows to interpret `1.23` or `234d` as `double`. `true` is automatically known to be a `boolean`. 

There are other literals in Java which we will cover as we move through the class. In general, literals are the exception. Usually you need to explicitly tell Java to create a new instance of a type of data.
