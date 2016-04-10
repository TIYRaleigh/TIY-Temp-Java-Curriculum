Let's say you want to make a card game. You know you'll need a deck of cards. An individual playing card isn't all that complex, so we'll start there. 

Let's model a playing card. To start, let's think about what a card is and does.

* A real card is a combination of two things, a suit and a value (sometimes called a rank).
* A card has one of four suits: Clubs, Diamonds, Hearts or Spades.
* A card has one of thirteen values: Ace, 2 though 10, Jack, Queen and King.
* Suits have a color, red or black.
* A card can be flipped face up or face down.
* We'll want to describe a card.

<!-- example: a static method that take a string like "AH" and returns an ace of hearts -->

### Red

So, since we're making a card, the first thing we need is a `CardTest`. Let's make one! We need to test _something_ so I'll test the flipping behavior. 

```java
import org.junit.Test;

public class CardTest {

    @Test
    /**
     * Given a Card, and the card is face up,
     * When the card is flipped
     * Then the the card is face down
     */
    public void whenFlippedFromFaceUpThenFaceDown(){
        // Assemble
        Card card = new Card();

    }
}
```

As of yet, I don't actually have a `Card` class. IntelliJ doesn't like this and it yells at me:

![no card class test fails.png](https://tiy-learn-content.s3.amazonaws.com/021e5c62-no%20card%20class%20test%20fails.png)

I can't run this test since the project can't compile. This would be one example of a "Red".

### Green

Now that we have a failing test, we need to make it pass. This is easily accomplished by creating a Card class. IntelliJ has a nice shortcut in the opt-enter menu to create the class for you:

![create card class.png](https://tiy-learn-content.s3.amazonaws.com/d835de28-create%20card%20class.png)

This generates the following class:

```java
public class Card {
}
```

With only this simple class my project can compile and I can run my tests!

![basic test passes.png](https://tiy-learn-content.s3.amazonaws.com/92b40a44-basic%20test%20passes.png)

We have achieved "Green"!

### Refactor

The next step is to refactor. There's really nothing we need to clean up yet so we'll skip this step this time.

### Red (#2)

We've got a `Card` class now. When I create the card I want to be able to tell it what suit and value it is. This means I need a constructor. Since we're in the "Red" step we know we need to make our test fail. I'll do this by using the as-of-yet-nonexistent constructor in my test:

![no constructor test fails.png](https://tiy-learn-content.s3.amazonaws.com/01ebc6e8-no%20constructor%20test%20fails.png)

### Green (#2)

Now I'll make the test pass. I'll add a constructor that meets the requirements.

![constructor tests passing.png](https://tiy-learn-content.s3.amazonaws.com/97314b39-constructor%20tests%20passing.png)

Here I created the constructor to set two private properties. Now my tests pass!

### Refactor (#2)

Thinking into the future, I realize that I will need to have some way to control what we can set the suit and value to. I can't have a 15 of Wombats, for example. I'll create two private setters I can use to restrict the allowed values.

![tests pass again.png](https://tiy-learn-content.s3.amazonaws.com/6f0ce55f-tests%20pass%20again.png)

### Red... Green... Refactor... ad nauseam

This process repeats again and again. 

I forgot to add a property to indicate whether the card was face up or down. I'll update the test and add the property and constructor argument to make it pass.

I can then move onto the "act" part of our test. This is where I'd test a  `flip()` method and then implement it in the `Card` class.

Lastly, I'll want to work on the "assert" section. I'll want to assert the `Card` is facing the correct direction. I'll use a not-yet-existing `getFaceUp()` method in my assertion. I'll then implement the method in the `Card` class.

While doing this I discovered a new behavior. Cards have restricted values and suits. I'll start with one of these, create a behavior-based test, and make it pass. 

Rinse... repeat...

There are many [tutorials](https://www.google.com/search?q=java+tdd+tutorial&oq=java+tdd+tutorial&aqs=chrome..69i57j0l5.2947j0j7&sourceid=chrome&ie=UTF-8) online related to TDD. [One that might be useful to you is the JetBrains IntelliJ TDD tutorial.](https://www.jetbrains.com/help/idea/2016.1/tutorial-test-driven-development.html?origin=old_help)

<!-- demo: continue working on the CardTest and Card classes in lecture -->
