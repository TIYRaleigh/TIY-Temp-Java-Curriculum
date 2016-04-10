**Syntax:** `<data type>[] <variable name> = new <data type>[<number of elements in the array>]`

An `array` is a _data structure_ that can hold a specified number of elements of a specified data type in a specified order. A data structure is a just a collection of data stored in computer memory in some particular (but irrelevant to us) order. 

![pillbox.jpg](https://tiy-learn-content.s3.amazonaws.com/124d2124-pillbox.jpg)

Arrays are the most simplistic way of collecting lists of data in Java. Let's take a look at a simple example of an array.

```java
public class Main {

    public static void main(String[] args){

        // create a new array of ints with 7 elements
        int[] x = new int[7];

        // put some values in the first 5 places
        x[0] = 543;
        x[1] = 9213;
        x[2] = 687;
        x[3] = 698;
        x[4] = 6;

        System.out.println(x[3]);
    }

}
```

This example shows how we create a new array, put values into the array, and read a specific value from the array. 

The first line we're concerned with is `int[] x = new int[7]`. 

Breaking this down, we first come across `int[] x`. We already know that the `int` keyword tells Java we're working with integers. The `[]` square brackets means that this is an array. In other words, we're telling Java that we're creating an array to hold `int` values. Seeing the `x`, we know that we are creating a variable named `x` that will refer to our array of `int` values.

Next, we find the `=` assignment operator. We already know this means that the value to the right of the operator will be assigned into the variable on the left. Since we've declared that the variable on the left refers to an array of int values, we know that the expression to the right of the operator must _be_ an array of int values.

Finally we come to `new int[7]`. Again, we already know that the `new` keyword is used to create a new instance of an object. Again, the `int` keyword indicates that we're working with `int` values. The `[7]` at the very end is similar to the `[]` to the left of the `=` operator. Again, the square brackets indicate that this is an array. The value inside the square brackets indicates how many `int` values the array can hold.

Putting it back together, this line tells us that we're creating a variable named `x` to hold an array of `int` values. We're using this variable to refer to a specific new array of seven `int` values.

Now let's look at the next few lines of code:

```java
x[0] = 543;
x[1] = 9213;
x[2] = 687;
x[3] = 698;
x[4] = 6;
```

You'll have noted that these all follow the same pattern: `x[<index>] = <some int value>`. In particular, let's break down the first line, `x[0] = 543`:

The first thing we come across is `x`. This is our variable. We declared that this variable was an array of int values. Next we find `[0]`. As always, the square brackets tell us this has something to do with an array. 

Peeking ahead, we see the `=` assignment operator. The assignment operator gives us a hint about what the `[0]` means. We know the assignment operator assigns the value on the right to the variable on the left. That means `x[0]` must be a variable. We also know that variable names are only allowed to have alphanumeric and underscore characters. This means `x[0]` must be a special type of variable, which it is. 

Arrays hold a specified number of elements of a specified data type in a specified order. As such, the `[0]` is telling us which _index_ of the array we're working with. An index is a specific _element_ in an array. An element is one distinct value; in this case an int value. So, the `[0]` tells us we're working with the "zeroth" element in the array.

You already know the assignment operator well.

Putting this line back together, it tells us that we're assigning the value `543` into the array of `int` values named `x` at it's zeroth index.

For all intents and purposes, x[0], x[1], ..., and x[7] are all distinct variables. They just happen to be collected together into a specific order.

Arrays in Java are _zero indexed_. A zero indexed array is an array where the first element is at the 0th spot. In fact, everything in Java is zero indexed. Any time you need to get to the first element in a collection you will go to the 0 index. 

To complicate matters, you have to remember that when you declare a new array you specify the number of elements in the array. That means that `new int[7]` is creating an array with 7 elements with indexes 0 to 6.

This can be confusing since this isn't how humans intuitively count. If you're the next person to be served at a bank, you'd say you're first in line. Java would say you're zeroth in line. As you move forward in your programming career and learn more languages you will find that almost all of them are zero indexed. 

Returning to the five lines of code above, we now know that we're assigning 5 distinct `int` values into the first five elements (0 to 4) in the array of `int` values we're calling `x`. 

The final line of relevant code in our `main()` method is `System.out.println(x[3])`. We already know that `System.out.println()` prints text to the console. Since there's no assignment operator to be seen, we know that we must be reading `x[3]` which we now know is the `int` value in index 3 of the array. Humans would call this the 4th value in `x`. From the assignment block we know this was set to `698`. Indeed, when you run the program, this is what's printed out.

> 698
