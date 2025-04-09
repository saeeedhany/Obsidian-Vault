##### definition of the function :
Function is basically a set of statements that takes inputs, perform some computation and produces output.

##### Syntax : 
Return_type function_name(set_of_inputs); *inputs provide to the function*
- its not necessary to provide anything to input field.

##### why functions ?
There are two important reasons of why we are using functions :
*1.* **Reusability**
	once the function is defined, it can be reused over and over again.
*2.* **Abstraction**
	if you are just using the function in your program then you don't have to worry about how it works inside!
	**Example :** *scanf* function

**Lets demonstration the use of function**
```C
#include <sdtio.h>

int areaOfRect(int length, int breadth) {
	int area;
	int area = length * breadth;
	return area;
}

int main () {
	int l = 10, b = 5;
	int area = areaOfRect(l,b);
	printf("%d\n", area);
}
```


##### Function declaration :
similarly, function declaration (also called *function prototype*) means declaring the properties of a function to the compiler.

**For Example** int fun(int, char);
*1.* Name of function: *fun*
*2.* Return Type of function: *int*
*3.* Number of parameters: *2*
*4.* Type of parameter one: *int*
*5.* Type of parameter two: *char*

**Important Takeaway :**
Its not necessary to put the name of the parameters in function prototype.
*For Example :* int fun(int var1, char var2); *not necessary to mention these names var1, var2*.
- its important to mention the name of parameter in function definition but not important in function declaration.

```C
#include <stdio.h>

char fun();

int main() {
	char c = fun();
	printf("%c", c); // the ouput is still 'a'
}

char fun() {
	return 'a';
}
```

##### so is it necessary to declare the function before using it ?
**Not** necessary but it is preferred to declare the function before using it.

*Why is it not necessary?*
```C
#include <stdio.h>

char fun() {
	return 'a';
}
int main() {
	char c = fun();
	printf("%c", c);
}
```
Here we've not written any function prototype but i have define the function before actually calling it. *it will work fine*

*So what happens when we use the function before using it?*
```C
#include <stdio.h>

int main() {
	char c = fun();
	printf("%c", c);
}
char fun() {
	return 'a';
}
```
Here it will produce the ERROR. *Conflicting type of fun()*


##### Function definition :
Function definition consists of block of code which is capable of performing some specific task.

**for Example :**
```C
int add(int a, int b) {
	int sum;
	sum = a + b;
	return sum;
}
```
*this is what definition means*

**So how really function work ?**
```C
int add(int, int);

int main() {
	int m = 20, n = 30, sum;
	sum = add(m, n);
	printf("sum is %d", sum);
}
int add(int a, int b) {
	return (a + b);
}
```

- *int add(int, int)*  in this block there is no name to mention the prototype of a function.
	*recall :* There is no need to mention names of the parameter

- after that in the *main* function we have int *m = 20* *n = 30* and *sum* will store the final result of *m* and *n* 
- after that in the next line we have *sum = add(m, n)* 
	*add(m, n)* this is the way you call a function.
	! while calling a function, you should mention the return type of the function. 
	also you should not mention the data type of the arguments.
- after this stage the control will move from this position *sum = add(m , n)* to the actual definition of the function
	*int add(int a, int b)* here this is the the way of how you define a function 
	! it is important to mention both data type and name of parameter.

**So how it actually work??**
- *int add(int a, int b)* after defining the function by the data type *int* and values *a* and *b*, now there are two void boxes that has no value, so value of *m* which is *20* will pass to *a* and value of *n* which is *30* will pass to *b*, so now *a* will contain value *20* and *b* will contain value *30* 
- *return (a +b)* inside the function we will manipulating this values that means we are adding this variables, so *a* will get replaces by *20* and *b* will get replaces by *30* and then finally will add them together which will return *50*.
- simply we return this *50* back to this calling procedure *sum = add(m, n)* to be *sum = 50*, simply after that we print *sum* equal *50* 


##### so What is the difference between an argument and a parameter?

**Parameter :** is a variable in the declaration and definition of the function.
**Argument :** is the actual value of the parameter that gets passed to the function.

!! *Parameter* is also called as *Formal Parameter* and *Argument* is also called as *Actual 
Parameter*.


##### Call by Value & Call by Reference..

###### Recall :
**Actual Parameter -** The parameter passed to a function.
**Formal Parameter -** The parameter received by a function.
```
// we have add(m, n);

/* int add(int a, int b) {
	return (a + b)
}*/
```
- in this example *add(m, n);* is called an *Actual Parameter*
- and from the set of function *int add(int a, int b) {//block of code}* the content inside brackets called *Forma Parameter*

##### Call by Value :
Here value of an actual parameter will be copied to formal parameters and these two different parameters store values in different location.

```C 
int x = 10, y = 20; // so variable x contain value of 10 and y contain 20
fun(x, y)
```
*So what we actually doing to that calling procedure?*
- first we are passing that values of *x* and *y* to the function definition
```C
int fun(int x, int y) {
	x = 20;
	y = 10;
}
```
- so the variable inside the declared function contain these variables *x* contain *10* and *y* contain *20*.
- these variables is local to this function, when his function procedure finishes we get back to this *fun(x, y)* procedure and these variables *int fun(int x, int y)* will get destroyed, and whatever changes you made in this variables *int fun(int x, int y)* will never get reflected back to these variables *fun(x, y)*.
- so if you tried to print the values of *x* and *y* it will give *x = 10* and *y = 20* which mean the original values.

**so what is the Call By Value ?**
it means that you simply passes the values to the variables and not the variables itself.

so whatever the changes you made to these variables will never reflected back to these variables.


##### Now what is Call by Reference ?
Here both actual and formal parameters refers to same [[memory location.]]
therefore, any changes made to the formal parameters will get reflected to actual parameters.

Here instead of passing values, we pass [[addresses]].
```C
int x = 10, y = 20;
fun(&x, &y);
```
- Now we have variable *x* and variable *y* with addresses *1000* for *x* and *2000* for *y*, and the value of *x* is *10* and the value of *y* is *20* .
> here we notice the difference, instead of writing *x* and *y* directly we also mentioning these (&) operator, which also known as **Address of Operator**.
   *That means we are simply passing the addresses of these variables instead of passing the values*, so (&) of *x* mean *Address of x* and (&) of *y* means *Address of y*
   
- so in the definition of the function address of *x* and *y* is received instead of values.
```C
int fun(int *ptr1, int *ptr2) {
	*ptr1 = 20;
	*ptr2 = 10;
}
```
- Now as addresses are received by this function, therefore some special kind of variable is required to store them, as we simply declare a variable over here *(int normal_var, int normal_var2)* in the parameters list then they are not capable enough to hold these addresses, There fore we required special variables called [[Pointers]].
> **[[Pointers]]** are those variables which can store addresses of some other variables

- So in the function parameter we have Two pointers *ptr1* and *ptr2*, *ptr1* will store the address of *x* which is *1000*, and *ptr2* will store the address of *y* which is *2000* 
- Now inside this function we have two statements *ptr1 = 20;* and *ptr2 = 10*.
> in the normal situation when we call a variable by his name we store his value, but when we defining it by ( * ) so this simply means that access the value of that particular address. and this ( * ) known as the reference operator.which is just apposite to that particular ( & ) its also called as reference operator.

- when we simply write *ptr1* we are accessing the content of *ptr1* which is in this case is *1000* , therefore *ptr1* will replaced by *1000* 
- so when we write start in front of *1000* that means we are trying to access the content of this particular address *1000*, this means we are **[[Mapping]]** *1000*, and this simply means we are trying to access the content of variable *x* which is *10* 
- now here we assigning *20* that means we changing this value to *20*, similarly when we are writing *ptr2* we are trying to access it's content which is *2000*, and when we write ( * ) we are simply mapping it, that means this location *2000*, and we trying to access his content in this particular location which is *y*, now as we assigning *10* in it for this value will get replaced by *20*.
- as this function finishes we go back to this calling procedure *fun(&x, &y)* and after that simply print the content of *x* and *y* as now in this case value of *x* will get change to *20* and *y* will get change to *10*
- so the output will be // x = 20, y = 10

##### so this is the difference between Calling by Value & Calling by Reference.

**Call By Value -** we are passing the copies or values of the variables to the other variables in the definition.
**Call By Reference -** Then in that case we are passing the addresses to the other function, which are received by by the [[Pointers]] 

#function


 




 

