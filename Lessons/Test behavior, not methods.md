The general rule in testing is not to test functions. Writing a bazillion tests to test getter and setter methods that just change property values is, at best, boring. At worst, it's a waste of time to write the tests and a waste of time to run them.

Instead of writing tests for methods, focus on writing tests for behaviors. To identify behaviors, first think about the responsibilities of your class. Look at the relevant methods and try to think about the different paths that could be taken through the code and be sure to test each one.

* **Loops** - Look for loops in your code and ask your self some questions.
	* What impacts the loop? 
	* What happens if you loop over nothing? 
	* What happens when you loop over one item? 
	* What happens when you loop over many items?
* **Conditionals** - Think about the different conditions your code is aware of.
	* Under what conditions will each block of code execute? 
	* What is the default condition?
* **Exceptions** - Think about the different ways in which exceptions are intentionally thrown.
* `Variants` - Consider the data you're working with. 
	* What different variations are expected?
	* What if a variable is null?
	* What happens if a given boolean variable is true vs. false?
	* What specific values change behavior?

By giving deliberate thought to your class' responsibilities and behaviors you can identify many useful test cases. I don't necessarily need to write every single test case either. Pick the most important ones and write those. If you run into a problem write a test that fix the problem and write a test that shows that the problem is resolved.

In general, experiment, but realize that testing is a critical habit to form and often a differentiating factor between mediocre programmers and amazing programmers.
