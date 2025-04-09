***Question 1 -*** Consider the following two statements
```C
int *p = &i;
p = &i;
```
First statement is the declaration and second is simple assignment statement why isn't in second statement, p is preceded by * symbol?

*Solution :* In C, * symbol has different meanings depending on the context in which it's used.

At the time of declaration, * symbol is not acting as an indirection operator.

\* symbol in the first statement tells the compiler that p is a pointer to an integer.
But, if we write <code>*p = &i</code> then it is wrong, because here \* symbol indicates the indirection operator and we cannot assign the address to some integer variable.

> **Pointers -** can hold the addresses.  while..
> **Variables -** can hold the values.




