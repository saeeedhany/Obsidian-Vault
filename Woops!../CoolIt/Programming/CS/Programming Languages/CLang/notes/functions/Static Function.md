##### Basics :
- In *C* Functions are global by default.
- This means if we want to access the function outside from the file where it is declared, we can access it easily.
- Now if we want to restrict this access, then we make our function static by simply putting a keyword *static* in front of the function.

**Example :**
```C
#include <stdio.h>
#include "OtherFile.c" // external file that has the actual called function.

int fun(int, int);

int main() {
	int sum = fun(3,5);
	printf("sum is : %d", sum);
	return 0;
}
```
*Here this is the main file that will be printed*

```C
int fun(int a, int b) {
	int c;
	c = a + b;
	return c;
}
```
- in this case if we execute the code, the external function will work so that code will work

*But if we add a **Static** in front of a function that will make the function just work in the file that it made in it*
```C
static int fun(int a, int b) {
	int c;
	c = a + b;
	return c;
}
```
- now this code will not work.