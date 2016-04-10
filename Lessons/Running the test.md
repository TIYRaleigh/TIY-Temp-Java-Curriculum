
A test isn't any good unless we can run it. Happily, IntelliJ has features built in to make running tests very easy. When looking at a test in IntelliJ, there are green icons to the left of the class method declarations.

![run tests.png](https://tiy-learn-content.s3.amazonaws.com/a3f3a378-run%20tests.png)

If you click the icon next to the class declaration all of the methods annotated with `@Test` will be executed. If you click an icon next to a specific test method, only that method will be executed. 

You can also run all of the tests in the `/test` folder or any package therein by right clicking on the `/test` folder or a specific test package and clicking on it and selecting Run 'All Tests'.

![run all tests.png](https://tiy-learn-content.s3.amazonaws.com/74d7c776-run%20all%20tests.png)

When tests are run, IntelliJ will show a window displaying progress and results.

![test results.png](https://tiy-learn-content.s3.amazonaws.com/5d589cb9-test%20results.png)

This screenshot shows the `whenHighFiveReceivedThenHighFiveCountIncreases` test passing. We now know that this behavior works as expected. You will quickly learn that the color green is your favorite color. 
