## Create a GitHub Repository

Create a new repository named "TIY-99-bottles-of-beer".

## Instructions

* Write a program that will output the _words_ to the 99 bottles of beer on the wall song. In text. For example:

	> Ninety nine bottles of beer on the wall, ninety nine bottles of beer!
	> Take one down, pass it around!
	> Ninety eight bottles of beer on the wall!

	Rinse, repeat. 

* Make sure you handle plurals correctly. It's one bottle, not one bottle_s_! 
* Instead of outputting numbers, output words. IE: Ninety nine instead of 99.

### Hints

There are many ways to solve this problem. Off the top of my head, these are some ideas you might want to consider. They are _not_ to be considered the only way or the expected way you solve this problem, only inspiration.

* You might want to consider creating a class that is responsible for translating numbers to words. For example, maybe a class that provides a static method `NumberTranslator.toWord(99)` would return "Ninety nine". 
* You will want to find a way to isolate digits. Maybe you can use the modulo operator to find remainders? `97%10 == 7`. You can also use `String.valueOf()` to convert a number to a `String`. `Strings` are a collection of characters so perhaps you can use a [method of `String`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html) to get a specific character?
* Would switch statements be good for translating numbers to words?
* Maybe you could make methods for each digit group? `NumberTranslator.tens(99) == 9` or maybe `NumberTranslator.tens(99) == "nine"`

## Beast Mode

* Make the number of bottles configurable.
* Make the number of bottles taken down configurable. Maybe we take two bottles down rather than one?
* Make the item container being counted configurable. For example, rather than bottles, perhaps it is boxes, or winnebagos. Consider how you'll handle plurals.
* Make the contents of the container configurable. For example, rather than beer, maybe it's clowns, or snowballs.
* Make the location of the container/contents configurable. For example, rather than "on the wall" it's "under the stairs".
