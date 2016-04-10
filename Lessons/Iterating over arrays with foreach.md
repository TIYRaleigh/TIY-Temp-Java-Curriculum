**Syntax:**

```java
for(<data type> <loop variable name> : <array variable>){
	<body to loop over>
}
```

This is a a _foreach_ loop. It is an alternative syntax of for loops that we haven't discussed yet. Foreach loops are very similar to traditional for loops, but you don't need to manually manage the loop with three expressions. Instead, the for loop automatically creates a new variable for the next index in the array on each iteration through the loop.

We can update the last example like this:

```java
public class Main {

    public static void main(String[] args){

        try {
            Person[] myPeople = new Person[4];

            myPeople[0] = new Person("Doug", 38, 6);
            myPeople[1] = new Person("Liz", 38, 5.5);
            myPeople[2] = new Person("Collin", 12, 5);
            myPeople[3] = new Person("Audrey", 9, 4.8);

            for (Person myPerson : myPeople) {
                System.out.println(myPerson.describe());
            }

        } catch (Exception e){
            System.out.println(e.toString());
        }

    }

}
```

The operative line is `for (Person myPerson : myPeople) {`. I find that it helps to mentally substitute the word "in" when you see the ":". As such this would read something like, "For each Person object in myPeople, make a new variable, myPerson, and then execute the loop's body. Keep doing this until you run out of People in the myPeople array."

In general, this is the preferred way to loop over an array. It might not always be appropriate, so you do need to know both syntaxes.

<!-- exercise: write something to sort an unsorted array -->
