We'll focus on a technique for TDD called Red Green Refactor. Red Green Refactor is a cyclical process:

1. **Red**
	First, you start by writing just enough unit testing code that your test fails.
2. **Green**
	Next, you write just enough code that your test passes.
3. **Refactor**
	Finally, you go back and clean up your code.

As a developer, you simply repeat this process over and over again. As you work the process you will build a very cohesive set of tests and classes that are closely related. The tests will help you catch _regressions_ as you evolve your code. A regression is a test that used to pass but which is now failing.
