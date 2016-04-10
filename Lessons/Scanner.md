Most useful programs require some form of user input. So far, all of our programs have been quite static. They set some static, unchanging, variables, apply some logic, and output the same result every time.

There are many ways to handle user input in Java, one of which is the [Scanner](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html) class. One use for the Scanner class is to read user input on the command line. Check this out:

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args){

        // setup our scanner
        Scanner input = new Scanner(System.in);

        // ask the user who they are
        System.out.print("What's your name? ");

        // read their answer
        String name = input.next();

        // Ask the user to describe themselves
        System.out.print("What is one word that describes you? ");

        // read their answer
        String description = input.next();

        // Greet the user
        System.out.printf("Hi there %s, you glorious %s person!\n", name, description);
    }
}
```

The first thing we do here is to create a new instance of the `Scanner` class. In the constructor we're telling `Scanner` to read from the _stdin_. Stdin means standard input. IE: command line input. As a user types into the console `Scanner` will collect their input. We can read this input using methods that `Scanner` provides. 

After asking the user their name we use the `Scanner` class' `next()` method to read the user's name. What this is really doing is reading the stdin until it finds a line break character. Next, we ask for a descriptive word and read the input again using `next()`. This second call reads from where the previous call ended to the next line break. In this manner, we can read the user's input to prompts.

[`Scanner` provides many methods](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html#method.summary) for reading input, but in general we'll likely stick with `next()`.
