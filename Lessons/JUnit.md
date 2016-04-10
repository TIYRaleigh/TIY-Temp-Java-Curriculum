[JUnit](http://junit.org/junit4/) is a _unit testing_ _framework_ for Java. Unit tests are separate code you write to test your production application's code. A framework is a collection of classes and other resources that standardize how certain programming tasks are accomplished. So, JUnit is a collection of classes and tools used to test the code you're writing. JUnit is just one of many testing frameworks in Java, but it's one we're using in class.

<!-- explain that this is an xUnit-style framework. JUnit wasn't the first, but it's been very influential -->

Unit tests are called unit tests because each test intentionally tests a  very small portion of your larger program. You will write many tests to test an entire application. These tests help confirm that new changes don't don't break existing features of your program. They can also offer insight into how your existing systems work

<!-- todo: many applications have thousands of tests -->
<!-- todo: maybe show the tests for larger systems? something open source? -->

Unit tests are only for programmers. They're not typically packaged and shipped as a part of the software being built. They're not used by anyone other than programmers. The application itself doesn't _depend_ on the unit tests, since the tests are not required for the application to function. However, the tests depend on the application because, well, the application must exist to be tested. 
