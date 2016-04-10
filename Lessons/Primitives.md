_Primitives_ are the most basic type of data in Java. They are pure, simple, values and serve as building blocks for more complex types of data.

Previous examples in this class have used the primitive data type of integer. An integer is one of many primitive data types.

The most common primitive data types are:

* **boolean** A value indicating true or false.
* **integer** A whole number.
* **long** A (potentially very big) whole number.
* **double** A (potentially very big) decimal number.
* **char** A single character.

We'll skip over the other primitives. [You can get more details about primitive data types here.](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)

### Boolean

**Keyword:** `boolean`

Booleans are primitive values that indicate _true_ or _false_.

Is 12 greater than 42? `False`.

Is Doug an Iron Yard instructor? `True`.

We can use boolean values to make decisions and control what our application does. For example, we can check to see if a user is logged into our application. If not (`false`) they are sent to a login form. If so (`true`), they may use the application.

```java
public class Example {
    public static void main(String[] args){
    
        boolean skyIsBlue = true;
		boolean oceanIsOrange = false;
		
		System.out.print("The sky is blue: ");
      	System.out.println(skyIsBlue);
      
		System.out.print("The ocean is orange: ");
      	System.out.println(oceanIsOrange);
		
    }
}
```

### Integer

**Keyword:** `int`

Integers represent whole numbers. Whole numbers are the numbers we count with, 1, 2, 3..., etc.

In Java, integers are any whole number from -2,147,483,648 to 2,147,483,647.

_Note: Java's syntax for integers does not allow for commas!_

Here are some example integers:

* -2147483648
* -7836832
* -74
* 0
* 1
* 42
* 90032
* 2147483647

These are _not_ integers:

* -123.456
* 0.57721
* 3.1415
* 4.6692
* 90032.0000000001


```java
public class Example {
    public static void main(String[] args){
    
        int speedLimit = 35;
		int actualSpeed = 47;
		
		System.out.println("The speed limit is: " + 35);
		System.out.println("You were actually going: " + 47);
		
    }
}
```

### Double

**Keyword:** `double`

Doubles represent decimal numbers. Unfortunately, it is difficult to represent decimal numbers precisely in binary. Because of this, doubles are actually _estimates_ of decimal value. This can be a problem when comparing values. We'll come back to this.

Doubles should not be used when doing anything with money. If you need that, take a look at [BigDecimal](https://docs.oracle.com/javase/8/docs/api/java/math/BigDecimal.html).

Doubles can be any number from -9,223,372,036,854,775,808 (very small) to 9,223,372,036,854,775,807 (exceptionally large). Again, you can't actually use commas in Java numbers.

Here are some example doubles:

* -2147483648
* -7836832
* -123.456
* -74
* 0
* 0.57721
* 1
* 3.1415
* 4.6692
* 42
* 90032
* 90032.0000000001
* 2147483647

You can add a "d" onto the end of a number to explicitly differentiate doubles from integers:

* 0.57721d

or

* 90032d


```java
public class Example {
    public static void main(String[] args){
    
        double pi = 3.1415926535;
		double weight = 190d;

      	System.out.println("Pi to 10 digits is: " + pi);
      	System.out.println("This thing weighs " + weight + " pounds.");
    }
}
```
Double are sometimes called _floating point numbers_. There is  another data type in Java named _float_ that also represents floating point numbers. The value range for floats is smaller than doubles (and ints). Therefore, floats are less precise than doubles. For everything we're going to do in this class, doubles should be sufficient.

### Char

**Keyword:** `char`

A char represents a single character. For example:

* a
* Z
* 9
* @
* ë
* ß

```java
public class Example {
    public static void main(String[] args){
    
        char theFirstLetter = 'a';
        char theLastLetter = 'Z';
		char ampersand = '&';
		
      	System.out.println("These chars are: " + theFirstLetter + " " + ampersand + " " + theLastLetter);
      
    }
}
```

As you can imagine, a single character has limited utility. We'll need to find a way to collect a sets of characters together to form words and sentences. We'll get back to this later.

### Null

**Keyword:** `null`

Null is not actually a type of data. Null is the absence of value. It is not zero. It is not anything. It is the black hole of values.

Null can be used to tell Java that there is no value for a variable. For example, what is the address of a homeless person? Null. They have no address.

<!-- todo: see if the class can come up with their own examples of null -->

```java
public class Example {
    public static void main(String[] args){
    
        String address = null;
		
      	System.out.println(address);
    }
}
```
