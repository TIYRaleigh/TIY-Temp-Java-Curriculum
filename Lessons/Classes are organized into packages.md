Java comes with a staggering number of classes; more than **_20,000_**! These classes that Java includes are called the _Java Class Library_ (JCL). Beyond that, there are probably hundreds of millions (as a guess) of classes created by Java developers every year. 

**Question:** How likely do you think it is that none of these classes have the same name?

**Answer:** 0%. 

**Question:** How likely is it that there are projects that need to use more than one of these classes that share the same name?

**Answer:** 100%

So, how do we distinguish between different classes with the same name? The answer is _packages_. Packages are basically folders on disk where we place our classes. 

So far, we've only used the root, unnamed, package. This means that our Java class files are in the root of the source directory.

![no packages.png](https://tiy-learn-content.s3.amazonaws.com/95e6ae12-no%20packages.png)

The sample project above has a number of classes, but they are all in the root package. On disk, all the files are in the same directory.

By contrast, the image below shows a project where the class files have been organized into packages.

![has packages.png](https://tiy-learn-content.s3.amazonaws.com/dc77f5de-has%20packages.png)

This project has four packages:

* com.theironyard
* com.theironyard.controllers
* com.theironyard.entities
* com.theironyard.services

On disk, these packages are actually just nested directories:

![packages on disk.png](https://tiy-learn-content.s3.amazonaws.com/a425b706-packages%20on%20disk.png)

The classes in this project have been organized into packages by concept. All of the entities and services are in their respective packages.

Returning to Java's extensive class library, it too is organized into packages. Obviously, owing to the size of the JCL, there are many hundreds of packages. This is important because, even within the JCL, there are several classes that have the same names. A good example of this would be `Color`. Java has two different classes named `Color` in two different packages.

* java.awt.Color
* javafx.scene.paint.Color

On disk, you can imagine that these two classes are sorted into different folders. 

### Package naming conventions

Package names typically follow a specific convention. Packages that are distributed with Java start with "java". 

* **java.***
	The `java` package contains the core Java classes.

* **javax.***
	The `javax` package contains extensions on the core Java class library. Originally these classes were considered optional, but over time they've become integral to Java. In a nutshell, this package is essentially the same as the `java` package, but with a different name.

* **javafx.***
	This package contains all of the classes related to the JavaFX desktop user interface library.

<!-- todo: do I need to explain what domain names are? -->

Packages not created by Oracle typically follow a reverse domain name scheme. For instance, we could have placed our `Person` class in a package `com.theironyard`. In fact, this is the scheme that was used in the previous screenshot. 

The reverse domain name approach is very handy because, for the most part, every company has its own domain name on the internet, and the domain name is distinct. 

On the internet we have many _top level domains_ (TLD). The most familiar of these are probably `com` and `org`. The Iron Yard's domain name is theironyard.com. This can be translated as the `theironyard` domain in the `com` top level domain. We can be even more specific by adding a subdomain such as `www` or `online`. 

In general, a given project in a company or organization gets a unique name. So, if [The Iron Yard Online](https://online.theironyard.com) was written in Java, its root package would likely be `com.theironyard.online`.
