![[precedence_table-2.jpg]]
![[operator_priority2.jpg]]

#### **Important Facts:**
- Associativity can only help if there are two or more operators of same precedence and not when there is just one operator.

##### Example:
```C
int fun() {
printf("random text");
return 1;
}

int fun2() {
printf("another random text");
return 1;
}

int main() {
int a = fun() + fun2();
printf("%d", a);
return 0;
}
```
*Which function is called first? fun() of fun2()*.

**It's not defined -** whether fun() or fun2() will be called first. it's **Compiler Dependent**.



