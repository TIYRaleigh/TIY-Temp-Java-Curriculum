`HashSet` is another type of collection, but unlike ArrayList and HashMap, they are not indexed. You can't refer to a specific object within a `HashSet`. Also, the objects in a `HashSet` are unique. You can't add the same object twice.

```java
import java.util.HashSet;

public class Main {

    public static void main(String[] args) throws Exception{

        // define our HashSet
        HashSet<Person> myPeople = new HashSet<>();

        // add elements to the HashMap
        myPeople.add(new Person("Doug", 38, 6));
        myPeople.add(new Person("Liz", 38, 5.5));
        myPeople.add(new Person("Collin", 12, 5));
        myPeople.add(new Person("Audrey", 9, 4.8));

        // output all people (note that they're not in the order we inserted them)
        for(Person person : myPeople){
            System.out.println(person.describe());
        }
    }
}
```

This example outputs:

> Collin is 12 years old and 5.0 feet tall. Collin has received 0 high fives.
> Liz is 38 years old and 5.5 feet tall. Liz has received 0 high fives.
> Doug is 38 years old and 6.0 feet tall. Doug has received 0 high fives.
> Audrey is 9 years old and 4.8 feet tall. Audrey has received 0 high fives.

This example looks a lot like the `ArrayList` example. The primary difference is that we can't actually get to "Collin", or "Audrey" directly. Also, we can't add the same object twice. If you try to add the same object twice it is simply ignored, that object is already in the set.

```java
import java.util.HashSet;

public class Main {

    public static void main(String[] args) throws Exception{

        // define our HashSet
        HashSet<Person> myPeople = new HashSet<>();

        // add elements to the HashMap
        Person doug = new Person("Doug", 38, 6);
        Person liz = new Person("Liz", 38, 5.5);

        myPeople.add(doug);
        myPeople.add(liz);
        myPeople.add(liz);

        // output all people (note that they're not in the order we inserted them)
        for(Person person : myPeople){
            System.out.println(person.describe());
        }
    }
}
```

The output here shows that the second time we tried to add "Liz" nothing happened. We only have one Liz:

> Liz is 38 years old and 5.5 feet tall. Liz has received 0 high fives.
> Doug is 38 years old and 6.0 feet tall. Doug has received 0 high fives.

### add() 

**Syntax:** `<HashSet instance>.add(<object to add>)`

The `add()` method adds an object to a `HashSet`. If the object already exists in the `HashSet`, then nothing happens.

### remove() 

**Syntax:** `<HashSet instance>.remove(<object to remove>)`

The `remove()` method removes an object from a HashSet. 

### contains()

**Syntax:** `<HashSet instance>.contains(<object>)`

The `contains()` method returns a boolean indicating whether or not the specified object is in the `HashSet`.

### size()

**Syntax:** `<HashSet instance>.size()`

The `size()` method returns the number of elements in the `HashSet`.

<!-- exercise: write a class that, given two sets, can output where the sets intersect or not. -->
