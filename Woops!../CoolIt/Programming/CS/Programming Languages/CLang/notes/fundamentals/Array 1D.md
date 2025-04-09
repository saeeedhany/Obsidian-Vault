**Definition of array :**
An array is a *[[data structure]]* containing a number of data values (all of which are of same type).

Also, each data structure is designed to organize data to suit a specific purpose.

**For example:** Array is a data structure which you can visualize as follows:
![[arrayVisualisation.png]]
Imagine an *array* as a large chunk of memory divided into smaller block of memory and each block is capable if sorting data value of some type.

**Declaration and definition of *1D* array**..

*Syntax :* 
```
data_type nameOfTheArray[no. of elements];
```

*For example :* 
```
int arr[5]; \\ the definition of this statment..
\\Compiler will allocate a contiguous block of memory of size = 5*sizeof(int)

arr | | | | | |

```

**Question ??**
Can we specify the length of the array as *5.679*? Or
Can it be of type other than *integer*?

**Answer** is NO!

*the length of an array can be specified by an integer constant expression.
```
int arr[5];
int arr[5+5];
int arr[5*3];

int a;
int arr[a = 21/3];

int arr[-5]; // this is FALSE // length of an array can not be negative
```

**Best Practice**
Specifying the length of an array using **[[macro]]** is considered to be an excellent practice.
```
#define N 10
int arr[N];
```

#### **Accessing Elements From 1D array**
*To access an array element, just write :*
```
array_name[index]

arr | | | | | |  
     1 2 3 4 5
```
Accessing the first element of an array : <code>*arr[0]*</code>

#### **How to initializing 1D array**

```
\\Method One
arr[5] = {1,2,4,5,6,96};

\\Method Two
arr[] = {1,2,4,5,6,96}; // you didn't have to specify the length

\\Method Three // not a preferred method!!!!
int arr[5]; // you have to specify the length
arr[0] = 1;
arr[1] = 2;
arr[2] = 3; .. and so on

//Method Four
int arr[5];
for (i = 0; i < 5; i++) {
	scanf("%d", &arr[i]); //scan inputs by the user
}
```


**Some Questions**
*#1 -* What if number of elements are lesser than the length specified?
```
int arr[10] = {1,2,3,4,5,6};
```
*Answer :* The remaining locations of the array are filled by value 0.
```
int arr[10] = {1,2,3,4,5,6,0,0,0,0};
```

*A small TIP*
instead of writing this way : 
```
int arr[10];
for(i = 0; i < 10; i++) {
	arr[i] = 0;
}
```

You may write it like this : 
```
int arr[10] = {0};
```

*Why Not* <code>int arr[10] = {}</code>
Because this is illegal.
You must have to specify at least 1 element. it cannot be completely empty.

What is **Designated Initialization** of array?
- Sometimes we want something like this:
```
int arr[10] = {1, 0, 0, 0, 0, 2, 3, 0, 0, 0};
```
*So how great it would be if i don't have to explicit write these zeros*!!

So *We want* :
- *1* in position *0*
- *2* in position *5*
- *3* in position *6*

```
int arr[10] = {[0] = 1, [5] = 5, [6] = 3};
```
This way of initialization is called *designated initialization*.
And each number in the square brackets is said to be a *designator*.

**Advantages :**
- No need to bother about the entries counting zeros.
```
int arr[15] = {1, 0,0,0,0, 2, 0,0,0,0,0,0,0,0,0}; 
\\ we can simply write it like that
int arr[15] = {[0] = 1, [5] = 2};
```

- No need to bother about the order at all
```
int arr[15] = {[0] = 1, [5] = 2};
// as the same as 
int arr[15] = {[5] = 2, [0] = 1};
```

**Be CAREFUL!**
If the length of an array *'n'*, then each designator must be between *0* and *n-1*
```
int a[5] = {[0] = 4, [4] = 50}; // this is right
int a[5] = {[0] = 4, [5] = 50}; // this is wrong
```

*What if i won't mention the length?*
- Designatrors could be any non-negative integer.
- Compiler will deduce the length of the array from the larges designator in the list

**If there is a clash, then designator will win.


*also If we want to know the length of an array* we can use ..
```
Sizeof(name_of_arr)/sizeof(name_of_arr[0]) // we will devide this into two parts

//First part
Sizeof(name_of_arr)
int a[] = {1,2,3,4,5,6,7,8,9,10}
// there is total 10 integers  assume that each integer requires 4bytes
// sizeof(a) = 4 * 10 = 40 

//Second part
sizeof(name_of_arr[0])
int a[] = {1,2,3,4,5,6,7,8,9,10}
//This mean sizeof(a[0]);
//sizeof(a[0]) = 4bytes

//so it will be 
sizeof(a)/sizeof(a[0])
   40   /   4    =  10  // so the length of an array is 10

```


Next lecture will be about [[Multidimensional Arrays]].


#datastructure


