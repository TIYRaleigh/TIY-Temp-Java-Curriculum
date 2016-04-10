It can be extremely handy to loop over an array and interact with each item, one at a time. In fact, looping over structures of data like arrays are one of the more common things programmers do. 

One way to loop over an array is to use a `for` loop like this:

```java
public class Main {

    public static void main(String[] args){

        try {
            Person[] myPeople = new Person[4];

            myPeople[0] = new Person("Doug", 38, 6);
            myPeople[1] = new Person("Liz", 38, 5.5);
            myPeople[2] = new Person("Collin", 12, 5);
            myPeople[3] = new Person("Audrey", 9, 4.8);

            for(int x = 0 ; x < myPeople.length ; x++) {
                System.out.println(myPeople[x].describe());
            }

        } catch (Exception e){
            System.out.println(e.toString());
        }

    }

}
```

This will output:

> Doug is 38 years old and 6.0 feet tall. Doug has received 0 high fives.
> Liz is 38 years old and 5.5 feet tall. Liz has received 0 high fives.
> Collin is 12 years old and 5.0 feet tall. Collin has received 0 high fives.
> Audrey is 9 years old and 4.8 feet tall. Audrey has received 0 high fives.

Let's analyze the for loop:

We can see that the initializing expression in the for loop is `int x = 0`. This just says that we're creating a variable named `x` to hold `int` values and its initial value is `0`. The initial value is 0 because we're going to use x to specify the index of the array that we're looping over. 

The conditional expression expression in the for loop is `x < myPeople.length`. This says that we will continue to execute the body of the for loop while the variable `x` (which we created in the initializing expression) is less than the number of elements in the `myPeople` array. So, if there are 10 elements in the array, we will continue looping while `x` is less than 10. The maximum value of `x` will be 9. The array has 10 indexes, from 0 to 9. As such, we don't want `x` to ever be 10. There is no index 10 in the array.

The afterthought expression in the for loop is `x++`. This means that we will increment `x` after each execution of the for loop's body. 

Within the body we're just outputting the description of the person at the `x`th index.
