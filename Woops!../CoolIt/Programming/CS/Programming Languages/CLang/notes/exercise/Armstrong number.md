#### So What is an armstrong number?
An Armstrong number of *order n* is a number in which each digit when when multiplied by *n number of times* and finally added together, results the same number.

**Example :**
371 as a 3 digit number, therefore, its order is 3.

Now here each digit is multiplied by *itself 3 times* and finally added together and results on our original number i.e.

3 * 3 * 3 + 7 * 7 * 7+ 1 * 1 * 1 = 27 + 343 + 1 = 371

**So How to write a program which checks whether a number is an armstrong number or not ?**
Here are some steps to do it..

*Step #1 -* First find out, how many digits are there in you number
```C
Count = 0;

while (q != 0) {
	q /= 10;
	count++;
}
```
*now how this work*
- First we already know that by divided the number by 10 it gives us the number except the last digit.
- So *count* will count the number of operations that takes to finish the while loop.
- First of all it will divide the number let's take the number *371* as a sample, and will extract the *37* then it store it at *q*, then it repeat the same process with the new stored number now it's *37* so it will divided it to be *3* then it will store at *q* again the it will repeat the same process to be *0* as a final operation so now it *count* it 3 times so the number that we store from the begin is *3* digit number.

*step #2 -* Multiply each digit *n* times *in our example, n = 3* and add them together
```C
cnt = count, result = 0;

while (q != 0) {
	rem = q % 10;
	while (cnt != 0) {
		mul = mu * rem;
		cnt--;
	}
	result = result + mul;
	cnt = count;
	q /= 10;
	mul = 1
}
```
*in this program there is some steps we need to know*
- First we will take this part
```C
while (q != 0) {
	rem = q % 10;
	while (cnt != 0) {
		mul = mu * rem;
		cnt--;
	}
```
*in this part*
- We first divided *q* by *10* to extract the remainder digit
- then we check if the *cnt* is *not equal* to *0*, we have to know that tha *cnt* variable stores the *count* value which is *3* from previous equation!, so if it's *0* it come outside this loop. 
- inside the while loop that checks the condition we have the *mul* variable that has a value *mul * rem (remainder)*, so based on the condition it will multiply the remainder 3 times.
- and then we simply decrement the value by one with *cnt--* 
*SO THIS WHILE LOOP HELPS US TO MULTIPLY EACH DIGIT 3 TIMES*

- After this we will take this simple part
```C
result = result + mul;
	cnt = count;
	q /= 10;
	mul = 1
}
```
- in this simple part we store the output in the *result* variable.
- then we initialize again *cnt* with *count* .
- and then after that we divide *q* by *10*, so we will be able to store the quotient.
- and then we initialize *mul* by *1*.

*Step #3 -* Check whether the calculated result is equal to the actual number or not
```C
if (result == number) {
	printf("%d is an armstrong number.", number);
}else {
	printf("%d is not an armstrong number", number);
}
```


**Now here is the actual program :**
```C
#include <stdio.h>
int main() {
	int number, count = 0, result = 0, mul = 1, cnt, rem;
	printf("Please enter a number:);
	scanf("%d", &number);
	
	int q = number;
	while (q != 0) {
		q /= 10;
		cnt++;
	}
	cnt = count;
	q = number;
	
	while (q != 0) {
		rem = q % 10;
		while (cnt != 0) {
			num = mul * rem;
			cnt--;	
		}
		result = result + mul;
		cnt = count;
		q /= 10;
		mul = 1;
	}
	
	if (result == number) {
		printf("%d is an armstrong number", number);
	}else {
		printf("%d is not an armstrong number", number);
	}
}
```



#practice 