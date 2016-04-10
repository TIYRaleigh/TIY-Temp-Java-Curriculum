Let's focus back on this line from the `ArrayList` example:

```java
ArrayList<Person> myPeople = new ArrayList<>();
```

This expression includes two things we haven't seen before, `<Person>` and `<>`. These are called _generics_. Generics are used to specify what type of  data a collection contains. Another way of saying this is that collections are generic, they can hold any type of data. This can be a bad thing. Generics are used to specify that a generic collection is explicitly holding a specific type of object.

To understand this, let's create a list that doesn't use generics:

![no generics on arraylist.png](https://tiy-learn-content.s3.amazonaws.com/0c0d6778-no%20generics%20on%20arraylist.png)

Here I've removed the generics. This shows us that IntelliJ, at least, doesn't like this. It's warning us we're performing an unchecked operation. This means is that Java is going to treat whatever we store in the `ArrayList` as the most generic type of object (`Object`). In effect, Java doesn't know that the `ArrayList` contains `Person` instances. That's why we're seeing the error on line 19. Java doesn't know that this object has a `describe()` method any more, so we can't call it. 

Not using generics allows us to put any type of data in the Array, even types that aren't explicitly the same. For example:

```java
import java.util.ArrayList;
import java.util.Date;

public class Main {

    public static void main(String[] args) throws Exception{

        // define our ArrayList
        ArrayList myPeople = new ArrayList();

        // add elements to the ArrayList
        myPeople.add(new Person("Doug", 38, 6));
        myPeople.add(new Person("Liz", 38, 5.5));
        myPeople.add(new Person("Collin", 12, 5));
        myPeople.add(new Person("Audrey", 9, 4.8));
        myPeople.add(new Date());

        // describe person 4
        System.out.println(myPeople.get(3));
        // describe index 5
        System.out.println(myPeople.get(4));
    }
}
```

This outputs the following:

> Person@511d50c0
> Thu Apr 07 08:25:52 EDT 2016

Java knows every object it works with can be printed to the console one way or another and that's what it does here. But, because it doesn't know a `Date` from a `Person`, we can't call the `describe()` method of our `Person` instances.

Even if we have a compelling reason to have different types of data in an ArrayList (which we probably don't), we should still specify a generic of `<Object>`. `Object` is the _base class_ in Java. It can stand in for any other class.

See, no ugly messages:

![generic object arraylist.png](https://tiy-learn-content.s3.amazonaws.com/4fb0dcab-generic%20object%20arraylist.png)

In a nutshell, always use generics. 
