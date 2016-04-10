Computers were invented to do repetitive tasks that humans are really bad at. Have you ever lost count of something? Have you forgotten your place in a long list? Luckily, Java won't do that.

There are a few ways to loop over data in Java. We'll touch on three of them here and revisit them again later in the class.

### For loop

<!-- todo: this might be a good place to demo step debugging -->

**Syntax:** 

```java
for(<initializing expression> ; <conditional expression> ; <afterthought expression> ){
	<body to loop over>
}
```

`For` loops seem complicated on the surface, but they're actually pretty simple. Typically, what we're telling Java is that we're going to loop from one value, to another value, stepping incrementally each iteration through the loop.

Let's break down an example `for` loop:

```java
public class Example {
    public static void main(String[] args){
      
		for(int x = 0 ; x <= 10 ; x++){
            System.out.println(x);
        } 
      
	}
}
```

We'll focus in on the first line of code first. The `for` keyword simply tells Java that this is a `for` loop. Inside the parenthesis we have three  distinct expressions separated by semicolons. I'll explain these using my placeholder descriptions I used in the syntax above.

#### Initialization Expression

The first expression in the parenthesis is the initializing expression. The initializing expression is generally used to define a variable and its initial value. In our example it is `int x = 0`. We're telling Java that when we start the loop we have a variable named x and its initial value is 0.

A variable defined here only exists inside the `for` loop's body. Also, while I'd typically discourage the use of a one-letter variable name such as `x`, in this case it's pretty typical. Often iteration variables like this are just used as an index. (IE: get me item 1, get me item 2, get me item 3, etc...)

#### Conditional Expression

The second expression is a conditional expression. Java will continue executing the `for` loop while the conditional is `true`. In our example, the conditional expression is `x <= 10`. Our loop will execute while `x`, the variable we defined in the initialization expression, is less than or equal to `10`.

Be warned, if the conditional expression never evaluates to `false` then the loop will continue forever, causing your program to hang. If you've ever had an application hang on you for no apparent reason, there's a non-zero chance that it was because of an infinite loop.

That said, there are reasons to intentionally put your application into an infinite loop, though it has to be done correctly to prevent your application from hanging or hogging unreasonable system resources.

#### Afterthought Expression

The final expression is the "afterthought" expression. This is executed on each iteration through the loop, after the body of the for loop is executed. In our example the afterthought expression is `x++`. This tells Java that each time we iterate over the loop we should increment `x`, the variable we defined in the initialization expression.

So, putting all of this together, our example loop from above will follow this flow:

1. **Initialization:** Define a variable named `x` and set its value to `0`.

2. **Conditional:** Is `x` less than or equal to `10`? Yes.
3. **Body:** Output `0` to the console.
4. **Afterthought:** Increment `x`, setting it to `1`.

5. **Conditional:** Is `x` less than or equal to `10`? Yes.
6. **Body:** Output `1` to the console.
7. **Afterthought:** Increment `x`, setting it to `2`.

8. **Conditional:** Is `x` less than or equal to `10`? Yes.
9. **Body:** Output `2` to the console.
10. **Afterthought:** Increment `x`, setting it to `3`.

	... ect, etc ...

31. **Afterthought:** Increment `x`, setting it to `10`.

32. **Conditional:** Is `x` less than or equal to `10`? Yes.
33. **Body:** Output `10` to the console.
34. **Afterthought:** Increment `x`, setting it to `11`.

35. **Conditional:** Is `x` less than or equal to `10`? No.

And, we're done with our loop.

It's worth noting at all three of the expressions in the for loop are optional and can be left blank.

<!-- todo: An assignment here might make someone loop backwards from 10 to 0 -->

<!-- todo: demo an infinite loop -->

### While loop

**Syntax:** 

```java
while(<conditional expression>){
	<body to loop over>
}
```

`While` loops are similar to `for` loops, but they only have a single conditional expression. The conditional expression in a `while` loop is executed before the body. 

Here's an example `while` loop that does the same thing as the `for` loop above:

```java
public class Example {
    public static void main(String[] args){
      
		int x = 0;
        while(x <= 10){
            System.out.println(x);
            x++;
        }
      
	}
}
```

Note that in this example we defined our own variable that is an equivalent to the initializing variable in the `for` loop example. We also increment it at the end of the `while` loop's body, just like we did in the afterthought expression in the `for` loop. We don't _need_ to do this, per se, all we need is the conditional expression after the `while` keyword.

Abbreviated, our logic looks like this:

1. Is x less than or equal to 10? Yes
2. Output x and increment it to 1.
3. Is x less than or equal to 10? Yes
4. Output x and increment it to 2.
5. Is x less than or equal to 10? Yes
6. Output x and increment it to 3.

... ect, etc ...

22. Is x less than or equal to 10? Yes
23. Output x and increment it to 11.
24. Is x less than or equal to 10? No.

And, we're done with our loop.

You should note that the conditional expression is evaluated before and after each iteration through the loop.

Remember how I wrote that there were sometimes justifiable reasons to create an infinite loop? Well, one easy way to do that is with this code:

```java
while(true){
	// do something
}
```

In general `while` looks are a lot less common than `for` loops.

### Do while loop

**Syntax:** 

```java
do{
	<body to loop over>
} while(<conditional expression>);
```

The `do while` loop is almost identical to the `while` loop, except that the conditional expression is only evaluated at the end of the loop. The body of the loop is always executed at least once. If the conditional expression evaluates to `true` the loop is run again. This continues until the conditional expression evaluates to `false`.

Here's the same loop from 0 to 10, but in `do while` form:

```java
public class Example {
    public static void main(String[] args){
      
		int x = 0;

        do{
            System.out.println(x);
            x++;
        } while(x <= 10);
      
	}
}
```

One thing to note is that if x were any value at all, this expression would always output it once. For example:

```java
public class Example {
    public static void main(String[] args){
      
		int x = 15;

        do{
            System.out.println(x);
            x++;
        } while(x <= 10);
      
	}
}
```

This will output `15` to the console one time, but will not loop since `15` is greater than `10`.

This is probably the least common form of looping in Java. I don't recommend using it unless you have a good reason.

### Break

**Syntax:** break;

The break expression is used to immediately break out of a loop (or a case statement as we saw previously).

In this example I want to start at a number and loop forward in steps of 3 until I find a number divisible by 7. When found, I want to stop my loop completely:

```java
for (int z = 3 ; ; z += 3) {
    System.out.println(z);

    if (z % 7 == 0) {
        break;
    }
}
```

The output from this example would be:

> 3
> 6
> 9
> 12
> 15
> 18
> 21

<!-- todo: run this code. step through in the debugger. try a few different values of x. -->

This example shows a few interesting things. 

* The initializing expression doesn't have to define a variable named `x` or set it to `0`.
* I didn't define a conditional expression in the `for` loop.
* I'm incrementing by `3`, not `1`, using an operator we haven't seen before. The `+=` operator sets the variable to the left of the operator to the sum of the values to the left and right of the operator. This is a type of assignment operator. There is an equivalent for each of the arithmetic operators.
* I have used nested blocks of code. There's an `if` statement inside our `for` loop's body.
* My conditional expression in the `if` statement uses the remainder  and the equality operators.

There's a lot going on here!

### Continue

**Syntax:** continue;

`Continue` is just like the `break` keyword, except that it only breaks out of the current iteration of the loop. The loop does continue on, we just don't process anything in the loop after the continue statement.

In the following example I'm looping from `1` to `10`, incrementing by 1. On each iteration of the loop I'm outputting "Hey! " without a trailing line break. If `x` is divisible by `3` I skip to the next iteration of the loop. Otherwise, I output x and a new line character and continue the loop.

```java
for (int x = 1; x <= 10; x++) {
    System.out.print("Hey! ");

    if(x % 3 == 0) {
        continue;
    }

    System.out.println(x);
}
```

This example results in this output to the console:

> Hey! 1
> Hey! 2
> Hey! Hey! 4
> Hey! 5
> Hey! Hey! 7
> Hey! 8
> Hey! Hey! 10

This is a rather contrived example of the continue statement since we could have just used an if statement like this:

```java
if(x % 3 != 0){
	System.out.println(x);
}
```

However, you will definitely find places where the continue statement is useful.

### Nested loops

The last thing to note about loops - or really any other blocks of code in Java - is that they can be _nested_ within each other. For example, we could output a times table like this:

```java
public class Example {
    public static void main(String[] args){
      
		for(int x = 1 ; x <= 12 ; x++){

            // print out the columns in this row of the times table
            for(int y = 1 ; y <= 12 ; y++){

                // calculate the product
                int product = x * y;

                // output the product
                System.out.print(product + " ");

            }

            // start a new line
            System.out.print("\n");
        }
      
	}
}
```
