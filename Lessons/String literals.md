**Syntax:** `"<some text>"`

`String` is a class that represents a collection of letters. In english, this is what you use to make bits of text like words, sentences, paragraphs, or the next great american novel. (I don't recommend the latter.)

Strings are unique in Java in that they have a _string literal_ syntax. Java automatically recognizes that the characters contained between double quotes represent a `String` object. 

We've already used string literals throughout this class:

```java
public class Example {
    public static void main(String[] args){
        System.out.println("Hello World!");
    }
}
```

In this familiar example, `"Hello World!"` is a String. More accurately, `"Hello World!"` is an _instance_ of a string expressed in string literal syntax. 
