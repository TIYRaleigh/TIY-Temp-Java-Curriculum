### Java is a programming language

In English we know that we start sentences with capitol letters and end them with periods, question marks, or exclamation points. We know the basic sentence structure of "subject verb noun". Sentences can be collected together to communicate complex messages. This is the _syntax_ of English. All human languages have their own syntax.

All programming languages also have their own syntax. Java code is written in Java's syntax. Unlike spoken languages, a programming language's rules are very strict. In English, a missing comma isn't the end of the world. You can usually intuit what a writer is trying to communicate, even if their grammar isn't perfect. However, computers do not have intuition. They require very precise and particular instructions, communicated in exactly the right manner. Missing even a single semicolon will prevent your program from working at all. Seriously!

The programming language Java is the syntax you use to tell the computer what it is supposed to be doing.

```java
public class HelloWorld {

    public static void main(String[] args) {
        System.out.println("Hello, world!");
    }

}
```

This file must be named HelloWorld.java for it to compile.

![Screen Shot 2016-04-04 at 12.52.19 PM.png](https://tiy-learn-content.s3.amazonaws.com/5b77edad-Screen%20Shot%202016-04-04%20at%2012.52.19%20PM.png)

### What is a compiler?

Computers only speak one language: Binary. Ones and zeros. That's it. A CPU receives instructions in binary and it does exactly what the instructions tell it to do. Unfortunately, humans don't speak binary. Perhaps we could memorize it? Back in the dark ages of programming, this is essentially what programmers did. Mnemonics, known as _assembly code_, were created that humans could more easily memorize. A programmer would write assembly code and later _manually_ translate to binary.

![Example assembly and binary instructions](https://tiy-learn-content.s3.amazonaws.com/aeef70ab-example%20assembly%20and%20binary%20instructions.png)

No mere mortal wants manually translate assembly code to binary. Good programmers are often lazy, and so eventually programs were created to translate assembly code into binary instructions automatically. These were the first _compilers_.

A compiler takes source code written in a programming language and translates it into binary instructions a CPU can understand.

Over time, compilers mature and add features that take us further from the world of assembly to the world of modern programming languages.

But, there's a catch! Different CPUs speak _different_ binary languages! This means that we need different compilers for different CPUs. Mix in the complexities of supporting different operating systems, and it becomes very difficult to write a program that is _cross platform_. A cross platform program is one that can be run on multiple operating systems and CPU architectures.

This is why there so many applications only run on one platform. An application written to run on iOS on an iPhone can't work on Android, much less Windows 10.

### The Java compiler

The Java compiler is, well, a compiler. Surprise!

However, unlike traditional compilers that write binary instructions for a particular CPU and OS, the Java compiler writes its own dialect of binary called _Java bytecode_. Java bytecode isn't created for any particular CPU or OS. In fact, by itself, Java bytecode is essentially useless.

The java compiler can be executed on the command line using the `javac` command line program.

The command line program we use to compile java code is is `javac`. 

![Screen Shot 2016-04-04 at 12.54.04 PM.png](https://tiy-learn-content.s3.amazonaws.com/8a92bce7-Screen%20Shot%202016-04-04%20at%2012.54.04%20PM.png)

### The Java Runtime Environment

Since a Java program is not compiled for a specific CPU or OS, we can't just execute it like any other program. Instead, we need the Java Runtime Environment. This is the "Java" you have probably downloaded and installed many times over.

The JRE is actually a virtual computer. It simulates the CPU and hardware of a real computer. Just like any other CPU, Java's virtual CPU has its own instruction set. This instruction set is Java bytecode! As the JRE executes your program, it actually compiles the Java bytecode into binary instructions your computer can execute. This process is called Just in Time (JIT) compiling. A handy side effect of this is that Java bytecode can be executed anywhere the JRE can be installed, regardless of hardware or operating system.

Through this process of JIT compiling, thee JRE effectively hides from the programmer everything that makes a particular CPU or OS unique. The computer itself becomes a black box to a Java developer. We no longer care what CPU or OS we're using. We no longer care about the _implementation_, we only care that it works. The JRE takes care of everything else for us.

This process of hiding implementation details is called _abstraction_. Abstraction will be a theme in this class.

<!-- demo: actually run the program using java. note the syntax: java helloworld.class -->

### The Java Development Kit

The Java Development Kit is key to all of the above. It provides everything we need to make Java applications. In particular, the JDK provides the `javac` command we use to compile Java code.

The JDK also includes the JRE, which provides the `java` command we use to execute our Java bytecode. Many other useful tools are included for debugging, analyzing code, and packaging applications for distribution.

We installed the JDK during the install party.

### So, what _is_ Java?

Java is a collection of tools used to compile and execute code written in the Java programming language.
