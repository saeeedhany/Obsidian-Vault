- Comma Operator can be used as a **Separator**.
##### Example:
```C
int a = 3, b = 4, c = 8;  //Multiple definition in single line.
```

*we can right this ↑ instead of this  ↓* 
```C
int a = 3;
int b = 4;
int c = 8;
```


- A comma operator can be used as an *Operator*.
##### Example:
```C
int a = (3, 4, 8);  //ouput: 8

printf("%d", a);
```
**Comma Operator -** returns the rightmost operand in the expressions and it simply evaluates the rest of the operands and finally reject them.

so what this line mean? *simply evaluates the rest of the operands and finally reject them*
```C
int var = (printf("%s\n", "HEllo!"), 5);

printf("%d", var); // output: Hello! then 5 why?
```

**Explanation:**
we might think that comma operator simply reject the statement and 5 will be returned into the *var* variable.     //your right! **BUT**  it will not simply reject the statement, First is will evaluate the statement then it will reject it.

so the value will be returned to *var* after evaluating the first operand.


- Comma Operator is having **Least precedence** among all the operators available in C.
##### Example:
```C
int a;
a = 3, 4, 8;  //output: 3! Why!!!

printf("%d", a);
```

**Explanation:**
As we sea you might think that the the value will be 8 as because comma operator will return the rightmost value to this particular variable a **BUT YOU ARE WRONG**. 

As comma operator having the least precedence, and we can see that there is one more operator called [[Assignment Operator]] as assignment operator has a higher precedent over the comma operator there for it will evaluated first.

so this particular statement is equal to:
```C
int a;
(a = 3), 4, 8;

printf("%d", a);
```
*Therefor value 3 will be assigned to a and simply a will be printed. after that comma operator will be evaluated, but as we know this 8 value has to be returned to some variable but there is no variable over here so it will do nothing.*

##### Example 2:
```C
int a = 3, 4, 8;

printf("%d", a);
```
**Note -** here comma is behaving like a **separator**.
- Comma Separator acts like a **Separator** within function calls and definitions, variable declaration, and [[enum]] declaration.

```C
int a = 3, 4, 8;  //Error
```

**Explanation:**
This statement is equivalent to: 
```C
int a = 3, int 4, int 8;
```
*We can not start a variable name with a digit!!!*

##### Example 3:
```C
int a;
a = (3, 4, 8);  // ouput: 8

printf("%d", a);
```
**Note -** Bracket has the highest precedence that any other operator.
 so what inside the **(Bracket)** will be evaluated first then the assignment operator.


#operators 