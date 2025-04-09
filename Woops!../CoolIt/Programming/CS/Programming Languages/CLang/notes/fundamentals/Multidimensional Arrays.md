*Multidimensional Arrays* can be defined as an *array of arrays*
![[MDArray1.png]]

General form of declaring N-dimensional array is as follows:
```
data_type name_of_array[size1][size2]...[sizeN];
```

*For example :*
```
int a[3][4]; //two dimensional array
int a[3][4][5]; //Three dimensional array
and so on..
```

**Size Calculation**
Size of multidimensional array can be calculated by multiplying the size of all the dimensions.
*For Example :*
```
size of a[10][20] = 10 * 20 = 200 //number of elements
				  = 200 * 4 = 800bytes
```

**Initialize Two Dimensional Array**
```
// Method One
int a[2][3] = {1,2,3,4,5,6};

// Method Two //Better one
int a[2][3] = {{1,2,3},{4,5,6}};
```

**Accessing 2D array elements**
using *Row* index and *Column* index.

For Example:
We can access element stored in 1st *row* and 2nd *column* of below array.
```
    0 1 2
	_ _ _
  0|1|2|3|
  1|4|5|6|
    _ _ _

   a[0][1]
```

**Print 2 dimensional array**
```C
// For printing 1D array elements we use single for loop like this
int a[5] = {1,2,3,4,5};
for(i = 0; i < 5; i++) {
	printf("%d", a[i]);
}

// So if we want to print a 2D array elements we will use two nested for loops

int a[2][3] = {{1,2,3},{4,5,6}};
	for (i = 0; i < 2; i++) {
		for(j = 0; j < 3; j++) {
			printf("%d", a[i][j]);
		}
	}
```


#### Three Dimensional Array

**Accessing the 3D array Elements**
```
int arr[2][3][3];
```
This means that the first <code>[2]</code> mean i want *two* **2D** arrays each one has <code>[3]</code> *rows* and <code>[3]</code> *columns*

**Initialize 3 Dimensional array**



**Multiplication of Matrix**

*Important Points:*
- In order to multiply two matrices, No.Columns of 1st matrix = No.Rows of 2nd matrix
- Also, size of the resultant matrix depends on No.rows of 1st matrix and no.columns of 2nd matrix


#### **Constant array**
Either one dimensional or multi-dimensional arrays can be made constant by starting the declaration with the keyword *const*.

*For Example:*
```
const int a[10] = {1,2,3,4,5,6,7,8,9,10}; //Not able to edit

a[1] = 24; //it will reduse an error
```

**Advantages**
It assures us that the program will not modify the array which may contain some valuable information.

It also helps the compiler to catch errors by informing that there is no intention to modify this array.


**Points to be Noted**
- Variables length *Cannot have **static** storage duration*
- Variable length array does not have the initialize.




