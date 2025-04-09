**The Idea of this problem is too simple -** it's just about to use an increment and decrement operator with some algorithm.

**Algorithm :** If *x = 3, y  = 4*
*Step #1 -* x++; y--;
*Step #2 -* repeat step 1 until y become *0*.

**Explain :**
```C
x = 4, y = 3
```
- after step 1 *x* will become *5* and *y* becomes *2*
- after step 2 *x* will become *6* and *y* becomes *1*
- after step 3 *x* will become *7* and *y* becomes *0*, after this particular step the operation will stop because we reach the *ZERO*. and *x* now is *7* so the result is *7*.

**Now the actual Code :** 
```C
#include <stdio.h>

int main() {
	int x, y;
	printf("Enter the two numbers you want to add");
	scanf("%d %d", x, y);

	while (y != 0) {
		x++;
		y--;
	}
	printf("Sum of the two values is %d", x);
	return 0;
}
```


#practice 