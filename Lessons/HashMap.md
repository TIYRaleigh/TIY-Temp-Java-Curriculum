The Hashmap class holds a collection of objects indexed by other objects. Where an ArrayList stores objects in an ordered list and indexes them using integers, a HashMap does not guarantee the order of elements and indexes them by any other object. 

```java
import java.util.HashMap;
import java.util.Map;

public class Main {

    public static void main(String[] args) throws Exception{

        // define our HashMap
        HashMap<String, Person> myPeople = new HashMap<>();

        // add elements to the HashMap
        myPeople.put("Doug", new Person("Doug", 38, 6));
        myPeople.put("Liz", new Person("Liz", 38, 5.5));
        myPeople.put("Collin", new Person("Collin", 12, 5));
        myPeople.put("Audrey", new Person("Audrey", 9, 4.8));

        // output Person Collin
        System.out.printf("Collin: %s\n\n", myPeople.get("Collin").describe());

        // output all keys people (note that they're not in the order we inserted them)
        for(Map.Entry<String, Person> personEntry : myPeople.entrySet()){
            System.out.printf("%s: %s\n", personEntry.getKey(), personEntry.getValue().describe());
        }
    }
}
```

This example is a bit more complex than what we've seen so far. First off, we import two classes, `java.util.HashMap` and `java.util.Map`. The `HashMap` class is our HashMap. The `Map` class isn't actually a class, it's an interface. We'll get to what an interface is later. Suffice it to say that it's basically a more generic class than `HashMap`. 

```java
HashMap<String, Person> myPeople = new HashMap<>();
```

This line of code creates our `HashMap`. As with `ArrayList` we have generics that we use to specify what the `HashMap` contains, but these generics have two items, `String` and `Person`. This is because we're telling the `HashMap` not only what type of data it's collecting (`Person`), but also what type of data we're using to index it (`String`). 

The next chunk shows how we add Person objects into our HashSet:

```java
myPeople.put("Doug", new Person("Doug", 38, 6));
```

The put() method accepts the key - the value you're indexing the set by, in this case "Doug" - and the object you're putting into the collection.

We can retreive specific values from the HashMap using its get() method:

```java
myPeople.get("Collin")
```

This gets the `Person` that has the key "Collin". Because we used generics, Java knows that this is a `Person` object.

There are many ways to get the elements in a HashMap. For this example I elected to use the `entrySet()` method. This method returns a `Set`. `Set` is another type of collection that contains only unique elements and not in any particular order. This specific `Set` contains five distinct `Map.Entry` objects. `Entry` is a _nested class_ in the `Map` class. We're accessing it via dot notation.

Each `Entry` has two properties, `key` and `value`, which we access using getters. Because we're using generics, Java knows that the data types for `key` and `value` are `String` and `Person` respectively. `Key` is what we indexed the `Person` by in the `HashMap`. `Value` is the `Person` we stored.

```java
for(Map.Entry<String, Person> personEntry : myPeople.entrySet()){
    System.out.printf("%s: %s\n", personEntry.getKey(), personEntry.getValue().describe());
}
```

Because `Set` objects are iterable we can use the foreach syntax and get a `Map.Entry` instance on each iteration. Inside the body of the loop we get the `String` `key` using `getKey()` and the `Person` using `getValue()` from the `Map.Entry`.

Maybe we want to have a HashMap that indexes ArrayLists of People by a date (perhaps their hire date or birthday). This shows how you might do that:

```java
import java.time.LocalDate;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.Map;

public class Main {

    public static void main(String[] args) throws Exception{

        // define our HashMap
        HashMap<LocalDate, ArrayList<Person>> peopleByDate = new HashMap<>();

        // Add the people associated with 12/9/1977
        LocalDate date1 = LocalDate.of(1977, 12, 9);

        ArrayList<Person> people1 = new ArrayList<>();
        people1.add(new Person("Doug", 38, 6));
        people1.add(new Person("Liz", 38, 5.5));

        peopleByDate.put(date1, people1);

        // Add the people associated with 3/1/2016
        LocalDate date2 = LocalDate.of(2016, 3, 1);

        ArrayList<Person> people2 = new ArrayList<>();
        people2.add(new Person("Collin", 12, 5));
        people2.add(new Person("Audrey", 9, 4.8));
        people2.add(new Person("Chris", 48, 5.9));

        peopleByDate.put(date2, people2);

        // output the HashMap
        System.out.println(peopleByDate + "\n");

        // Output this stuff in a more readable manner:

        // loop over each key/value pair in our peopleByDate object
        for(Map.Entry<LocalDate, ArrayList<Person>> datePeople : peopleByDate.entrySet()){
            // output the date
            System.out.println(datePeople.getKey());

            // output the people associated with this date.
            // remember that the value is actually an ArrayList
            for(Person person : datePeople.getValue()){
                System.out.printf("\t%s\n", person.getName());
            }
        }
    }
}
```

[`HashMap` has many useful methods.](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html) Here are some of the highlights:

### put()

**Syntax:** `<HashMap instance>.add(<key>, <object to add>)`

The `put()` method adds an object to a `HashMap`, using the specified key to index it.

### get()

**Syntax:** `<HashMap instance>.get(<key>)`

The `get()` method gets the specified object from the `HashMap`.

### entrySet()

**Syntax:** `<HashMap instance>.entrySet()`

You can use the `entrySet()` method to get a `Set` of `Map.Entry` objects that are the keys and values in the `HashMap`. This may be useful for looping.

### keySet()

**Syntax:** `<HashMap instance>.keySet()`

The `keySet()` method returns a `Set` of the keys used to index objects in the HashMap.

```java
import java.util.HashMap;
import java.util.Map;

public class Main {

    public static void main(String[] args) throws Exception{

        // define our HashMap
        HashMap<String, Person> myPeople = new HashMap<>();

        // add elements to the HashMap
        myPeople.put("Doug", new Person("Doug", 38, 6));
        myPeople.put("Liz", new Person("Liz", 38, 5.5));
        myPeople.put("Collin", new Person("Collin", 12, 5));
        myPeople.put("Audrey", new Person("Audrey", 9, 4.8));

        // output Person Collin
        System.out.println(myPeople.keySet());
    }
}
```

This example outputs:

> [Collin, Liz, Audrey, Doug]

### values()

**Syntax:** `<HashMap instance>.values()`

The `values()` method returns a generic `Collection` of the values stored in the `HashMap`. `Collection` objects are iterable so this is also good for looping over just the unordered values in a `HashMap`.

```java
import java.util.HashMap;
import java.util.Map;

public class Main {

    public static void main(String[] args) throws Exception{

        // define our HashMap
        HashMap<String, Person> myPeople = new HashMap<>();

        // add elements to the HashMap
        myPeople.put("Doug", new Person("Doug", 38, 6));
        myPeople.put("Liz", new Person("Liz", 38, 5.5));
        myPeople.put("Collin", new Person("Collin", 12, 5));
        myPeople.put("Audrey", new Person("Audrey", 9, 4.8));

        // output all keys people (note that they're not in the order we inserted them)
        for(Person person : myPeople.values()){
            System.out.println(person.describe());
        }
    }
}
```

This example outputs:

> Collin is 12 years old and 5.0 feet tall. Collin has received 0 high fives.
> Liz is 38 years old and 5.5 feet tall. Liz has received 0 high fives.
> Audrey is 9 years old and 4.8 feet tall. Audrey has received 0 high fives.
> Doug is 38 years old and 6.0 feet tall. Doug has received 0 high fives.

### containsKey()

**Syntax:** `<HashMap instance>.containsKey(<key>)`

The `containsKey()` method returns a boolean indicating if the `HashMap` contains a given key.

### containsValue()

**Syntax:** `<HashMap instance>.containsValue(<specific object>)`

The `containsKey()` method returns a boolean indicating if the `HashMap` contains a specific object instance.
