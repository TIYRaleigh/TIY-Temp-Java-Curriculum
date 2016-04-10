**Syntax:** `<data type> <variable name>`

Do you remember basic algebra from middle school? Remember how variables could stand in for numeric values? Variables in Java are the same concept, but they can stand in for other types of data too.

In algebra you might say that `x = 2016`. Now, anywhere you see `x` you can substitute `2016`. That works in Java too. You can store any type of data in a variable - not just numbers - but we'll have to come back to that.

```java
public class Example {
    public static void main(String[] args){

		// An example variable
        int x = 2016;
        
		// Anywhere we see "x" we know it means "2016", just like algebra!
		System.out.print(x + 4);
		
    }
}
```

Variables in Java don't need to be single letters like `x`. In Java variable names can be entire words, though there are some important rules you have to follow.

* Variable names are _case sensitive_! A variable named `person` can only be accessed as `person`, not `Person`, `PERSON`, `perSon`, or any other variation.
* Variables can only start with a letter, the underscore character `_`, or a dollar sign `$`. This means that a variable may not start with a number or any other special character.
* Subsequent characters in the variable name can be any combination of letters, numbers, dollar signs, or underscores.

Here are some valid (though mostly terrible) variable names:

* `x`
* `X`
* `person`
* `$system`
* `_______`
* `a`
* `NAME`

Here are some invalid variable names:

* `@username`
* `1thing`
* `\[person\]`
* `something with spaces`

There are some common conventions used when naming variables in Java:

### Give variables meaningful names that are easily understood.

Don't unnecessarily abbreviate or use acronyms. For example, a variable named `delay` is much easier to understand than one named `dly` or `d`. I'd much rather see an excessively long variable name I can easily understand rather than a short one that is inscrutable.

### Variables should either be lower case or [camelCase](https://en.wikipedia.org/wiki/CamelCase).

In camel case the first letter of a variable is always lowercase. If the variable is made up of multiple words strung together, the first letter of each subsequent word is capitalized.

Here are some good variable names:

* `name`
* `camelCase`
* `grossDomesticProduct`
* `weightPerPigeon`

Here are some bad variable names:

* `NAME`
* `camelcase`
* `gdp`
* `wpp`

In some other languages it is common to separate multiple words with underscore. EG: `gross_domestic_product`. That is not the convention in Java. You will occasionally see variable names that are all upper case where words are separated by underscores, but these are used for a specific purpose. EG: `MAX_VALUE`

### Static Typing

All variables in java are _statically typed_. In other words, you, as the developer, have to explicitly tell Java what type of data a variable stores. Data is any type of information. It could be an audio file, the geographic location of two cities, your own age, weight, and height, or anything else. For now we'll focus on really simply types of data.

When setting a variable in Java you explicitly specify the variable's data type, its name, and, optionally, an initial value. If we wanted to create a variable to hold a simple numeric value we could write.


```java
public class Example {
    public static void main(String[] args){
    
        // create a variable to hold the meaning of life
        int meaningOfLife = 42;
      
      	// output the value of meaningOfLife
      	System.out.println(meaningOfLife);
		
    }
}
```

In this example, `int` tells Java that the variable is an integer; a whole or counting number. We name the variable `meaningOfLife`. The `=` sign tells Java that we're setting the variable to `42`. 

In English this is the same as saying, "Remember that the meaning of life is 42!"
