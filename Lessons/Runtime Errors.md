The first indication something went wrong in your program is usually an error message. These are called _runtime exceptions_. A runtime exception is an error that crops up when you application is running. 

Java does everything it can to prevent runtime errors. This why Java is a compiled language. The process of compiling a program insures that all the required variables, logic, syntax, etc, are correct. 

Remember how Java yells at you if you don't handle an exception that's thrown? You have to either catch it or allow your method to throw it. If an exception is never caught it is eventually dumped to the console and your program is terminated. You might recognize this as a crash. This is why Java tries to force you to handle all exceptions.

Runtime exceptions are, well, the exception to the rule. Java doesn't force you to catch or throw runtime exceptions, though you can.

To resolve runtime exceptions you will need to figure out what's causing the problem and then put logic in place to either prevent the exception or catch the exception.

For example:

### What if you try to divide by zero? That's a `ArithmeticException`!

```java
import java.util.Scanner;

public class Example {
    public static void main(String[] args)  {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Gimme a number to divide: ");
        int numberToDivide = Integer.parseInt(scanner.nextLine());

        System.out.print("What should I divide it by?: ");
        int divideBy = Integer.parseInt(scanner.nextLine());

        int x = numberToDivide/divideBy;

        System.out.println(numberToDivide + " divided by " + divideBy + " equals " + x);
    }
}
```

This `Example` class compiles just fine. But, if you run it and try to divide by zero, this is the output you receive:

```
/Library/Java/JavaVirtualMachines/jdk1.8.0_73.jdk/Contents/Home/bin/java ...
Gimme a number to divide: 50
What should I divide it by?: 0
Exception in thread "main" java.lang.ArithmeticException: / by zero
	at Example.main(Example.java:14)

Process finished with exit code 1
```

This message tells you that there was an exception (`Exception in thread "main"`), what type of exception it was (`ArithmeticException`), and a (hopefully) helpful error message (`/ by zero`). In english we can read this as "There was an arithmetic exception. You can't divide by 0."

Everything following the error message is the _stack trace_. The stack trace is the exact set of method calls Java was executing when the exception was thrown. In this case there was only one method being executed, `Example.main()`. Or, in other words, the `main()` method in the `Example` class. 

We also see the exact line of code where the exception occurred, `Example.java:14`. This tells us the problem was in `Example.java` at line 14. IntelliJ even gives us a link we can click to take us right to that line in that file.

To resolve this problem you could use `try/catch` like this:

```java
import java.util.Scanner;

public class Example {
    public static void main(String[] args) {
        try {
            Scanner scanner = new Scanner(System.in);

            System.out.print("Gimme a number to divide: ");
            int numberToDivide = Integer.parseInt(scanner.nextLine());

            System.out.print("What should I divide it by?: ");
            int divideBy = Integer.parseInt(scanner.nextLine());

            int x = numberToDivide / divideBy;

        System.out.println(numberToDivide + " divided by " + divideBy + " equals " + x);

        } catch (ArithmeticException e){
            System.out.println("Oops, you can't divide by zero.");
        }

    }
}
```

Running this gives you the following output:

> Gimme a number to divide: 50
> What should I divide it by?: 0
> Oops, you can't divide by zero.

You can do the same thing by applying a little logic using `if`:

```java
import java.util.Scanner;

public class Example {
    public static void main(String[] args)  {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Gimme a number to divide: ");
        int numberToDivide = Integer.parseInt(scanner.nextLine());

        System.out.print("What should I divide it by?: ");
        int divideBy = Integer.parseInt(scanner.nextLine());

        if(divideBy != 0) {
            int x = numberToDivide / divideBy;

            System.out.println(numberToDivide + " divided by " + divideBy + " equals " + x);
        } else {
            System.out.println("Oops, you can't divide by zero.");
        }
    }
}
```

### What if you try to access an element of an array that doesn't exist? That's an `IndexOutOfBoundsException`!

Take a look at this code:

```java
import java.util.Scanner;

public class Example {
    public static void main(String[] args)  {

        int[] numbers = {23,743,7,60};

        for(int x = 1 ; x <= numbers.length ; x++){
            System.out.println("The number at position " + x + " is " + numbers[x]);
        }

    }
}
```

This code looks reasonable on the surface. It seems that the programmer wanted to loop over an array of integers and output the value at each index. Let's see what output we get in IntelliJ we get when we run the program:

> Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 4
	at Example.main(Example.java:9)
> The number at position 1 is 743
> The number at position 2 is 7
> The number at position 3 is 60

We get three values printed out and an `ArrayIndexOutOfBoundsException`. Looking at the output, we can see that the value at index 1 is 743. But wait, shouldn't that be 23?! No, arrays are zero-indexed. The programmer should have started the loop at 0.

Now, the error message tells us that there was an  `ArrayIndexOutOfBoundsException`. Additionally, it tells us ": 4". This isn't a terribly verbose message, but it tells us that the `ArrayIndexOutOfBoundsException` occurred when we tried to read the element at index 4. Since arrays are zero index and we have four elements, there is no index 4. Hence, the runtime exception.

### What if I try to use an object, but it's null? That's an `NullPointerException`!

This is the granddaddy of all runtime errors. This error means that you defined a variable to hold a specific type of object, set it to null, and then tried using it. 

Consider this code. It is supposed to prompt a user for their name, age, and height. It uses that to create a new instance of a `Person` and then describe that `Person`. I even went to the trouble of catching number format exceptions incase a user types in something that's not a valid number for the age and height prompts.

```java
import java.util.Scanner;

public class Example {
    public static void main(String[] args)  {
        Scanner scanner = new Scanner(System.in);

        // define a variable to hold our person
        Person person = null;

        // let's collect information about this person
        System.out.print("What is your name?: ");
        String name = scanner.nextLine();

        // declare some default values for age and height
        int age = 0;
        double height = 0;

        // let's collect this information from the user.
        try {
            System.out.print("What is your age?: ");
            age = Integer.parseInt(scanner.nextLine());

            System.out.print("What is your height?: ");
            height = Double.parseDouble(scanner.nextLine());

        } catch (NumberFormatException e){
            System.out.println("Sorry, I didn't understand that number! " + e.getMessage());
        }

        // if we have valid information, let's create an instance of the Person
        if(age != 0 && height != 0){
            try {
                person = new Person(name, age, height);
            } catch (Exception e) {
                System.out.println(e.getMessage());
            }
        }

        // describe the person
        System.out.println(person.describe());

    }
}
```

But, if we run this program and provide a non-numeric value for the age or height we see this output:

> What is your name?: Doug
> What is your age?: 38
> What is your height?: sandwich
> Sorry, I didn't understand that number! For input string: "sandwich"
> Exception in thread "main" java.lang.NullPointerException
> 	at Example.main(Example.java:40)
	
So, while we did handle the potential `NumberFormatException`, we didn't correctly handle the case when we don't instantiate a `Person`. When `age` or `height` are 0 the `person` variable remains set to `null`. `Null`, being the absence of a `Person`, doesn't have a `describe()` method to call. It's like yelling fire in an empty movie theater; there's no one there to hear it. This causes the `NullPointerException`.

To resolve this `NullPointerException` we need to update our logic so that we only try to output the description when we actually have a `Person`.

```java
import java.util.Scanner;

public class Example {
    public static void main(String[] args)  {
        Scanner scanner = new Scanner(System.in);

        // define a variable to hold our person
        Person person = null;

        // let's collect information about this person
        System.out.print("What is your name?: ");
        String name = scanner.nextLine();

        // declare some default values for age and height
        int age = 0;
        double height = 0;

        // let's collect this information from the user.
        try {
            System.out.print("What is your age?: ");
            age = Integer.parseInt(scanner.nextLine());

            System.out.print("What is your height?: ");
            height = Double.parseDouble(scanner.nextLine());

        } catch (NumberFormatException e){
            System.out.println("Sorry, I didn't understand that number! " + e.getMessage());
        }

        // if we have valid information, let's create an instance of the Person
        if(age != 0 && height != 0){
            try {
                // instantiate the person
                person = new Person(name, age, height);

                // describe the person
                System.out.println(person.describe());

            } catch (Exception e) {
                System.out.println(e.getMessage());
            }
        } else {
            System.out.println("I can't describe this person!");
        }
    }
}
```

In this example I just moved the call to `describe()` to a place where I know the `Person` will not be `null`. I also added an error message for when the `Person` would be `null`.

#### The Billion Dollar Mistake

Setting a variable to `null` is called a _null pointer_. IE: The variable is "pointing" at a `null` value. The inventor of the null pointer is a guy named Tony Hoare. He calls the null pointer his billion-dollar mistake.

Here's what he says about it:

> I call it my billion-dollar mistake. It was the invention of the null reference in 1965. At that time, I was designing the first comprehensive type system for references in an object oriented language (ALGOL W). My goal was to ensure that all use of references should be absolutely safe, with checking performed automatically by the compiler. But I couldn't resist the temptation to put in a null reference, simply because it was so easy to implement. This has led to innumerable errors, vulnerabilities, and system crashes, which have probably caused a billion dollars of pain and damage in the last forty years.
