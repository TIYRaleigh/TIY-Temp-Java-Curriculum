### Boilerplate

All Java files must follow a specific structure. This is the _syntax_ of Java. At an absolute minimum a Java file must contain this:

```java
class Example {}
```

<!-- demo: create this file in a text editor and compile it -->

Even though this code does absolutely nothing, it must be saved in a file named Example.java. For now, I'm going to gloss over the specifics of this code. All you need to worry about is that the text after the `class` keyword must match the name of the file and that the file's extension must be `.java`.

<!-- demo: rename Example and show that it doesn't work -->

Throughout this class we will progressively add more code to files like this one.

For first part of this class we will be creating programs that run from the command line. These are programs like the `ssh-keygen` command we used to create our SSH key when configuring our Github account. 

The Example.java file can't be executed on the command line yet. To do this we need to add more boilerplate code.

```java
public class Example {
    public static void main(String[] args){
        System.out.println("Hello World!");
    }
}
```

This, you can actually run! When run, it will print out "Hello World!" to the terminal.

![Output of Example Hello World.png](https://tiy-learn-content.s3.amazonaws.com/0d74569a-Output%20of%20Example%20Hello%20World.png)

<!-- demo: demo this -->

You may be wondering what all this code means. Don't worry about it. You have to understand a bit of Java before you'll be able to really understand this... Java. It's a bit of a chicken or egg problem.

Here's what I _do_ want you to understand. Do you see the word `main`? `main` is preceded by and followed by gibberish. Let's not worry about the gibberish for now. All you need to know is that this denotes the _main method_, though you don't need to know what a method is. Yet. 

Everything between the first `{` curly brace after the `main` keyword to the subsequent `}` curly brace is called the method *body*.

Ultimately, every Java application has a main method somewhere. This is the starting point for any Java application. It's what Java executes first when you run the application. For now, let's only focus on the `main` method's body. 

This is the body of the `main` method in our `Example.java` file:

```java
System.out.println("Hello World!");
```

While we're getting started, this is where we will put our code. So, if you see a line of code like this:

```java
1+1;
```

You should assume that it's in a `main` method of a file like our `Example.java`.

### Comments

Source code can be inscrutable. Understanding _your own_ code can be challenging, much less someone else's. While your program might make sense to a computer, humans are the ones who have to write and maintain that code. It's essential that we communicate to ourselves and other what exactly we are trying to accomplish. 

_Comments_ denote lines or blocks of text the compiler completely ignores. These are very useful for leaving helpful messages to yourself or others in your source code. For example, you can explain the purpose of a variable, write out the logic behind a block of code, or defend your good honor in the face of bad code. 
You can also use comments to _comment out_ chunks of code you don't want to use, but don't want to delete either. 

I will liberally comment my code through this class. I expect your code to be at least as commented as mine, if not more so.

### Line comments

**Syntax:** `//<your comment>`

Line comments are used to add a comment to a single line of source code. As soon as Java sees `//` it will stop processing anything until the end of that line of text.

```java
public class Example {
    public static void main(String[] args){
    
        // Java will ignore this line.

        // Print out "Hello, world!"
        System.out.println("Hello, world!"); // Java will still process this line, but it will stop as soon as it finds this comment.  

        // int meaningOfLife = 42;
		
    }
}
```

### Block comments

**Syntax:** `/*<your comment>*/`

Block comments are used to add comments that stretch across multiple lines of code. As soon as Java sees `/*` it will stop processing anything until it finds `*/`.

```java
public class Example {
    public static void main(String[] args){
    
        /* 
        This will be ignored
        The contents have no impact
        Share your insights here
        */

        System.out.println("Hello, world!"); 

        /*
        int meaningOfLife = 42;
        int weightPerPigeon = 10;
        */
		
    }
}
```

### Semicolons

Semicolons are extremely important in Java. Every _statement_ must end with a semicolon. A statement is generally a line of code inside a _block_ of code like the `main` method. The semicolon tells Java that it has reached the end of an statement. Since we typically only have one statement per line of code, a semicolon tends to denote the end of a line of code. 

This code won't compile because the statements inside the main method's body aren't terminated with semicolons:

```java
public class Example {
    public static void main(String[] args){
    
        System.out.println("Hello World!")
		
    }
}
```

This, however, will compile:

```java
public class Example {
    public static void main(String[] args){
    
        System.out.println("Hello World!");
		
    }
}
```

Semicolons may seem like a small detail, but it is a **huge** issue. One of the most common problems <span style="text-decoration:line-through;">new</span> programmers have is forgetting semicolons. This often results in error messages that are difficult to understand. These errors are confusing because they tell you where Java _didn't_ find a semicolon, rather than where the semicolon should have been.

<!-- todo: either show an example error message or produce the error in a demo -->

I hope you like semicolons! 
