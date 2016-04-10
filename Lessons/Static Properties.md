**Syntax:** `<access modifier> static <variable definition>`

Consider the numbers pi and e:

* π = 3.14159...
* e = 2.71828...

These values are important mathematically, but never change. 

The `java.lang.Math` class has two static properties for these, `Math.PI` and `Math.E`. 

```java
public class Example {
    public static void main(String[] args) throws Exception  {

        // the radius of a circle
        double radius = 2.5;

        // calculate the area of the circle
        double area = Math.PI * (radius * radius);

        // calculate the circumference
        double circumference = 2 * Math.PI * radius;

        System.out.println("A circle with a radius of " + 2.5 + " inches " +
                "has an area of " + area + " square inches " +
                "and a circumference of " + circumference + " inches.");

    }
}
```

Looking at the example above, you can see that I didn't have to create an instance of the `Math` class to access the `PI` property. Instead, I can access the property directly from the `Math` class itself! 

Static properties are used when a given value doesn't "belong" to a specific instance of an object. Neither `PI` or `E` ever change and are never specific to an instance of "a Math". You don't have your own personal value of pi and I don't have my own value for e.

### Final keyword

**Syntax:** `<access modifier> final <variable definition>`

There is another keyword that's very common when working with static properties: _final_. A final property (static or not) is one that, once set, can never be changed again. Oftentimes these are set in a constructor when the object is instantiated.

The value of `PI` and `E` will never change. Java defines these properties as both static _and_ final. This means that you can't set or change the value of `PI`, only read it.

Static final properties are very often used for _named constants_. A named constant is a value (like pi or e) that never change. In the case of a person, they always have two eyes. We could add this to our `Person` class with a static final property:

```java
public class Person {
    
    /**
     * A static property indicating how many eyes a Person has.
     */
    public static final int NUMBER_OF_EYES = 2;

	// ... other code ...
}
```

### Static property naming convention

We previously discussed the common conventions for naming variables in Java. In the case of static properties, this convention is thrown out the window.

The convention when naming static properties is that they are entirely in upper case and words are separated by underscores. 

Here are some good static property names:

* `NAME`
* `RED`
* `HOURS_IN_DAY`
* `MAX_WEIGHT_PER_PIGEON`

Here are some bad static property names:

* `name`
* `hoursInDay`
* `gdp`
* `wpp`
