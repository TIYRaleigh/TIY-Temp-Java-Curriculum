In an IntelliJ project we will have numerous files and folders. Most relevant to testing, we will have a `/src` folder and `/test` folder in the root directory of our projects.

![project structure with tests.png](https://tiy-learn-content.s3.amazonaws.com/32349f80-project%20structure%20with%20tests.png)

The `/src` folder contains our class files organized into packages. In this screenshot all of the classes are in the default package. 

The `/test` folder contains all of our test classes. The classes and packages in this directory should correspond (as much as possible) to the classes in the `/src` directory. 

The screenshot above shows a few things. In particular, we have two classes in our `/test` directory, `ExampleTest` and `PersonTest`. These two tests correspond to the `Example` and `Person` classes in the `/src` directory. There are three other classes in the /src directory that are not tested. Don't worry about those, as the screenshot is not from a "real" project. 

<!-- todo: these untested files are stuff I've produced while making materials for this class -->

You create the `/test` folder by right clicking on the project and selecting New > Folder.

![New folder.png](https://tiy-learn-content.s3.amazonaws.com/7be0702b-New%20folder.png)

Next, right click on the new folder and select Mark Directory As > Test Sources Root. IntelliJ will now highlight this folder and files in green to indicate they are tests.

![Mark as test sources root.png](https://tiy-learn-content.s3.amazonaws.com/2f79acf7-Mark%20as%20test%20sources%20root.png)

You can now create packages and classes in your `/test` directory just like you do in the `/src` directory.

<!-- demo: option-enter on class name in .java file to open dialog to create new test. -->
