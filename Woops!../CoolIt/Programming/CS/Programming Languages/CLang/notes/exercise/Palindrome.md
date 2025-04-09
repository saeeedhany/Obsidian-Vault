#### what is palindrome?
A number or a word or a phrase if read backwards gives the same number or word or a phrase as it is being read forward.

##### Example : 
1221, racecar, 24542, etc..

##### *The idea :*
make last number the first number, 2nd last number the second number and so on.

that means you need to reverse the number and if the reversed number is equal to the actual number that we can say that the number is palindrome.
*so our central idea is to reverse the number*


##### *the main idea :*
**What happens when we module the number by 10?**
- When we module any number by 10 then the **remainder** that we get is always the last digit of that number, and the **quotient** that we get is always the number except the last digit.
##### Example : 
```
	456 -> remainder = 6
		   quotient = 45
```
*So this is the main concept to understand how the operation work*

**this is the code :**
```C
#include <stdio.h>

int num, reversed_num = 0, remainder, orig;

printf("Enter an integer num");
scanf("%d", &num);

orig = num;

if (num < 0) {
	printf("Please enter a positive value");
}

while (num != 0) {
	remainder = num % 10;
	reversed_num = reversed_num * 10 + remainder;
	num /= 10;
}

if (num == reversed_num) {
	printf("It's a palindrome number");
}else {
	printf("It's not a palindrome number");
}

```

**Explanation :**
- About This part 
```C
if (num < 0) {
	printf("Please enter a positive value");
}
```
in this part we check if the number is not equal to any negative number because there is no way for the palindrome number to be negative.

- Now here is the main part ..
```C
while (num != 0) {
	remainder = num % 10;
	reversed_num = reversed_num * 10 + remainder;
	num /= 10;
}
```
*In this particular part we go through a several stages*
- we first check if the number that we input is not equal to *ZERO*, if not?
- then we extract the remainder number by *module it by 10*. so if the number that we input is equal to *121*, the remainder will be *= 1*
- after that we we move the existing numbers to left to open a field to the new number by *reversed_num = reversed_num * 10 + remainder.* to be in this case at the first check *1*.
- then divide the number *num* by 10 by *num /= 10*.
- then it will repeat the same idea until it reach the number *ZERO* so the while loop will stop and by the if statement after it, it will check if its a [[Palindrome]] number or not.


#practice 