An Integrated Development Environment (IDE) is a type of tool that programmers use to write code. IDEs are essentially a pain text editors with features that make programming easier.

### Common Java IDEs

There are numerous IDEs used for writing Java code. To a big degree, the IDE one uses is just a preference. One _feels_ better to you than all of the others. You might choose to use one just because it's familiar. On the other hand, your future employer might dictate an IDE that everyone uses at work. In this class we'll be using IntelliJ Ultimate. 

* **IntelliJ IDEA**

	![intellij-logo.png](https://tiy-learn-content.s3.amazonaws.com/7c509c5b-intellij-logo.png)

	[IntelliJ](https://www.jetbrains.com/idea/) IDEA Ultimate is an awesome IDE by [JetBrains](https://www.jetbrains.com/). It slices, it dices, it even makes julian fries. Seriously, it's great. This is what we'll be using. I almost never remember to call it Idea, IntelliJ is quite sufficient.

* **Eclipse**

	![eclipse logo.png](https://tiy-learn-content.s3.amazonaws.com/9d6d1fbe-eclipse%20logo.png)

	[Eclipse](http://www.eclipse.org/) is an very power IDE. It's open source and can do everything IntelliJ does.

* **NetBeans**

	![netbeans logo.png](https://tiy-learn-content.s3.amazonaws.com/3518ea1e-netbeans%20logo.png)

	I've never used NetBeans, but I know it's a thing. If you're curious about it, go check it out.

* **Others**

	If you google [Java IDE](https://www.google.com/search?q=java+ide&oq=Java+IDE&aqs=chrome.0.0l3j69i60j0l2.196j0j4&sourceid=chrome&ie=UTF-8) you'll find dozens of options. Developers like their tools.

### Code insight

An IDE _parses_ your code to understand how it works. Parsing is the process of breaking your code into parts to analyze how it works. By doing this, an IDE can make suggestions as you type your code. The suggestions are extremely helpful because it can difficult to remember certain keywords and syntax as you program.

![code insight.png](https://tiy-learn-content.s3.amazonaws.com/9caed340-code%20insight.png)

Many IDEs support multiple languages, allowing you to use one tool while writing many different types of code.

### Build and Run

IDEs tools to _compile_ your source code. Compiling is how your source code is turned from plain text into something a computer can execute.

IDEs allow programmers to compile and execute the programs they are writing. As you work, you will want to make small changes and then test them to make sure they work correctly. Not having to switch out of the IDE to see your program work can streamline your workflow and help you stay in the zone.

![Run code in IDE.png](https://tiy-learn-content.s3.amazonaws.com/a8cded3e-Run%20code%20in%20IDE.png)

### Step debugging

One of the most critical features of an IDE is step debugging. Using any modern IDE for Java you can add _stop points_ to your code. Stop points instruct the IDE to pause execution of your program on a specified line of code.

While paused, you are able to inspect the state of your program, checking that variables and values are changing as you expect. You can also step through code, one line at a time and make sure that your logic is working correctly.

![debugger.png](https://tiy-learn-content.s3.amazonaws.com/7bc610dd-debugger.png) 

### Test execution

One of the most important aspects of programming is being able to effectively test your code. While you could point and click or type to try to test your application, it quickly becomes nearly impossible to do this for every change you make. Sometimes small changes in one part of you application may have unexpected ramifications in a different part of your application. If you don't test everything every time you can find your self surprised by bugs, even some bugs you thought you'd already squished!

One tool programmers use to mitigate this are _unit tests_. Unit tests are small scripts that test the various components that make up your program. Each script, a test, either passes or fails. An IDE will make it easy to run your tests to see what's broken.

![failing test.png](https://tiy-learn-content.s3.amazonaws.com/2f4a184f-failing%20test.png)

### Refactoring and code generation

Many IDEs have tools to help generate or reorganize code. Frankly, I don't want you to think too much about this now. In fact, pretend I never said anything.
