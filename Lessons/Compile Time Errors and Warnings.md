Programming languages are not forgiving. If your source code has any syntax problems you won't even be able to compile it, much less run it. This is called a _compile time error_. There are many reasons a compile time error might crop up, but, thankfully, modern IDEs are really good at helping you find and fix them.

In addition to error messages, the compiler may also output _warnings_. Warnings are messages telling you that you've written code that Java compiled, but which might be problematic now or in the future. For example, you will receive warnings if you try to compile code that depends on deprecated methods in the `Date` class.

### Missing Semicolon

As we know, semicolons are required to terminate expressions in Java. If you forget a semicolon you'll get a compile time error. This is what you might see in IntelliJ if you forget a semicolon:

![missing semicolon.png](https://tiy-learn-content.s3.amazonaws.com/12864ffd-missing%20semicolon.png)

Let's break this down:

`Information:Using javac 1.8.0_73 to compile java sources`

Line one of the message tells us we're compiling with version 1.8.0_73 of the javac compiler.

`Information:java: Errors occurred while compiling module 'Java Curriculum'`

Line two tells us that errors were encountered while compiling our project.

`Information:3/28/16, 1:32 PM - Compilation completed with 1 error and 0 warnings in 1s 159ms`

This tells us that there was only 1 error found and no warnings.

```
/Users/doug/Projects/Java Curriculum/src/Person.java
	Error:(83, 71) java: ';' expected
```

This is the important bit in the error message. The first line here tells us that `/Users/doug/Projects/Java Curriculum/src/Person.java` is the file that couldn't be compiled. The second line tells us where Java thinks the semicolon is missing, `(83, 71)`. The first number, 83, is the line number, and the second, 71, is the column number in `Person.java`. It just so happens that this is exactly right. 

Happily, IntelliJ has many inspections that help notify us of problems in our code. IntelliJ lights up like a christmas tree when something goes wrong.

![intellij inspection error indications.png](https://tiy-learn-content.s3.amazonaws.com/3cb63171-intellij%20inspection%20error%20indications.png)

### Missing curly braces

Missing curly braces can be a royal headache. Check out this error:

<!-- todo: this next bit is crap. I need a clear head to write this -->

![missing curly brace  error.png](https://tiy-learn-content.s3.amazonaws.com/ec2b01e3-missing%20curly%20brace%20%20error.png)

Javac is reporting 6 compilation errors! Oh no! I can easily tell that the problem file is `/Users/doug/Projects/Java Curriculum/src/Person.java`. But, the error messages are misleading. They suggest either a missing semicolon or something wrong with the start of an expression. None of these say anything about curly braces.

In this situation IntelliJ again saves our bacon. 

![missing curly brace.png](https://tiy-learn-content.s3.amazonaws.com/5c009c68-missing%20curly%20brace.png)

First off, notice that the file with the problem is marked with a red squiggly line. Then, within the problem file, the scroll bar area on the right has a red line. If you scroll over this red line you can find a bit of code with a red squiggly line. Finally, hovering over the red squiggly line gives you a useful message: '}' expected. This is exactly correct!

Note that IntelliJ correctly identified line 93 as being the problem. The output from javac was not nearly as useful.


### IntelliJ to the rescue!

In general, since we're working with a modern IDE, you won't run into too many of these problems. IntelliJ tries to make problem code _really_ obvious. For example, here I didn't provide the parenthesis when calling  the `describe()` function on a `Person` object.

![missing parens.png](https://tiy-learn-content.s3.amazonaws.com/6c0dd9dd-missing%20parens.png)

Of note, the actual message reported, "Cannot resolve symbol 'describe'", might be a bit misleading. We know we added a describe method to the `Person` class, but IntelliJ is saying it doesn't exist. 

That's not quite right. IntelliJ isn't saying the method doesn't exist, it's saying the `Person` class doesn't have a public property named `describe`. There's a difference. 

A computer can't intuit that you might mean to call the `describe` function. You are explicitly telling it to look for a property named `describe`. 

#### Side note about being explicit 

So, why couldn't Java be made to figure out that I want to call the `describe` function when one exists and there is no `describe` property? Technically speaking, this isn't impossible, Oracle could update Java and add this as a feature. The logic is fairly simple. The problem is, we begin to enter a gray area. 

What happens if we have both a property named `describe` and a method named `describe`? How would Java know which to use? Perhaps we could add rules to the language to define when each is used? Sure, but it adds complexity to the language. 

The more esoteric rules  programmers must remember, the harder it is to write programs. These types of rules can lead to unexpected bugs. It's also inconsistent. You'd be able to treat a method with no arguments differently than a method with arguments. It's hard to read - how would _you_ know what was being referred to. On top of everything, any extra processing slows applications down.

It's just easier for everyone - you _and_ the compiler - if we just keep the language simple and explicit. 
