**Syntax:** `<access modifier> static <method definition>`

Just like static properties, Java also allows for _static methods_. Static methods also belong to a class, not to an object instance and everything about the lifecycle of a static property applies to a static method.

Because static methods are not instance specific, they can't access an object's instance data. They can only access static properties within the class. Static methods are never used where the state of an object is concerned. 

There are a few examples of static methods in the JCL:

### Static methods for Math

The Math class we were just discussing has more than just two static properties. It also has a bunch of methods for (as you might expect) doing math. We don't ever have an "instance of a math". Math just... is. Thus, it makes sense that these math methods would be static.

Here are a few examples:

* **`abs(value)`**
	Returns the absolute value of the value you provide.
* **`cbrt(value)`**
	Finds the cube root of the provided value.
* **`hypot(side1, side2)`**
	Calculates the length of a hypotenuse of a triangle; the pythagorean theorem.
* **`tan(value)`**
	Gives you the tangent of the provided number.

```java
public class Example {
    public static void main(String[] args) throws Exception  {

        // calculate the distance between two points
        int[] point1 = {3, 1};
        int[] point2 = {-5, 5};

        // calculate the length of x and y
        int x = point2[0] - point1[0];
        int y = point2[1] - point1[1];

        // use hypot() to find the length of the line between the two points
        double dist = Math.hypot(x, y);

        System.out.println(x);
        System.out.println(y);
        System.out.println(dist);

    }
}
```

This example shows a way to calculate the distance between two points, (3,1) and (-5,5). I could have written out ![sqrt of x squared plus y squared.gif](https://tiy-learn-content.s3.amazonaws.com/48babec0-sqrt%20of%20x%20squared%20plus%20y%20squared.gif) as `Math.sqrt(Math.pow(x, 2) + Math.pow(y, 2))`, but the static `hypot()` method was easier.

![distance-between-two-points.png](https://tiy-learn-content.s3.amazonaws.com/51f7eb1d-distance-between-two-points.png)

### Static methods of Calendar

Earlier in the class we touched on the `Date` class. Historically, when working with dates or times you would have used the [`java.util.Date`](https://docs.oracle.com/javase/8/docs/api/java/util/Date.html), [`java.util.Calendar`](https://docs.oracle.com/javase/8/docs/api/java/util/Calendar.html), and [`java.util.TimeZone`](https://docs.oracle.com/javase/8/docs/api/java/util/TimeZone.html) classes. These classes have a number of problems. ([If you're interested, read about them here.](http://www.oracle.com/technetwork/articles/java/jf14-date-time-2125367.html)) 

As of Java 8, Oracle introduced a whole collection of new classes dedicated to working with dates and times. These classes are in the [`java.time`](https://docs.oracle.com/javase/8/docs/api/java/time/package-summary.html) package. For this example we'll focus in on one class in particular, [`java.time.LocalDateTime`](https://docs.oracle.com/javase/8/docs/api/java/time/LocalDateTime.html).

Many of the classes in the `java.time` package have private constructors. Private constructors have the side effect of preventing other classes from creating new instances of a given class. For example, the `LocalDateTime` class has a private constructor. This means that you can't create a new instance of the `LocalDateTime` class. 

![private constructor.png](https://tiy-learn-content.s3.amazonaws.com/dc879ee4-private%20constructor.png)

You may be wondering what use a class that can't be constructed is. But, remember, the constructor is private. This may mean that _you_ can't make a new instance of the `LocalDateTime` class, but it doesn't mean the _class itself_ can't. (Remember, only you can touch your privates!) The `LocalDateTime` class exposes its private constructor through static methods. Presumably this is because constructing a new `LocalDateTime` instance is non-trivial. 

Here are a few ways to create a new `LocalDateTime` instance:

```java
import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.ZoneId;
import java.time.format.DateTimeFormatter;

public class Main {
    public static void main(String[] args){

        // This define formatters for outputting our dates and times
        DateTimeFormatter timeFormat = DateTimeFormatter.ofPattern("h:mm:ss a");
        DateTimeFormatter dateFormat = DateTimeFormatter.ofPattern("MMMM d, y");

        // Get the current time in this time zone
        LocalDateTime now = LocalDateTime.now();

        System.out.printf("The date and time right now is: %s on %s\n",
                now.format(timeFormat),
                now.format(dateFormat));

        // Get the current time in Dubai
        LocalDateTime dubaiNow = LocalDateTime.now(ZoneId.of("Asia/Dubai"));

        System.out.printf("The date and time right now in Dubai is: %s on %s\n",
                dubaiNow.format(timeFormat),
                dubaiNow.format(dateFormat));

        // Get Doug's birthday
        LocalDate birthday = LocalDate.of(1977, 12, 9);

        System.out.printf("Doug was born: %s",
                birthday.format(dateFormat));
    }
}
```
