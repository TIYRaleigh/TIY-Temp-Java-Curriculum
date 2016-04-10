Essentially, all software begins executing on the first line and continues until it reaches the last line. It's sort of like the script for a play: Romeo says something, Juliette says something, they both die, end of story. 

Actually, it's a bit more complex than that. It's more like one of those interactive dinner theaters. There's one script, but it branches depending on who the audience decides the murderer is.

I think of conditionals like a series of dams on a river. They control and redirect the flow of the river.

In programming we use conditional logic to control this flow. Conditions are criteria that must be met for a block of code to be executed. For example:

* Did the user push the jump button? 
	* If so: Then make the character jump.
	
*  Is is the temperature in the refrigerator higher than 34 degrees?
	* If so: Turn on the cooling unit. 

* Has the user filed their TPS report today?
	* If so: 
		* Thank them for being such a valued employee.
	* If not:
		* Nag them.
		
<!-- todo: add picture? -->

<!-- todo: cover sheet? -->

### If statements

**Syntax:**

```Java
if(<conditional expression that evaluates to true>){
	<block of code>
}
```

An `if` statement executes a _block_ of code only if a conditional expression evaluates to true. Blocks of code are the lines of code between curly braces.

Remember the logical operators we just discussed? This is where they really come into play. For example:

```java
public class Example {
    public static void main(String[] args){

        boolean milk = true;
        boolean cream = false;
        boolean soyMilk = false;

        boolean caffeinatedEspresso = true;
        boolean decaffeinatedEspresso = false;

        boolean darkChocolate = true;
        boolean lightChocolate = false;

        if( (milk || cream || soyMilk) &&
                (caffeinatedEspresso || decaffeinatedEspresso) &&
                (darkChocolate || lightChocolate) ){
            System.out.println("This is a mocha!");
        }
    }
}
```

Note that the parenthesis control the order of operations, grouping chunks of the expression into single logical units. For example, by itself, `(milk || cream || soyMilk)` evaluates to true because `milk` is true. `(caffeinatedEspresso || decaffeinatedEspresso)` is true because `caffeinatedEspresso` is true. And, `(darkChocolate || lightChocolate)` is true because `darkChocolate` is true. Ultimately we get `true && true && true` which evaluates to true.

The curly braces in the `if` statement are optional if the block of code in the if statement is only one line long. For example:

```java
if(age < 21)
	boolean canByAlcohol = false;
```

But, as a new developer, I really recommend you do not use this syntax.

### Else statements

**Syntax:**

```Java
if(<conditional expression that evaluates to true>){
	<block of code>
} else {
	<a different block of code>
}
```

Sometimes you want to do one thing or something else. Maybe you want steak or chicken. Usually you don't want both. 

An `else` statement can be tacked onto the end of an if statement. The block of code enclosed in the curly braces after the `else` statement are only executed if the original conditional statement is false.

```java
public class Example {
    public static void main(String[] args){
      
		boolean milk = true;
        boolean cream = false;
        boolean soyMilk = false;

        boolean caffeinatedEspresso = false;
        boolean decaffeinatedEspresso = false;

        boolean darkChocolate = false;
        boolean lightChocolate = false;

        if( (milk || cream || soyMilk) && 
                (caffeinatedEspresso || decaffeinatedEspresso) &&
                (darkChocolate || lightChocolate) ){
            System.out.println("This is a mocha!");
        } else {
            System.out.println("I don't know what this is, but it's not a mocha!");
        } 
      
	}
}
```

### Else If statements

**Syntax:**

```Java
if(<conditional expression that evaluates to true>){
	<block of code>
} else if(<different true conditional expression>){
	<another block of code>
} else {
	<a different block of code>
}
```

Often you will want to make decisions based on more than only one conditional statement. In this case you can use _else if_ statements. 

Java will evaluate the first `if` statement. If that's false, it will check the next `else if` statement. If that's false, it will continue checking `else if` statements until one evaluates to `true`. If none of them evaluate to `true` the else `block` (if provided) will be executed, if provided. Only one block of code in the entire statement can be executed. 

```java
public class Example {
    public static void main(String[] args){
      
		boolean milk = true;
        boolean cream = false;
        boolean soyMilk = false;

        boolean caffeinatedEspresso = false;
        boolean decaffeinatedEspresso = false;

        boolean darkChocolate = false;
        boolean lightChocolate = false;

        // is this a mocha?
        if( (milk || cream || soyMilk) && 
                (caffeinatedEspresso || decaffeinatedEspresso) &&
                (darkChocolate || lightChocolate) ){
            System.out.println("This is a mocha!");

        // is this a latte?
        } else if( (milk || cream || soyMilk) && 
                (caffeinatedEspresso || decaffeinatedEspresso) &&
                !(darkChocolate || lightChocolate) ) {
            System.out.println("This is a latte!");

        // is this just milk?
        } else if(milk && !cream && !soyMilk && 
                !caffeinatedEspresso && !decaffeinatedEspresso &&
                !darkChocolate && !lightChocolate ) {
            System.out.println("This is just milk!");

        // who knows what the heck this is...
        } else {
            System.out.println("I don't know what this is.");
        } 
      
	}
} 
```

Take particular note of the order of the `if` and `else-if` statements. If we put the latte conditional first we would never  reach the mocha conditional. This is because a mocha is just a latte, but with chocolate. In other words, be sure to carefully consider what order your `if`, `else if`, and `else` blocks are written.

### Switch statement

**Syntax:** 

```java
switch(<variable>){
	case <value 1>: 
		<block of code>
		<optional break; statement>
	case <value 2>:
		<block of code>
		<optional break; statement>
	case <value 3>:
		<block of code>
		<optional break; statement>
	<more case statements, blocks, and break statements>
	default:
		<block of code>
		<optional break; statement>
}
```

The `switch` statement is another tool for applying conditional logic. It is used to match a single value against many possible options and then to execute all of the following blocks of code and/or the default block.

`Case` statements can be hard to understand. They define the entry point into multiple distinct blocks of code. By default, the first matched block of code is executed and then execution continues on to the next block of code and so forth, even though the case value doesn't match. However, adding a `break` statement in a case block will _break_ out of the entire `switch` statement and no subsequent `case` block will be executed. 

For example (note that `System.out.print()` is just like `System.out.println()` but it doesn't add a new line.):

```java
switch(number){
    case 10:
        System.out.print("10 ");
    case 9:
        System.out.print("9 ");
        break;
    case 8:
        System.out.print("8 ");
        break;
    case 7:
        System.out.print("7 ");
    case 6:
        System.out.print("6 ");
    case 5:
        System.out.print("5 ");
    case 4:
        System.out.print("4 ");
    case 3:
        System.out.print("3 ");
    case 2:
        System.out.print("2 ");
        break;
    case 1:
        System.out.print("1 ");
    default:
        System.out.print("0");
}
```

The case statement above has several different outcomes depending on the value of the variable `number`, which we'll assume is an integer.

These are:

* **10:** 10 9
* **9:** 9
* **8:** 8
* **7:** 7 6 5 4 3 2
* **6:** 6 5 4 3 2
* **5:** 5 4 3 2
* **4:** 4 3 2
* **3:** 3 2
* **2:** 2
* **1:** 1 0
* **0:** 0
* **7945:** 0
* **-125:** 0
* **any other integer:** 0

In general, the `switch` statement only works with primitive data types. There are exceptions to this, but we won't cover them here.

Take note that you also can't use complex conditional expressions in case statements. A variable either matches a specific value, or it doesn't.

In my opinion, avoid `case` statements unless you have a really good reason. They're hard to understand and easy to screw up. `If` statements are more verbose, but easier to understand and more capable.
