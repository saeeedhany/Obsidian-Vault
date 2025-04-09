#### In this lecture we will practice a problem solved question..
**Example :**
```C
#include <stdio.h>

	int i = 1024;
	for (; i; i >>= 1) 
		printf("Hello World!");
	return 0;
```
*How many times will "Hello World!" printed in this program?*

**Conclusions :**
- as we now we have to add this structure between the bracket *initialization; condition; increment/decrement;* but in this situation we did not do that 
	-  **and this is because we did not have to do it but we should put the semicolon ";" .** 
- after that we know that the ">>"  is a right shift operator that make the binary number of this character shift to right as this: 
	```C
	// so if the number is 1024 that means this in binary = 100 0000 0000
	// so it should shift to right to be = 010 0000 0000 = 512
	//and then check if the condition is still true or not 
	//if true it keeps his work to be = 001 0000 0000 = 256
	// still true so it will keep work 
	// untill it reach the number 1 = 000 0000 0001
	// then it will give us the FALSE then the loop will stop.
	```
- and this process take an eleven (11) time to reach the false so the answer is 11 times.

**other Example :**
```C
#include <stdio.h>

int main() {
	int i;
	for(i = 0; i < 20; i++) {

		switch(i) {
			case 0: i += 5;
			case 1: i += 2;
			case 5: i += 5;
			default: i += 4;
		}
		printf("%d\n", i);
	}
}
```
*What is the output of the following C program fragment?*

**Conclusions :**
- as we know see every thing is great except we lose the "break" after each statement from the switch case so it will go through each one separately without sopping until it reach the numbers *16, 21*.
~ **So DON'T forget the BREAK after every case !!**



#practice

 