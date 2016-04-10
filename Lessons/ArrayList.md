ArrayList is a class that is very similar to an array. An ArrayList is just an indexed set of objects, but without the limitations inherent in arrays. 

Here's a quick example similar to previous examples:

```java
import java.util.ArrayList;

public class Main {

    public static void main(String[] args) throws Exception{

        // define our ArrayList
        ArrayList<Person> myPeople = new ArrayList<>();

        // add elements to the ArrayList
        myPeople.add(new Person("Doug", 38, 6));
        myPeople.add(new Person("Liz", 38, 5.5));
        myPeople.add(new Person("Collin", 12, 5));
        // add a person before Collin
        myPeople.add(2, new Person("Audrey", 9, 4.8));

        // output Person 2
        System.out.printf("Person at index 2: %s\n\n", myPeople.get(1).describe());

        // output all people
        for(Person person : myPeople){
            System.out.println(person.describe());
        }
    }
}
```

Since we're using `ArrayList` we must first import the class. Once we do that, we can create a new instance of an `ArrayList` using `new`. The syntax for this is a bit different than what we've seen so far, but we'll come back to that. For now, just know that the `<Person>` bit indicates that the ArrayList only holds `Person` objects. The `<>` in the `new` expression is a syntactic "me too".

Once we have the `myPeople` ArrayList we can start adding elements to the `ArrayList` using its `add()` method. In the example I initially add three people, Doug, Liz, and Collin. Respectively, these have the indexes 0, 1, and 2. 

![arraylist 3 elements.png](https://tiy-learn-content.s3.amazonaws.com/0c396a69-arraylist%203%20elements.png)

You can see that I accessed the second Person by index using the `get()` method: `myPeople.get(1)`, returning Liz. 

Now, let's look at this line:

```java
myPeople.add(2, new Person("Audrey", 9, 4.8))
``` 

The first version we saw of the `add()` method only accepts one argument, the object to append to the end of the list. This version accepts two arguments, the index to insert the object at and the object to add. When we call this method it inserts the object specified in the second argument at the specified index. Anything at or after that point in the `ArrayList` is pushed down one index. 

![arraylist add method.png](https://tiy-learn-content.s3.amazonaws.com/ca75d761-arraylist%20add%20method.png)

Because we retrieved a `Person` using the `get()` method we can immediately call the `describe()` method on the person using _method chaining_. 

At the end of the example we see that we can use foreach syntax to loop over the `ArrayList`. Each time we iterate through the loop we get the next `Person` instance in the `ArrayList`

[`ArrayList` has many useful methods.](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html) Here are some of the highlights:

### add()

**Syntax:** `<ArrayList instance>.add(<object to add>)`

or 

**Syntax:** `<ArrayList instance>.add(<index>, <object to add>)`

Adds the provided object to the `ArrayList`. If the index is not specified the object is appended to the end of the list. If the index is provided the object is added at that index and any objects at or after that index are shifted by one step.

### get()

**Syntax:** `<ArrayList instance>.get(<index of object>)`

The `get()` method returns the object at the specified index.

### contains()

**Syntax:** `<ArrayList instance>.contains(<object the list might contain>)`

The `contains()` method returns a boolean value indicating if the specified object is contained in the `ArrayList`. It's important to note that this must be the exact same object in memory, not just an object that's configured the same as what you're checking for. IE: They have the same `hashCode`.

### indexOf()

**Syntax:** `<ArrayList instance>.indexOf(<object the list might contain>)`

This method is similar to the `contains()` method except that it returns the first index of the specified object if it's found in the `ArrayList`. If the `ArrayList` doesn't contain the object this method returns -1.

See also: [lastIndexOf()](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html#lastIndexOf(java.lang.Object))

### remove()

**Syntax:** `<ArrayList instance>.add(<object to remove>)`

or 

**Syntax:** `<ArrayList instance>.add(<index>)`

The `remove()` method can be used to remove the first instance of the specified object instance from the `ArrayList`. Alternatively, you can specify the index of an element to remove.

### size()

**Syntax:** `<ArrayList instance>.add`

Use `size()` to find out how many elements the `ArrayList` contains.
