Step debugging is probably the most powerful tool at your disposal for debugging your code. At it's heart, step debugging allows you to place _stop points_ in your code. Stop points are places where the debugger will pause the execution of your program and allow you to examine the values of your variables, run expressions, and even make some changes.

I'll go over some of the main points below, but [you can find out all sorts of details about the IntelliJ debugger here.](https://www.jetbrains.com/help/idea/2016.1/debugging.html?origin=old_help)

### Break points

Break points indicate places where you want to pause execution. To add a break point in IntelliJ, open the file you want to debug and click to the right of the line number you want want to pause at.

![set breakpoint.gif](https://tiy-learn-content.s3.amazonaws.com/e5db764d-set%20breakpoint.gif)

In the example above, I set a break point at line 16 of `Main.java`. The debugger will pause each time it reaches this line, _before_ it executes the line.

### Start the debugger

To start the debugger, just click the debug icon to the right of the run icon in the toolbar. The shortcut for this is ctrl-d. As soon as your program reaches a break point it will stop and wait for your instructions.

![start debugger.gif](https://tiy-learn-content.s3.amazonaws.com/c03eda66-start%20debugger.gif)

This shows the debugger being started and then pausing at the stop point on line 16. When this happens the debug window is displayed. 

### Inspecting variables

When the debugger is stopped I can use the debug window to inspect variables. The code being debugged creates a multiplication table. Perhaps I want to watch the values as they are added to the matrix to make sure they're correct.

![watches and variables.gif](https://tiy-learn-content.s3.amazonaws.com/c3aef5c8-watches%20and%20variables.gif)

In this example I add three watch expressions. These are expressions that Java will evaluate when execution is paused. This lets me see the values of `x`, `y`, and the expression `x * y`. Using this, I can step through the code until we reach a point where `x * y` isn't zero. 

Once we've started creating some non-zero values I go into the variables pane and inspect the products array. I can expand it to see the set of 13 arrays that it holds (0 to 12). I can also expand each of those array. When I look at the array at index 0, I can see that all the values are 0, which is what I expect. When I look at the next array I see that we have set some of the values. I then continue execution a few times to show how the products array is updated on each iteration through the loop.

### Reload Changed Classes

IntelliJ also provides a nice feature to allow you to reload changed classes. This can be used while debugging to make changes and test them as you make the changes. The biggest limitation to this is that you can't reload the currently executing function.

![reload classes.gif](https://tiy-learn-content.s3.amazonaws.com/23d90a84-reload%20classes.gif)

There is a lot going on in this demo. In a nutshell, I've written a program to create an array of 8 `Person` objects and loop over it to output descriptions. I show you how I can step into and over code using the debugger and how you can see output to the console (IE: print debugging). After outputting a few descriptions I change the `describe()` function in the `Person` class and reload it using `Run > Reload Changed Classes`. The next time the `describe()` method is called it returns the updated message.

### Inline debugging

One more feature of the debugger in IntelliJ is _inline debugging_. Inline debugging shows the values of variables on each line as you execute them. 

![inline debugging.gif](https://tiy-learn-content.s3.amazonaws.com/aec1fb2a-inline%20debugging.gif)

[There's more information on inline debugging here.](https://www.jetbrains.com/help/idea/2016.1/inline-debugging.html?origin=old_help)
