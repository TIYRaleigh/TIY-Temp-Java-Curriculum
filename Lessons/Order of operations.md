Do you remember [PEMDAS](https://www.mathsisfun.com/operation-order-pemdas.html) from math class? PEMDAS is an acronym used to remember the order that operations must be performed in a mathematical expression. In math this would be:

* Parenthesis
* Exponents
* Multiplication and Division (left to right)
* Addition and Subtraction (left to right)

Using this, we know that `42 - 8 * 34 = -230` because the `*` multiplication operator has higher precedence than the `-` subtraction operator. `8 * 34 = 272` and `42 - 272 = -230`. If we didn't follow the correct order of operations, we might have incorrectly found the answer to be 1156.

### Parenthesis

Just like in math, you can use parenthesis in Java to explicitly indicate order of operations. Java treats each set of parenthesis as a separate expression. Java evaluates parenthesis starting from the innermost pair, and works outward. Each set of parenthesis is replaced with its evaluated value before the outer set of parenthesis are evaluated.

Imagine we have this expression in Java:

```java
(42 - (8 + 24)) * ((7 + (4 + 3)) / 2)
```

Java would step through this like so:

1. `(42 - (8 + 24)) * ((7 + (4 + 3)) / 2)`
1. `(42 - 32) * ((7 + 7) / 2)`
1. `10 * (14 / 2)`
1. `10 * 7`
1. `70`

### Operator precedence

Java evaluates expression based on operator precedence. First expressions in parenthesis are evaluated. After that, or as a part of that, Java will evaluate expressions based on its own order of operations.

1. `++` - prefix or postfix increment
1. `--` - prefix or postfix decrement
1. `-` - unary negation
1. `!` - not
1. `*`, `/`, `%` - multiplication, division and remainder (left to right)
1. `+`, `-` - addition and subtraction (left to right)
1. `==` - equality
1. `!=` - inequality
1. `&&` - logical and
1. `||` - logical or
1. `=` - assignment

I have left out a number of other operators and keywords we haven't discussed. [A full list of operator precedence can be found here.](http://bmanolov.free.fr/javaoperators.php)

Let's take a look at an example expression and determine how Java would evaluate it. This is the same expression as before, just without parenthesis:

```java
42 - 8 + 24 * 7 + 4 + 3 / 2
```

Java will start reading this expression, left to right, looking for operators in order of precedence. First, Java will look for `++` increment operators, then `--` decrement operators, and so on.

Nothing is found until Java starts looking for multiplication, division and remainder operators. Since Java reads left to right, the first operator found is a `*` multiplication operator. The value immediately to the left of the `*` operator is 24 and to the right is 7.

```java
42 - 8 + 24 * 7 + 4 + 3 / 2
```

Effectively becomes...

```java
42 - 8 + (24 * 7) + 4 + 3 / 2
```

... and evaluates to:

```java
42 - 8 + 168 + 4 + 3 / 2
```

Continuing to the right, Java next finds the `/` division operator. The value to the left of the `/` operator is 3 and to the right is 2.

```java
42 - 8 + 168 + 4 + 3 / 2
```

Effectively becomes...

```java
42 - 8 + 168 + 4 + (3 / 2)
```

... and evaluates to:

```java
42 - 8 + 168 + 4 + 1
```

Wait, _**what?**_ How does `3 / 2 = 1`?! Remember that we're working with integers in this expression. In integer division `3 / 2` _is_ 1. If either the 3 or 2 had been a double, the answer would have been 1.5: `3d / 2 = 1.5`.

Having completed evaluating multiplication, division and remainder operators, Java starts looking for addition and subtraction. Again, this is done left to right. Java will first find the `-` operator followed by an `+` operator followed by two more.

```java
42 - 8 + 168 + 4 + 1
```

Effectively becomes...

```java
(42 - 8) + 168 + 4 + 1
```

... and evaluates to:

```java
34 + 168 + 4 + 1
```

The pattern continues.

```java
34 + 168 + 4 + 1
```

... becomes ...

```java
(34 + 168) + 4 + 1
```

... becomes ...

```java
202 + 4 + 1
```

... etc...

```java
(202 + 4) + 1
```

... etc...

```java
206 + 1
```

At last we reach the final expression and evaluate that to 207!

### Operator precedence and logical operators

When writing code, pay particular attention to the order of operations of logical operators. Their precedence, as a subset from above, is:

1. `!` - not
1. `==` - equality
1. `!=` - inequality
1. `&&` - logical and
1. `||` - logical or

Since we're talking about Java, we may as well make a coffee metaphor. A mocha is a coffee drink generally made up of a milk, cream, or similar alternative; caffeinated or decaffeinated espresso; and dark or white chocolate.

![mocha.jpg](https://tiy-learn-content.s3.amazonaws.com/826bb5bf-mocha.jpg)

Let's pretend we had this code telling us what we have or don't have:

```java
boolean milk = true;
boolean cream = false;
boolean soyMilk = false;

boolean caffeinatedEspresso = true;
boolean decaffeinatedEspresso = false;
boolean darkChocolate = true;
boolean lightChocolate = false;
```

Perhaps you could determine if this is a mocha using this expression?

```java
boolean isMocha = milk || cream || soyMilk && caffeinatedEspresso || decaffeinatedEspresso && darkChocolate || lightChocolate;
```

<!-- todo: execute this code and show that it does at least evaluate to true -->

This evaluates to true, so clearly we have a mocha! Awesome! Right? Maybe not. What if we only had milk?

```java
boolean milk = true;
boolean cream = false;
boolean soyMilk = false;

boolean caffeinatedEspresso = false;
boolean decaffeinatedEspresso = false;
boolean darkChocolate = false;
boolean lightChocolate = false;

boolean isMocha = milk || cream || soyMilk && caffeinatedEspresso || decaffeinatedEspresso && darkChocolate || lightChocolate;
```

<!-- todo: execute this code and show that it also evaluate to true (which is bad) -->

Uh oh! According to our logic, milk by itself _is_ a mocha! How can this be? Let's step through like Java would to find out.

Java will step down through operators in their order of precedence, reading left to right. The first operator it will find is the `&&` logical and operator. The value to the left of the first `&&` operator is `soyMilk` and to the right is `caffeinatedEspresso`. Both of these are false. Since the `&&` operator only returns true when both operands are true, this subexpression evaluates to false.

```java
milk || cream || soyMilk && caffeinatedEspresso || decaffeinatedEspresso && darkChocolate || lightChocolate
```

Effectively becomes...

```java
milk || cream || (soyMilk && caffeinatedEspresso) || decaffeinatedEspresso && darkChocolate || lightChocolate
```

... and evaluates to:

```java
milk || cream || false || decaffeinatedEspresso && darkChocolate || lightChocolate
```

Next Java finds the second `&&` operator. `decaffeinatedEspresso` is on the left and `darkChocolate` is on the right. Again, both of these values are false, so this subexpression evaluates to false.

```java
milk || cream || false || decaffeinatedEspresso && darkChocolate || lightChocolate
```

Effectively becomes...

```java
milk || cream || false || (decaffeinatedEspresso && darkChocolate) || lightChocolate
```

... and evaluates to:

```java
milk || cream || false || false || lightChocolate
```

Now we're left with only the `||` logical or operators. Java will evaluate these one at a time, left to right. Only `milk` is true, but the `||` logical or operator returns true if _either_ of the operands are true. This means Java goes through this progression:

```java
milk || cream || false || false || lightChocolate
```

Becomes...

```java
(milk || cream) || false || false || lightChocolate
```

`milk` is true and `cream` is false, so this evaluates to:

```java
true || false || false || lightChocolate
```

Rinse and repeat...

```java
(true || false) || false || lightChocolate
```

Becomes:

```java
true || false || lightChocolate
```

Effectively...

```java
(true || false) || lightChocolate
```

Becomes:

```java
true || lightChocolate
```

And, since `lightChocolate` is false, our final statement effectively becomes:

```java
(true || false)
```

And this, at long last, evaluates to `true`. Thus, we have mistakenly determined that, by itself, milk is a mocha.

![oh shit you did it just like I told you to.jpg](https://tiy-learn-content.s3.amazonaws.com/fb5fd7f5-oh%20shit%20you%20did%20it%20just%20like%20I%20told%20you%20to.jpg)

Dammit Java!

Obviously this isn't true, so what do we do? The first thing we need to do is reconsider what we're trying to express. Starting back at the beginning, we know a mocha has three distinct parts, something milk-ish, espresso of some sort, and chocolate. We only have a mocha if we have all three parts.

We have something milk-ish if we have milk, cream, or soy milk. We have an expression for this: `milk || cream || soyMilk`.

We have something that is espresso only if we have caffeinated or decaffeinated espresso. Again, we have an expression for this: `caffeinatedEspresso || decaffeinatedEspresso`

We have something chocolate only if we have dark or light chocolate. Once again, we have an expression for this: `darkChocolate || lightChocolate`

All we need to do is tell Java to evaluate each of those expressions first and then, if all of those expressions are true, we have a mocha. Luckily this is extremely, painfully, simple. We use parenthesis:

```java
(milk || cream || soyMilk) && (caffeinatedEspresso || decaffeinatedEspresso) && (darkChocolate || lightChocolate)
```

As always, Java evaluates this expression left to right in the order of precedence. Here, Java will first see an expression in parenthesis:

```java
milk || cream || soyMilk
```

Since there are no more _nested_ parenthesis, Java will evaluate this expression:

```java
(milk || cream) || soyMilk
```

`milk` is true, `cream` is false, so `milk || cream` is true.

```java
true || soyMilk
```

`soyMilk` is false, but we already have a `true`, so `true || soyMilk` is true.

Returning to our original expression,

```java
(milk || cream || soyMilk) && (caffeinatedEspresso || decaffeinatedEspresso) && (darkChocolate || lightChocolate)
```

becomes...

```java
true && (caffeinatedEspresso || decaffeinatedEspresso) && (darkChocolate || lightChocolate)
```

`caffeinatedEspresso || decaffeinatedEspresso` is false since both variables are false. So this becomes...

```java
true && false && (darkChocolate || lightChocolate)
```

`darkChocolate || lightChocolate` is also false since both variables are false. So finally we get...

```java
true && false && false
```

`true && false` is false:

```java
false && false
```

Obviously, `false && false` is false. Now we have correctly determined that milk alone does not a mocha make.

My advice to you is to always make judicious use of parenthesis. Be painfully explicit in your logical expressions. This not only helps reduce difficult to debug errors, it also makes your code easier for humans to understand.
