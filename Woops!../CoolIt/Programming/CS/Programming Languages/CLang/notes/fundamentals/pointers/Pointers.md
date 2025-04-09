- Pointer is a special variable that is capable of storing some address.
- It points to a memory location where the first byte is.

**Syntax for declaring POINTER variable**
General syntax for declaring pointer variables:
```
data_type *Pointer_name;
```
*data_type* - Here data type refers to the type of the value that the pointer will point to.

**Need of address of operator**
- simply declaring a pointer is not enough.
- it is important to *initialize pointer* before use.
- One way to initialize a pointer is to *assign address of some variable*.
```C
int x = 5;  // we have now a variable "x" containes "5" as its value with base case like 1000

int *ptr; // here there is a pointer that stores a value with an integer type lets say that it has a base case 2000

ptr = &x; // here "&" means the address of operator 
          // now we can store the address of "x" to the pointer variable "ptr"
```

*Therefore we can write these the first two line in one single line*
```C
int x = 5, *ptr = &x;
```
**!!** Also this line <code>ptr = &x;</code> is an assignment statement so we can write the statement at the time of declaration. 

**Value of Operator in Pointer**
*Value of* operator/<font color="#00b0f0">indirection</font> operator/<font color="#00b050">dereference</font> operator an operator that is used to access the value stored at the location pointed by the pointer.
```C
int x = 5, *ptr = &x;

printf("%d", *ptr); // value of operator
```
**!!** it says go to the address of object and take what is stored in the object.

*We can also change the value of the object pointed by the pointer*
```C
int x = 5, *ptr = &x;
*ptr = 4;
```
So what is just say??
- it say by simply writing <code>ptr</code> i can access the content of this <code>ptr</code> that is *1000*.
- with the help of this " * " *dereference* operator or *value of* operator i can simply go to this particular location and can access its value.
- after accessing this value by the help of this <code>*ptr = 4;</code> assignment statement i can change it's value so now the variable contains *4*.
*Now i can simply print this program on the screen*
```
Printf("%d", *ptr); // output : 4
```

**A word of CAUTION**
**!!** Never apply the indirection operator to the uninitialized pointer
*For Example:*
```C
int *ptr; // we not initialized this point location
printf("%d", *ptr); // output : undefined behaviour
```

**!!** Assigning value to uninitialized pointer is **<font color="#ff0000">dangerous</font>**.
```C
int *ptr;
*ptr = 1; // output : segmentation fault
```
we trying to assign a value to an object which pointed by this pointer, but it's not pointing to any location.

**Assigning a content to one Pointer to another pointer**
```C
int i = 10;
int *p, *q;
p = &i;
q = p;
```
- Now we give the value of <code>*p</code> the address of value *i*.
- And then we pass the same value of <code>*p</code> to <code>*q</code> as it is, the address to *i*.
-- So if we print the value of <code>*p</code> and <code>*q</code> it will gives us <code>10 10</code> as an output.


**Warning !!!**
-- We should not returning the address of some *Local variable*. <u>for more details --></u> [[C storage classes]]

--> [[Pointers Important Questions]]


