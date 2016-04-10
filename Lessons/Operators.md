![hello operator.jpg](https://tiy-learn-content.s3.amazonaws.com/910fb126-hello%20operator.jpg)

Operators are used to manipulate data. They can act on one, two, or even three individual values. They might modify the data directly or produce an entirely value that we can work with.

[The full set of Java operators can be seen here](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/opsummary.html)

### Assignment operator

**Operator:** `=`

**Syntax:** `<Variable to set> = <Value to assign to the variable>`

We've already seen the assignment operator. The assignment operator is used to set the value of a variable. The variable being set is to the left of the `=` sign. The value to use is to the right of the `=` operator.

```java
public class Example {
    public static void main(String[] args){
    
        boolean skyIsBlue = true;
		boolean oceanIsOrange = false;
		
		System.out.println("The sky is blue: " + skyIsBlue);
		System.out.println("The ocean is orange: " + oceanIsOrange);
		
    }
}
```

Because Java is statically typed, you must always be sure to only assign values to variables of the same type. For example, you can't set a boolean variable to `'c'`.

```java
public class Example {
    public static void main(String[] args){

		// this doesn't work!
        boolean skyIsBlue = 'c';
		boolean oceanIsOrange = false;
		
		System.out.println("The sky is blue: " + skyIsBlue);
		System.out.println("The ocean is orange: " + oceanIsOrange);
		
    }
}
```

That said, there are some places where Java will automatically convert data types for you. For example, you can set a double variable to an integer value. Java will simply convert the integer to a double for you. This is called _widening_. The reason this can be done is that a double can contain all the information in an integer and more.

```java
public class Example {
    public static void main(String[] args){
    
      	// let's make an int
      	int weightAsInt = 190;
      
      	// let's make a double, but set it to an int
		double weightAsDouble = weightAsInt;

      	// hey look, the double became an int!
      	System.out.println("This thing weighs " + weightAsDouble + " pounds.");
    }
}
```

[If you're having trouble sleeping, consider reading more about conversions and promotions in Java.](https://docs.oracle.com/javase/specs/jls/se7/html/jls-5.html)

### Arithmetic operators

Computers excel at arithmetic. After all, that's what they're designed to do!

#### Addition operator

**Operator:** `+`

**Syntax:** `<a value> + <another value>`

**Returns:** The sum of the two values.

The addition operator adds two values together. The value to the left of the `+` sign is added to the value on the right. The resulting value is _returned_. This works more or less as you would think it should.

```java
public class Example {
    public static void main(String[] args){
    
      	int dozen = 4 + 8;
      
      	System.out.println("A dozen is " + dozen + " things.");
      	
      	// Note: this doesn't work as expected without the parenthesis around "dozen + 1". Any ideas why?
      	// Hint: It has something to do with algebra. Think about PEMDAS. 
      	// Another Hint: It also has something to do with handling different data types.
      	System.out.println("A baker's dozen is " + (dozen + 1) + " things.");
    }
}
```

The above example shows that you can combine two or more operators in a single _expression_. Remember that the `=` operator assigns the value on the right into the variable on the left. Logically, Java has to _evaluate_ the value on the right first. The result of that evaluation is what the `=` operator assigns into the variable.

You should also take note that the result of adding 4 to 8 is an integer value. The variable we're setting is also an integer. We always have to be thinking about data types.

<!-- todo: some code examples of the addition operator -->

Going back to the automatic conversions we just discussed, Java will automatically convert some data types for you when using arithmetic operators. For example, adding a double to an integer results in a value that is a double, not an integer.

<!-- todo: ask the class if they can figure out why? -->

```java
double accountBalance = 100 + 12.34d;
```

<!-- todo: explain the example -->

#### Subtraction operator

**Operator:** `-`

**Syntax:** `<a value> - <another value>`

**Returns:** The difference of the two values.

Similar to the addition operator, the subtraction operator subtracts the value to the right of the `-` symbol from the value on the left and returns the result.

```java
public class Example {
    public static void main(String[] args){
    
      	int bottlesOfBeerOnTheWall = 99;
      	int quantityToTakeDown = 1;
      	int remainingBottlesOfBeerOnTheWall = bottlesOfBeerOnTheWall - quantityToTakeDown;
      
      	System.out.println(bottlesOfBeerOnTheWall + " bottles of beer on the wall,");
      	System.out.println(bottlesOfBeerOnTheWall + " bottles of beer!");
      	System.out.println("Take " + quantityToTakeDown + " down,");
      	System.out.println("pass it around!");
      	System.out.println(remainingBottlesOfBeerOnTheWall + " bottles of beer on the wall!");
      	
    }
}
```

#### Multiplication operator

**Operator:** `*`

**Syntax:** `<a value> * <another value>`

**Returns:** The product of the two values.

The multiplication operator multiplies the value to the left of the `*` symbol by the value on the right and returns the result.

```java
public class Example {
    public static void main(String[] args){
    
		int rocksInABox = 9;
      	double rockWeight = 2.34; // pounds
      	double boxWeight = rocksInABox * rockWeight;
      
      	System.out.println("This box of " + rocksInABox + " rocks weighs " + boxWeight + " pounds.");          
    }
}
```

#### Division operator

**Operator:** `/`

**Syntax:** `<a value> / <another value>`

**Returns:** The quotient of the two values.

The division operator divides the value to the left of the `/` symbol by the value on the right and returns the result.

```java
public class Example {
    public static void main(String[] args){
    
		int rocksInABox = 9;
      	double boxWeight = 21.06;
      	double averageWeightOfRock = boxWeight / rocksInABox;
      
      	System.out.println("The average weight of a rock in this box is " + averageWeightOfRock + " pounds.");          
    }
}
```

Division is an interesting beast as far as types are concerned. Consider this example:

```java
public class Example {
    public static void main(String[] args){
      
      	double x = 3/2;
      
		System.out.println(x);          
    }
}
```

You might expect that `3/2` would return `1.5`, a double, but it doesn't. It actually returns `1`! This is because _operands_, `3` and `2`, are integers, not doubles. If at least one of the operands is a double, then the result will be a double.

```java
public class Example {
    public static void main(String[] args){
      
      	double x = 3d/2;
      
		System.out.println(x);          
    }
}
```

Keep in mind that this behavior with integers may actually be useful. For example, imagine you run a breakfast restaurant serving omelets. Each omelet requires 3 eggs and you have 116 eggs total. How many people can you feed?

```java
public class Example {
    public static void main(String[] args){
      
      	int eggsPerOmelet = 3;
      	int numberOfEggs = 116;
      	int maxOmelets = numberOfEggs/eggsPerOmelet;
      
		System.out.println("You can make " + maxOmelets + " omelets!");          
    }
}
```

According this this expression you can feed 38 customers. A nice round integer like 38 is much more useful than 38.666666666666664, since we can't feed two thirds of a person. Granted, we could round this down, but that's another step, and not something you'd know how to do yet.

<!-- todo: ask the class why there's a 4 at the end of 38.666666666666664 -->

You can't divide an integer by zero. However, you can divide a double by zero. If you did the prework [you might have read about this](https://www.ktbyte.com/java-tutorial/book/primitives). In addition to representing normal numbers, doubles can also represent infinity, negative infinity, and _NaN_. NaN stands for Not a Number and means exactly that. Dividing a double by 0 results in infinity.

```java
123d/0;
```

#### Remainder operator

**Operator:** `%`

**Syntax:** `<a value> % <another value>`

**Returns:** The remainder when dividing the two values.

Remember long division from elementary school?

![Long division - the bane of 4th graders everywhere.](https://tiy-learn-content.s3.amazonaws.com/2095fdec-long%20division.gif)

The remainder operator, often called the modulo operator, returns the remainder when dividing the value to the left of the `/` symbol by the value to the right.

Going back to the omelet example, perhaps you want to know how many eggs will be left over if you sell all of your omelets?

```java
public class Example {
    public static void main(String[] args){
      
      	int eggsPerOmelet = 3;
      	int numberOfEggs = 116;
      	int eggsRemaining = numberOfEggs % eggsPerOmelet;
      
		System.out.println("After making all your omelets you will have " + eggsRemaining + " eggs remaining.");
	}
}
```

### Unary operators

Unary operators work with only one operand. Some unary operators modify the operand itself, others simply return the result of the operation.

#### Unary increment

**Operator:** `++`

**Syntax:** `<a variable>++` or `++<a variable>`

**Returns:** It depends...

The unary increment operator is used to add 1 to a variable. This example shows how a variable `x` is incremented. The result of this is that `x` becomes 124.

```java
public class Example {
    public static void main(String[] args){
      
      	int x = 123;
		System.out.println("x is " + x);
      
		x++;
		System.out.println("x is now " + x);
	}
}
```

The `++` symbol can be placed before or after a variable. However, the location of the operator changed its behavior subtly. This is because the unary increment operator doesn't only modify the variable being incremented, it also returns one of two values, depending on where the operator is placed.

Placing the operator after the variable increments the variable and returns the value of the variable _before_ it is incremented.

```java
public class Example {
    public static void main(String[] args){
      
      	int x = 123;
		System.out.println("x is " + x);
      
      	int y = x++;
      
		System.out.println("y is " + y); // maybe not what you'd expect.
		System.out.println("x is now " + x);
	}
}
```

You can read the last line of this sample as, "set y to the value of x, then increment x by 1." In this example `x` becomes 124 and `y` becomes 123.

Placing the operator before the variable causes the variable to be incremented before the new value is returned.

```java
public class Example {
    public static void main(String[] args){
      
      	int x = 123;
		System.out.println("x is " + x);
      
      	int y = ++x;
      
		System.out.println("y is " + y); // probably what you'd expect.
		System.out.println("x is now " + x);
	}
}
```

You can read the last line of this sample as, "increment x by 1 and then set y to the value of x." In this example both `x` and `y` become 124.

#### Unary decrement

**Operator:** `--`

**Syntax:** `<a variable>--` or `--<a variable>`

**Returns:** It depends...

Similar to the unary increment operator, the unary decrement operator subtracts 1 from a variable.

```java
public class Example {
    public static void main(String[] args){
      
      	int x = 123;
		System.out.println("x is " + x);
      
		x--;
		System.out.println("x is now " + x);
	}
}
```

In this example `x` becomes 122.

As with the unary increment operator, the placing the `--` operator before the variable returns the result after the variable has been decremented. Placing the `--` operator after the variable returns the variable before it is decremented.

#### Unary negation

**Operator:** `-`

**Syntax:** `-<a variable or value>`

**Returns:** A negated value.

Just like in math, you use the negation operator to denote negative numbers.

```java
public class Example {
    public static void main(String[] args){
      
      	int x = -123;
		System.out.println("x is " + x);
      
	}
}
```

It can also be used to negate values, again, just like it math. The negative of a negative is positive.

```java
public class Example {
    public static void main(String[] args){
      
      	int x = -123;
      	
      	// y is the negative value of x. A negative negative is a positive.
		int y = -x;
      
		System.out.println("x is " + x);
		System.out.println("y is " + y);
      
	}
}
```

In this example `y` becomes 123.

### Comparison operators

Very often we need to compare values. Java provides a set of operators we can use to compare two values.

#### Equality operator

**Operator:** `==`

**Syntax:** `<a value> == <another value>`

**Returns:** True if the value on the left is equal to the value on the right.

The equality operator `==` is simple, it just checks to see if two values are the same. If so, true; if not, false.

```java
public class Example {
    public static void main(String[] args){
      
      	System.out.println(5 == 5);
		System.out.println(5 == 6);
      
	}
}
```

Since 5 does, in fact, equal 5 the first line evaluates to true. However, since 5 is not 6, the second line evaluates to false.

Be sure to note that the equality operator, `==`, is completely different from the assignment operator, `=`. The former checks to see if two values are equal while the latter sets the value of a variable. It is a common error to accidentally use the assignment operator when you mean to use the equality operator.

<!-- todo: demonstrate that you can't write code like 5 = 5 -->

#### Inequality operator

**Operator:** `!=`

**Syntax:** `<a value> != <another value>`

**Returns:** True if the value on the left is _not_ equal to the value on the right.

The inequality operator `!=` is the exact opposite of the equality operator, it checks to see if two values are different. If different, true; if the same, false.

```java
public class Example {
    public static void main(String[] args){
      
		System.out.println(5 != 5);
      	System.out.println(5 != 6);
      
	}
}
```

Since 5 doesn't equal 6 the first line evaluates to true. However, since 5 is the same as 5, the second line evaluates to false.

#### Greater Than Operator

**Operator:** `>`

**Syntax:** `<a value> > <another value>`

**Returns:** True if the value on the left is greater than the value on the right.

```java
public class Example {
    public static void main(String[] args){
      
		System.out.println(5 > 5);
      	System.out.println(5 > 6);
      	System.out.println(6 > 5);
      
	}
}
```

#### Less Than Operator

**Operator:** `<`

**Syntax:** `<a value> < <another value>`

**Returns:** True if the value on the left is less than the value on the right.

```java
public class Example {
    public static void main(String[] args){
      
		System.out.println(5 < 5);
      	System.out.println(5 < 6);
      	System.out.println(6 < 5);
      
	}
}
```

#### Greater Than Or Equal To Operator

**Operator:** `>=`

**Syntax:** `<a value> >= <another value>`

**Returns:** True if the value on the left is greater than or equal to the value on the right.

```java
public class Example {
    public static void main(String[] args){
      
		System.out.println(5 >= 5);
      	System.out.println(5 >= 6);
      	System.out.println(6 >= 5);
      
	}
}
```

#### Less Than Or Equal To Operator

**Operator:** `<=`

**Syntax:** `<a value> <= <another value>`

**Returns:** True if the value on the left is less than or equal to the value on the right.

```java
public class Example {
    public static void main(String[] args){
      
		System.out.println(5 <= 5);
      	System.out.println(5 <= 6);
      	System.out.println(6 <= 5);
      
	}
}
```

### Comparison Operators Notes

Be aware that comparison operators can only be used with two values, the value to left of the operator and the value to the right of the operator. Whereas in math we can write ` 1 < x < 10`, that will result in an error in Java.

### Logical Operators

So far we've seen how to modify, combine, and compare values using arithmetic, unary, and comparison operators. Now we need to learn how to make decisions accordingly.

Logical operators return boolean true or false values. We can use these to control how our programs behave.

#### Logical And

**Operator:** `&&`

**Syntax:** `<a boolean value> && <another boolean value>`

**Returns:** True if both boolean values provided are true, otherwise false.

In programming you will often want to make decisions based on one or more conditions. For example, among other criteria, [NASA will only launch a rocket if](http://www.nasa.gov/centers/kennedy/news/releases/2003/release-20030128.html) the wind speed is below 42 knots and the sky is clear. This can be expressed using the logical and operator.

```java
public class Example {
    public static void main(String[] args){
      
		double currentWindSpeed = 26.4;

        boolean windSpeedOk = currentWindSpeed < 42;
        boolean skyIsClear = true;

        boolean goForLaunch = windSpeedOk && skyIsClear;
      
      	System.out.println("Go for launch?: " + goForLaunch);
      
	}
}
```

In this example we determine that we are go for launch because the wind speed is below the allowed threshold and the sky is clear.

However, if the wind speed is too high, the sky isn't clear, or both, then the `goForLaunch` would be false.

#### Logical Or

**Operator:** `||`

**Syntax:** `<a boolean value> || <another boolean value>`

**Returns:** True if either or both boolean values are true, false if both values are false.

The logical or operator is similar to the "and" operator, but is only false if both operands are false.

```java
public class Example {
    public static void main(String[] args){
      
		boolean iWantTea = false;
      	boolean iWantCoffee = true;
      
      	boolean iWantAWarmBeverage = iWantTea || iWantCoffee;
      
      	System.out.println("Do I want a warm beverage?: " + iWantAWarmBeverage);
      
	}
}
```

#### Logical Not

**Operator:** `!`

**Syntax:** `!<a boolean value or variable>`

**Returns:** The opposite of the boolean value provided.

In English the word "not" negates what comes next. The not operator in Java does the same thing. Essentially you can make something not-true or not-false using the `!` operator.

```java
public class Example {
    public static void main(String[] args){
      
		boolean oppositeOfTrue = !true;
        boolean oppositeOfFalse = !false;
      
      	System.out.println("The opposite of true is " + oppositeOfTrue);
      	System.out.println("The opposite of false is " + oppositeOfFalse);
      
	}
}
```

You might want to note that there a few ways that people refer to the `!` symbol. Non-programmers would call this an exclamation point. We all know it's not. Some programmers like to call `!` "bang". In this class we'll call it "not" as in, "not true" or "not false".

### Other Operators

There are a number of other operators we haven't covered because they're not important at this point. You can [read more on Java operators here](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/operators.html).
