Early on in this class we talked about primitive values. These are data types boolean, integer, long, double, and char. (Null being the absence of value is not a data type.) Just like above, we can create arrays of these primitive data types. If you need an array of 100 doubles you'd write something like `double[] myStuff = new double[100]`. Easy-peasy. 

There is one significant gotcha when working with arrays of primitive values. Every element in the array gets a default value. All 100 elements in the `myStuff` array of doubles is defaulted to 0.0! 

```java
public class Main {

    public static void main(String[] args){

        double[] myStuff = new double[100];

        System.out.println(myStuff[72]);
    }

}
```

The output from this is:

> 0.0

The default primitive values are:

* **boolean:** false
* **integer:** 0
* **long:** 0
* **double:** 0.0
* **char:** The 'null' character. Effectively, all the characters you can type are in a gigantic array (google UTF-8). The 103rd character is 'g'. The 9th character is tab. The 0th character is the null character. At a lower level than Java, the null character is used to denote the end of strings.
