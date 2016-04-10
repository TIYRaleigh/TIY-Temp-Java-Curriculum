One more interesting fold with arrays is that you can make arrays of arrays. These are often called matrixes or multidimensional arrays. An example of a multidimensional might be a multiplication table.

```java
public class Main {

    public static void main(String[] args){

        // this is the maximum number we'll multiply. IE: 12 x 12 = 144.
        int max = 12;

        // create a 2d array allowing for the correct number of fields from 0 to max.
        int[][] products = new int[max + 1][max + 1];

        // loop over the rows in the matrix
        for(int x = 0 ; x < max ; x++){
            // loop over the columns in this matrix
            for(int y = 0 ; y < max ; y++){
                // set this element in the matrix to the product of x and y
                products[x][y] = x * y;
            }
        }

        // what is 6*3?
        System.out.println("6 x 3 = " + products[6][3]);

        // what is 0*5?
        System.out.println("0 x 5 = " + products[0][5]);

        // what is 11*12?
        System.out.println("11 x 12 = " + products[11][12]);
        
    }

}
```

Starting at the top, the first line of note is `int[][] products = new int[max + 1][max + 1]`. 

Breaking this down, we first come across `int[][]`. We already know that `int[]` is an array of integers. Unsurprisingly, `int[][]` is an array of arrays of integers. 

To the right of the assignment operator we have `new int[max + 1][max + 1]`. One new thing we've got going on here is that we're setting the number of elements in the array according to a variable value. We want to multiply all of the numbers from 0 to 12 (`max`). That's 13 numbers, hence `max+1`. If we only wanted to multiply 0 to 3 we'd set `max` to 3 and everything else would still work. 

The `new int[max + 1][max + 1]` bit tells Java that we have an array with `max + 1` elements. Each of these elements are themselves an array of `max + 1` `int` values.

Subsequently I have a loop and a nested loop. These aren't looping over the 2D array, they're looping from a minimum value of 0 to `max+1`. The outer loop is effectively determining the row in the table we're working with. The inner loop is the column. Combined they define a specific cell.

![multiplication_table_1.gif](https://tiy-learn-content.s3.amazonaws.com/df529131-multiplication_table_1.gif)

On each iteration of the inner loop we execute `products[x][y] = x * y`. We already know that `= x * y` will assign the product of `x` and `y` to the variable on the left. The variable on the left is a specific element a 2D array, `products[x][y]`. `x` indicates which of the arrays to write to (aka row). `y` indicates which index in that array (aka cell).

If you so wish you can create arrays of arrays of arrays of arrays of arrays.... to your heart's content. I don't recommend it, but you can. Frankly, there are better ways to organize your data, like classes.

<!-- todo: this might be a good place to take a break and do some review -->
