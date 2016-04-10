You can also create arrays of objects like String or our Person class. Since String has a literal form we'll look at that first. The following example creates an array that can hold five instances of String:

```java
public class Main {

    public static void main(String[] args){

        String[] myStuff = new String[5];

        System.out.println(myStuff[3]);

    }

}
```

It is noteworthy that we don't create any instances of `String` in this example. We do create an instance of an array that can hold five `String` objects, but we don't actually assign any String instances into the array. Because of this, our `System.out.println(myStuff[3])` has nothing to print. The output when you run this program is:

> null

Null is the absence of value. This is telling us we have put nothing in the 4th index (`[3]`) of our `myStuff` array. 

We can set `String` objects into array elements just like we did with `int` values.

```java
public class Main {

    public static void main(String[] args){

        String[] myStuff = new String[5];

        myStuff[0] = "Paddle game";
        myStuff[1] = "Remote control";
        myStuff[2] = "Matches";
        myStuff[3] = "Lamp";
        myStuff[4] = "Chair";

        System.out.println(myStuff[3]);

    }

}
```

Now our program outputs:

> Lamp

Arrays work the same with with other types of classes. We can easily create an instance of our Person class:

```java
public class Main {

    public static void main(String[] args){

        try {
            Person[] myPeople = new Person[4];

            myPeople[0] = new Person("Doug", 38, 6);
            myPeople[1] = new Person("Liz", 38, 5.5);
            myPeople[2] = new Person("Collin", 12, 5);
            myPeople[3] = new Person("Audrey", 9, 4.8);

            System.out.println(myPeople[3].describe());

        } catch (Exception e){
            System.out.println(e.getMessage());
        }

    }

}
```

In this example I create an array that holds four `People` objects. I assign four new instances of `Person` into the four array indexes. Lastly I output a description of the `Person` at index 3. 

If I had not assigned a `Person` to one of the indexes then that spot would be `null`.
