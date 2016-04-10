Arrays in Java are not very robust. Once created, an array always has the same number of elements. You can't search arrays directly. You can't easily sort arrays. This is why Oracle added the `Arrays` class.

The `Arrays` class specializes in working with arrays. In fact, it only has static methods and you can not create an instance of the `Arrays` class. 

Here are some notable static methods `Arrays` provides:

* **`copyOf(orignal, newLength)`**
	The `copyOf()` method can be used to resize an array by creating a new array of the requested size and copying all of the values from the original array into the new array.
* **`fill(array, value)`**
	The `fill()` method can be used to set all of the elements in an array with a given value. 
* **`sort(array)`**
	The `sort()` method is used to sort an array.
* **`toString(array)`**
	The `toString()` method is used to make a string representation of an array.

```java
import java.util.Arrays;

public class Example {
    public static void main(String[] args) throws Exception  {

        int[] numbers = {32, 763, 2, 56, 23, 63, 934};

        Arrays.sort(numbers);

        System.out.println(Arrays.toString(numbers));

    }
}
```

[Check out the full list of static methods on the Arrays class.](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html)
